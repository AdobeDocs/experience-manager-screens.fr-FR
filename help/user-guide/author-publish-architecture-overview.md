---
title: Présentation de l’architecture de création et de publication
description: L’architecture d’AEM Screens ressemble à l’architecture classique d’AEM Sites. Le contenu est créé sur une instance d’auteur AEM puis répliqué vers plusieurs instances de publication.
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: 02929219a064e3b936440431e77e67e0bf511bf6
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 43%

---

# Présentation de l’architecture de création et de publication {#author-and-publish-architectural-overview}

Cette page met l’accent sur les sujets suivants :

* **Présentation des serveurs de publication**
* **Présentation de l’architecture**
* **Processus d’enregistrement**

## Prérequis {#prerequisites}

Avant de commencer avec les serveurs de création et de publication, vous devez connaître au préalable les éléments suivants :

* **Topologie AEM**
* **Création et gestion de projet AEM Screens**
* **Processus d’enregistrement d’appareil**

>[!NOTE]
>
>Cette fonctionnalité d’AEM Screens n’est disponible que si vous avez installé AEM 6.4 Screens Feature Pack 2. Pour accéder à ce Feature Pack, vous devez contacter l’assistance d’Adobe et demander à y accéder. Une fois que vous avez l’autorisation, téléchargez-la à partir de Package Share.

## Présentation {#introduction}

L’architecture d’AEM Screens ressemble à l’architecture classique d’AEM Sites. Le contenu est créé sur une instance de création AEM avant d’être répliqué sur plusieurs instances de publication. Les périphériques sur AEM Screens peuvent désormais se connecter à une batterie de publication AEM via l’équilibreur de charge. Plusieurs instances de publication AEM peuvent être ajoutées afin de continuer la mise à l’échelle la batterie de publication.

*Par exemple*, un auteur de contenu AEM Screens émet une commande sur le système de création pour un périphérique particulier. Cet appareil est configuré pour interagir avec une ferme de publication ou un auteur de contenu AEM Screens qui obtient des informations sur les appareils configurés pour interagir avec les fermes de publication.

Le diagramme suivant illustre l’environnement de création et l’environnement de publication.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Design architectural {#architectural-design}

Il existe cinq composants architecturaux qui facilitent cette solution :

* ***Réplication du contenu*** de l’auteur à la publication pour l’affichage par les appareils

* ***Reverse*** réplication de contenu binaire de l’environnement de publication (reçu des périphériques) vers l’environnement de création.
* ***Envoi*** des commandes de l’auteur à la publication via des API REST spécifiques.
* ***Messagerie*** entre les instances de publication pour synchroniser les commandes et les mises à jour des informations sur les périphériques.
* ***Interrogation*** par l’auteur des instances de publication pour obtenir des informations sur les périphériques via des API REST spécifiques.

### Réplication (transfert) du contenu et des configurations  {#replication-forward-of-content-and-configurations}

Les agents de réplication standard sont utilisés pour répliquer le contenu du canal AEM Screens, les configurations d’emplacement et les configurations de périphérique. Cela permet aux auteurs de mettre à jour le contenu d’un canal et, éventuellement, de passer par un processus d’approbation avant de publier les mises à jour du canal. Un agent de réplication doit être créé pour chaque instance de publication de la batterie de publication.

Le diagramme suivant illustre le processus de réplication :

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>Un agent de réplication doit être créé pour chaque instance de publication de la batterie de publication.

### Agents et commandes de réplication Screens  {#screens-replication-agents-and-commands}

Des agents de réplication spécifiques personnalisés Screens sont créés pour envoyer des commandes de l’instance Auteur à l’appareil AEM Screens. Les instances de publication AEM servent d’intermédiaire pour transférer ces commandes à l’appareil.

Cela permet aux auteurs de continuer à gérer l’appareil, par exemple d’envoyer des mises à jour à l’appareil et de prendre des captures d’écran à partir de l’environnement de création. Les agents de réplication AEM Screens ont une configuration de transport personnalisée, comme les agents de réplication standard.

### Messagerie entre les instances de publication  {#messaging-between-publish-instances}

Souvent, une commande n’est censée être envoyée qu’une seule fois à un appareil. Toutefois, dans une architecture de publication équilibrée en charge, on ignore à quelle instance de publication le périphérique se connecte.

Par conséquent, l’instance de création envoie le message à toutes les instances de publication. Cependant, seul un message unique doit être relayé à l’appareil. Pour garantir un message correct, la communication doit avoir lieu entre les instances de publication. Cela est réalisé en utilisant *Apache ActiveMQ Artemis*. Chaque instance de publication est placée dans une topologie à couplage faible à l’aide du service de découverte Sling basé sur Oak et ActiveMQ est configuré de sorte que chaque instance de publication puisse communiquer et créer une file de messages unique. Le périphérique AEM Screens interroge la ferme de publication AEM par le biais de l’équilibreur de charge et sélectionne la commande en haut de la file d’attente.

### Réplication inverse {#reverse-replication}

Souvent, suite à une commande, un type de réponse est attendu du périphérique Screens pour être transféré vers l’instance d’auteur. Pour réaliser cette AEM ***Réplication inverse*** est utilisée.

* Créez un agent de réplication inverse pour chaque instance de publication, semblable aux agents de réplication standard et aux agents de réplication AEM Screens.
* Une configuration de lanceur de workflow écoute les noeuds modifiés sur l’instance de publication AEM et déclenche à son tour un workflow pour placer la réponse de l’appareil dans la boîte d’envoi de l’instance de publication AEM.
* Dans ce contexte, une réplication inverse n’est utilisée que pour les données binaires (fichiers journaux et captures d’écran, par exemple) fournies par les appareils. Les données non binaires sont récupérées par interrogation.
* Le sondage de réplication inverse de l’instance d’auteur AEM récupère la réponse et l’enregistre dans l’instance d’auteur.

### Interrogation des instances de publication  {#polling-of-publish-instances}

L’instance d’auteur doit être en mesure d’interroger les appareils pour obtenir une pulsation et connaître l’état d’intégrité d’un appareil connecté.

Les appareils envoient un ping à l’équilibreur de charge et sont routés vers une instance de publication. L’état de l’appareil est ensuite révélé par l’instance de publication AEM via une API de publication diffusée à l’adresse **api/screens-dcc/devices/static** pour tous les périphériques actifs et **api/screens-dcc/devices/&lt;device_id>/status.json** pour un périphérique unique.

L’instance de création interroge toutes les instances de publication et fusionne les réponses d’état de l’appareil en un seul état. La tâche planifiée qui interroge l’auteur est `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` et peut être configurée en se basant sur une expression cron.

## Enregistrement {#registration}

L’enregistrement continue d’être généré sur l’instance de création AEM. L’appareil d’AEM Screens pointe vers l’instance de création et l’enregistrement est terminé.

Une fois qu’un appareil est enregistré dans l’environnement de création AEM, la configuration de l’appareil et les affectations de canal/planification sont répliquées sur les instances de publication AEM. La configuration de l’appareil AEM Screens est ensuite mise à jour afin de pointer vers l’équilibreur de charge situé en amont de la batterie de publication AEM. Il s’agit d’une configuration unique. Une fois que le périphérique Screens est connecté à l’environnement de publication, il peut continuer à recevoir des commandes provenant de l’environnement de création. Il ne doit jamais être nécessaire de connecter directement l’appareil AEM Screens à l’environnement de création AEM.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Étapes suivantes {#the-next-steps}

Une fois que vous avez compris la conception architecturale de la configuration de création et de publication dans AEM Screens, reportez-vous à la section [Configuration de la création et de la publication pour AEM Screens](author-and-publish.md) pour plus d’informations.

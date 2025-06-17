---
title: Vue d’ensemble de l’architecture de création et de publication
description: L’architecture d’AEM Screens ressemble à l’architecture classique d’AEM Sites. Le contenu est créé sur une instance de création AEM avant d’être répliqué sur plusieurs instances de publication.
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 96%

---

# Vue d’ensemble de l’architecture de création et de publication {#author-and-publish-architectural-overview}

Cette page met l’accent sur les sujets suivants :

* **Présentation des serveurs de publication**
* **Présentation de l’architecture**
* **Processus d’enregistrement**

## Conditions préalables {#prerequisites}

Avant de commencer avec les serveurs de création et de publication, vous devez connaître au préalable :

* **Topologie AEM**
* **Création et gestion de projet AEM Screens**
* **Processus d’enregistrement d’appareil**

>[!NOTE]
>
>Cette fonctionnalité AEM Screens n’est disponible que si vous avez installé le pack de fonctionnalités 2 pour AEM 6.4 Screens. Pour accéder à ce pack de fonctionnalités, contactez l’assistance d’Adobe et demandez à y accéder. Lorsque vous disposez de l’autorisation, téléchargez-la à partir de Partage de modules.

## Présentation {#introduction}

L’architecture d’AEM Screens ressemble à l’architecture classique d’AEM Sites. Le contenu est créé sur une instance de création AEM avant d’être répliqué sur plusieurs instances de publication. Les appareils sur AEM Screens peuvent désormais se connecter à une batterie de serveurs de publication AEM via la répartition de charge. Plusieurs instances de publication AEM peuvent être ajoutées afin de continuer la mise à l’échelle de la batterie de serveurs de publication.

*Par exemple*, un auteur ou une autrice de contenu AEM Screens émet une commande sur le système de création pour un appareil particulier. Ce périphérique est configuré pour interagir avec une batterie de publication. Ou pour interagir avec un auteur ou une autrice de contenu AEM Screens qui obtient des informations sur les appareils configurés pour interagir avec les batteries de publication.

Le diagramme suivant illustre l’environnement de création et l’environnement de publication.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Design architectural {#architectural-design}

Il existe cinq composants architecturaux qui facilitent cette solution :

* ***Réplication du contenu*** de l’instance de création à l’instance de publication pour l’affichage par les appareils

* Réplication ***inverse*** du contenu binaire de l’environnement de publication (reçu des appareils) vers l’environnement de création.
* ***Envoi*** de commandes de l’instance de création vers l’instance de publication via des API REST spécifiques.
* ***Messagerie*** entre les instances de publication pour synchroniser les commandes et les mises à jour des informations sur les appareils.
* ***Interrogation*** par l’auteur ou l’autrice des instances de publication pour obtenir des informations sur les appareils via des API REST spécifiques.

### Réplication (transfert) du contenu et des configurations {#replication-forward-of-content-and-configurations}

Les agents de réplication standard servent à répliquer le contenu du canal, les configurations d’emplacement et les configurations d’appareil AEM Screens. Cette fonctionnalité permet aux auteurs et autrices de mettre à jour le contenu d’un canal et, éventuellement, de passer par un processus d’approbation avant de publier les mises à jour du canal. Un agent de réplication doit être créé pour chaque instance de publication de la batterie de serveurs de publication.

Le diagramme suivant illustre le processus de réplication :

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>Un agent de réplication doit être créé pour chaque instance de publication de la batterie de serveurs de publication.

### Agents et commandes de réplication Screens {#screens-replication-agents-and-commands}

Des agents de réplication spécifiques personnalisés Screens sont créés pour envoyer des commandes de l’instance Auteur à l’appareil AEM Screens. Les instances de publication AEM servent d’intermédiaire pour transférer ces commandes à l’appareil.

Ce processus permet aux auteurs et autrices de continuer à gérer l’appareil, par exemple d’envoyer des mises à jour à l’appareil et de prendre des captures d’écran à partir de l’environnement de création. Les agents de réplication AEM Screens ont une configuration de transport personnalisée, comme les agents de réplication standard.

### Messagerie entre les instances de publication {#messaging-between-publish-instances}

Souvent, une commande n’est censée être envoyée à un appareil qu’une seule fois. Cependant, dans une architecture de publication avec équilibrage de charge, l’instance de publication à laquelle l’appareil se connecte est inconnue.

Par conséquent, l’instance de création envoie le message à toutes les instances de publication. Cependant, seul un message unique doit être relayé à l’appareil. Pour garantir un message correct, une communication doit avoir lieu entre les instances de publication. Cette communication est réalisée en utilisant *Apache ActiveMQ Artemis*. Chaque instance de publication est placée dans une topologie à couplage faible à l’aide du service de découverte Sling basé sur Oak. ActiveMQ est configuré de sorte que chaque instance de publication puisse communiquer et créer une file de messages unique. L’appareil AEM Screens interroge la batterie de serveurs de publication AEM via la répartition de charge et sélectionne la commande qui se trouve au sommet de la file.

### Réplication inverse {#reverse-replication}

Dans de nombreux cas, après une commande, on attend une certaine réponse de la part de l’appareil Screens, qui sera transmise à l’instance de création. Pour ce faire, on a recours à la ***réplication inverse*** AEM.

* Créez un agent de réplication inverse pour chaque instance de publication, semblable aux agents de réplication standard et aux agents de réplication Screens.
* Une configuration de lanceur de workflow écoute les nœuds modifiés sur l’instance de publication AEM et déclenche à son tour un workflow pour placer la réponse de l’appareil dans la boîte d’envoi de l’instance de publication.
* Dans ce contexte, une réplication inverse n’est utilisée que pour les données binaires (fichiers journaux et captures d’écran, par exemple) fournies par les appareils. L’interrogation des données non binaires est récupérée.
* La réplication inverse interrogée à partir de l’instance de création AEM récupère la réponse et l’enregistre dans l’instance de création.

### Interrogation des instances de publication {#polling-of-publish-instances}

L’instance de création doit pouvoir interroger les appareils pour obtenir une pulsation et connaître le statut d’intégrité d’un appareil connecté.

Les appareils envoient un ping à l’équilibreur de charge et sont routés vers une instance de publication. Le statut de l’appareil est ensuite révélé par l’instance de publication AEM via une API de publication diffusée à l’adresse **api/screens-dcc/devices/static** pour tous les appareils actifs et **api/screens-dcc/devices/&lt;device_id>/status.json** pour un appareil unique.

L’instance de création interroge toutes les instances de publication et fusionne les réponses d’état de l’appareil en un seul état. La tâche planifiée qui interroge l’auteur est `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` et peut être configurée en se basant sur une expression cron.

## Enregistrement {#registration}

L’enregistrement continue d’être généré sur l’instance de création AEM. L’appareil AEM Screens pointe vers l’instance de création et l’enregistrement est terminé.

Une fois qu’un appareil a été enregistré dans l’environnement de création, la configuration de l’appareil et les affectations de canal/planning sont répliquées dans les instances de publication AEM. La configuration de l’appareil AEM Screens est ensuite mise à jour afin de pointer vers la répartition de charge situé en amont de la batterie de serveurs de publication AEM. Cet arrangement est destiné à être configuré une seule fois. Une fois que l’appareil Screens est connecté à l’environnement de publication, il peut continuer à recevoir des commandes provenant de l’environnement de création. Il ne devrait pas être nécessaire de connecter directement l’appareil AEM Screens à l’environnement de création AEM.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Étapes suivantes {#the-next-steps}

Lorsque vous avez compris la conception architecturale de la configuration de création et de publication dans AEM Screens, reportez-vous à la section [Configurer des instances de création et de publication pour AEM Screens](author-and-publish.md) afin d’en savoir plus.

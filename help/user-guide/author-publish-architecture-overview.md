---
title: Présentation de l’architecture Auteur et Publication
seo-title: Présentation de l’architecture Auteur et Publication
description: L’architecture des écrans AEM ressemble à une architecture traditionnelle des sites AEM. Le contenu est créé sur une instance d’auteur AEM, puis répliqué par la suite sur plusieurs instances de publication. Suivez cette page pour en savoir plus sur l'architecture de création et de publication.
seo-description: L’architecture des écrans AEM ressemble à une architecture traditionnelle des sites AEM. Le contenu est créé sur une instance d’auteur AEM, puis répliqué par la suite sur plusieurs instances de publication. Suivez cette page pour en savoir plus sur l'architecture de création et de publication.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Présentation de l’architecture Auteur et Publication {#author-and-publish-architectural-overview}

Cette page aborde les sujets suivants :

* **Présentation des serveurs de publication**
* **Présentation architecturale**
* **Processus d'enregistrement**

## Conditions préalables {#prerequisites}

Avant de vous familiariser avec les serveurs d’auteur et de publication, vous devez connaître au préalable :

* **Topologie AEM**
* **Création et gestion du projet AEM Screens**
* **Processus d'enregistrement de périphérique**

>[!NOTE]
>
>Cette fonctionnalité d’AEM Screens n’est disponible que si vous avez installé AEM 6.4 Screens Feature Pack 2. Pour accéder à ce Feature Pack, vous devez contacter l’assistance d’Adobe et demander à y accéder. Une fois que vous disposez des autorisations, vous pouvez le télécharger à partir de Package Share.

## Présentation {#introduction}

L’architecture des écrans AEM ressemble à une architecture traditionnelle des sites AEM. Le contenu est créé sur une instance d’auteur AEM, puis répliqué par la suite sur plusieurs instances de publication. Les périphériques AEM Screens peuvent désormais se connecter à une batterie de publication AEM via l’équilibreur de charge. Plusieurs instances de publication AEM peuvent être ajoutées pour continuer à mettre à l’échelle la batterie de publication.

*Par exemple*, un auteur de contenu AEM Screens émet une commande sur le système de création pour un périphérique particulier configuré pour interagir avec une batterie de publication ou un auteur de contenu AEM Screens qui obtient des informations sur les périphériques configurés pour interagir avec les fermes de publication.

Le diagramme suivant illustre les environnements de création et de publication.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Design architectural {#architectural-design}

Il existe cinq composants architecturaux qui facilitent cette solution :

* ***Réplication du contenu*** de l’auteur à la publication pour l’affichage par les périphériques

* ***Inverser*** la réplication du contenu binaire de la publication (reçu des périphériques) à l’auteur
* ***Envoi*** de commandes de l’auteur à la publication via des API REST spécifiques
* ***Messagerie*** entre les instances de publication pour synchroniser les commandes et les mises à jour des informations sur les périphériques
* ***Sondage effectué*** par l’auteur des instances de publication pour obtenir des informations sur les périphériques via des API REST spécifiques

### Réplication (transfert) du contenu et des configurations {#replication-forward-of-content-and-configurations}

Les agents de réplication standard sont utilisés pour répliquer le contenu du canal d’écran, les configurations d’emplacement et les configurations de périphérique. Cela permet aux auteurs de mettre à jour le contenu d’un canal et, éventuellement, de passer par un processus d’approbation avant de publier les mises à jour du canal. Un agent de réplication doit être créé pour chaque instance de publication de la batterie de publication.

Le diagramme suivant illustre le processus de réplication :

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>Un agent de réplication doit être créé pour chaque instance de publication de la batterie de publication.

### Agents et commandes de réplication d’écrans {#screens-replication-agents-and-commands}

Les agents de réplication spécifiques aux écrans personnalisés sont créés pour envoyer des commandes de l’instance d’auteur au périphérique AEM Screens. Les instances de publication AEM servent d’intermédiaire pour transférer ces commandes au périphérique.

Cela permet aux auteurs de continuer à gérer le périphérique, par exemple, d’envoyer les mises à jour du périphérique et de prendre des captures d’écran à partir de l’environnement de création. Les agents de réplication AEM Screens ont une configuration de transport personnalisée, comme les agents de réplication standard.

### Messagerie entre les instances de publication {#messaging-between-publish-instances}

Dans de nombreux cas, une commande n'est censée être envoyée à un périphérique qu'une seule fois. Toutefois, dans une architecture de publication équilibrée en charge, on ignore à quelle instance de publication le périphérique se connecte.

Par conséquent, l’instance d’auteur envoie le message à toutes les instances de publication. Cependant, seul un message unique doit être relayé au périphérique. Pour garantir un message correct, une communication doit avoir lieu entre les instances de publication. Ceci est réalisé en utilisant *Apache ActiveMQ Artémis. *Chaque instance de publication est placée dans une stratégie couplée de manière approximative à l’aide du service de découverte Sling basé sur Oak et ActiveMQ est configuré de sorte que chaque instance de publication puisse communiquer et créer une file d’attente de messages unique. Le périphérique Screens sonde la batterie de publication via l’équilibreur de charge et sélectionne la commande en haut de la file d’attente.

### Réplication inverse {#reverse-replication}

Dans de nombreux cas, après une commande, une sorte de réponse du périphérique Screens est attendue pour être transmise à l’instance d’auteur. Pour ce faire, la réplication ****** inverse AEM est utilisée.

* Créez un agent de réplication inverse pour chaque instance de publication, semblable aux agents de réplication standard et aux agents de réplication d’écrans.
* Une configuration de lanceur de processus écoute les noeuds modifiés à l’instance de publication et déclenche à son tour un flux de travail pour placer la réponse du périphérique dans la boîte d’envoi de l’instance de publication.
* Dans ce contexte, une réplication inversée n’est utilisée que pour les données binaires (fichiers journaux et captures d’écran, par exemple) fournies par les périphériques. Les données non binaires sont récupérées par l’interrogation.
* La réplication inversée interrogée à partir de l’instance d’auteur AEM récupère la réponse et l’enregistre dans l’instance d’auteur.

### Sondage des instances de publication {#polling-of-publish-instances}

L’instance d’auteur doit pouvoir interroger les périphériques pour obtenir une pulsation et connaître l’état d’intégrité d’un périphérique connecté.

Périphériques qui effectuent un test d’équilibrage de charge et sont acheminés vers une instance de publication. L’état du périphérique est ensuite révélé par l’instance de publication via une API de publication diffusée à l’adresse **api/screens-dcc/devices/stati** pour tous les périphériques actifs et **api/screens-dcc/devices/&lt;device_id&gt;/status.json** pour un périphérique unique.

L’instance d’auteur interroge toutes les instances de publication et fusionne les réponses d’état du périphérique en un seul état. La tâche planifiée qui effectue un sondage sur l’auteur est `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` et peut être configurée en fonction d’une expression cron.

## de Magento {#registration}

L’enregistrement continue d’être généré sur l’instance d’auteur AEM. Le périphérique des écrans AEM pointe vers l’instance d’auteur et l’enregistrement est terminé.

Une fois qu’un périphérique a été enregistré dans l’environnement de création, la configuration du périphérique et les affectations de canal/planification sont répliquées dans les instances de publication AEM. La configuration du périphérique AEM Screens est ensuite mise à jour afin de pointer vers l’équilibreur de charge situé devant la batterie de publication AEM. Il s’agit d’une configuration unique, une fois que le périphérique d’écran est connecté à l’environnement de publication, il peut continuer à recevoir des commandes provenant de l’environnement d’auteur et il n’est pas nécessaire de connecter directement le périphérique d’écran à l’environnement d’auteur.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Étapes suivantes {#the-next-steps}

Une fois que vous avez compris la conception architecturale de la configuration de l’auteur et de la publication dans les écrans AEM, reportez-vous à la section [Configuration de l’auteur et de la publication pour les écrans](author-and-publish.md) AEM pour plus d’informations.

---
title: Dépannage du Centre de contrôle des appareils
seo-title: Monitoring Screens
description: Consultez cette page afin de surveiller les performances de votre lecteur Screens et de votre appareil, et de dépanner les problèmes connexes à l’aide du tableau de bord de l’appareil.
seo-description: Follow this page to monitor and troubleshoot performance for your Screens player activity and device usingtheDevice dashboard.
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 79%

---

# Dépannage du Centre de contrôle des appareils {#troubleshooting-device-control-center}

Vous pouvez surveiller les performances et résoudre les problèmes associés pour l’activité de votre lecteur Screens et l’appareil de lecture à l’aide du tableau de bord de l’appareil. Cette page fournit des informations sur la façon de surveiller et de résoudre les problèmes de performances perçus pour le lecteur Screens et les appareils attribués.

## Surveillance et dépannage à partir du centre de contrôle des appareils {#monitor-and-troubleshoot-from-device-control-center}

Vous pouvez surveiller l’activité et ainsi résoudre les problèmes liés à votre lecteur Screens, à l’aide du tableau de bord de l’appareil.

### Tableau de bord du périphérique {#device-dashboard}

Suivez les étapes ci-dessous pour accéder au tableau de bord de l’appareil :

1. Accédez au tableau de bord du périphérique à partir de votre projet, par exemple : ***Test du projet*** > ***Périphériques***.

   Sélectionnez **Appareils** et **Gestionnaire d’appareils** dans la barre d’actions.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. La liste affiche les appareils affectés et non affectés, comme illustré ci-dessous.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Sélectionnez l’appareil (**NewTestDevice**) et cliquez sur **Tableau de bord** dans la barre d’actions.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. La page affiche les informations sur l’appareil, son activité et les détails le concernant pour vous permettre de surveiller les activités et les fonctions de l’appareil.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Surveillance de l’activité du périphérique {#monitor-device-activity}

Le panneau **Activité** affiche le dernier ping de votre lecteur Screens avec l’horodatage. Le dernier ping correspond à la dernière fois où l’appareil a contacté le serveur.

![chlimage_1](assets/chlimage_1.png)

En outre, cliquez sur **Collecter les journaux** dans le coin supérieur droit du panneau **Activité** afin de consulter les journaux pour votre lecteur.

### Mettre à jour les détails du périphérique {#update-device-details}

Consultez le panneau **Détails de l’appareil** pour afficher l’adresse IP de l’appareil, l’utilisation du stockage, la version du micrologiciel et le temps de disponibilité de votre appareil.

![chlimage_1-1](assets/chlimage_1-1.png)

Cliquez également sur **Effacer le cache** et **Mettre à jour** pour effacer le cache de votre appareil et mettre à jour la version du [micrologiciel](screens-glossary.md), respectivement, à partir de ce panneau.

Vous pouvez également cliquer sur les points de suspension **…** dans le coin supérieur droit du panneau **Détails de l’appareil** afin de redémarrer ou de rafraîchir l’état de votre lecteur.

![chlimage_1-2](assets/chlimage_1-2.png)

### Mise à jour des informations sur le périphérique {#update-device-information}

Consultez le panneau **INFORMATIONS SUR L’APPAREIL** pour afficher la mise à jour de configuration, le modèle du périphérique, le système d’exploitation du périphérique et les informations sur le shell.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Cliquez également sur les points de suspension (**…**) dans le coin supérieur droit du panneau Informations sur l’appareil pour afficher le panneau des propriétés ou mettre à jour l’appareil.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Cliquez sur **Propriétés** pour afficher la boîte de dialogue **Propriétés de l’appareil**. Vous pouvez modifier le titre de l’appareil ou sélectionner l’option **manuelle** ou **automatique** pour les mises à jour de configuration.

>[!NOTE]
>
>Pour plus d’informations sur les événements liés aux mises à jour automatiques ou manuelles d’un appareil, voir la section ***Mises à jour automatiques ou manuelles depuis le tableau de bord de l’appareil*** dans [Gestion des canaux](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Affichage d’une capture d’écran du lecteur {#view-player-screenshot}

Vous pouvez afficher la capture d’écran d’un lecteur à partir de l’appareil dans le panneau **CAPTURE D’ÉCRAN DU LECTEUR**.

Cliquez sur les points de suspension (**…**) dans le coin supérieur droit du panneau Capture d’écran du lecteur et sélectionnez **Actualiser la capture d’écran** pour afficher l’instantané du lecteur en cours d’exécution.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Gestion des préférences {#manage-preferences}

Le panneau **PRÉFÉRENCES** permet à l’utilisateur de modifier les préférences de l’**interface utilisateur d’administration**, du **sélecteur de canal** et du **débogage à distance** pour l’appareil.

>[!NOTE]
>Pour plus d’informations sur ces options, voir [Lecteur AEM Screens](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

De plus, cliquez sur **Paramètres** dans le coin supérieur droit pour mettre à jour les préférences de l’appareil. Vous pouvez mettre à jour les préférences suivantes :

* **URL du serveur**
* **Résolution**
* **Redémarrer la planification**
* **Nombre max. de fichiers journaux à conserver**.
* **Niveau de journal**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>Vous pouvez sélectionner l’un des niveaux de journal suivants :
>* **Désactiver**
>* **Déboguer**
>* **Infos**
>* **Avertissement**
>* **Erreur**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Dépannage des paramètres OSGi {#troubleshoot-osgi-settings}

Vous devez activer le référent vide pour autoriser l’appareil à publier des données sur le serveur. Par exemple, si la propriété de référent vide est désactivée, l’appareil ne pourra pas publier de capture d’écran.

Actuellement, certaines de ces fonctions ne sont disponibles que si l’option *Allow Empty d’Apache Sling Referrer Filter* est activée dans la configuration OSGi. Le tableau de bord peut afficher un avertissement indiquant que les paramètres de sécurité peuvent empêcher l’utilisation de certaines de ces fonctions.

Pour activer l’option Allow Empty d’Apache Sling Referrer Filter

1. Accédez à **Configuration de la console web Adobe Experience Manager**, à savoir `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Cochez l’option **allow.empty**.
1. Cliquez sur **Enregistrer**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Recommandations {#recommendations}

La section suivante recommande de surveiller les liens réseau, le serveur et les lecteurs afin de comprendre l’état de santé et de réagir aux problèmes.

AEM fournit une surveillance intégrée pour :

* *Heartbeat* toutes les 5 secondes pour indiquer que le lecteur AEM Screens est en cours d’utilisation.
* *Capture d’écran* du lecteur qui affiche ce qui s’affiche actuellement sur le lecteur.
* La variable *Micrologiciel du lecteur AEM Screens* version installée sur le lecteur.
* *Espace de stockage libre* sur le lecteur.

Recommendations pour la surveillance à distance avec des logiciels tiers :

* Utilisation du processeur sur les lecteurs.
* Vérifiez si le processus du lecteur AEM Screens est exécuté.
* Redémarrez/redémarrez à distance le lecteur.
* Notifications en temps réel.

Il est recommandé de déployer le matériel et le système d’exploitation du lecteur de manière à permettre une connexion distante afin de diagnostiquer les problèmes et de redémarrer le lecteur.

#### Ressources supplémentaires {#additional-resources}

Voir [Configuration et dépannage de la lecture vidéo](troubleshoot-videos.md) pour déboguer et dépanner les vidéos lues sur votre canal.

---
title: Résolution de problèmes dans le Centre de contrôle des périphériques
description: Découvrez comment surveiller les performances et résoudre les problèmes de l’activité de votre lecteur AEM Screens et du périphérique de lecture à l’aide du tableau de bord du périphérique.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 100%

---

# Résolution de problèmes dans le Centre de contrôle des périphériques {#troubleshooting-device-control-center}

Vous pouvez surveiller les performances et résoudre les problèmes concernant l’activité de votre lecteur AEM Screens et le périphérique de lecture à l’aide du tableau de bord du périphérique. Cette page fournit des informations sur la façon de surveiller et de résoudre les problèmes de performances perçus pour le lecteur Screens et les appareils attribués.

## Surveillance et dépannage à partir du centre de contrôle des appareils {#monitor-and-troubleshoot-from-device-control-center}

Vous pouvez surveiller l’activité et ainsi résoudre les problèmes concernant votre lecteur AEM Screens, à l’aide du tableau de bord du périphérique.

### Tableau de bord de l’appareil {#device-dashboard}

Pour accéder au tableau de bord de l’appareil, procédez comme suit :

1. Accédez au tableau de bord de l’appareil à partir de votre projet, par exemple, ***Projet de test*** > ***Appareils***.

   Cliquez sur **Périphériques** et sur **Gestionnaire de périphériques** dans la barre d’actions.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. La liste affiche les appareils affectés et non affectés, comme illustré ci-dessous.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Cliquez sur le périphérique (**NewTestDevice**) et cliquez sur **Tableau de bord** dans la barre d’actions.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. La page affiche les informations sur l’appareil, son activité et les détails le concernant pour vous permettre de surveiller les activités et les fonctions de l’appareil.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Surveillance de l’activité de l’appareil {#monitor-device-activity}

Le panneau **Activité** affiche le dernier ping de votre lecteur AEM Screens avec la date et l’heure. Le dernier ping correspond à la dernière fois où l’appareil a contacté le serveur.

![chlimage_1](assets/chlimage_1.png)

Cliquez également sur **Collecter les journaux** dans le coin supérieur droit du panneau **Activité** afin de consulter les journaux de votre lecteur.

### Mise à jour des détails d’un appareil {#update-device-details}

Consultez le panneau **Détails de l’appareil** pour pouvoir afficher l’adresse IP de l’appareil, l’utilisation du stockage, la version du micrologiciel et le temps de disponibilité du lecteur de votre appareil.

![chlimage_1-1](assets/chlimage_1-1.png)

Cliquez également sur **Effacer le cache** et **Mettre à jour** pour respectivement effacer le cache de votre appareil et mettre à jour la version du [micrologiciel](screens-glossary.md) à partir de ce panneau.

Cliquez également sur les points de suspension **...** dans le coin supérieur droit du panneau **Détails du périphérique** pour redémarrer ou actualiser le statut de votre lecteur.

![chlimage_1-2](assets/chlimage_1-2.png)

### Mise à jour des informations sur un appareil {#update-device-information}

Consultez le panneau **INFORMATIONS SUR L’APPAREIL**. Vous pouvez afficher ici la mise à jour de configuration, le modèle de l’appareil, le système d’exploitation de l’appareil et les informations sur le shell.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Cliquez également sur les points de suspension (**...**) dans le coin supérieur droit du panneau Informations sur l’appareil pour afficher les propriétés ou mettre à jour l’appareil.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Cliquez sur **Propriétés** pour afficher la boîte de dialogue **Propriétés de l’appareil**. Vous pouvez modifier le titre de l’appareil ou sélectionner l’option **manuelle** ou **automatique** pour les mises à jour de configuration.

>[!NOTE]
>
>Pour plus d’informations sur les événements liés aux mises à jour automatiques ou manuelles d’un appareil, voir la section ***Mises à jour automatiques ou manuelles depuis le tableau de bord de l’appareil*** dans [Gestion des canaux](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Affichage d’une capture d’écran du lecteur {#view-player-screenshot}

Vous pouvez afficher la capture d’écran d’un lecteur à partir de l’appareil dans le panneau **CAPTURE D’ÉCRAN DU LECTEUR**.

Cliquez sur les points de suspension (**...**) dans le coin supérieur droit du panneau Capture d’écran du lecteur, puis cliquez sur **Actualiser la capture d’écran** pour afficher l’instantané du lecteur en cours d’exécution.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Gestion des préférences {#manage-preferences}

Le panneau **PRÉFÉRENCES** permet à l’utilisateur ou l’utilisatrice de modifier les préférences de l’**interface utilisateur d’administration**, du **sélecteur de canal** et du **débogage à distance** pour l’appareil.

>[!NOTE]
>Pour en savoir plus sur ces options, voir [Lecteur AEM Screens](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Cliquez également sur **Paramètres** dans le coin supérieur droit pour mettre à jour les préférences de l’appareil. Vous pouvez mettre à jour les préférences suivantes :

* **URL du serveur**
* **Résolution**
* **Redémarrer la planification**
* **Nombre max. de fichiers journaux à conserver**.
* **Niveau de journal**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>Vous pouvez cliquer sur l’un des niveaux de journal suivants :
>* **Désactiver**
>* **Déboguer**
>* **Infos**
>* **Avertissement**
>* **Erreur**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Résolution des incidents des paramètres d’OSGi {#troubleshoot-osgi-settings}

Activez le référent vide pour autoriser l’appareil à publier des données sur le serveur. Par exemple, si la propriété de référent vide est désactivée, l’appareil ne pourra pas publier de capture d’écran.

Actuellement, certaines de ces fonctions ne sont disponibles que si l’option *Allow Empty d’Apache Sling Referrer Filter* est activée dans la configuration OSGi. Le tableau de bord peut afficher un avertissement indiquant que les paramètres de sécurité peuvent empêcher l’utilisation de certaines de ces fonctions.

Pour activer l’option Autoriser un filtre de référent vide d’Apache Sling, procédez comme suit :

1. Accédez à **Configuration de la console web Adobe Experience Manager**, à savoir `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Cochez l’option **allow.empty**.
1. Cliquez sur **Enregistrer**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Recommandations {#recommendations}

La section suivante recommande de surveiller les liens réseau, les serveurs et les lecteurs afin de comprendre l’intégrité et de réagir aux problèmes.

AEM fournit une surveillance intégrée pour :

* *Pulsation* toutes les 5 secondes pour indiquer que le lecteur AEM Screens est en cours de fonctionnement.
* *Copie d’écran* du lecteur qui affiche ce qui s’affiche sur le lecteur.
* Version du *micrologiciel du lecteur AEM Screens* installée sur le lecteur.
* *Espace de stockage libre* sur le lecteur.

Recommandations pour la surveillance à distance avec des logiciels tiers :

* Utilisation du processeur dans les lecteurs.
* Vérifiez si le processus du lecteur AEM Screens est exécuté.
* Redémarrage à distance du lecteur.
* Notifications en temps réel.

Il est recommandé de déployer le matériel et le système d’exploitation du lecteur de manière à permettre une connexion distante afin de diagnostiquer les problèmes et de redémarrer le lecteur.

#### Autres ressources {#additional-resources}

Voir [Configuration et dépannage de la lecture vidéo](troubleshoot-videos.md) pour déboguer et dépanner les vidéos lues sur votre canal.

---
title: Dépannage du Centre de contrôle des appareils
description: Découvrez comment surveiller les performances de votre lecteur AEM Screens et de votre périphérique et résoudre les problèmes qui s’y rattachent à l’aide du tableau de bord du périphérique.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 38%

---

# Dépannage du Centre de contrôle des appareils {#troubleshooting-device-control-center}

Vous pouvez surveiller les performances de votre lecteur AEM Screens et de votre périphérique et résoudre les problèmes qui s’y rattachent à l’aide du tableau de bord du périphérique. Cette page fournit des informations sur la façon de surveiller et de résoudre les problèmes de performances perçus pour le lecteur Screens et les appareils attribués.

## Surveillance et dépannage à partir du centre de contrôle des appareils {#monitor-and-troubleshoot-from-device-control-center}

Vous pouvez surveiller l’activité et donc dépanner votre lecteur AEM Screens, à l’aide du tableau de bord de l’appareil.

### Tableau de bord du périphérique {#device-dashboard}

Suivez les étapes ci-dessous pour accéder au tableau de bord de l’appareil :

1. Accédez au tableau de bord du périphérique à partir de votre projet, par exemple, ***Tester le projet*** > ***Périphériques***.

   Sélectionnez **Appareils** et **Gestionnaire d’appareils** dans la barre d’actions.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. La liste affiche les appareils affectés et non affectés, comme illustré ci-dessous.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Sélectionnez le périphérique (**NewTestDevice**) et sélectionnez **Tableau de bord** dans la barre d’actions.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. La page affiche les informations sur l’appareil, l’activité et les détails de l’appareil qui vous permettent de surveiller les activités et les fonctions de l’appareil.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Surveillance de l’activité du périphérique {#monitor-device-activity}

Le **panneau Activité** affiche le dernier ping de votre lecteur AEM Screens avec l’horodatage. Le dernier ping correspond à la dernière fois où le périphérique a contacté le serveur.

![chlimage_1](assets/chlimage_1.png)

**Sélectionnez également Collecter les** journaux dans le coin supérieur droit du panneau Activité **** pour afficher les journaux de votre lecteur.

### Mettre à jour les détails du périphérique {#update-device-details}

Vérifiez les **Détails du périphérique** pour afficher l’adresse IP du périphérique, l’utilisation du stockage, la version du micrologiciel et le temps de disponibilité de votre périphérique.

![chlimage_1-1](assets/chlimage_1-1.png)

Sélectionnez également **Effacer le cache** et **Mettre à jour** pour effacer le cache de votre appareil et mettre à jour la variable [micrologiciel](screens-glossary.md) version de ce panneau, respectivement.

Sélectionnez également **..** dans le coin supérieur droit du **Détails du périphérique** pour redémarrer ou actualiser l’état de votre lecteur.

![chlimage_1-2](assets/chlimage_1-2.png)

### Mise à jour des informations sur un périphérique {#update-device-information}

Vérifiez le panneau INFORMATIONS SUR **LE** PÉRIPHÉRIQUE. Ici, vous pouvez afficher la mise à jour de configuration, le modèle d’appareil, le système d’exploitation de l’appareil et les informations shell.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Sélectionnez également (**...**) dans le coin supérieur droit du panneau Informations sur le périphérique pour afficher les propriétés ou mettre à jour le périphérique.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Sélectionnez **Propriétés** pour afficher la boîte de dialogue Propriétés **du** périphérique. Vous pouvez modifier le titre de l’appareil ou sélectionner l’option **manuelle** ou **automatique** pour les mises à jour de configuration.

>[!NOTE]
>
>Pour plus d’informations sur les événements liés aux mises à jour automatiques ou manuelles d’un appareil, voir la section ***Mises à jour automatiques ou manuelles depuis le tableau de bord de l’appareil*** dans [Gestion des canaux](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Affichage d’une capture d’écran du lecteur {#view-player-screenshot}

Vous pouvez afficher la capture d’écran d’un lecteur à partir de l’appareil dans le panneau **CAPTURE D’ÉCRAN DU LECTEUR**.

Sélectionnez (**...**) dans le coin supérieur droit du panneau Capture d’écran du lecteur et sélectionnez **Actualiser la capture d’écran** pour afficher l’instantané du lecteur en cours d’exécution.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Gestion des préférences {#manage-preferences}

Le panneau **PRÉFÉRENCES** permet à l’utilisateur de modifier les préférences de l’**interface utilisateur d’administration**, du **sélecteur de canal** et du **débogage à distance** pour l’appareil.

>[!NOTE]
>Pour en savoir plus sur ces options, voir [AEM Screens lecteur](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Sélectionnez également **Paramètres** dans le coin supérieur droit pour mettre à jour les préférences du périphérique. Vous pouvez mettre à jour les préférences suivantes :

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

## Résolution des incidents des paramètres OSGi {#troubleshoot-osgi-settings}

Activez le référent vide pour permettre à l’appareil de publier des données sur le serveur. Par exemple, si la propriété de référent vide est désactivée, l’appareil ne pourra pas publier de capture d’écran.

Actuellement, certaines de ces fonctions ne sont disponibles que si l’option *Allow Empty d’Apache Sling Referrer Filter* est activée dans la configuration OSGi. Le tableau de bord peut afficher un avertissement indiquant que les paramètres de sécurité peuvent empêcher l’utilisation de certaines de ces fonctions.

Pour activer l’option Allow Empty d’Apache Sling Referrer Filter

1. Accédez à **Configuration de la console web Adobe Experience Manager**, à savoir `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Cochez l’option **allow.empty**.
1. Sélectionnez **Enregistrer**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Recommandations {#recommendations}

La section suivante recommande de surveiller les liens réseau, les serveurs et les lecteurs pour comprendre l’intégrité et réagir aux problèmes.

AEM offre une surveillance intégrée avec les fonctions suivantes :

* *Heartbeat* toutes les 5 secondes pour indiquer que le lecteur AEM Screens est en cours de fonctionnement.
* *Capture d’écran* du lecteur qui affiche ce qui s’affiche sur le lecteur.
* La variable *Micrologiciel du lecteur AEM Screens* version installée sur le lecteur.
* *Espace de stockage libre* sur le lecteur.

Recommendations pour la surveillance à distance avec des logiciels tiers :

* Utilisation de l’unité centrale sur les lecteurs.
* Vérifiez si le processus du lecteur AEM Screens est exécuté.
* Redémarrez/réinitialisez le lecteur à distance.
* Notifications en temps réel.

Il est recommandé de déployer le matériel et le système d’exploitation du Lecteur de manière à permettre la connexion à distance pour diagnostiquer les problèmes et redémarrer le Lecteur.

#### Autres ressources {#additional-resources}

Voir [Configuration et dépannage de la lecture vidéo](troubleshoot-videos.md) si vous souhaitez déboguer et résoudre les problèmes liés à la lecture de vidéos dans votre canal.

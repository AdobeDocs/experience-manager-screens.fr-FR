---
title: Dépannage du Centre de contrôle des périphériques
seo-title: Surveillance de Screens
description: Suivez cette page pour surveiller et dépanner les performances de l’activité du lecteur d’écran et du périphérique à l’aide du tableau de bord du périphérique.
seo-description: Suivez cette page pour surveiller et dépanner les performances de l’activité du lecteur d’écran et du périphérique à l’aide du tableau de bord du périphérique.
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Dépannage du Centre de contrôle des périphériques {#troubleshooting-device-control-center}

Vous pouvez surveiller et dépanner les performances de votre lecteur d’écran et de votre périphérique à l’aide du tableau de bord du périphérique. Cette page fournit des informations sur la façon de surveiller et de résoudre les problèmes de performances perçus pour le lecteur Screens et les périphériques attribués.

## Surveillance et dépannage à partir du centre de contrôle des périphériques {#monitor-and-troubleshoot-from-device-control-center}

Vous pouvez surveiller l’activité et, par conséquent, dépanner votre lecteur d’écrans, à l’aide du tableau de bord du périphérique.

### Tableau de bord du périphérique {#device-dashboard}

Suivez les étapes ci-dessous pour accéder au tableau de bord du périphérique :

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --&gt; ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. La liste affiche les périphériques affectés et non attribués, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Sélectionnez le périphérique (**NewTestDevice**) et cliquez sur **Tableau de bord** dans la barre d'actions.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. La page affiche les informations sur le périphérique, son activité et les détails le concernant pour vous permettre de surveiller les activités et les fonctions de périphérique.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Surveillance de l’activité du périphérique {#monitor-device-activity}

Le panneau **Activité** affiche le dernier ping de votre lecteur Screens avec l’horodatage. Le dernier ping correspond à la dernière fois où le périphérique a contacté le serveur.

![chlimage_1](assets/chlimage_1.png)

Additionally, click **Collect Logs** from the top right hand corner of the **Activity** panel to view the logs for your player.

### Mise à jour des détails d’un périphérique {#update-device-details}

Consultez le panneau **Détails du périphérique** pour afficher l’adresse IP du périphérique, l’utilisation du stockage, la version du micrologiciel et le temps de disponibilité de votre périphérique.

![chlimage_1-1](assets/chlimage_1-1.png)

En outre, cliquez sur **Effacer le cache** et **Mettre à jour** pour effacer le cache de votre périphérique et mettre à jour la version du [micrologiciel](screens-glossary.md), respectivement, à partir de ce panneau.

Vous pouvez également cliquer sur les points de suspension **…** dans le coin supérieur droit du panneau **Détails du périphérique** afin de redémarrer ou de rafraîchir l’état de votre lecteur.

![chlimage_1-2](assets/chlimage_1-2.png)

### Mise à jour des informations sur un périphérique {#update-device-information}

Consultez le panneau INFORMATIONS **SUR LE** PÉRIPHÉRIQUE pour afficher la mise à jour de configuration, le modèle de périphérique, le système d’exploitation du périphérique et les informations sur le shell.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Additionally, click the (**...**) from the top right corner of the Device Information panel to view properties or update the device.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Cliquez sur **Propriétés** pour afficher la boîte de dialogue **Propriétés du périphérique**. Vous pouvez modifier le titre du périphérique ou sélectionner l’option **manuelle** ou **automatique** pour les mises à jour de configuration.

>[!NOTE]
>
>To learn more about the events associated with device's automatic or manual updates, see the section ***Automatic versus Manual Updates from the Device Dashboard*** in [Managing Channels](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Affichage d’une capture d’écran du lecteur {#view-player-screenshot}

Vous pouvez afficher la capture d’écran d’un lecteur à partir du périphérique dans le panneau **CAPTURE D’ÉCRAN DU LECTEUR**.

Click (**...**) on the top right corner of the Player Screenshot panel and select **Refresh Screenshot** to view the snapshot of the running player.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Gestion des préférences {#manage-preferences}

The **PREFERENCES** panel allows the user to change preferences for **Admin UI**, **Channel Switcher**, and **Remote Debugging** for the device.

>[!NOTE]
>
>Pour plus d’informations sur ces options, voir [Lecteur AEM Screens](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

De plus, cliquez sur **Paramètres** dans le coin supérieur droit pour mettre à jour les préférences du périphérique. Vous pouvez mettre à jour les préférences suivantes :

* **URL du serveur**
* **Résolution**
* **Redémarrer la planification**
* **Nombre max. des fichiers journaux à conserver**
* **Niveau de journal**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>
>Vous pouvez sélectionner l’un des niveaux de journal suivants :
>
>* **Désactiver**
>* **Déboguer**
>* **Infos**
>* **Warning**
>* **Erreur**
>



![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Résolution des incidents des paramètres d’OSGi {#troubleshoot-osgi-settings}

Vous devez activer le référent vide pour autoriser le périphérique à publier des données sur le serveur. Par exemple, si la propriété de référent vide est désactivée, le périphérique ne pourra pas publier de capture d’écran.

Actuellement, certaines de ces fonctions ne sont disponibles que si *Apache Sling Referrer Filter Allow Empty* est activé dans la configuration OSGi. Le tableau de bord peut afficher un avertissement indiquant que les paramètres de sécurité peuvent empêcher l’utilisation de certaines de ces fonctions.

Suivez les étapes ci-après pour activer Apache Sling Referrer Filter Allow Empty

1. Navigate to **Adobe Experience Manager Web Console Configuration**, that is, `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Check the **allow.empty** option.
1. Cliquez sur **Enregistrer**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Recommandations {#recommendations}

Dans la section suivante, il est recommandé de surveiller les liens de réseaux, le serveur et les lecteurs pour en comprendre l’état et réagir face aux problèmes.

AEM offre une surveillance intégrée avec les fonctions suivantes :

* *Pulsation* toutes les cinq secondes pour indiquer que le lecteur AEM Screens est en fonction.
* *Capture d’écran* provenant du lecteur qui montre ce qu’il affiche actuellement.
* Version du *micrologiciel du lecteur AEM Screens* installée sur le lecteur.
* *Espace de stockage libre* sur le lecteur.

Recommandations pour la surveillance à distance avec un logiciel tiers :

* Utilisation de l’unité centrale sur les lecteurs.
* Vérifiez si le processus de lecteur AEM Screens est exécuté.
* Redémarrez/réinitialisez le lecteur à distance.
* Notifications en temps réel.

Il est recommandé de déployer le matériel et le système d’exploitation du lecteur de manière à se connecter à distance afin de diagnostiquer les problèmes et de redémarrer le lecteur.

#### Ressources supplémentaires {#additional-resources}

Voir Configuration de la lecture [vidéo et Dépannage](troubleshoot-videos.md) pour déboguer et dépanner les vidéos lues sur votre canal.

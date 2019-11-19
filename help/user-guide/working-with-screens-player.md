---
title: Utilisation d’AEM Screens Player
seo-title: Utilisation du lecteur Screens
description: Consultez cette page pour en savoir plus sur le lecteur Screens. Elle décrit également l’interface utilisateur d’administration et le sélecteur de canal.
seo-description: Consultez cette page pour en savoir plus sur le lecteur Screens. Elle décrit également l’interface utilisateur d’administration et le sélecteur de canal.
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Working with AEM Screens Player {#working-with-aem-screens-player}

Vous pouvez gérer le contenu du canal et d’autres paramètres sur le lecteur AEM Screens.

>[!NOTE]
>
>Appuyez sur ***Ctrl + Cmd + F**pour quitter le mode plein écran du lecteur OS X AEM Screens.*

Une fois que vous attribuez un canal à un affichage, le lecteur AEM Screens affiche le contenu. Vous pouvez configurer les paramètres de votre lecteur en utilisant les préférences de l’interface utilisateur d’administration (du tableau de bord) ou du lecteur lui-même.

## Utilisation du tableau de bord du périphérique {#using-the-device-dashboard}

Vous pouvez configurer les préférences de votre périphérique à partir de son tableau de bord, accessible via votre instance de création AEM.

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --&gt; ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Cliquez sur le périphérique pour ouvrir son tableau de bord.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Check the **PREFERENCES** panel. You can enable/disable the **Admin UI** and **Channel Switcher** for your player from these two options.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### L’interface utilisateur d’administration {#the-admin-ui}

Enabling the **Admin UI** from the preferences panel allows the user to open the admin settings from the Screens Player. En outre, si vous désactivez cette option dans le tableau de bord du périphérique, l’utilisateur ne peut pas ouvrir l’interface utilisateur d’administration à partir du lecteur.

Pour afficher l’interface utilisateur d’administration du lecteur Screens, appuyez longuement sur l’angle supérieur gauche afin d’ouvrir le menu Admin, sur votre lecteur AEM Screens avec fonction tactile activée ou en utilisant la souris. Elle affiche les informations une fois l’enregistrement terminé et les canaux chargés.

>[!NOTE]
>
>En outre, vous pouvez afficher le temps de disponibilité du lecteur AEM Screens pour vérifier l’intégrité de l’application.

![chlimage_1-3](assets/chlimage_1-3.gif)

Si vous sélectionnez l'option **Configuration** dans le menu latéral, vous pouvez également réinitialiser le **microprogramme**, les **préférences** ou **à l'usine à partir de cette boîte de dialogue.**

De plus, vous pouvez spécifier le nombre maximal de fichiers journaux à conserver pour un lecteur AEM Screens dans la valeur **maxi. des fichiers journaux à conserver**. Pour plus de détails, voir la capture d'écran ci-dessous.

>[!NOTE]
>
>L'option **Mettre à jour le microprogramme** fonctionne uniquement sur la cordova, comme les lecteurs Android.

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

Vous pouvez effacer le cache des canaux et des applications de l’IU d’administration dans le lecteur AEM Screens.

Sélectionnez **Cache de contenu** à partir du rail latéral pour mettre à jour le cache.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### Le sélecteur de canal {#the-channel-switcher}

Enabling the **Channel Switcher** from the preferences panel allows the user to open the channel selection/settings from the Screens Player.

En outre, si vous désactivez cette option dans le tableau de bord du périphérique, l’utilisateur ne peut pas contrôler les préférences de canal à partir du lecteur Screens.

Vous pouvez activer/désactiver et contrôler les paramètres de canal de votre lecteur Screens.

Pour afficher le sélecteur de canal du lecteur, appuyez longuement sur l’angle inférieur gauche afin d’ouvrir le sélecteur de canal qui permet de basculer entre les canaux et qui offre d’autres fonctions.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>Vous pouvez également activer ou désactiver le menu Admin et le sélecteur de canal pour le lecteur à partir du lecteur Screens.
>
>(Voir *Modification des préférences à partir du lecteur Screens*, comme mentionné dans la section ci-dessous.)

### Gestions des préférences à partir du lecteur AEM Screens {#managing-preferences-from-the-aem-screens-player}

Vous pouvez également modifier les paramètres de l’interface utilisateur d’administration et le sélecteur de canal à partir du lecteur.

Procédez comme suit pour modifier les préférences de votre lecteur :

1. Appuyez longuement dans le coin supérieur gauche du canal inactif pour ouvrir le panneau Admin.
1. Navigate to **Configuration** from the left action menu.
1. Enable/disable configuration for **Admin UI** or **Channel Switcher**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Dépannage du lecteur AEM Screens {#troubleshooting-aem-screens-player}

Vous pouvez résoudre de nombreux problèmes liés au lecteur AEM Screens (matériels et logiciels) :

| **Numéros** | **Recommandations** |
|---|---|
| Le stockage du lecteur est plein | Éliminer les fichiers inutiles |
| Réseau du lecteur perdu | Utilisez le câble Cat-5/Cat-6. Pour le wifi, réduisez la distance entre le routeur et le périphérique du lecteur. |
| Lecteur AEM Screens bloqué | Il est recommandé de disposer d’une application de contrôle qui vérifie que le lecteur d’écran AEM fonctionne toujours. |
| Paramètres du lecteur AEM Screens perdus | Vérifier la connexion au serveur AEM |
| AEM Screens Player ne démarre pas automatiquement après le redémarrage/redémarrage du lecteur | Vérification du dossier de démarrage ou de la procédure d'initialisation du système d'exploitation |
| AEM Screens Player affiche un contenu erroné/ancien | Vérifier la connexion réseau |

### Mises à jour du lecteur AEM Screens {#updates-for-aem-screens-player}

Il existe deux types de mises à jour du lecteur AEM Screens :

| **Méthode** | **Détails** | **via Remote** | **Automatique** | **0 temps d'arrêt** |
|---|---|---|---|---|
| Mise à jour du microprogramme | Application sur les lecteurs existants installés via la commande à distance. Après la mise à jour, le lecteur se rechargera automatiquement avec le contenu existant. | Oui | Le code  | Presque 1 à 3 secondes |
| Mises à jour du shell du lecteur | Il s’agit d’un nouveau fichier exécutable à déployer sur le lecteur. Cela requiert de copier à distance le nouveau fichier binaire sur le lecteur, d’arrêter la version en cours d’exécution et de démarrer la nouvelle version. Il peut être nécessaire de télécharger à nouveau le préchargement des modules. | Oui (via un shell distant) | Le code  | Non |

## Instructions de sélection du matériel pour le périphérique du lecteur {#hardware-selection-guidelines-for-player-device}

La section suivante présente les directives de sélection du matériel pour un projet Screens :

* Vous devez toujours vous procurer des composants ***commerciaux*** ou ***industriels*** pour le lecteur PC et le panneau d'affichage ou le projecteur.

* Communiquez toujours avec les fournisseurs qui desservent le marché de la signalisation numérique.
* Tenez toujours compte des facteurs environnementaux tels que la température ambiante et l’humidité relative.
* Examinez toujours les exigences en matière d'alimentation et de conditionnement d'alimentation.
* Examinez attentivement les besoins en performances et les ports d'E/S requis pour l'application.

Le tableau suivant récapitule les configurations matérielles avec les cas d’utilisation standard d’un projet AEM Screens :

<table>
 <tbody>
  <tr>
   <td>Configuration du lecteur</td>
   <td>Processeur</td>
   <td>Memory</td>
   <td>SSD de stockage</td>
   <td>GPU</td>
   <td>Affichage</td>
   <td>E/S</td>
   <td>Cas d’utilisation standard</td>
  </tr>
  <tr>
   <td>De base</td>
   <td>Processeur Intel® Atom double coeur, i3 ou quatre coeurs d'entrée de gamme</td>
   <td><p>4 Go de mémoire</p> <p>2 Mo de cache</p> </td>
   <td><p>・ChromeOS 32 Go</p> <p>・Windows 128 Go</p> </td>
   <td>OnBoard</td>
   <td>1920 x 1080</td>
   <td>DVI,<br /> Ethernet / Sans fil,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Boucle plein écran standard<br /> </li>
     <li>Partage de journée</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standard</td>
   <td>Processeur quatre coeurs Intel® Core i5</td>
   <td><p>8 Go de mémoire</p> <p>4 Mo de cache</p> </td>
   <td>128 GBB</td>
   <td>OnBoard</td>
   <td>3 840 x 2 160 (4 Ko)</td>
   <td>DVI, HDMI<br /> Ethernet / sans fil,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Contenu dynamique source unique</li>
     <li>Simple interactif</li>
     <li>1-3 Dispositions de zone</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avancé</td>
   <td>quatre coeurs avec hyperthreading, processeur Intel® Core i7</td>
   <td><p>16 Go de mémoire</p> <p>8 Mo de cache</p> </td>
   <td>256 Go</td>
   <td>Carte graphique dédiée</td>
   <td>3 840 x 2 160 (4 Ko)</td>
   <td>DVI, HDMI<br /> Ethernet / sans fil,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4 zones de contenu ou plus, lecture vidéo simultanée</li>
     <li>Interactif multi-page</li>
     <li>Déclencheurs de données multisource</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

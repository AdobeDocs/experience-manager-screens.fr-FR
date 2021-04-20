---
title: Utilisation du lecteur AEM Screens
seo-title: Utilisation du lecteur Screens
description: Consultez cette page pour en savoir plus sur le lecteur Screens. Elle décrit également l’interface utilisateur d’administration et le sélecteur de canal.
seo-description: Consultez cette page pour en savoir plus sur le lecteur Screens. Elle décrit également l’interface utilisateur d’administration et le sélecteur de canal.
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
feature: Administering Screens
role: Administrator
level: Intermediate
translation-type: ht
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: ht
source-wordcount: '1070'
ht-degree: 100%

---


# Utilisation du lecteur AEM Screens {#working-with-aem-screens-player}

Vous pouvez gérer le contenu du canal et d’autres paramètres sur l’écran AEM Screens.

>[!NOTE]
>
>Appuyez sur ***Ctrl+Cmd+F*** pour quitter le mode plein écran du lecteur AEM Screens pour OS X.

Une fois que vous attribuez un canal à un affichage, le lecteur AEM Screens affiche le contenu. Vous pouvez configurer les paramètres de votre lecteur en utilisant les préférences de l’interface utilisateur d’administration (du tableau de bord) ou du lecteur lui-même.

## Utilisation du tableau de bord du périphérique {#using-the-device-dashboard}

Vous pouvez configurer les préférences de votre périphérique à partir de son tableau de bord, accessible via votre instance de création AEM.

1. Accédez au tableau de bord du périphérique à partir de votre projet, par exemple, ***Projet de test*** > ***Périphériques***.

   Sélectionnez **Périphériques** et **Gestionnaire de périphériques** dans la barre d’actions.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Cliquez sur le périphérique pour ouvrir son tableau de bord.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Consultez le panneau **PRÉFÉRENCES**. Vous pouvez activer/désactiver l’**interface utilisateur d’administration** et le **sélecteur de canal** pour votre lecteur grâce à ces deux options.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### L’interface utilisateur d’administration {#the-admin-ui}

En activant l’**interface utilisateur d’administration** à partir du panneau Préférences, l’utilisateur peut ouvrir les paramètres d’administrateur du lecteur Screens. En outre, si vous désactivez cette option dans le tableau de bord du périphérique, l’utilisateur ne peut pas ouvrir l’interface utilisateur d’administration à partir du lecteur.

Pour afficher l’interface utilisateur d’administration du lecteur Screens, appuyez longuement sur l’angle supérieur gauche afin d’ouvrir le menu Admin, sur votre lecteur AEM Screens optimisé pour les écrans tactiles activée ou en utilisant la souris. Elle affiche les informations une fois l’enregistrement terminé et les canaux chargés.

>[!NOTE]
>
>En outre, vous pouvez afficher le temps de disponibilité du lecteur AEM Screens pour vérifier l’intégrité de l’application.

![chlimage_1-3](assets/chlimage_1-3.gif)

#### Accès aux options du menu de configuration {#configuration-options}

Vous pouvez mettre à jour vos configurations en sélectionnant l’option **Configuration** dans le menu latéral, comme illustré ci-dessous :

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

Le menu Configuration vous permet de modifier les paramètres suivants :

* Réinitialisez **Micrologiciel**, **Préférences** ou **Paramètres d’usine** dans cette boîte de dialogue.

* Indiquez le nombre maximal de fichiers journaux à conserver pour un lecteur AEM Screens dans **Nombre max. de fichiers journaux à conserver**.

* Activez ou désactivez **Menu d’administration**, **Sélecteur de canal** et **Activity UI** (IU d’activité) pour le lecteur Screens.

   Si la case **Activity UI** (IU d’activité) est cochée dans le menu **Configuration**, le lecteur AEM Screens affiche les *notifications d’activité du lecteur* dans le coin supérieur droit du lecteur, comme illustré ci-dessous.

   ![image](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>L’option **Mettre à jour le micrologiciel** fonctionne uniquement sur Cordova, comme les lecteurs Android.

>[!NOTE]
>
>Il est recommandé de désactiver l’**interface utilisateur d’administration** dans les déploiements de production.

#### Accès aux options du menu Cache de contenu {#content-cache-options}

Vous pouvez effacer le cache des canaux et des applications de l’IU d’administration dans le lecteur AEM Screens.

Sélectionnez **Cache de contenu** à partir du rail latéral pour mettre à jour le cache.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### Le sélecteur de canal {#the-channel-switcher}

En activant le **sélecteur de canal** à partir du panneau Préférences, l’utilisateur peut ouvrir la sélection ou les paramètres de canal du lecteur Screens.

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
1. Accédez à **Configuration** dans le menu d’actions à gauche.
1. Activez/désactivez la configuration pour l’**interface utilisateur d’administration** ou le **sélecteur de canal**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Dépannage du lecteur AEM Screens {#troubleshooting-aem-screens-player}

Vous pouvez résoudre de nombreux problèmes liés au lecteur AEM Screens (matériels et logiciels) :

| **Numéros** | **Recommandations** |
|---|---|
| L’espace de stockage du lecteur est plein | Éliminez les fichiers inutiles |
| Le lecteur a perdu le réseau | Utilisez un câble Cat-5/Cat-6. Pour une connexion Wi-Fi, réduisez la distance entre le routeur et le périphérique de lecture. |
| Le lecteur AEM Screens s’est bloqué | Il est recommandé de disposer d’une application de contrôle qui vérifie que le lecteur AEM Screens fonctionne toujours. |
| Perte des paramètres du lecteur AEM Screens | Vérifiez la connexion au serveur AEM |
| Le lecteur AEM Screens ne démarre pas automatiquement après le redémarrage du lecteur | Vérifiez le dossier de démarrage ou de la procédure d’initialisation du système d’exploitation |
| Le lecteur AEM Screens affiche un contenu erroné/obsolète | Vérifiez la connexion réseau |

### Mises à jour du lecteur AEM Screens {#updates-for-aem-screens-player}

Il existe deux types de mises à jour du lecteur AEM Screens :

| **Méthode** | **Détails** | **via À distance** | **Automatique** | **0 temps d’arrêt** |
|---|---|---|---|---|
| Mise à jour du micrologiciel | Application sur les lecteurs existants installés via la commande à distance. Après la mise à jour, le lecteur se rechargera automatiquement avec le contenu existant. | Oui | Personnalisé | Presque - 1 à 3 secondes |
| Mises à jour du shell du lecteur | Il s’agit d’un nouveau fichier exécutable à déployer sur le lecteur. Cela requiert de copier à distance le nouveau fichier binaire sur le lecteur, d’arrêter la version en cours d’exécution et de démarrer la nouvelle version. Il peut être nécessaire de télécharger à nouveau le préchargement des modules. | Oui (via un shell distant) | Personnalisé | Non |

## Instructions de sélection du matériel pour le périphérique de lecture {#hardware-selection-guidelines-for-player-device}

La section suivante présente les directives de sélection du matériel pour un projet Screens :

* Vous devez toujours vous procurer des composants de qualité ***professionnelle*** ou ***industrielle*** pour le lecteur PC comme pour le panneau d’affichage ou le projecteur.

* Adressez-vous toujours à des fournisseurs qui desservent le marché de la signalisation numérique.
* Tenez toujours compte des facteurs environnementaux tels que la température ambiante et l’humidité relative.
* Examinez toujours les exigences en matière d’alimentation et de conditionnement d’alimentation.
* Examinez attentivement les besoins en performances et les ports d’E/S requis pour l’application.

Le tableau suivant récapitule les configurations matérielles avec les cas d’utilisation standard d’un projet AEM Screens :

<table>
 <tbody>
  <tr>
   <td>Configuration du lecteur</td>
   <td>Processeur</td>
   <td>Mémoire</td>
   <td>Lecteur SSD</td>
   <td>GPU</td>
   <td>Affichage</td>
   <td>E/S</td>
   <td>Cas d’utilisation standard</td>
  </tr>
  <tr>
   <td>De base</td>
   <td>Processeur Intel® i3 double cœur ou Atom quadri-cœur d’entrée de gamme</td>
   <td><p>4 Go de mémoire</p> <p>2 Mo de cache</p> </td>
   <td><p>・ChromeOS 32 Go</p> <p>・Windows 128 Go</p> </td>
   <td>Intégré</td>
   <td>1920 x 1080</td>
   <td>DVI,<br /> Ethernet / Sans fil,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Boucle plein écran standard<br /> </li>
     <li>Tranches horaires</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standard</td>
   <td>Processeur quadri-cœur Intel® Core i5</td>
   <td><p>8 Go de mémoire</p> <p>4 Mo de cache</p> </td>
   <td>128 Go</td>
   <td>Intégré</td>
   <td>3840 x 2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / sans fil,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Contenu dynamique issu de source unique</li>
     <li>Interactif simple</li>
     <li>1-3 dispositions de zone</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avancé</td>
   <td>Processeur Intel® Core i7 quadri-cœur avec hyperthreading</td>
   <td><p>16 Go de mémoire</p> <p>8 Mo de cache</p> </td>
   <td>256 Go</td>
   <td>Carte graphique dédiée</td>
   <td>3840 x 2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / sans fil,<br /> 4 x USB</td>
   <td>
    <ul>
     <li>4 zones de contenu ou plus, lecture vidéo simultanée</li>
     <li>Interactif multipage</li>
     <li>Déclencheurs de données multisource</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

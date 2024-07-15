---
title: Création et gestion des canaux
description: Découvrez comment créer et gérer des canaux. Cette section explique également le tableau de bord du canal et la modification du contenu d’un canal.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 7bbd211a-f54f-42b9-a1b3-516efe6fb579
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 100%

---

# Création et gestion des canaux {#creating-and-managing-channels}

Un canal affiche une séquence de contenu (images et vidéos), mais également un site web ou une application monopage.

Vous découvrirez dans cette page comment créer et gérer des canaux pour AEM Screens.

**Conditions préalables** :

* [Configuration et déploiement de Screens](configuring-screens-introduction.md)
* [Création et gestion de projet Screens](creating-a-screens-project.md)

## Création d’un canal {#creating-a-new-channel}

Après avoir créé le projet AEM Screens, suivez les étapes ci-dessous pour lui créer un canal :

1. Cliquez sur le lien Adobe Experience Manager (en haut à gauche), puis sur Screens. Vous pouvez également accéder directement à `https://localhost:4502/screens.html/content/screens`.

1. Accédez à votre projet Screens et cliquez sur le dossier **Canaux**.

1. Cliquez sur **Créer** dans la barre d’actions.

   ![demochannel](assets/create-channel1.png)

1. Cliquez sur le modèle **Canal de séquence** dans l’assistant **Créer**, puis sur **Suivant**.

   ![demochannel](assets/create-channel2.png)

1. Saisissez le titre **ScreensChannel** et cliquez sur **Créer**.

   ![demochannel](assets/create-project4.png)

1. Un canal de séquence est maintenant ajouté à votre dossier **Canaux**.

### Types de canaux {#channel-types}

Les options de modèles suivantes sont disponibles avec l’assistant :

| **Option de modèle** | **Description** |
|---|---|
| Dossier de canaux | Créez un dossier pour stocker une collection de canaux. |
| Canal de séquence | Créez un canal qui lit les composants de manière séquentielle (l’un après l’autre comme une série de diapositives). |
| Canal d’application | Affichez votre application web personnalisée dans le lecteur Screens. |
| Canal d’écran partagé 1x1 | Affichez un composant dans une seule zone. |
| Canal d’écran partagé 1x2 | Affichez les ressources dans deux zones (division horizontale). |
| Canal d’écran partagé 2x1 | Affichez les ressources dans deux zones (division verticale). |
| Canal d’écran partagé 2x2 | Affichez les ressources dans quatre zones (division horizontale et verticale dans une matrice). |
| Canal d’écran partagé 2x3 | Affichez les ressources dans deux zones (division horizontale) où l’une des zones est plus grande que l’autre. |
| Canal d’écran partagé barre en L gauche ou droite | Les auteurs et autrices de contenus peuvent afficher différents types de ressources dans des zones de taille appropriée. |

>[!NOTE]
>
>Les canaux d’écran partagé divisent l’affichage en plusieurs zones, ce qui permet de lire plusieurs expériences simultanément, côte à côte. Les expériences peuvent être des ressources/du texte statiques ou des séquences incorporées.

>[!IMPORTANT]
>
>Après avoir créé et ajouté du contenu à votre canal, l’étape suivante consiste à créer un emplacement, puis à créer un affichage. Vous devez en outre attribuer ce canal à un affichage. Consultez les ressources ci-dessous à la fin de la section.

## Utilisation des canaux {#working-with-channels}

Vous pouvez modifier, copier, prévisualiser, supprimer un canal, et afficher ses propriétés et son tableau de bord.


![screen_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### Ajout de contenu à un canal et modification de ce contenu {#adding-editing-content-to-a-channel}

Pour ajouter du contenu à un canal ou modifier son contenu, suivez les étapes ci-dessous :

1. Cliquez sur le canal que vous souhaitez modifier (comme illustré ci-dessus).
1. Cliquez sur **Modifier** dans l’angle supérieur gauche de la barre d’actions pour pouvoir modifier les propriétés du canal. L’éditeur s’ouvre pour vous permettre d’ajouter au canal des ressources/composants que vous souhaitez publier.

>[!NOTE]
>Vous pouvez ajouter des composants à votre canal. Voir **[Ajout de composants à un canal](adding-components-to-a-channel.md)** pour plus d’informations.

![demochannel1](assets/demochannel1.gif)

**Chargement de vidéos vers le canal**

Suivez les étapes ci-dessous pour charger des vidéos vers votre canal :

1. Cliquez sur le canal vers lequel charger la vidéo.
1. Cliquez sur **Modifier** dans la barre d’actions.
1. Dans l’éditeur, cliquez sur **Vidéos** sous Ressources, puis faites glisser et déposez les vidéos requises.

>[!NOTE]
>Si vous rencontrez des problèmes lors du chargement des vidéos vers votre canal, reportez-vous à la section [Dépannage des vidéos](troubleshoot-videos.md).

### Affichage ou modification des propriétés d’un canal {#viewing-properties}

1. Cliquez sur le canal que vous souhaitez modifier.
1. Cliquez sur **Propriétés** dans la barre d’actions pour pouvoir afficher ou modifier les propriétés du canal. Les onglets suivants vous permettent de modifier les options.

![propriétés](assets/properties.gif)

### Affichage du tableau de bord {#viewing-dashboard}

1. Cliquez sur le canal que vous souhaitez modifier.
1. Cliquez sur **Tableau de bord** dans la barre d’actions.

![tableau de bord](assets/dashboard.gif)

### Informations sur le canal {#channel-information}

Le panneau Informations sur le canal fournit une description des propriétés ainsi qu’un aperçu du canal. Il vous permet également de voir si le canal est en ligne ou hors ligne.

Cliquez sur l’icône (**...**) dans la barre d’actions **INFORMATIONS SUR LE CANAL** pour pouvoir afficher les propriétés, modifier le contenu ou mettre à jour la mémoire cache (contenu hors ligne) du canal.

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

#### Affichage du manifeste {#view-manifest}

Vous pouvez afficher le manifeste à partir du tableau de bord des canaux.

>[!IMPORTANT]
>Cette option est disponible uniquement avec le pack de fonctionnalités 8 d’AEM 6.4 ou le pack de fonctionnalités 4 d’AEM 6.5.

Pour pouvoir activer cette option à partir du tableau de bord des canaux, procédez comme suit :

1. **Définir le canal sur Hors ligne**
   1. Cliquez sur le canal, puis sur **Propriétés** dans la barre d’actions.
   1. Accédez à l’onglet **Canal** et assurez-vous de désélectionner l’option **Mode Développement (forcer le canal à être en ligne)**.
   1. Cliquez sur **Enregistrer et fermer**.
1. **Mettre à jour le contenu hors ligne**
   1. Cliquez sur le canal, puis sur **Tableau de bord** depuis la barre d’actions.
   1. Accédez au panneau **INFORMATIONS SUR LES CANAUX** et cliquez sur *...*.
   1. Cliquez sur **Mettre à jour le contenu hors ligne**.

Vous devriez maintenant pouvoir voir l’option **Afficher le manifeste** depuis le panneau **INFORMATIONS SUR LES CANAUX** dans le tableau de bord des canaux.

![image1](assets/channel-one.png)


### Canaux en ligne et hors ligne {#online-and-offline-channels}

>[!NOTE]
>Par défaut, lorsque vous créez un canal, celui-ci est hors ligne.

Lorsque vous créez un canal, il peut être défini comme étant en ligne ou hors ligne.

Un ***canal en ligne*** affiche le contenu mis à jour dans l’environnement en temps réel, alors qu’un ***canal hors ligne*** affiche le contenu en mémoire cache.

Pour mettre le canal en ligne, procédez comme suit :

1. Accédez au canal comme **TestProject** > **Canaux** > **TestChannel**.

   Cliquez sur le canal.

   ![screen_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   Cliquez sur **Tableau de bord** dans la barre d’actions pour afficher le statut du lecteur. Le panneau **INFORMATIONS SUR LES CANAUX** indique si le canal est en ligne ou hors ligne.

   ![screen_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. Cliquez sur **Propriétés** dans la barre d’actions et accédez à l’onglet **Canal** comme illustré ci-dessous :

   ![screen_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. Cochez l’option **mode Développement** **(forcer le canal à être en ligne)** pour que le canal soit en ligne.

   Cliquez sur **Enregistrer et Fermer** pour enregistrer.

   ![screen_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   Retournez sur le tableau de bord des canaux. Vous pouvez alors voir le statut en ligne du lecteur dans le panneau **INFORMATIONS SUR LE CANAL**.

   ![screen_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>Pour reconfigurer votre canal comme étant hors ligne, désélectionnez l’option Mode Développement dans l’onglet **Propriétés** (comme indiqué à l’étape (3)). Ensuite, à partir du panneau **INFORMATIONS SUR LES CANAUX**, cliquez sur **Mettre à jour le contenu hors ligne**, comme illustré ci-dessous.

![dashboard2](assets/dashboard2.gif)

#### Mises à jour automatiques ou manuelles depuis le tableau de bord de l’appareil {#automatic-versus-manual-updates-from-the-device-dashboard}

Le tableau suivant répertorie les événements associés aux mises à jour automatiques ou manuelles depuis le tableau de bord de l’appareil.

<table>
 <tbody>
  <tr>
   <td><strong>Événement</strong></td>
   <td><strong>Mise à jour automatique de l’appareil</strong></td>
   <td><strong>Mise à jour manuelle de l’appareil</strong></td>
  </tr>
  <tr>
   <td>Modification de canal en ligne</td>
   <td>Le contenu est mis à jour automatiquement.</td>
   <td><p>Contenu mis à jour sur « Appareil : Configuration Push »</p> <p>Ou,</p> <p>Contenu mis à jour sur <strong><i>Appareil : Redémarrer</i></strong></p> </td>
  </tr>
  <tr>
   <td>Changement du canal hors ligne, mais le "contenu Push" du canal n’est PAS déclenché (aucune recréation du package hors ligne)</td>
   <td>Aucune mise à jour de contenu</td>
   <td>Aucune mise à jour de contenu</td>
  </tr>
  <tr>
   <td>Changement dans le canal hors ligne et le "contenu Push" du canal est déclenché (nouveau package hors ligne)</td>
   <td>Le contenu est mis à jour automatiquement.</td>
   <td><p>Contenu mis à jour sur <strong><i>Appareil : Configuration Push</i></strong></p> <p>Ou,</p> <p>Contenu mis à jour sur <strong><i>Appareil : Redémarrer</i></strong></p> </td>
  </tr>
  <tr>
   <td><p>Changement de configuration</p>
    <ul>
     <li>Affichage (canal forcé)</li>
     <li>Appareil</li>
     <li>Affectations de canal (nouveau canal, canal supprimé)</li>
     <li>Affectation de canal (rôle, événement, planification)</li>
    </ul> </td>
   <td>La configuration est mise à jour automatiquement.</td>
   <td><p>La configuration est mise à jour sur l’<strong><i>appareil : configuration push</i></strong>.</p> <p>Ou,</p> <p>Configuration mise à jour sur <strong><i>Appareil : Redémarrer</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### Affichages attribués {#assigned-displays}

Le panneau **Affichages attribués** indique quel affichage est associé à quel canal. Il fournit un instantané de l’affichage affecté avec la résolution.

Les affichages associés sont répertoriés dans le panneau **Affichages attribués**, comme illustré ci-dessous :

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
>Pour en savoir plus sur la création d’un affichage à un emplacement donné, consultez :
>
>* [Création et gestion des emplacements](managing-locations.md)
>* [Création et gestion des affichages](managing-displays.md)
>

Cliquez également sur l’affichage dans le panneau **AFFICHAGES ATTRIBUÉS** pour voir les informations relatives à l’affichage, comme illustré ci-dessous :

![chlimage_1-28](assets/chlimage_1-28.png)

### Étapes suivantes {#the-next-steps}

L’étape suivante, après la création d’un canal et l’ajout/la modification de contenu dans votre canal, consiste à apprendre à créer un emplacement et un affichage. ainsi qu’à attribuer un canal à cet affichage.

Consultez les ressources suivantes pour les étapes à venir :

* [Création et gestion des canaux](managing-channels.md)
* [Création et gestion des emplacements](managing-locations.md)
* [Création et gestion des affichages](managing-displays.md)

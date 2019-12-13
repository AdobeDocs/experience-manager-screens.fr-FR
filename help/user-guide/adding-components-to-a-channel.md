---
title: Ajout de composants à un canal
seo-title: Ajout de composants à un canal
description: Suivez cette page pour en savoir plus sur l’ajout de composants aux canaux dans un projet AEM Screens.
seo-description: Suivez cette page pour en savoir plus sur l’ajout de composants aux canaux dans un projet AEM Screens.
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Ajout de composants à un canal{#adding-components-to-a-channel}

Les composants sont des éléments fondamentaux de l’expérience AEM (Adobe Experience Manager). Vous pouvez utiliser un certain nombre de composants et les ajouter à votre canal dans un projet AEM Screens.

## Composants dans AEM Screens {#components-in-aem-screens}

AEM Screens fournit différents composants AEM qui peuvent être utilisés dans un projet Screens.

### Affichage des composants AEM Screens {#viewing-aem-screens-components}

Chaque fois que vous créez un projet AEM Screens, vous pouvez voir la liste des composants par défaut qui peuvent être ajoutés au projet.

Pour afficher les composants par défaut dans votre projet Screens, suivez les étapes ci-dessous :

1. Sélectionnez le canal. Par exemple, **We.Retail en magasin** &gt; **Canaux** &gt; **Canal inactif**.

1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur AEM.
1. Cliquez sur l’icône **+** de la barre latérale pour ouvrir les composants.
1. Tous les composants inclus par défaut dans un projet AEM Screens s’affichent, comme illustré dans la figure ci-dessous.

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### Ajout d’un composant {#adding-a-new-component}

AEM propose un certain nombre d’autres composants. Vous pouvez toujours ajouter d’autres composants (non inclus par défaut) à votre projet, pourvu qu’ils soient compatibles avec AEM Screens.

L’exemple suivant montre l’ajout d’un composant Livefyre à un projet AEM Screens :

1. Sélectionnez le canal dans lequel vous voulez ajouter un composant. Par exemple, **We.Retail en magasin** &gt; **Canaux** &gt; **Canal inactif**.

1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.
1. Select **Design** mode.
1. Sélectionnez l’éditeur de conception complet à droite et cliquez sur le symbole de paramètres pour ouvrir la boîte de dialogue **Conception ParSys**.
1. Vous pouvez sélectionner les composants que vous souhaitez importer dans votre projet AEM Screens. L’exemple suivant montre l’ajout du composant **Livefyre** à un projet AEM Screens.

![adding_components](assets/adding_components.gif)

>[!NOTE]
>
>De la même façon, vous pouvez ajouter à votre projet autant de nouveaux composants que vous le souhaitez, s’ils sont compatibles avec AEM Screens.

## Présentation des composants AEM Screens {#understanding-aem-screen-components}

La section suivante explique les composants des écrans AEM que vous pouvez utiliser dans votre projet.

>[!NOTE]
>
>Pour afficher les propriétés de n’importe quel composant, sélectionnez-le, puis cliquez sur l’icône en forme de marteau afin d’ouvrir/d’afficher les propriétés.

### Application {#application}

Le composant **Application** permet d’ajouter une application au canal.

Le composant Application possède les propriétés suivantes :

| **Propriété** | **Description** |
|---|---|
| ***Chemin de l’application*** | Sélectionnez le chemin absolu où se trouve l’application. |
| ***Durée (ms)*** | Sélectionnez la durée de l’application. Par défaut, la durée est définie sur -1, ce qui signifie que l’élément s’exécute pour toujours (c’est-à-dire, l’application d’une seule page). Si vous définissez une valeur supérieure à 0 pour la durée, l’élément s’affiche pendant la durée spécifiée avant que l’élément suivant n’apparaisse. |

L’exemple suivant montre comment incorporer un composant Application avec l’aperçu de ses propriétés :

![adding_components_application](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>Reportez-vous à l’exemple ci-dessus pour afficher les propriétés de chacun des composants ci-dessous.

### Canal {#channel}

Le composant **Canal** permet d’ajouter un canal entier à votre projet.

Le composant Canal présente les propriétés suivantes :

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td><strong><em>Chemin du canal</em></strong></td>
   <td>Sélectionnez le chemin absolu où se trouve l’application.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Durée (ms)</em></strong></td>
   <td>Sélectionnez la durée complète du canal. La définition de la durée sur -1 indique que le canal incorporé exécutera sa longueur entière dans un canal particulier.</td>
  </tr>
 </tbody>
</table>

### Page incorporée {#embedded-page}

Une **page incorporée** permet d’ajouter une page incorporée à un projet. Par exemple, il peut s’agir d’une application web ou d’un catalogue de produits.

La page incorporée présente les propriétés suivantes :

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td><strong><em>Chemin d’accès à la page<br /> </em></strong></td>
   <td>Sélectionnez le chemin absolu où se trouve le canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Durée (ms)</em></strong></td>
   <td>Sélectionnez la durée complète du canal. La définition de la durée sur -1 indique que le canal incorporé exécutera sa longueur entière dans un canal particulier.</td>
  </tr>
 </tbody>
</table>

### Séquence incorporée {#embedded-sequence}

>[!NOTE]
>
>Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

Une séquence incorporée permet d’ajouter un canal de séquence incorporée dans votre canal existant (avec d’autres ressources).

La séquence incorporée présente les propriétés suivantes :

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>Chemin du canal</td>
   <td>Sélectionnez le chemin absolu de la séquence que vous souhaitez inclure dans votre canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Durée (ms)</em></strong></td>
   <td>Sélectionnez la durée complète du canal. La définition de la durée sur -1 indique que le canal incorporé exécutera sa longueur entière dans un canal particulier.</td>
  </tr>
  <tr>
   <td><strong><em>Stratégie</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### Séquence incorporée dynamique {#dynamic-embedded-sequence}

Une séquence incorporée dynamique permet d’ajouter une séquence similaire à la séquence incorporée mentionnée ci-dessus, mais par l’intermédiaire du rôle de canal.

Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

La séquence incorporée dynamique présente les propriétés suivantes :

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td><strong><em>Rôle d’attribution de canaux</em></strong><br /> </td>
   <td>Saisissez le rôle du canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Durée (ms)</em></strong></td>
   <td>Sélectionnez la durée complète du canal. La définition de la durée sur -1 indique que le canal incorporé exécutera sa longueur entière dans un canal particulier.</td>
  </tr>
  <tr>
   <td><strong><em>Stratégie</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### Fragment d’expérience {#experience-fragment}

Un fragment d’expérience vous permet d’ajouter un fragment d’expérience (groupe d’un ou de plusieurs composants, y compris le contenu et la mise en page pouvant être référencés dans les pages) à votre canal AEM Screens. Faites glisser et déposez le composant dans l’éditeur AEM et sélectionnez le fragment d’expérience.

Pour en savoir plus sur la création d’un fragment d’expérience et son utilisation dans un projet AEM Screens, voir [Utilisation de fragments](experience-fragments-in-screens.md)d’expérience.

![exp](assets/exp.gif)

| **Propriété** | **Description** |
|---|---|
| **Fragment d’expérience** |
| ***Fragment d’expérience*** | Sélectionnez le fragment d’expérience. |
| ***Durée*** | Sélectionnez la durée entière du fragment d’expérience lu dans le canal. |
| **Configuration hors ligne** |
| ***Bibliothèques côté client*** | Fichiers JavaScript et CSS. |
| ***Fichiers statiques*** | Fichiers statiques que vous pouvez ajouter en tant que configurations hors ligne à votre fragment d’expérience. |

>[!NOTE]
>
>Les bibliothèques **côté** client et les fichiers **** statiques que vous ajoutez à partir de ce composant s’ajouteront aux bibliothèques **côté** client déjà configurées et aux fichiers statiques ajoutés à partir des **propriétés du fragment d’expérience.**

### Image {#image}

Cette fonction permet d’ajouter une image au canal.

La ressource image présente trois onglets, à savoir **Image**, **Accessibilité** et **Séquence** :

| **Propriété** | **Description** |
|---|---|
| **Image** |
| ***Ressource image*** | Sélectionnez la ressource image. |
| ***Titre*** | Titre de l’image. |
| ***Lier à*** | Ajoutez un lien vers l’image. |
| ***Description*** | Brève description de l’image. |
| ***Taille*** | Taille de l’image. |
| **Accessibilité** |
| ***Texte de remplacement*** | Texte de remplacement de l’image. |
| **Séquence** |
| ***Durée*** | Sélectionnez la durée complète de l’image. La définition de la durée sur -1 indique que l’image incorporée exécutera toute sa longueur dans un canal particulier. |

### Transition {#transition}

Le composant Transition permet d’ajouter une transition au projet Screens.

L’illustration suivante montre le composant de transition (ajouté par glisser-déposer) dans l’éditeur.

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

Sélectionnez l’icône de transition et cliquez sur **Configurer** (icône de clé à molette) pour ouvrir la boîte de dialogue **Transition** . Cette boîte de dialogue comprend trois onglets :

* **Transition**
* **Séquence**
* **Activation**

>[!NOTE]
>
>Par défaut, la séquence est définie sur 600 ms. Vous pouvez mettre à jour la séquence de transition vers une autre valeur à l’aide de l’onglet **Séquence** .

![transition](assets/transition.gif)

Le composant Transition présente les propriétés suivantes :

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td><strong>Transition</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Type</em></strong></td>
   <td><p>Type de la transition entre l’élément précédent et le suivant. Le <strong>type</strong> de transition comprend les options suivantes :</p>
    <ul>
     <li><strong>Normal</strong></li>
     <li><strong>Fondu</strong></li>
     <li><strong>Glissement depuis la droite</strong></li>
     <li><strong>Glissement depuis la gauche</strong></li>
     <li><strong>Glissement depuis le haut</strong></li>
     <li><strong>Glissement depuis le bas</strong></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Séquence</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Durée</em></strong></td>
   <td>Sélectionnez la durée complète de la transition. Par défaut, il est défini sur 600 ms.</td>
  </tr>
  <tr>
   <td><strong>Activation</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Actif de</em></strong></td>
   <td>Horodatage qui décrit le moment où la transition peut être active.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Actif jusqu’à</em></strong></td>
   <td>Horodatage qui décrit jusqu’au moment où la transition peut être active.</td>
  </tr>
  <tr>
   <td><strong><em>Planifier</em></strong></td>
   <td>Ajoutez une planification prédéfinie.</td>
  </tr>
 </tbody>
</table>

### Vidéo {#video}

Le composant Vidéo permet d’ajouter une vidéo à votre projet Screens.

Le composant Vidéo présente les propriétés suivantes :

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td><em><strong>Contenu vidéo</strong></em></td>
   <td>Sélectionnez le lien vers la vidéo.</td>
  </tr>
  <tr>
   <td><em><strong>Durée</strong></em></td>
   <td>Sélectionnez la durée de la vidéo. Par défaut, la durée est définie sur -1, ce qui signifie que l’élément s’exécute pour toujours. Si vous définissez une durée supérieure à 0, l’élément s’affiche pendant la durée spécifiée avant que l’élément suivant n’apparaisse.<br /> </td>
  </tr>
  <tr>
   <td><em><strong>Création de rendu</strong></em></td>
   <td><p>Si le rapport d’aspect de la vidéo ne correspond pas à l’écran, vous pouvez ajuster le rendu à l’aide des options <strong>Contenir</strong> ou <strong>Couverture</strong>.</p> <p><em>Contenir</em> signifie que l’intégralité de la vidéo est affichée et que les zones manquantes sont remplies par une bordure noire.</p> <p><em>Couverture</em> signifie que la vidéo couvre toute la fenêtre, mais que certaines parties dépassant sur les côtés sont masquées.</p> </td>
  </tr>
  <tr>
   <td><em><strong>Taille</strong></em></td>
   <td>Taille de la vidéo.</td>
  </tr>
 </tbody>
</table>


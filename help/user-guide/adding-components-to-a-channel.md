---
title: Ajout de composants à un canal
description: Découvrez comment ajouter des composants aux canaux d’un projet AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 56dbe098-05db-4fc3-977f-e50a0a312d64
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 81%

---

# Ajout de composants à un canal{#adding-components-to-a-channel}

Les composants sont des éléments fondamentaux de l’expérience AEM (Adobe Experience Manager). Vous pouvez utiliser un certain nombre de composants et les ajouter au canal d’un projet AEM Screens.

## Composants dans AEM Screens {#components-in-aem-screens}

AEM Screens fournit différents composants AEM qui peuvent être utilisés dans un projet Screens.

### Affichage des composants AEM Screens {#viewing-aem-screens-components}

Lorsque vous créez un projet AEM Screens, vous pouvez voir la liste des composants par défaut qui peuvent être ajoutés au projet.

Pour afficher les composants par défaut dans le projet Screens, procédez comme suit :

1. Cliquez sur le canal. Par exemple : **`We.Retail In Store`** > **Canaux** > **Canal inactif**.

1. Cliquez sur **Modifier** dans la barre d’actions.
1. Dans l’éditeur AEM, cliquez sur l’icône **+** dans la barre latérale.
1. Tous les composants fournis par défaut dans un projet AEM Screens s’affichent, comme illustré dans la figure ci-dessous.

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### Ajout d’un nouveau composant {#adding-a-new-component}

AEM fournit plusieurs autres composants. Vous pouvez toujours ajouter d’autres composants (non inclus par défaut) à votre projet, étant donné que ces composants sont compatibles avec AEM Screens.

L’exemple suivant illustre l’ajout d’un composant Livefyre à un projet AEM Screens :

1. Cliquez sur le canal dans lequel vous souhaitez ajouter un composant. Par exemple : **`We.Retail In Store`** > **Canaux** > **Canal inactif**.

1. Cliquez sur **Modifier** dans la barre d’actions.
1. Cliquez sur le mode **Conception**.
1. Cliquez sur l’ensemble de l’éditeur de conception à droite, puis sur le symbole des paramètres afin d’ouvrir la boîte de dialogue **Conception parsys**.
1. Vous pouvez cliquer sur les composants que vous souhaitez importer dans le projet AEM Screens. L’exemple suivant illustre l’ajout de la variable **Livefyre** à un projet AEM Screens.

![adding_components](assets/adding_components.gif)

>[!NOTE]
>
>De la même façon, vous pouvez ajouter au projet autant de nouveaux composants que vous le souhaitez, s’ils sont compatibles avec AEM Screens.

## Présentation des composants AEM Screens {#understanding-aem-screen-components}

La section suivante décrit les composants AEM Screens que vous pouvez utiliser dans le projet.

>[!NOTE]
>
>Pour afficher les propriétés d’un composant, cliquez dessus, puis sur l’icône en forme de marteau afin d’ouvrir/d’afficher les propriétés.

### Application {#application}

Le composant **Application** permet d’ajouter une application au canal.

Le composant d’application possède les propriétés suivantes :

| **Propriété** | **Description** |
|---|---|
| ***Chemin de l’application*** | Cliquez sur le chemin absolu où se trouve l’application. |
| ***Durée (ms)*** | Cliquez sur la durée de l’application. Par défaut, la durée est définie sur -1, ce qui signifie que l’élément s’exécute indéfiniment (c’est-à-dire, une application d’une seule page). Si vous définissez une valeur supérieure à 0 pour la durée, l’élément s’affiche pendant la durée spécifiée avant que l’élément suivant n’apparaisse. |

L’exemple suivant illustre la manière dont un composant d’application doit être incorporé avec l’aperçu de ses propriétés :

![adding_componentsapplication](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>Consultez l’exemple ci-dessus pour afficher les propriétés de chacun des composants ci-dessous.

### Canal {#channel}

Le composant **Canal** permet d’ajouter un canal entier au projet.

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
   <td>Sélectionnez la durée complète du canal. Si vous définissez la durée sur -1, cela signifie que le canal incorporé s’exécute pendant toute sa durée dans un canal donné.</td>
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
   <td>Sélectionnez la durée complète du canal. Si vous définissez la durée sur -1, cela signifie que le canal incorporé s’exécute pendant toute sa durée dans un canal donné.</td>
  </tr>
 </tbody>
</table>

### Séquence incorporée {#embedded-sequence}

>[!NOTE]
>
>Pour en savoir plus sur les séquences incorporées, voir [Séquences incorporées](embedded-sequences.md) sous la section Création dans Screens .

Une séquence incorporée permet d’ajouter un canal de séquence incorporée dans votre canal existant (avec d’autres ressources).

La séquence incorporée présente les propriétés de page suivantes :

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>Chemin du canal</td>
   <td>Sélectionnez le chemin absolu de la séquence que vous souhaitez inclure dans le canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Durée (ms)</em></strong></td>
   <td>Sélectionnez la durée complète du canal. Si vous définissez la durée sur -1, cela signifie que le canal incorporé s’exécute pendant toute sa durée dans un canal donné.</td>
  </tr>
  <tr>
   <td><strong><em>Stratégie</em></strong></td>
   <td>Définissez-la sur <strong>original</strong> ou <strong>seul(e)</strong>. La définition de la valeur sur la variable <strong>original</strong> signifie que la séquence secondaire s’exécute entièrement à chaque cycle de la séquence parente. L’autre valeur possible est <strong>unique</strong>. Une telle valeur n’affiche qu’un élément de la séquence secondaire à chaque exécution. Par exemple, le premier élément de la première boucle et le second élément de la deuxième boucle.</td>
  </tr>
 </tbody>
</table>

### Séquence incorporée dynamique {#dynamic-embedded-sequence}

Une séquence incorporée dynamique permet d’ajouter une séquence similaire à la séquence mentionnée ci-dessus, sauf par rôle de canal.

Pour en savoir plus sur les séquences incorporées, voir [Séquences incorporées](embedded-sequences.md) sous la section Création dans Screens .

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
   <td>Sélectionnez la durée complète du canal. Si vous définissez la durée sur -1, cela signifie que le canal incorporé s’exécute pendant toute sa durée dans un canal donné.</td>
  </tr>
  <tr>
   <td><strong><em>Stratégie</em></strong></td>
   <td>Définissez-la sur <strong>original</strong> ou <strong>seul(e)</strong>. La définition de la valeur sur la variable <strong>original</strong> signifie que la séquence secondaire s’exécute entièrement à chaque cycle de la séquence parente. L’autre valeur possible est <strong>unique</strong>. Une telle valeur n’afficherait qu’un seul élément de la séquence secondaire à chaque exécution. Par exemple, le premier élément de la première boucle et le second élément de la deuxième boucle.</td>
  </tr>
 </tbody>
</table>

### Fragment d’expérience {#experience-fragment}

Un fragment d’expérience vous permet d’ajouter un fragment d’expérience (un groupe d’un ou plusieurs composants comprenant un contenu et une disposition pouvant être référencés dans les pages) à votre canal AEM Screens. Glissez-déposez le composant vers l’éditeur AEM, puis cliquez sur le fragment d’expérience.

Pour en savoir plus sur la création d’un fragment d’expérience et son utilisation dans un projet AEM Screens, reportez-vous à [Utilisation de fragments d’expérience](experience-fragments-in-screens.md).

![exp](assets/exp.gif)

| **Propriété** | **Description** |
|---|---|
| **Fragment d’expérience** |
| ***Fragment d’expérience*** | Sélectionnez le fragment d’expérience. |
| ***Durée*** | Sélectionnez la durée complète du fragment d’expérience lu dans le canal. |
| **Configuration hors ligne** |
| ***Bibliothèques côté client*** | Fichiers JavaScript et CSS. |
| ***Fichiers statiques*** | Fichiers statiques que vous pouvez ajouter en tant que configurations hors ligne à votre fragment d’expérience. |

>[!NOTE]
>
>Les **bibliothèques côté client** et les **fichiers statiques** que vous ajoutez depuis ce composant viennent s’ajouter aux **bibliothèques côté client** déjà configurées et aux fichiers statiques ajoutés à partir des **propriétés** du fragment d’expérience.

### Image {#image}

Une image permet d’ajouter une image à votre canal.

La ressource image comporte trois onglets, à savoir : **Image**, **Accessibilité** et **Séquence** :

| **Propriété** | **Description** |
|---|---|
| **Image** |
| ***Ressource image*** | Cliquez sur la ressource image. |
| ***Titre*** | Titre de l’image. |
| ***Lier à*** | Ajoutez un lien vers l’image. |
| ***Description*** | Brève description de l’image. |
| ***Taille*** | Taille de l’image. |
| **Accessibilité** |
| ***Texte de remplacement*** | Texte secondaire de l’image. |
| **Séquence** |
| ***Durée*** | Par défaut, la durée est définie sur *8 000 ms*. Si vous souhaitez modifier la durée de lecture de l’image, mettez à jour le champ **Durée**. |

### Transition {#transition}

Le composant Transition permet d’ajouter une transition au projet Screens.

L’illustration suivante représente le composant de transition (ajouté par glisser-déposer) dans l’éditeur.

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

Cliquez sur l’icône de transition, puis sur **Configurer** (icône en forme de clé à molette) pour ouvrir la boîte de dialogue **Transition**. Cette boîte de dialogue comprend trois onglets :

* **Transition**
* **Séquence**
* **Activation**

>[!NOTE]
>
>Par défaut, la séquence est définie sur 600 ms. Vous pouvez mettre à jour la séquence de transition vers une autre valeur via l’onglet **Séquence**.

![Transition](assets/transition.gif)

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
   <td><p>Type de la transition entre l’élément précédent et le suivant. Le <strong>type</strong> de transition comprend les options suivantes :</p>
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
   <td>Sélectionnez la durée complète de la transition. Par défaut, elle est définie sur 600 ms.</td>
  </tr>
  <tr>
   <td><strong>Activation</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Actif à partir de</em></strong></td>
   <td>Horodatage indiquant le moment à partir duquel la transition peut être active.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Actif jusqu’à</em></strong></td>
   <td>L’horodatage décrit jusqu’à quel moment la transition peut être active.</td>
  </tr>
  <tr>
   <td><strong><em>Planning</em></strong></td>
   <td>Ajoutez une planification prédéfinie.</td>
  </tr>
 </tbody>
</table>

### Vidéo {#video}

Le composant Vidéo permet d’ajouter une vidéo au projet Screens.

Le composant Vidéo présente les propriétés suivantes :

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td><em><strong>Contenu vidéo</strong></em></td>
   <td>Cliquez sur le lien vers la vidéo.</td>
  </tr>
  <tr>
   <td><em><strong>Durée</strong></em></td>
   <td>Sélectionnez la durée de la vidéo. Par défaut, la durée est définie sur -1, ce qui signifie que l’élément s’exécute indéfiniment. Si vous définissez une valeur supérieure à 0 pour la durée, l’élément s’affiche pendant la durée spécifiée avant que l’élément suivant n’apparaisse.<br /> </td>
  </tr>
  <tr>
   <td><em><strong>Création de rendu</strong></em></td>
   <td><p>Si le format de la vidéo ne correspond pas à l’écran, vous pouvez modifier le rendu à l’aide des options <strong>Contenir</strong> ou <strong>Couverture</strong>.</p> <p><em>Contenir</em> signifie que l’intégralité de la vidéo est affichée et que les zones manquantes sont remplies d’une bordure noire.</p> <p><em>Couverture</em> signifie que la vidéo couvre toute la fenêtre d’affichage, mais que certaines parties qui débordent sur les côtés sont masquées.</p> </td>
  </tr>
  <tr>
   <td><em><strong>Taille</strong></em></td>
   <td>Taille de la vidéo.</td>
  </tr>
 </tbody>
</table>

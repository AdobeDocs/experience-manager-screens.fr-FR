---
title: Prise en charge des miniatures pour les vidéos dans AEM Screens
description: Cette page décrit comment ajouter la prise en charge des miniatures pour les vidéos dans Screens.
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: ec58cd9171e359b451eaad7015d42b41ef1bff3f
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 100%

---

# Prise en charge des miniatures pour les vidéos {#thumbnail-support-videos}

## Présentation {#introduction}

Un auteur de contenu peut définir une miniature de vidéos afin de pouvoir utiliser l’image en tant qu’espace réservé et de pouvoir tester correctement la lecture et le ciblage du contenu, alors que l’équipe concernée peut s’occuper de la finalisation de la vidéo elle-même. L’image peut également être utilisée au cas où la lecture de la vidéo échouerait.

L’ajout de la prise en charge d’une miniature sur le composant vidéo permet au client d’ajouter correctement un composant valide dans le canal, avec le contenu réel, et d’effectuer toutes les configurations de ciblage avant que la vidéo ne soit réellement diffusée.

>[!NOTE]
>Si la miniature est définie pour un composant vidéo, elle sera lue en cas d’échec de la lecture vidéo sur le lecteur. Cela vous permet de diffuser le message souhaité à l’audience (en lui permettant de lire le contenu) au lieu de l’ignorer complètement.

La prise en charge des miniatures vous permet d’effectuer les opérations suivantes :

* Préparer une expérience sur un canal lorsque les vidéos ne sont pas encore prêtes ou lorsque vous ne souhaitez pas nécessairement tester un téléchargement de ressource volumineux sur les lecteurs.

* Définir un mécanisme de secours en cas de problèmes de lecture sur l’appareil.

## Utilisation de miniatures dans les vidéos {#using-thumbnails}

Suivez les étapes ci-dessous pour utiliser des miniatures dans les vidéos :

1. Accédez à un canal Screens existant ou créez-en un.

1. Sélectionnez le canal et cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.

   ![image](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. Ajoutez ou modifiez un composant vidéo existant, comme illustré dans le schéma ci-dessous.

   ![image](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. Sélectionnez la vidéo et cliquez sur l’icône *clé à molette* pour ouvrir les propriétés vidéo.

   ![image](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. Une boîte de dialogue **Vidéo** s’ouvre, dans laquelle vous pouvez afficher la zone de dépôt **Miniature**.

   ![image](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. Faites glisser une image à partir du sélecteur de ressources vers la zone de dépôt **Miniature** et cliquez sur **Terminé**.

   ![image](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. Cliquez sur **Aperçu**.

1. Si une vidéo est définie sur le composant, elle sera lue. Si ce n’est pas le cas, et que la miniature est définie, la miniature sera affichée. Sinon, le composant est considéré comme non configuré et sera ignoré.

## Cas d’utilisation pris en charge lors de l’utilisation de miniatures dans des vidéos {#understand-use-case}

La miniature dans les vidéos prend en charge les cas d’utilisation suivants :

* Un composant vidéo sans configuration sera ignoré.

* Un composant vidéo dont seule la miniature est définie affichera la miniature.

* Un composant vidéo avec une vidéo (si la vidéo présente un rendu correct) et une miniature lira la vidéo.

* Un composant vidéo avec une vidéo définie affichera la miniature en cas d’erreur de lecture ou passera simplement à l’élément suivant si la miniature n’est pas configurée.

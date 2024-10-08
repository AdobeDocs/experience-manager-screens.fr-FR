---
title: Prise en charge des miniatures pour les vidéos dans AEM Screens
description: Découvrez comment ajouter la prise en charge des miniatures pour les vidéos dans AEM Screens.
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 100%

---

# Prise en charge des miniatures pour les vidéos {#thumbnail-support-videos}

## Présentation {#introduction}

Un auteur ou une autrice de contenu peut définir une miniature pour les vidéos afin que l’image soit utilisée comme espace réservé. Cette personne peut tester correctement la lecture et le ciblage du contenu, tandis que l’équipe appropriée termine la vidéo proprement dite. L’image peut également être utilisée au cas où la lecture de la vidéo échouerait.

L’ajout de la prise en charge d’une miniature sur le composant vidéo permet au client ou à la cliente d’ajouter correctement un composant valide dans le canal, avec le contenu réel, et d’effectuer toutes les configurations de ciblage avant que la vidéo ne soit diffusée.

>[!NOTE]
>Si la miniature est définie pour un composant vidéo, elle est lue en cas d’échec de la lecture vidéo sur le lecteur. Cette solution de secours permet de diffuser le message souhaité à l’audience (en lui permettant de lire le contenu) au lieu de l’ignorer complètement.

La prise en charge des miniatures vous permet de :

* Préparer une expérience sur un canal lorsque les vidéos ne sont pas encore prêtes ou lorsque vous ne souhaitez pas nécessairement tester un téléchargement de ressource volumineux sur les lecteurs.

* Définir un mécanisme de secours en cas de problèmes de lecture sur l’appareil.

## Utilisation de miniatures dans les vidéos {#using-thumbnails}

Pour utiliser une miniature dans les vidéos, procédez comme suit :

1. Accédez à un canal AEM Screens existant ou créez-en un.

1. Cliquez sur le canal et sur **Modifier** dans la barre d’actions.

   ![image](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. Ajoutez ou modifiez un composant vidéo existant, comme illustré dans le schéma ci-dessous.

   ![image](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. Cliquez sur la vidéo et sur l’icône en forme de *clé à molette*.

   ![image](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. Une boîte de dialogue **Vidéo** s’ouvre, dans laquelle vous pouvez afficher la zone de dépôt **Miniature**.

   ![image](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. Faites glisser une image à partir du sélecteur de ressources vers la zone de dépôt **Miniature** et cliquez sur **Terminé**.

   ![image](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. Cliquez sur **Aperçu**. 

1. Si une vidéo est définie sur le composant, elle est lue. Si ce n’est pas le cas, et que la miniature est définie, alors la miniature s’affiche. Sinon, le composant est considéré comme non configuré et est ignoré.

## Cas d’utilisation pris en charge lors de l’utilisation de miniatures dans des vidéos {#understand-use-case}

La miniature dans les vidéos prend en charge les cas d’utilisation suivants :

* Un composant vidéo sans configuration est ignoré.

* Un composant vidéo dont seule la miniature est définie affiche la miniature.

* Un composant vidéo avec une vidéo (si la vidéo présente un rendu correct) et une miniature lit la vidéo.

* Un composant vidéo avec une vidéo définie affiche la miniature en cas d’erreur de lecture ou passe simplement à l’élément suivant si la miniature n’est pas configurée.

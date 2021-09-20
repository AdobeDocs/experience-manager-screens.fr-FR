---
title: Prise en charge des miniatures pour les vidéos dans AEM Screens
description: Cette page décrit comment ajouter la prise en charge des miniatures pour les vidéos dans Screens.
index: false
source-git-commit: 07b5b6159b09c0c1301a5e782dfe959d0b83a7d2
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# Prise en charge des miniatures pour les vidéos {#thumbnail-support-videos}

## Présentation {#introduction}

Un auteur de contenu peut définir une miniature pour les vidéos afin que l’image puisse être utilisée comme espace réservé et tester correctement la lecture et le ciblage du contenu, pendant que la vidéo réelle est en cours de finalisation par l’équipe appropriée. L’image peut également être utilisée, au cas où la lecture de la vidéo échouerait.

L’ajout de la prise en charge d’une miniature sur le composant vidéo permet au client d’ajouter correctement un composant valide dans le canal, avec le contenu réel, et d’effectuer toutes les configurations de ciblage avant que la vidéo ne soit réellement diffusée.

>[!NOTE]
>Si elle est définie sur le composant vidéo, la miniature est lue en cas d’échec de la lecture vidéo sur le lecteur. Cela vous permet de diffuser le message souhaité à l’audience (en lisant le contenu) au lieu de l’ignorer complètement.

La prise en charge des miniatures vous permet d’effectuer les opérations suivantes :

* Préparez une expérience de canal lorsque les vidéos ne sont pas encore prêtes ou lorsque vous ne souhaitez pas nécessairement tester un téléchargement de ressource volumineux sur les lecteurs.

* Définissez un mécanisme de secours, en cas de problèmes de lecture sur l’appareil.

## Utilisation de miniatures dans les vidéos {#using-thumbnails}

Suivez les étapes ci-dessous pour utiliser des miniatures dans les vidéos :

1. Accédez à un canal Screens existant ou créez-en un.

1. Sélectionnez le canal et cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.

1. Ajoutez ou modifiez un composant vidéo existant, comme illustré dans la figure ci-dessous.

1. Sélectionnez la vidéo et cliquez sur l’icône *clé à molette* pour ouvrir les propriétés vidéo.

1. La boîte de dialogue **Vidéo** s’ouvre, dans laquelle vous pouvez afficher la zone de dépôt **Miniature**.

1. Faites glisser une image du sélecteur de ressources vers la zone de dépôt **Miniature** et cliquez sur **Terminé**.

1. Cliquez sur **Aperçu**.

1. Si une vidéo est définie sur le composant, elle est lue. Si ce n’est pas le cas, et que la miniature est définie, la miniature est lue. Sinon, le composant est considéré comme non configuré et sera ignoré.

## Cas d’utilisation pris en charge lors de l’utilisation de miniatures dans des vidéos {#understand-use-case}

La miniature dans les vidéos prend en charge les cas d’utilisation suivants :

* Un composant vidéo sans configuration sera ignoré.

* Un composant vidéo dont seule la miniature est définie lit la miniature.

* Un composant vidéo avec la vidéo (si la vidéo présente un rendu correct) et la miniature s’affiche.

* Un composant vidéo avec la visionneuse de vidéos lit la miniature, en cas d’erreur de lecture, ou passe simplement à l’élément suivant si la miniature n’est pas configurée.

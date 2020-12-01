---
title: Rapport d’affectation de contenu
description: Cette page décrit le téléchargement et l’utilisation du rapport d’affectation de contenu.
translation-type: tm+mt
source-git-commit: b9091708221f92b11e859f0da8a7080b31b0af77
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 3%

---


# Rapport d’affectation de contenu {#content-assignment-report}

La fonction Rapport d’affectation de contenu permet à un administrateur AEM Screens ou à un auteur d’exporter un rapport *d’affectation de* contenu qui peut être au format tableur.

## Utilisation du rapport d’affectation de contenu {#using-content-assignment-report}

Le rapport Affectation de contenu permet à un auteur AEM Screens ou à un administrateur de télécharger le rapport qui contient tous les actifs, tels que les images et les vidéos, dans tous les Canaux créés dans un projet AEM Screens. En outre, il inclut les informations des canaux entiers affectés à tous les affichages désignés et, dorénavant, tous les périphériques affectés à leurs affichages désignés.

### Utilisation de la fonction de rapport Affectation de contenu{#downloading-content-assignment-report-fp}

#### Configuration du projet {#setting-up-project}

Pour télécharger le rapport d’affectation de contenu à partir d’un projet AEM Screens, procédez comme suit :

1. Create an AEM Screens titled as **DemoScreens**.

1. Créez deux canaux de séquence dans **DemoScreens** tels que **ChannelOne** et **ChannelTwo**.

1. Select **ChannelOne** and click **Edit** from the action bar. Ajoutez peu de ressources (images/vidéos) à ce canal. De même, ajoutez des ressources à **ChannelTwo**.

1. Accédez au dossier Emplacements depuis **DemoScreens** —> **Locations** et créez trois emplacements différents intitulés **SanJose**, **Dublin et SanFrancisco.******

1. Accédez à chacun des emplacements et créez un affichage pour chaque emplacement, par exemple **SanJoseMain** sous **SanJose** , **DublinMain** sous **Dublin emplacement, et SanFranciscoMain sous emplacement SanFrancisco.**********

1. Affectez un périphérique à chacun des écrans.

#### Téléchargement du rapport d’affectation de contenu {#downloading-content-assignment-report}

Une fois que vous avez configuré votre projet AEM Screens et que vous avez affecté des affichages à chacun des emplacements, comme indiqué dans les étapes précédentes.

>[!NOTE]
>La fonction Rapport d’affectation de contenu est accessible uniquement au niveau du projet.

Suivez les instructions ci-dessous pour télécharger le rapport d’affectation de contenu :

1. Navigate to your AEM Screens project and select the project **DemoScreens**.

1. Cliquez sur le rapport Affectation de contenu dans la barre d’actions. Une feuille excel doit être téléchargée sur votre ordinateur local.

   >[!NOTE]
   >La feuille excel téléchargée comprend quatre colonnes, telles que **Canaux**, **Actifs**, **Affichages** et **Périphériques, qui peuvent être utilisées pour étudier plus en détail ces quatre entités.**





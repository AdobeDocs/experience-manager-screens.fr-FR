---
title: Rapport d’affectation de contenu
description: Cette page décrit le téléchargement et l’utilisation du rapport d’affectation de contenu.
translation-type: tm+mt
source-git-commit: b93baeeb26e48b906ee1ddfc034112f8b73615af
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 3%

---


# Rapport d’affectation de contenu {#content-assignment-report}

La fonction Rapport d’affectation de contenu permet à un administrateur AEM Screens ou à un auteur d’exporter un *rapport d’affectation de contenu* au format tableur.

## Utilisation du rapport d&#39;affectation de contenu {#using-content-assignment-report}

Le rapport Affectation de contenu permet à un auteur AEM Screens ou à un administrateur de télécharger le rapport qui contient tous les actifs, tels que les images et les vidéos, dans tous les Canaux créés dans un projet AEM Screens. En outre, il inclut les informations des canaux entiers affectés à tous les affichages désignés et, dorénavant, tous les périphériques affectés à leurs affichages désignés.

Le rapport Affectation de contenu permet non seulement la prévisualisation de tous les Canaux, actifs, écrans et périphériques du projet AEM Screens sélectionné, mais il fournit également une structure de haut niveau de votre projet.

### Utilisation du rapport d’affectation de contenu {#downloading-content-assignment-report-fp}

#### Configuration du projet {#setting-up-project}

Pour télécharger le rapport d’affectation de contenu à partir d’un projet AEM Screens, procédez comme suit :

1. Créez un AEM Screens intitulé **DemoScreens**.

   ![image](/help/user-guide/assets/content-assignment-report/car-1.png)

1. Créez deux canaux de séquence dans **DemoScreens** tels que **ChannelOne** et **ChannelTwo**.

   ![image](/help/user-guide/assets/content-assignment-report/car-2.png)

1. Sélectionnez **ChannelOne** et cliquez sur **Modifier** dans la barre d&#39;actions. Ajoutez peu de ressources (images/vidéos) à ce canal. De même, ajoutez des ressources à **ChannelTwo**.

1. Accédez au dossier Emplacements à partir de **DemoScreens** —> **Emplacements** et créez trois emplacements différents intitulés **SanJose**, **Dublin** et **SanFrancisco**.

   ![image](/help/user-guide/assets/content-assignment-report/car-3.png)

1. Accédez à chacun des emplacements et créez un affichage pour chaque emplacement, par exemple **SanJoseMain** sous **SanJose**, **DublinMain** sous **Dublin** et **SanFranciscoMain** sous **SanFrancisco**.

1. Affectez un périphérique à chacun des écrans.

   >[!NOTE]
   >Pour en savoir plus sur l&#39;affectation d&#39;un canal à un affichage, consultez [Affectation de Canal](/help/user-guide/channel-assignment.md).

#### Téléchargement du rapport d&#39;affectation de contenu {#downloading-content-assignment-report}

Une fois que vous avez configuré votre projet AEM Screens et affecté des affichages à chacun des emplacements, comme indiqué dans les étapes précédentes, vous êtes prêt à télécharger le rapport Affectation de contenu.

>[!NOTE]
>La fonction Rapport d’affectation de contenu est accessible uniquement au niveau du projet.

Suivez les instructions ci-dessous pour télécharger le rapport d’affectation de contenu :

1. Accédez à votre projet AEM Screens et sélectionnez le projet **DemoScreens**.

1. Cliquez sur **Rapport d&#39;affectation de contenu** dans la barre d&#39;actions. Une feuille excel doit être téléchargée sur votre ordinateur local.

   ![image](/help/user-guide/assets/content-assignment-report/can-download.png)

   >[!NOTE]
   >La feuille de calcul téléchargée comprend quatre colonnes, telles que **Canaux**, **Actifs**, **Affichages** et **Appareils**, qui peuvent être utilisés pour étudier plus en détail ces quatre entités se rapportant à votre projet AEM Screens.






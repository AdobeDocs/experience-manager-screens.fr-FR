---
title: Rapport d’affectation de contenu
description: Découvrez le téléchargement et l’utilisation du rapport d’affectation de contenu relatif à AEM Screens.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 27%

---

# Rapport d’affectation de contenu {#content-assignment-report}

La fonction Rapport d’affectation de contenu permet à un administrateur ou à un auteur AEM Screens d’exporter un *rapport d’affectation de contenu* au format tableur.

## Utilisation du rapport d’affectation de contenu {#using-content-assignment-report}

Le rapport d’affectation de contenu permet à un auteur ou à un administrateur AEM Screens de télécharger le rapport qui contient toutes les ressources, telles que les images et les vidéos, dans tous les canaux créés dans un projet AEM Screens. Il inclut également les informations sur l’ensemble des canaux affectés à tous les affichages désignés et désormais tous les périphériques affectés à leurs affichages désignés.

Le rapport d’affectation de contenu permet non seulement de prévisualiser tous les canaux, ressources, écrans et périphériques du projet AEM Screens sélectionné, mais il offre également une structure de haut niveau de votre projet.


### Conditions préalables {#pre-reqs}

Avant de télécharger le rapport d’affectation de contenu, assurez-vous d’avoir configuré un projet AEM Screens avec des canaux, des emplacements et des périphériques.
Pour plus d’informations, consultez les ressources suivantes :

1. [Création et gestion des projets](/help/user-guide/creating-a-screens-project.md)
1. [Création et gestion des canaux](/help/user-guide/managing-channels.md)
1. [Création et gestion des emplacements](/help/user-guide/managing-locations.md)
1. [Création et gestion des affichages](/help/user-guide/managing-displays.md)
1. [Création d’appareils](/help/user-guide/managing-devices.md)
1. [Attribution de canaux](/help/user-guide/channel-assignment-latest-fp.md)


## Téléchargement du rapport d’affectation de contenu {#downloading-content-assignment-report-fp}

Lorsque vous avez configuré votre projet AEM Screens et affecté des affichages à chacun des emplacements, comme indiqué aux étapes précédentes, téléchargez le rapport d’affectation de contenu.

>[!NOTE]
>La fonction Rapport d’affectation de contenu n’est accessible qu’au niveau du projet.

Suivez les instructions ci-dessous pour télécharger le rapport d’affectation de contenu :

1. Accédez à votre projet AEM Screens et cliquez sur le projet . **DemoScreens**.

1. Cliquez sur **Rapport d’affectation de contenu** dans la barre d’actions.

   ![image](/help/user-guide/assets/content-assignment-report/can-download.png)

1. La feuille de calcul téléchargée se compose de deux onglets, **Emplacements** et **Contenu**. L’onglet Emplacement affiche quatre colonnes, telles que **Emplacements**, **Affichages**, **Canaux**, et **Périphériques** qui peut être utilisé pour examiner plus en détail ces quatre entités se rapportant à votre projet AEM Screens.

   ![image](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >Les données affichées dans la feuille de calcul sont triées par ordre alphabétique dans un format facile à lire.

1. Sélectionnez l’un des canaux dans la fonction **Canaux** ouvre la colonne **Contenu** . De son côté, il vous dirige directement vers ce canal et vous donne des informations sur les ressources (images et vidéos) associées à ce canal spécifique.

   ![image](/help/user-guide/assets/content-assignment-report/report-sheet2.png)

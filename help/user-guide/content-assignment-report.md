---
title: Rapport d’attribution de contenu
description: Découvrez le téléchargement et l’utilisation du rapport d’attribution de contenu relatif à AEM Screens.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
TQID: https://experienceleague.adobe.com/Pwq3ebRrbCufXFMk7R-FJj90xq4b7gLOcLvslch2L5o
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 404
ht-degree: 85%

---

# Rapport d’attribution de contenu {#content-assignment-report}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

La fonction Rapport d’affectation de contenu permet à un administrateur ou à un auteur AEM Screens d’exporter un *rapport d’affectation de contenu* au format tableur.

## Utilisation du rapport d’affectation de contenu {#using-content-assignment-report}

Le rapport d’attribution de contenu permet à un auteur ou une autrice, ou à une équipe d’aministration AEM Screens de télécharger le rapport contenant toutes les ressources, comme les images et les vidéos, pour tous les canaux créés dans un projet AEM Screens. En outre, ce rapport contient les informations relatives à l’ensemble des canaux affectés à tous les affichages désignés et, dorénavant, à tous les appareils affectés à leurs affichages désignés.

Le rapport d’attribution de contenu permet non seulement la prévisualisation de tous les canaux, ressources, écrans et appareils du projet AEM Screens sélectionné, mais il apporte également une structure de haut niveau de votre projet.


### Conditions préalables {#pre-reqs}

Avant de télécharger le rapport d’attribution de contenu, assurez-vous d’avoir configuré un projet AEM Screens avec des canaux, des emplacements et des appareils.Pour plus d’informations, référez-vous aux ressources ci-dessous :

1. [Créer et gérer des projets](/help/user-guide/creating-a-screens-project.md)
1. [Création et gestion des canaux](/help/user-guide/managing-channels.md)
1. [Création et gestion des emplacements](/help/user-guide/managing-locations.md)
1. [Création et gestion des affichages](/help/user-guide/managing-displays.md)
1. [Création d’appareils](/help/user-guide/managing-devices.md)
1. [Attribution de canaux](/help/user-guide/channel-assignment-latest-fp.md)


## Téléchargement du rapport d’affectation de contenu {#downloading-content-assignment-report-fp}

Après avoir configuré votre projet AEM Screens et attribué des affichages à chacun des emplacements, comme indiqué aux étapes précédentes, vous pouvez télécharger le rapport d’attribution de contenu.

>[!NOTE]
>La fonction Rapport d’affectation de contenu n’est accessible qu’au niveau du projet.

Suivez les instructions ci-dessous pour télécharger le rapport d’affectation de contenu :

1. Accédez à votre projet AEM Screens et cliquez sur le projet **DemoScreens**.

1. Cliquez sur **Rapport d’attribution de contenu** dans la barre d’actions.

   ![image](/help/user-guide/assets/content-assignment-report/can-download.png)

1. La feuille de calcul téléchargée se compose de deux onglets, tels que **Emplacements** et **Contenu**. L’onglet Emplacements comprend quatre colonnes, **Emplacements**, **Affichages**, **Canaux** et **Appareils**. Vous pouvez examiner plus en détail ces quatre entités se rapportant à votre projet AEM Screens.

   ![image](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >Les données affichées dans la feuille de calcul sont triées par ordre alphabétique dans un format facile à lire.

1. Sélectionnez l’un des canaux dans la colonne **Canaux** pour ouvrir l’onglet **Contenu**. Vous accédez ensuite directement à ce canal et recevez des informations sur les ressources (images et vidéos) associées à ce canal spécifique.

   ![Image](/help/user-guide/assets/content-assignment-report/report-sheet2.png)


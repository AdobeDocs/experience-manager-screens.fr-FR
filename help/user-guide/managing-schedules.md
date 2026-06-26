---
title: Créer et gérer des planifications
description: Découvrez les plannings qui vous permettent d’organiser les canaux en groupes réutilisables afin de ne pas avoir à répéter leur affectation individuellement.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
TQID: https://experienceleague.adobe.com/FJomd-Wz-r8vJZK7PH6wgL4LY3zRmOucBhIbTdjUmQ4
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: ba4275ba-c29a-4197-90dc-5a633402ca3cid: cf6d61d1-acb6-4411-ad1b-25fb57e94db6id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 416
ht-degree: 65%

---

# Créer et gérer des plannings {#creating-and-managing-schedules}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Les **plannings** dans AEM Screens vous permettent d’organiser les canaux en groupes réutilisables. Cela signifie que vous n’avez pas à répéter leur attribution individuellement pour chaque affichage sur lequel vous souhaitez afficher votre contenu.

Lorsqu’ils sont combinés avec des ***tranches horaires***, les plannings permettent de définir une planification globale avec plusieurs canaux qui s’exécutent à des moments spécifiques de la journée et de réutiliser cette configuration pour tous vos affichages simultanément.

>[!NOTE]
>
>Cette fonctionnalité d’AEM Screens est disponible uniquement si vous avez installé le pack de fonctionnalités 1 d’AEM 6.3 Sites. Pour accéder à ce pack de fonctionnalités, contactez l’assistance d’Adobe et demandez à y accéder. Lorsque vous disposez des autorisations nécessaires, vous pouvez le télécharger à partir de Partage de modules.

## Créer un planning {#creating-a-schedule}

Vous pouvez créer pour votre projet Screens un planning qui peut gérer toutes les activités de votre cas d’utilisation.

Suivez les étapes ci-dessous pour créer un planning pour votre canal :

1. Cliquez sur le lien Adobe Experience Manager (en haut à gauche), puis sur Screens. Vous pouvez également utiliser le lien d’accès direct : `http://localhost:4502/screens.html/content/screens`.
1. Accédez au projet Screens et cliquez sur **Planifications**.
1. Cliquez sur **Créer** dans la barre d’actions.
1. Cliquez sur **Planning** dans l’assistant **Créer**, puis sur **Suivant**.

1. Saisissez le **Nom** et le **Titre**, puis cliquez sur **Créer**.

Vous voyez un dossier de plannings avec le nom et le titre de votre projet.


## Afficher le tableau de bord {#viewing-dashboard}

Lorsque vous avez créé le dossier de plannings dans votre projet, vous pouvez afficher les détails du tableau de bord des plannings.

Procédez comme suit pour afficher le tableau de bord des plannings. L’exemple suivant illustre le tableau de bord du projet `We.Retail` :

1. Accédez au dossier **Plannings** du projet Screens (par exemple, `We.Retail`).

   ![chlimage_1](assets/chlimage_1.png)

1. Cliquez sur **Tableau de bord** dans la barre d’actions.

   Trois panneaux s’affichent : **INFORMATIONS SUR LE PLANNING**, **CANAUX ATTRIBUÉS** et **AFFICHAGES ATTRIBUÉS**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Panneau d’informations sur la planification** - Cliquez sur Propriétés dans le coin supérieur droit du panneau d’informations sur la planification pour afficher/modifier les propriétés de la planification.

   **Panneau Canaux attribués** - Cliquez sur +Attribuer un canal dans le coin supérieur droit du panneau CANAUX ATTRIBUÉS pour ouvrir la boîte de dialogue Attribution de canal.

   **Panneau Affichages attribués** - Cliquez sur l’un des affichages du panneau AFFICHAGES ATTRIBUÉS pour ouvrir le tableau de bord d’affichage.


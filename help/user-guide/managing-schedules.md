---
title: Création et gestion des plannings
description: Découvrez les planifications qui vous permettent d’organiser les canaux en groupes réutilisables, de sorte que vous n’ayez pas à répéter leur attribution individuellement.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 76%

---

# Création et gestion des plannings {#creating-and-managing-schedules}

**Planifications** dans AEM Screens vous permet d’organiser les canaux en groupes réutilisables. Cela signifie que vous n’avez pas à répéter leur attribution individuellement pour chaque affichage sur lequel vous souhaitez afficher votre contenu.

Lorsqu’ils sont combinés avec des ***tranches horaires***, les plannings permettent de définir une planification globale avec plusieurs canaux qui s’exécutent à des moments spécifiques de la journée et de réutiliser cette configuration pour tous vos affichages simultanément.

>[!NOTE]
>
>Cette fonctionnalité d’AEM Screens est disponible uniquement si vous avez installé le pack de fonctionnalités 1 d’AEM 6.3 Sites. Pour accéder à ce pack de fonctionnalités, contactez l’assistance d’Adobe et demandez à y accéder. Lorsque vous disposez des autorisations nécessaires, vous pouvez le télécharger à partir de Partage de modules.

## Création d’une planning {#creating-a-schedule}

Vous pouvez créer pour votre projet Screens un planning qui peut gérer toutes les activités de votre cas d’utilisation.

Pour créer un planning pour votre canal, procédez comme suit :

1. Cliquez sur le lien Adobe Experience Manager (en haut à gauche), puis sur Screens. Vous pouvez également utiliser le lien d’accès direct : `http://localhost:4502/screens.html/content/screens`.
1. Accédez au projet Screens et cliquez sur **Planifications**.
1. Cliquez sur **Créer** dans la barre d’actions.
1. Cliquez sur **Planning** dans l’assistant **Créer**, puis sur **Suivant**.

1. Saisissez le **Nom** et le **Titre**, puis cliquez sur **Créer**.

Vous voyez un dossier de plannings avec le nom et le titre de votre projet.


## Affichage du tableau de bord {#viewing-dashboard}

Une fois que vous avez créé un dossier de planifications dans votre projet, vous pouvez afficher les détails à partir du tableau de bord des planifications.

Procédez comme suit pour afficher le tableau de bord des plannings. L’exemple suivant illustre le tableau de bord du projet `We.Retail` :

1. Accédez au dossier **Plannings** du projet Screens (par exemple, `We.Retail`).

   ![chlimage_1](assets/chlimage_1.png)

1. Cliquez sur **Tableau de bord** dans la barre d’actions.

   Trois panneaux s’affichent : **INFORMATIONS SUR LE PLANNING**, **CANAUX ATTRIBUÉS** et **AFFICHAGES ATTRIBUÉS**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Panneau Informations sur le planning** Cliquez sur Propriétés dans le coin supérieur droit du panneau INFORMATIONS SUR LE PLANNING pour afficher/modifier les propriétés du planning.

   **Panneau Canaux attribués** Cliquez sur +Attribuer le canal dans le coin supérieur droit du panneau CANAUX ATTRIBUÉS pour ouvrir la boîte de dialogue Attribution de canaux.

   **Panneau Affichages attribués** Cliquez sur l’un des affichages dans le panneau AFFICHAGES ATTRIBUÉS pour ouvrir le tableau de bord de l’affichage.

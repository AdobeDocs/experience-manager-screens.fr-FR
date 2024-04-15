---
title: Mise à jour de contenu en tant que service
description: Découvrez la mise à jour de contenu en tant que service.
contentOwner: Jyotika syal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: de9f669b-9ce7-4d70-99b4-0b69ef3c1af5
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 68%

---

# Mise à jour de contenu en tant que service {#content-update-as-a-service}

Cette section couvre les sujets suivants relatifs à la mise à jour de contenu en tant que service :

* **Présentation**
* **Utilisation de la mise à jour hors ligne en bloc**

<!--
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permission you can download it from Package Share. -->

## Vue d’ensemble {#overview}

Mise à jour hors ligne en bloc, vous permet de mettre à jour tous les canaux en bloc. Cela évite d’avoir à naviguer vers un canal particulier pour en mettre à jour le contenu. Vous pouvez plutôt mettre à jour tout le contenu des canaux d’un projet spécifique en un seul instant.

Vous pouvez également planifier cette activité pour une période de trafic réseau plus faible.

>[!NOTE]
>
>La fonction Mise à jour hors ligne en bloc est optimisée de manière à ne mettre à jour que les canaux qui ont été modifiés.

## Utilisation de la mise à jour hors ligne en bloc {#using-bulk-offline-update}

Vous pouvez manuellement utiliser la mise à jour hors ligne en bloc à partir de l’interface utilisateur ou programmer la mise à jour en bloc à partir des services OSGi.

### Utilisation de l’interface utilisateur d’AEM Screens {#using-aem-screens-user-interface}

Suivez les étapes ci-dessous pour utiliser la mise à jour hors ligne en bloc pour un projet AEM Screens :

1. Accédez à votre projet AEM Screens.
1. Sélectionnez le projet, puis sélectionnez **Mettre à jour le contenu hors ligne** depuis la barre d’actions pour mettre à jour manuellement le contenu du canal.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configuration de la console Web d’Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Suivez les étapes ci-dessous pour utiliser la mise à jour hors ligne en bloc pour un projet AEM Screens :

1. Configuration de la console Web d’Adobe Experience Manager.
1. Recherchez des services de mise à jour hors ligne en bloc.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Ajoutez les propriétés suivantes :

   **Chemin du projet** Spécifiez le chemin d’accès de votre projet AEM Screens. Le chemin est habituellement `/content/screens/<Name of your project>`.

   *Par exemple*, `/content/screens/we-retail`. Vous pouvez trouver ce chemin dans l’URL en sélectionnant un projet sous AEM Screens (ne sélectionnez pas l’icône).

   >[!NOTE]
   >
   >Spécifiez le chemin du projet par rapport à votre canal.

   **Fréquence des planifications** Indiquez une heure, par exemple, 17 h, à laquelle ce service doit mettre à jour le contenu hors ligne.

1. Sélectionner **Enregistrer** vous pouvez donc enregistrer vos paramètres. Tout votre contenu est mis à jour à l’heure indiquée.

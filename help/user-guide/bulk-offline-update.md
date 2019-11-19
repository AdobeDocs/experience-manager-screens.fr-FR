---
title: Mise à jour hors ligne en bloc
seo-title: Mise à jour hors ligne en bloc
description: Suivez cette page pour savoir comment mettre à jour tous les canaux en bloc.
seo-description: Suivez cette page pour savoir comment mettre à jour tous les canaux en bloc.
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Mise à jour hors ligne en bloc {#bulk-offline-update}

Cette section traite des sujets suivants sur la mise à jour hors ligne en bloc :

* **Présentation**
* **Utilisation de la mise à jour hors ligne en bloc**

>[!CAUTION]
>
>Cette fonctionnalité d’AEM Screens est disponible uniquement si vous avez installé AEM 6.3 Feature Pack 3 ou AEM 6.4 Screens Feature Pack 1.
>
>Pour accéder à ce Feature Pack, vous devez contacter l’assistance d’Adobe et demander à y accéder. Une fois que vous disposez des autorisations, vous pouvez le télécharger à partir de Package Share.

## Présentation {#overview}

Mise à jour hors ligne en bloc, vous permet de mettre à jour tous les canaux en bloc. Cela évite les problèmes de navigation vers un canal particulier et de mise à jour du contenu. Vous pouvez plutôt mettre à jour tout le contenu des canaux d’un projet spécifique en un seul instant.

Vous pouvez également planifier cette activité pour une période de trafic réseau plus faible.

>[!NOTE]
>
>La fonction Mise à jour hors ligne en bloc est optimisée pour mettre à jour uniquement les canaux qui ont été modifiés.

## Utilisation de la mise à jour hors ligne en bloc {#using-bulk-offline-update}

Vous pouvez manuellement utiliser la mise à jour hors ligne en masse à partir de l’interface utilisateur ou programmer la mise à jour en masse à partir des services OSGi.

### Utilisation de l’interface utilisateur d’AEM Screens {#using-aem-screens-user-interface}

Suivez les étapes ci-dessous pour utiliser la mise à jour hors ligne en masse pour un projet AEM Screens :

1. Accédez à votre projet AEM Screens.
1. Sélectionnez le projet et cliquez sur **Mettre à jour le contenu** hors ligne dans la barre d’actions pour mettre à jour manuellement le contenu du canal.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configuration de la console Web d’Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Suivez les étapes ci-dessous pour utiliser la mise à jour hors ligne en masse pour un projet AEM Screens :

1. Configuration de la console Web d’Adobe Experience Manager.
1. Recherchez les services de mise à jour hors ligne en masse.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Ajoutez les propriétés suivantes :

   **Chemin** du projet Spécifiez le chemin d’accès de votre projet AEM Screens. Le chemin est habituellement `/content/screens/<Name of your project>`.

   *Par exemple*, `/content/screens/we-retail`. Vous pouvez trouver ce chemin dans l’URL en sélectionnant un projet sous AEM Screens (ne cliquez pas sur l’icône).

   >[!NOTE]
   >
   >Spécifiez le chemin du projet par rapport à votre canal.

   **Fréquence** de planification Indiquez une heure, par exemple, 17 h ou 17 h, à laquelle ce service doit mettre à jour le contenu hors ligne.

1. Cliquez sur **Enregistrer** pour enregistrer vos paramètres et votre contenu sera mis à jour au moment indiqué.


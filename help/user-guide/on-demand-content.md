---
title: Mise à jour du contenu à la demande
description: Découvrez la mise à jour du contenu à la demande pour la gestion des publications.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 90%

---

# Mise à jour de contenu à la demande {#on-demand}

Cette section décrit le contenu à la demande pour la gestion des publications.

## Gérer la publication : diffuser des mises à jour de contenu de l’auteur à publier sur l’appareil {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Vous pouvez publier le contenu et annuler sa publication à partir d’AEM Screens. **Gérer la publication** vous permet de diffuser des mises à jour de contenu de l’auteur à publier sur l’appareil. Vous pouvez publier/annuler la publication de contenu pour l’ensemble de votre projet AEM Screens ou uniquement pour l’un de vos canaux, emplacements, appareils, applications ou plannings.

### Gérer la publication d’un projet AEM Screens {#managing-publication-for-an-aem-screens-project}

Pour diffuser des mises à jour de contenu de l’instance de création vers l’instance de publication vers l’appareil pour un projet AEM Screens, procédez comme suit :

1. Accédez à votre projet AEM Screens.
1. Cliquez sur **Gérer la publication** dans la barre d’actions pour publier le projet vers l’instance de publication.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. L’assistant **Gérer la publication** démarre. Vous pouvez cliquer sur l’**Action** et également définir l’heure de publication sur maintenant ou plus tard. Cliquez sur **Suivant**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Cochez la case pour cliquer sur l’intégralité du projet dans l’assistant **`Manage Publication`**.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Cliquez sur **+ Inclure les enfants** dans la barre d’actions et décochez toutes les options pour publier tous les modules de votre projet, puis cliquez sur **Ajouter** pour publier.

   >[!NOTE]
   >
   >Par défaut, toutes les cases seront cochées et vous devrez les décocher manuellement pour publier tous les modules de votre projet.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Boîte de dialogue Comprendre l’inclusion des enfants**

   Les étapes mentionnées ci-dessus montrent comment publier l’intégralité du contenu. Si vous voulez utiliser les trois autres alternatives disponibles, vous devez cocher cette option.
Par exemple, l’image suivante montre comment vous pouvez gérer et mettre à jour uniquement les pages modifiées de votre projet :
   ![image](assets/author-publish-manage.png)

   Suivez les explications ci-dessous pour comprendre les options disponibles :

   1. **Inclure uniquement les enfants directs** :
cette option vous permet de gérer les mises à jour uniquement sur les sous-nœuds de la structure de votre projet.
   1. **Inclure uniquement les pages modifiées** :
cette option vous permet de gérer les mises à jour uniquement sur les pages modifiées du projet où les modifications se trouvent dans la structure de votre projet.
   1. **Inclure uniquement les pages déjà publiées** :
cette option vous permet de gérer les mises à jour uniquement sur les pages qui ont déjà été publiées.


1. Dans l’**`Manage Publication wizard`**, cliquez sur **Publier**.

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Patientez quelques secondes/minutes pour que le contenu atteigne l’instance de publication.
   >
   >
   >    1. Le workflow ne fonctionne pas si le projet ne contient aucune modification et qu’il n’y a pas lieu de **mettre à jour le contenu hors ligne**.
   >    1. Le workflow ne fonctionne pas si l’auteur ne termine pas le processus de réplication (le contenu est chargé sur l’instance de publication) après avoir sélectionné le bouton **Publier** dans le workflow de gestion de la publication.

   >[!CAUTION]
   >Si, en tant que créateur ou créatrice de contenu, vous souhaitez voir les modifications apportées aux appareils connectés à l’instance de création, cliquez sur **Mettre à jour le contenu hors ligne** dans le tableau de bord du canal ou en sélectionnant le projet. Dans ce cas, le contenu hors ligne n’est mis à jour que dans l’instance de création.

1. Accédez au projet et cliquez sur **Mettre à jour le contenu hors ligne** dans la barre d’actions. Cette action transfère la même commande à l’instance de publication, de sorte que les fichiers compressés hors ligne soient également créés sur votre instance de publication.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >Une fois que vous avez terminé le workflow de gestion de la publication, et si un lecteur pointe vers l’instance de création, déclenchez la mise à jour du contenu hors ligne dans l’instance de création. La mise à jour hors ligne est créée sur l’instance de création.

   >[!CAUTION]
   >
   >Déclenchez la mise à jour du contenu hors ligne dans l’instance de création si un lecteur est enregistré sur le serveur de création. La mise à jour du contenu hors ligne n’est pas requise pour le lecteur enregistré sur l’instance de publication.

### Gérer la publication d’un canal {#managing-publication-for-a-channel}

Pour diffuser des mises à jour de contenu de l’instance de création vers l’instance de publication puis vers l’appareil pour un canal dans un projet AEM Screens, procédez comme suit :

>[!NOTE]
>
>Suivez cette section uniquement si un canal contient des modifications. Si un canal ne comporte aucune modification après le contenu hors ligne de la mise à jour précédente, le processus de gestion des publications pour un canal individuel ne fonctionne pas.

1. Accédez à votre projet AEM Screens et cliquez sur le canal.
1. Cliquez sur **Gérer la publication** dans la barre d’actions pour publier le canal sur votre instance de publication.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. L’assistant **Gérer la publication** s’ouvre. Vous pouvez cliquer sur l’**Action** et également définir l’heure de publication sur maintenant ou plus tard. Cliquez sur **Suivant**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Cliquez sur **Publier** dans l’assistant **`Manage Publication`**.

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Patientez quelques secondes/minutes pour que le contenu atteigne l’instance de publication.

1. Le déclenchement de **Mettre à jour le contenu hors ligne** dans le tableau de bord du canal envoie le contenu hors ligne vers l’instance de création uniquement, mais pas vers l’instance de publication. Les étapes 1 à 4 permettent d’envoyer le contenu hors ligne vers l’instance de publication.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Publiez d’abord, puis déclenchez la mise à jour du contenu hors ligne, comme indiqué dans les étapes précédentes.

### Réaffectation de canal et d’appareil : {#channel-and-device-re-assignment}

Si vous avez réassigné un appareil, vous devez publier à la fois l’affichage initial et le nouvel affichage, une fois que l’appareil a été réassigné au nouvel affichage.

De même, si vous avez réassigné un canal, vous devez publier à la fois l’affichage initial et le nouvel affichage, une fois que le canal a été réassigné au nouvel affichage.

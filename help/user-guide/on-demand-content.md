---
title: Mise à jour du contenu On-Demand
description: Découvrez la mise à jour de contenu à la demande pour la gestion des publications.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 31%

---

# Mise à jour du contenu On-Demand {#on-demand}

Cette section décrit le contenu On-Demand pour la gestion des publications.

## Gestion de la publication : diffusion de mises à jour de contenu de l’auteur à la publication sur appareil {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Vous pouvez publier et dépublier le contenu à partir d’AEM Screens. La fonction Gérer la publication vous permet de diffuser des mises à jour de contenu de l’auteur à publier sur l’appareil. Vous pouvez publier ou dépublier du contenu pour l’ensemble du projet AEM Screens ou uniquement pour l’un de vos canaux, un de vos emplacements, un de vos appareils, une de vos applications ou un planning.

### Gestion de la publication pour un projet AEM Screens {#managing-publication-for-an-aem-screens-project}

Pour diffuser des mises à jour de contenu de l’auteur à la publication sur appareil pour un projet AEM Screens, procédez comme suit :

1. Accédez à votre projet AEM Screens.
1. Sélectionner **Gérer la publication** à partir de la barre d’actions afin que vous puissiez publier le projet sur votre instance de publication.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. L’assistant de **Gérer la publication** démarre. Vous pouvez sélectionner l’**Action** et programmer l’heure de publication sur maintenant ou plus tard. Sélectionnez **Suivant**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Cochez la case pour pouvoir sélectionner l’ensemble du projet à partir de l’. **`Manage Publication`** assistant.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Sélectionner **+ Inclure les enfants** dans la barre d’actions, désélectionnez toutes les options afin de publier tous les modules de votre projet et sélectionnez **Ajouter** pour publier.

   >[!NOTE]
   >
   >Par défaut, toutes les cases sont cochées et vous devez les décocher manuellement pour publier tous les modules de votre projet.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Comprendre la boîte de dialogue Inclure les enfants**

   Les étapes mentionnées ci-dessus montrent comment publier l’intégralité du contenu. Si vous souhaitez utiliser les trois autres alternatives disponibles, vous devez cocher cette option particulière.
Par exemple, l’image suivante montre comment gérer et mettre à jour uniquement les pages modifiées de votre projet :
   ![image](assets/author-publish-manage.png)

   Suivez les explications ci-dessous pour comprendre les options disponibles :

   1. **Inclure seulement les enfants immédiats**: cette option vous permet de gérer les mises à jour uniquement sur les sous-nœuds de la structure de votre projet.
   1. **Inclure seulement les pages modifiées**: cette option vous permet de gérer les mises à jour uniquement sur les pages modifiées du projet, où les modifications se trouvent dans la structure du projet.
   1. **Inclure seulement les pages déjà publiées**: cette option vous permet de gérer les mises à jour uniquement sur les pages qui ont été publiées précédemment.


1. À partir du **`Manage Publication wizard`**, sélectionnez **Publish**.

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Patientez quelques secondes/minutes pour que le contenu atteigne l’instance de publication.
   >
   >
   >    1. Le workflow ne fonctionne pas s’il n’y a aucune modification dans le projet et rien pour **Mettre à jour le contenu hors ligne**.
   >    1. Le processus ne fonctionne pas si l’auteur n’effectue pas le processus de réplication (le contenu est toujours téléchargé vers l’instance de publication) après avoir cliqué sur le bouton **Publier** dans le processus de gestion de la publication.

   >[!CAUTION]
   >Si, en tant qu’auteur ou créateur de contenu, vous souhaitez voir les modifications apportées aux appareils connectés à l’instance d’auteur, cliquez sur **Mettre à jour le contenu hors ligne** dans le tableau de bord du canal ou en sélectionnant le projet. Dans ce cas, le contenu hors ligne n’est mis à jour que dans l’instance d’auteur.

1. Accédez au projet et cliquez sur **Mettre à jour le contenu hors ligne** dans la barre d’actions. Cette action transfère la même commande vers l’instance de publication, de sorte que les fichiers compressés hors ligne soient également créés sur votre instance de publication.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >Une fois que vous avez terminé le workflow de gestion de publication et qu’il existe un lecteur pointant vers l’instance d’auteur, déclenchez la mise à jour du contenu hors ligne dans l’instance d’auteur. Cela crée la mise à jour hors ligne sur l’instance d’auteur.

   >[!CAUTION]
   >
   >Déclenchez la mise à jour du contenu hors ligne dans l’instance d’auteur si vous avez enregistré un lecteur sur le serveur de création. La mise à jour du contenu hors ligne n’est pas nécessaire pour le lecteur enregistré dans l’instance de publication.

### Gestion de la publication pour un canal {#managing-publication-for-a-channel}

Suivez les étapes ci-dessous pour diffuser des mises à jour de contenu à partir de l’appareil Auteur > Publication > pour un canal dans un projet AEM Screens :

>[!NOTE]
>
>Suivez cette section uniquement si un canal contient des modifications. Si un canal ne comporte aucune modification après le contenu hors ligne de la mise à jour précédente, le processus de gestion des publications pour un canal individuel ne fonctionne pas.

1. Accédez à votre projet AEM Screens et sélectionnez le canal.
1. Sélectionner **Gérer la publication** à partir de la barre d’actions afin que vous puissiez publier le canal sur votre instance de publication.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. L’assistant de **Gérer la publication** démarre. Vous pouvez sélectionner l’**Action** et programmer l’heure de publication sur maintenant ou plus tard. Sélectionnez **Suivant**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Sélectionner **Publish** à partir du **`Manage Publication`** assistant.

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Patientez quelques secondes/minutes pour que le contenu atteigne l’instance de publication.

1. Déclenchement **Mettre à jour le contenu hors ligne** dans le tableau de bord du canal transmet uniquement le contenu hors ligne à l’instance d’auteur, mais pas à l’instance de publication. Les étapes 1 à 4 concernent la publication de contenu hors ligne vers l’instance de publication.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Publiez d’abord, puis déclenchez la mise à jour du contenu hors ligne comme résumé dans les étapes précédentes.

### Réaffectation de canal et d’appareil : {#channel-and-device-re-assignment}

Si vous avez réaffecté un appareil, vous devez publier à la fois l’affichage initial et le nouvel affichage, une fois que l’appareil a été réaffecté au nouvel affichage.

De même, si vous avez réaffecté un canal, vous devez publier à la fois l’affichage initial et le nouvel affichage, une fois le canal réaffecté au nouvel affichage.

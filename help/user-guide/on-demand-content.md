---
title: Mise à jour de contenus à la demande
seo-title: Mise à jour de contenus à la demande
description: 'Suivez cette page pour en savoir plus sur la mise à jour de contenu à la demande.  '
seo-description: 'Suivez cette page pour en savoir plus sur la mise à jour de contenu à la demande.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 7250f7a2150debc12b7cc7acc4193f6d4bd5aa7b

---


# Mise à jour de contenus à la demande {#on-demand}

Cette section décrit le contenu à la demande pour la gestion des publications.

## Gestion de la publication : Diffusion des mises à jour de contenu de l’Auteur à des fins de Publication sur le Périphérique {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Vous pouvez publier et annuler la publication de contenu à partir d’AEM Screens. La fonction Gérer les publications vous permet de diffuser des mises à jour de contenu de l’auteur à la publication sur le périphérique. Vous pouvez publier/annuler la publication de contenu pour l’ensemble de votre projet AEM Screens ou uniquement pour l’un de vos canaux, emplacements, périphériques, applications ou planifications.

### Gestion de la publication pour un projet AEM Screens {#managing-publication-for-an-aem-screens-project}

Suivez les étapes ci-dessous pour diffuser des mises à jour de contenu de l’auteur à la publication sur le périphérique pour un projet AEM Screens :

1. Accédez à votre projet AEM Screens.
1. Cliquez sur **Gérer la publication** dans la barre d’actions pour publier le projet vers l’instance de publication.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. The **Manage Publication** wizard opens. Vous pouvez sélectionner l’ **action** et programmer l’heure de publication pour maintenant ou plus tard. Cliquez sur **Suivant**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Cochez la case pour sélectionner l’intégralité du projet dans l’assistant **Gérer la publication** .

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Cliquez sur **+ Inclure les enfants** dans la barre d’actions et désactivez toutes les options pour publier tous les modules de votre projet, puis cliquez sur **Ajouter** pour publier.

   >[!NOTE]
   >
   >Par défaut, toutes les cases seront cochées et vous devrez les décocher manuellement pour publier tous les modules de votre projet.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Boîte de dialogue Inclure les enfants**

   L’étape mentionnée ci-dessus montre comment publier l’intégralité du contenu. Si vous voulez utiliser les trois autres alternatives disponibles, vous devrez vérifier cette option.
Par exemple, l’image suivante vous permet de gérer et de mettre à jour uniquement les pages modifiées de votre projet :
   ![image](assets/author-publish-manage.png)

   Suivez les explications ci-dessous pour comprendre les options disponibles :

   1. **Inclure uniquement les enfants**immédiats :
Cette option vous permet de gérer les mises à jour uniquement sur les sous-noeuds de la structure de votre projet.
   1. **Inclure uniquement les pages**modifiées :
Cette option vous permet de gérer les mises à jour uniquement sur les pages modifiées du projet où les modifications sont trouvées dans la structure du projet.
   1. **Inclure uniquement les pages**déjà publiées :
Cette option permet de gérer les mises à jour uniquement sur les pages qui ont été publiées auparavant.


1. Cliquez sur **Publier** dans l’assistant **Gérer la publication.**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Patientez quelques secondes/minutes pour que le contenu atteigne l’instance de publication.
   >
   >
   >    1. Le flux de travail ne fonctionne pas s’il n’y a aucune modification dans le projet et rien pour **mettre à jour le contenu** hors ligne.
   >    1. Le flux de travaux ne fonctionne pas si l’auteur n’effectue pas le processus de réplication (le contenu est toujours téléchargé vers l’instance de publication) après avoir cliqué sur le bouton **Publier** dans le processus de gestion de la publication.


   > [!CAUTION]
   > Si, en tant qu’auteur ou créateur de contenu, vous souhaitez voir les modifications apportées aux périphériques connectés à l’instance d’auteur, cliquez sur **Mettre à jour le contenu** hors ligne à partir du tableau de bord du canal ou en sélectionnant le projet. Dans ce cas, le contenu hors ligne de la mise à jour n’est exécuté que dans l’instance d’auteur.

1. Accédez au projet et cliquez sur **Mettre à jour le contenu** hors ligne dans la barre d’actions. Cette action transfère la même commande à l’instance de publication, de sorte que les fichiers compressés hors ligne soient également créés sur l’instance de publication.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >Une fois que vous avez terminé le processus de gestion de la publication et qu’un lecteur pointe vers l’instance d’auteur, vous devez déclencher le contenu hors ligne de la mise à jour dans l’instance d’auteur, qui crée la mise à jour hors ligne sur l’instance d’auteur.

   >[!CAUTION]
   >
   >Vous devez déclencher la mise à jour du contenu hors ligne dans l’instance d’auteur, si un lecteur est enregistré sur le serveur d’auteur. La mise à jour du contenu hors ligne n’est pas requise pour le lecteur enregistré sur l’instance de publication.

### Gestion des publications pour un canal {#managing-publication-for-a-channel}

Suivez les étapes ci-dessous pour diffuser des mises à jour de contenu de l’auteur à la publication sur l’appareil pour un canal dans un projet AEM Screens :

>[!NOTE]
>
>Suivez cette section uniquement si un canal contient des modifications. Si un canal ne comporte aucune modification après le contenu hors ligne de la mise à jour précédente, le processus de gestion des publications pour un canal individuel ne fonctionne pas.

1. Accédez à votre projet d’écrans et sélectionnez le canal.
1. Cliquez sur **Gérer la publication** dans la barre d’actions pour publier le canal vers l’instance de publication.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. The **Manage Publication** wizard opens. Vous pouvez sélectionner l’ **action** et programmer l’heure de publication pour maintenant ou plus tard. Cliquez sur **Suivant**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Cliquez sur **Publier** dans l’assistant **Gérer la publication.**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Patientez quelques secondes/minutes pour que le contenu atteigne l’instance de publication.

1. Une fois que vous avez terminé le processus de gestion de la publication, vous devez déclencher le contenu hors ligne de la mise à jour dans l’auteur, qui crée la mise à jour hors ligne sur l’instance d’auteur.

   Accédez au tableau de bord du canal et cliquez sur **Mettre à jour le contenu** hors ligne. Cette action transfère la même commande à l’instance de publication, de sorte que les fichiers compressés hors ligne soient également créés sur l’instance de publication.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Vous devez d’abord publier, puis déclencher la mise à jour du contenu hors ligne, comme l’indiquent les étapes précédentes.

### Réaffectation de canal et de périphérique : {#channel-and-device-re-assignment}

Si vous avez réaffecté un périphérique, vous devez publier à la fois l’affichage initial et le nouvel affichage, une fois le périphérique réaffecté au nouvel affichage.

De même, si vous avez réaffecté un canal, vous devez publier à la fois l’affichage initial et le nouvel affichage, une fois que le canal a été réaffecté au nouvel affichage.
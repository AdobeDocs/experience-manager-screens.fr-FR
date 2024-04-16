---
title: Mise à jour du contenu On-Demand
description: Découvrez la mise à jour du contenu On-Demand pour la gestion des publications.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 24%

---

# Mise à jour du contenu On-Demand {#on-demand}

Cette section décrit le contenu On-Demand pour la gestion des publications.

## Gestion de la publication : diffusion des mises à jour de contenu de l’auteur à la publication sur le périphérique {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Vous pouvez publier et dépublier le contenu à partir d’AEM Screens. La fonction Gérer la publication vous permet de diffuser des mises à jour de contenu de l’auteur à publier sur le périphérique. Vous pouvez publier/annuler la publication de contenu pour l’ensemble du projet AEM Screens ou uniquement pour l’un de vos canaux, emplacement, périphérique, application ou planification.

### Gestion de la publication pour un projet AEM Screens {#managing-publication-for-an-aem-screens-project}

Suivez les étapes ci-dessous pour diffuser des mises à jour de contenu de l’auteur à la publication sur le périphérique pour un projet AEM Screens :

1. Accédez à votre projet AEM Screens.
1. Cliquez sur **Gérer la publication** à partir de la barre d’actions afin de pouvoir publier le projet sur votre instance de publication.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. L’assistant de **Gérer la publication** démarre. Vous pouvez cliquer sur le bouton **Action** et planifiez également l’heure de publication pour maintenant ou plus tard. Cliquez sur **Suivant**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Cochez la case pour que vous puissiez cliquer sur l’intégralité du projet à partir de la **`Manage Publication`** assistant.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Cliquez sur **+ Inclure les enfants** dans la barre d’actions et désélectionnez toutes les options afin de publier tous les modules de votre projet, puis cliquez sur **Ajouter** pour publier.

   >[!NOTE]
   >
   >Par défaut, toutes les cases sont cochées et vous devez les décocher manuellement pour publier tous les modules de votre projet.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Comprendre la boîte de dialogue Inclure les enfants**

   Les étapes mentionnées ci-dessus montrent comment publier l’intégralité du contenu. Si vous souhaitez utiliser les trois autres alternatives disponibles, vous devez cocher cette option particulière.
Par exemple, l’image suivante montre comment gérer et mettre à jour uniquement les pages modifiées de votre projet :
   ![image](assets/author-publish-manage.png)

   Suivez les explications ci-dessous pour comprendre les options disponibles :

   1. **Inclure uniquement les enfants immédiats**: cette option vous permet de gérer les mises à jour uniquement sur les sous-noeuds de la structure de votre projet.
   1. **Inclure uniquement les pages modifiées**: cette option vous permet de gérer les mises à jour uniquement sur les pages modifiées du projet où les modifications se trouvent dans la structure de votre projet.
   1. **Inclure uniquement les pages déjà publiées**: cette option permet de gérer les mises à jour uniquement sur les pages qui ont été publiées auparavant.


1. Dans la **`Manage Publication wizard`**, cliquez sur **Publier**.

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Patientez quelques secondes/minutes pour que le contenu atteigne l’instance de publication.
   >
   >
   >    1. Le workflow ne fonctionne pas s’il n’y a aucune modification dans le projet et rien pour **Mettre à jour le contenu hors ligne**.
   >    1. Le processus ne fonctionne pas si l’auteur n’effectue pas le processus de réplication (le contenu est toujours téléchargé vers l’instance de publication) après avoir sélectionné la variable **Publier** dans le workflow de gestion des publications.

   >[!CAUTION]
   >Si, en tant qu’auteur ou créateur de contenu, vous souhaitez voir les modifications apportées aux appareils connectés à l’instance d’auteur, cliquez sur **Mettre à jour le contenu hors ligne** dans le tableau de bord du canal ou en sélectionnant le projet. Dans ce cas, le contenu hors ligne n’est mis à jour que dans l’instance d’auteur.

1. Accédez au projet et cliquez sur **Mettre à jour le contenu hors ligne** dans la barre d’actions. Cette action transfère la même commande à l’instance de publication, de sorte que les fichiers compressés hors ligne soient également créés sur votre instance de publication.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >Une fois que vous avez terminé le processus de gestion de la publication, et si un lecteur pointe vers l’instance d’auteur, déclenchez la mise à jour du contenu hors ligne dans l’auteur. Cela crée la mise à jour hors ligne sur l’instance d’auteur.

   >[!CAUTION]
   >
   >Déclenchez la mise à jour du contenu hors ligne dans l’instance d’auteur si un lecteur est enregistré sur le serveur de création. La mise à jour du contenu hors ligne n’est pas requise pour le lecteur enregistré sur l’instance de publication.

### Gestion des publications pour un canal {#managing-publication-for-a-channel}

Suivez les étapes ci-dessous pour diffuser des mises à jour de contenu à partir de l’instance Auteur > Publier > Appareil pour un canal dans un projet AEM Screens :

>[!NOTE]
>
>Suivez cette section uniquement si un canal contient des modifications. Si un canal ne comporte aucune modification après le contenu hors ligne de la mise à jour précédente, le processus de gestion des publications pour un canal individuel ne fonctionne pas.

1. Accédez à votre projet AEM Screens et cliquez sur le canal.
1. Cliquez sur **Gérer la publication** à partir de la barre d’actions afin de pouvoir publier le canal sur votre instance de publication.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. L’assistant de **Gérer la publication** démarre. Vous pouvez cliquer sur le bouton **Action** et planifiez également l’heure de publication pour maintenant ou plus tard. Cliquez sur **Suivant**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Cliquez sur **Publier** de la **`Manage Publication`** assistant.

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Patientez quelques secondes/minutes pour que le contenu atteigne l’instance de publication.

1. Déclenchement **Mettre à jour le contenu hors ligne** dans le tableau de bord du canal envoie uniquement le contenu hors ligne à l’instance d’auteur, mais pas à l’instance de publication. Les étapes 1 à 4 permettent de transférer du contenu hors ligne vers l’instance de publication.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Publiez d’abord, puis déclenchez la mise à jour du contenu hors ligne, comme indiqué dans les étapes précédentes.

### Réaffectation de canal et de périphérique : {#channel-and-device-re-assignment}

Si vous avez réaffecté un appareil, publiez l’affichage initial et le nouvel affichage, une fois que l’appareil a été réaffecté au nouvel affichage.

De même, si vous avez réaffecté un canal, publiez à la fois l’affichage initial et le nouvel affichage, une fois le canal réaffecté au nouvel affichage.

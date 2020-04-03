---
title: Application d’une marque et d’un style personnalisés pour les incrustations de texte
seo-title: Application d’une marque et d’un style personnalisés pour les incrustations de texte
description: Suivez cette page pour savoir comment appliquer une marque et un style personnalisés pour les incrustations de texte.
seo-description: Suivez cette page pour savoir comment appliquer une marque et un style personnalisés pour les incrustations de texte.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: f91faa23c7c5c4f0f705c77251554b64efaf2611

---


# Marque et style personnalisés pour les incrustations de texte {#creating-custom-branding-styling}

Suivez cette page pour savoir comment appliquer une marque et un style personnalisés pour les incrustations de texte.

## Création d’une marque et d’un style personnalisés pour les incrustations de texte {#steps-custom-branding}

Suivez les étapes ci-dessous pour créer une marque et un style personnalisés pour les incrustations de texte :

1. Créez un projet AEM Screens intitulé **customstyle** et un intitulé **DemoBrand**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. A partir de l’éditeur, faites glisser une image et ajoutez une incrustation de texte au fichier.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Pour savoir comment ajouter une incrustation de texte à votre fichier dans un éditeur de , reportez-vous à la section Incrustation de [texte](/help/user-guide/text-overlay.md).

1. Accédez à CRXDE Lite à partir de votre instance AEM --> Outils --> **CRXDE Lite**.

1. Vous devez créer une conception personnalisée dans `/apps/settings/wcm/designs/<your-project>/`, par exemple, dans ce cas.

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Accédez au fichier static.css et définissez les règles CSS suivantes. Également illustré dans la figure ci-dessous.

   ```shell
    //global styles
    .cq-Screens-textOverlay
    { … }
    //authoring overrides
    .aem-AuthorLayer-Edit .cq-Screens-textOverlay { … }
    // light text variant
    .cq-Screens-textOverlay-color--light
    { … }
     // dark text variant
    .cq-Screens-textOverlay-color--dark { … }
   ```
   ![image](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Copiez le chemin vers votre projet, dans ce cas, le chemin sera `/apps/settings/wcm/designs/customstyle`.

1. Accédez au  de intitulé **DemoBrand** (créé à l’étape(1)) et cliquez sur **Propriétés** dans la barre d’actions après avoir sélectionné le .

1. Accédez à l’onglet **Avancé** et vérifiez le champ **Conception** .
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Par défaut, le champ **Conception** affiche le chemin pointant vers les conceptions du dossier libs.

1. Mettez à jour le champ **Conception** avec le chemin d’accès au dossier du projet. Dans ce cas, ce sera le cas `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Cliquez sur **Enregistrer et fermer** pour mettre à jour le chemin de conception.


## Affichage du résultat {#viewing-the-result}

Une fois les étapes précédentes terminées, vous pouvez mettre à jour votre fichier *statis.css* à partir de **CRXDE Lite** et, par conséquent,  la mise à jour de votre mise en page de texte ajoutée à la ressource.

Suivez les étapes ci-dessous pour de la conception mise à jour à la mise en page de texte :

1. Accédez à votre projet AEM Screens intitulé **customstyle** et à un  intitulé **DemoBrand** , puis cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.

1. Comme vous avez maintenant ajouté la conception à votre champ **Conceptions** , comme mentionné ci-dessus, cliquez sur **** pour  la mise en forme actuelle de l’image avec l’incrustation de texte.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Accédez à votre fichier static.css dans CRXDE Lite, par exemple, ajoutez la police.
   ![image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Une fois que vous avez enregistré les modifications et rechargé le, vous verrez une mise à jour de la police d’incrustation de texte, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. De plus, vous pouvez supprimer les deux derniers blocs de code du fichier static.css pour supprimer la mise en forme encadrée autour de l’incrustation de texte.
   ![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Vous allez  la modification mise à jour dans votre  où l’incrustation de texte est ajoutée à l’image, comme illustré ci-dessous.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

Ainsi, en suivant les étapes des sections précédentes, vous pouvez mettre à jour votre marque et votre style personnalisé pour les incrustations de texte ajoutées à vos fichiers.










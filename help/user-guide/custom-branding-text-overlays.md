---
title: Application d’une valorisation de marque et de styles personnalisés aux superpositions de texte
description: Découvrez comment appliquer une valorisation de marque et des styles personnalisés aux superpositions de texte appliquées aux ressources d’un canal AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 44%

---

# Image de marque et styles personnalisés pour les superpositions de texte {#creating-custom-branding-styling}

Découvrez comment appliquer une valorisation de marque et des styles personnalisés aux superpositions de texte appliquées à vos ressources dans un canal AEM Screens.

## Création d’une image de marque et de styles personnalisés pour les superpositions de texte {#steps-custom-branding}

Pour créer une valorisation de marque et des styles personnalisés pour les superpositions de texte :

1. Créez un projet AEM Screens. Cet exemple présente la fonctionnalité en créant un projet nommé **`customstyle`** et un canal intitulé **DemoBrand**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dans l’éditeur, faites glisser une image et ajoutez une superposition de texte à la ressource.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Pour savoir comment ajouter une superposition de texte à votre ressource dans un éditeur de canal, voir [Superposition de texte](/help/user-guide/text-overlay.md).

1. Accédez à CRXDE Lite à partir de votre instance AEM > Outils > **CRXDE Lite**.

1. Créez une conception personnalisée dans `/apps/settings/wcm/designs/<your-project>/`, par exemple, dans ce cas, accédez à `/apps/settings/wcm/designs/customstyle/`

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Créez un *static.css* et définissez les règles CSS suivantes. À ce propos, la figure ci-dessous illustre un exemple de règles CSS.

   ```shell
    //global styles
    cq-Screens-textOverlay {
    padding: 1em;
    font-size: 3rem;
    line-height: 1em;
     }
    //authoring overrides
   .aem-AuthorLayer-Edit .cq-Screens-textOverlay {
    display: none;
    padding: 0;
    font-size: 1rem;
    }
     // light text variant
    .cq-Screens-textOverlay-color--light {
     background-color: rgba(0, 0, 0, .6);
     }
     // dark text variant
     .cq-Screens-textOverlay-color--dark {
      background-color: rgba(255, 255, 255, .6);
    }
   ```

   ![image](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Copiez le chemin vers votre projet. Dans ce cas, le chemin est : `/apps/settings/wcm/designs/customstyle`.

1. Accédez au canal intitulé **DemoBrand** (créé à l’étape(1)), puis cliquez sur **Propriétés** dans la barre d’actions après avoir sélectionné le canal.

1. Accédez à l’onglet **Avancé** et cliquez sur le champ **Conception**.
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Par défaut, la variable **Conception** affiche le chemin pointant vers les conceptions dans le dossier libs .

1. Mettez à jour le champ **Conception** en indiquant le chemin d’accès de votre dossier de projet. En l’occurrence, il s’agit de `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Cliquez sur **Enregistrer et fermer** pour mettre à jour le chemin de la conception.

   >[!IMPORTANT]
   >Vous pouvez éventuellement superposer les modèles Screens existants pour injecter vos propres conceptions par défaut ou créer entièrement votre propre modèle. Pour plus d’informations, suivez les étapes ci-dessous.

1. Pour superposer les modèles Screens existants afin d’incorporer vos propres conceptions par défaut :

   1. Superposez `/libs/screens/core/templates/sequencechannel` à `/apps/screens/core/templates/sequencechannel`.
   1. Modifiez la variable *`cq:designPath`* dans `/apps/screens/core/templates/sequencechannel/jcr:content` pour qu&#39;il pointe vers la nouvelle conception.

1. Pour créer intégralement votre propre modèle :
   1. Copiez `/libs/screens/core/templates/sequencechannel` dans `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifiez la variable *`cq:designPath`* dans `/apps/customstyle/templates/styled-sequencechannel/jcr:content` pour qu&#39;il pointe vers la nouvelle conception.


### Mise à jour des ACL {#updating-acls}

Mettez à jour les listes de contrôle d’accès de ces conceptions afin que le lecteur puisse les télécharger.

1. Accédez à la page d’administration des utilisateurs, sélectionnez le fichier `screens-<project>-devices group` et autorisez-le à accéder en lecture au chemin de conception personnalisé.

1. Accordez au groupe `screens-<project>-administrators` des autorisations de lecture et de modification sur ce chemin.

## Afficher le résultat {#viewing-the-result}

Une fois les étapes précédentes terminées, vous pouvez mettre à jour votre *static.css* fichier à partir de **CRXDE Lite** et, par conséquent, afficher la mise à jour de la superposition de texte déjà ajoutée à la ressource.

Pour voir la conception mise à jour avec la superposition de texte, procédez comme suit :

1. Accédez à votre projet AEM Screens intitulé **`customstyle`** > **Canaux** > **DemoBrand**. Cliquez sur le canal, puis sur **Modifier** dans la barre d’actions.

1. La conception ayant été ajoutée à votre champ **Conceptions** comme mentionné ci-dessus, cliquez sur **Aperçu** pour voir les styles actuels de l’image avec la superposition de texte.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Accédez à votre fichier *static.css* dans CRXDE Lite, puis ajoutez la police, par exemple `font-family: "Lucida Console", Courier, monospace;`, à ce fichier, comme illustré ci-dessous.

   ![image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Lorsque vous enregistrez les modifications et rechargez l’aperçu, une mise à jour de la police de superposition de texte s’affiche, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. En outre, vous pouvez supprimer les deux derniers blocs de code du *static.css* pour supprimer le style encadré autour de la superposition de texte.

![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Affichez la modification mise à jour dans l’aperçu où la superposition de texte est ajoutée à l’image.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Vous êtes maintenant prêt à mettre à jour votre marque et votre style personnalisé pour les superpositions de texte ajoutées à vos ressources.

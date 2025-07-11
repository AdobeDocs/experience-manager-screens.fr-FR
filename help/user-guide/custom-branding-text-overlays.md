---
title: Application d’une image de marque et de styles personnalisés aux superpositions de texte
description: Découvrez comment appliquer une image de marque et des styles personnalisés aux superpositions de texte de vos ressources dans un canal AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 96%

---

# Image de marque et styles personnalisés pour les superpositions de texte {#creating-custom-branding-styling}

Découvrez comment appliquer une image de marque et des styles personnalisés aux superpositions de texte de vos ressources dans un canal AEM Screens.

## Création d’une image de marque et de styles personnalisés pour les superpositions de texte {#steps-custom-branding}

Pour créer une valorisation de marque et des styles personnalisés pour les superpositions de texte :

1. Créez un projet AEM Screens. Cet exemple illustre la fonctionnalité en créant un projet nommé **`customstyle`** et un canal intitulé **DemoBrand**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. Dans l’éditeur, faites glisser et déposez une image, puis ajoutez une superposition de texte à la ressource.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Pour savoir comment ajouter une superposition de texte à votre ressource dans un éditeur de canal, voir [Superposition de texte](/help/user-guide/text-overlay.md).

1. Accédez à CRXDE Lite à partir de votre instance AEM > Outils > **CRXDE Lite**.

1. Créez une conception personnalisée dans `/apps/settings/wcm/designs/<your-project>/`, par exemple. Dans le cas présent, accédez à `/apps/settings/wcm/designs/customstyle/`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Créez le fichier *static.css* et définissez les règles CSS suivantes. À ce propos, la figure ci-dessous illustre un exemple de règles CSS.

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

1. Copiez le chemin vers votre projet. Dans le cas présent, ce chemin est `/apps/settings/wcm/designs/customstyle`.

1. Accédez au canal intitulé **DemoBrand** (créé à l’étape(1)), puis cliquez sur **Propriétés** dans la barre d’actions après avoir sélectionné le canal.

1. Accédez à l’onglet **Avancé** et cliquez sur le champ **Conception**.
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Par défaut, le champ **Conception** affiche le chemin pointant vers les conceptions du dossier de bibliothèques.

1. Mettez à jour le champ **Conception** en indiquant le chemin d’accès de votre dossier de projet. En l’occurrence, il s’agit de `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Cliquez sur **Enregistrer et fermer** pour mettre à jour le chemin de la conception.

   >[!IMPORTANT]
   >Vous pouvez effectuer une superposition des modèles Screens existants pour incorporer vos propres conceptions par défaut ou créer intégralement votre propre modèle. Pour plus d’informations, suivez les étapes ci-dessous.

1. Pour superposer les modèles Screens existants afin d’incorporer vos propres conceptions par défaut :

   1. Superposez `/libs/screens/core/templates/sequencechannel` à `/apps/screens/core/templates/sequencechannel`.
   1. Modifiez la propriété *`cq:designPath`* dans `/apps/screens/core/templates/sequencechannel/jcr:content` pour qu’elle pointe vers la nouvelle conception.

1. Pour créer intégralement votre propre modèle :
   1. Copiez `/libs/screens/core/templates/sequencechannel` dans `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifiez la propriété *`cq:designPath`* dans `/apps/customstyle/templates/styled-sequencechannel/jcr:content` pour qu’elle pointe vers la nouvelle conception.


### Mise à jour des ACL {#updating-acls}

Mettez à jour les listes de contrôle d’accès de ces conceptions afin que le lecteur puisse les télécharger.

1. Accédez à la page d’administration des utilisateurs, sélectionnez le fichier `screens-<project>-devices group` et autorisez-le à accéder en lecture au chemin de conception personnalisé.

1. Accordez au groupe `screens-<project>-administrators` des autorisations de lecture et de modification sur ce chemin.

## Afficher le résultat {#viewing-the-result}

Après avoir suivi les étapes précédentes, vous pouvez mettre à jour le fichier *static.css* à partir de **CRXDE Lite** et ainsi voir la mise à jour de la superposition de texte déjà ajoutée à la ressource.

Pour voir la conception mise à jour avec la superposition de texte, procédez comme suit :

1. Accédez à votre projet AEM Screens intitulé **`customstyle`** > **Canaux** > **DemoBrand**. Cliquez sur le canal, puis sur **Modifier** dans la barre d’actions.

1. La conception ayant été ajoutée à votre champ **Conceptions** comme mentionné ci-dessus, cliquez sur **Aperçu** pour voir les styles actuels de l’image avec la superposition de texte.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Accédez à votre fichier *static.css* dans CRXDE Lite, puis ajoutez la police telle que `font-family: "Lucida Console", Courier, monospace;` à ce fichier, comme illustré ci-dessous.

   ![Image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Lorsque vous enregistrez les modifications et chargez à nouveau la prévisualisation, vous voyez une mise à jour de la police de superposition de texte, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Vous pouvez également supprimer les deux derniers blocs de code du fichier *static.css* pour supprimer le style encadré autour de la superposition de texte.

![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Voyez la modification mise à jour dans la prévisualisation, avec la superposition de texte ajoutée à l’image.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Vous pouvez à présent mettre à jour votre marque et à appliquer votre style personnalisé pour les superpositions de texte ajoutées à vos ressources.

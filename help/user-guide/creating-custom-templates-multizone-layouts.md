---
title: Création de modèles personnalisés dans des dispositions multizones
description: Découvrez comment créer des modèles personnalisés dans les dispositions MultiZone pour AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: c142830a37461a36baae15f543bd43b0ae8a62a7
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 30%

---

# Création de modèles personnalisés pour des dispositions multizones {#creating-custom-templates-multizone}

Cette page explique comment créer un modèle personnalisé dans une disposition multizone.

## Points importants {#considerations}

Avant de créer un modèle personnalisé dans une disposition multizone, vous devez tenir compte de deux points importants :

1. **Taille fixe en pixels ou taille en pourcentages** :

   Choisissez d’utiliser une taille de pixels fixe pour différentes zones pour votre disposition personnalisée ou de créer une disposition personnalisée à l’aide de pourcentages.

   >[!NOTE]
   >L’utilisation d’un pourcentage pour définir des zones pour votre disposition personnalisée vous permet de réutiliser le modèle sur différentes tailles d’écran.

1. **Convention d’affectation de noms** :

   Avant de comprendre comment créer des modèles multizones personnalisés à utiliser dans un projet AEM Screens, vous devez connaître le libellé des modèles que vous souhaitez créer.

   | **Nom de la disposition** | **Description** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | Disposition paysagère à trois zones permettant de créer trois zones :<br>* Zone 1 comme 20% de l&#39;écran horizontal et vertical de la gauche<br>* La zone 2 représente 80 % de l&#39;écran horizontal et 20 % de l&#39;écran vertical à droite<br>* Zone 3 comme 100 % de l&#39;écran horizontal et 80 % de l&#39;écran vertical avec rapport d&#39;aspect de 16:9 |
   | `Upper20-PortraitHD2Zone` | Modèle de portrait en deux zones qui couvre 20 % de l’écran depuis le haut, avec un format de 16:9 |
   | `Right20-LandscapeSD3Zone` | Modèle à trois zones qui couvre 20 % de l’écran depuis la droite, avec un format de 4:3 |

   >[!IMPORTANT]
   >Les zones définies dans la disposition personnalisée ne correspondent pas nécessairement aux proportions globales de l’ensemble de la disposition. La convention d’affectation de noms appliquée dans ce document définit les proportions de l’ensemble de la disposition personnalisée.

## Exemple de cas d’utilisation `Left20-LandscapeHD3Zone` Disposition {#custom-template-one}

Suivez la section ci-dessous pour créer un modèle personnalisé *`Left20-LandscapeHD3Zone`* avec la configuration suivante :

* **`Left20`** - Zone supérieure sur la gauche couvrant 20 % de la taille de l’écran horizontal et vertical.
* **`Landscape`** - Orientation de l’écran
* **`HD`** - Le rapport d’aspect est de 16:9.
* **`3Zone`** - Trois zones de l&#39;affichage.

## Représentation visuelle de la disposition multizone {#multi-layout-visual-one}

Le `Left20-LandscapeHD3Zone` La disposition permet de créer la disposition multizone suivante dans votre projet :

![image](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Création d’un `Left20-LandscapeHD3Zone` Disposition {#landscape-layout-one}

Suivez les étapes ci-dessous pour créer un `Left20-LandscapeHD3Zone` Mise en page d’un projet AEM Screens.

1. Créez un projet AEM Screens appelé . **`customtemplate`**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Accéder à **CRXDE Lite** depuis votre instance AEM > Outils > **CRXDE Lite**.

1. Créez un dossier sous **applications** intitulé **`customtemplate`**. De même, créez un autre dossier appelé . **modèle** sous **`customtemplate`**, comme le montre la figure ci-dessous.

   ![image](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >Sélectionner **Enregistrer tout** à partir de la barre d’actions du CRXDE Lite chaque fois que vous créez, modifiez ou copiez du contenu vers l’un des nœuds . Sinon, vous ne pouvez pas valider les mises à jour.

1. Copiez le modèle de la barre de gauche depuis `/libs/screens/core/templates/splitscreenchannel/lbar-left` vers `/apps/customtemplate/template`.

1. Renommez la **barre de gauche** copiée (`/apps/customtemplate/template`) en indiquant **my-custom-layout**.
   ![image](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Accéder à `/apps/customtemplate/template/my-custom-layout` et mettez à jour les propriétés **`jcr:description`** vers *Modèle pour`Left20-LandscapeHD3Zone`* et **`jcr:title`** vers *`Left20-LandscapeHD3Zone`*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Accédez à l’ **`offline-config`** nœud à partir de `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` et mettez à jour le **`jcr:title`** vers *`Left20-LandscapeHD3Zone`*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Accédez à l’ *`jcr:content`* propriété de **my-custom-template** de `/apps/customtemplate/template/my-custom-layout/jcr:content` et mettez à jour le **`cq:cssClass`** pour que vous puissiez utiliser **aem-Layout-my-custom-layout**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. En vous référant à l’étape (4) au cours de laquelle vous avez copié le modèle lbar-left, vous pouvez afficher trois grilles réactives sous `my-custom-layout/jcr:content`. Ajoutez une classe CSS personnalisée à chacune des grilles réactives du *`cq:cssClass`* propriété , par exemple, *my-custom-layout—top-left* pour *r1c1* nœud.

   ![image](/help/user-guide/assets/custom-multizone/custom-template7.png)

   De même, ajoutez *my-custom-layout--top-right* pour *r1c2* et *my-custom-layout--bottom* pour le nœud *r2c1*.

   >[!NOTE]
   >Ces classes personnalisées sont utilisées dans le CSS pour définir la largeur/hauteur de ces grilles réactives.

   >[!NOTE]
   >Vous pouvez ajouter ou supprimer les grilles réactives en fonction du nombre total de grilles souhaité. Dans cet exemple, deux grilles de la première ligne et une grille de la deuxième ligne sont mises en surbrillance, il y a donc au total trois grilles réactives (r1c1, r1c2, r2c1).

1. Copiez `/libs/settings/wcm/designs/screens` dans `/apps/settings/wcm/designs/` et renommez la conception copiée **custom-template-designs**.

1. Accéder à `/apps/settings/wcm/designs/custom-template-designs` et mettez à jour la propriété . *`jcr:title`* de **custom-template-designs** vers **customtemplate-design**.

1. Accédez à `/apps/settings/wcm/designs/custom-template-designs` et créez un fichier static.css.

1. Copiez le contenu dans le fichier `static.css` :

   ```shell
       /*my-custom-layout styles*/
      .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-left {
       width:20%;
       height: 36%;
      float: left !important;
      }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-right {
      width:80%;
      height: 36%;
     float: left !important;
     }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--bottom {
     width:100%;
     height: 64%;
     }
   ```

   >[!NOTE]
   >Vous pouvez mettre à jour les pourcentages pour qu’ils répondent aux exigences de votre modèle personnalisé.

1. Accéder à `/apps/<project>/templates/my-custom-layout/jcr:content` et mettez à jour la propriété . *`cq:designPath`* vers `/apps/settings/wcm/designs/customtemplate-designs` vous pouvez ainsi charger les styles configurés dans static.css.

   >[!NOTE]
   >Saisissez tous les styles plutôt que de les copier ou de les coller, ce qui peut entraîner des espaces blancs et des problèmes de style CSS.

## Affichage du résultat {#viewing-result}

Suivez les étapes ci-dessous pour utiliser le modèle personnalisé ci-dessus dans votre projet AEM Screens :

1. Accédez au projet Screens que vous avez créé à l’étape (1) et sélectionnez le dossier **Canaux**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Sélectionner **Créer** dans la barre d’actions, sélectionnez le modèle **`Left20-LandscapeHD3Zone`** à partir du **Créer** assistant.

   ![image](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Après avoir créé un canal avec le modèle personnalisé, vous pouvez ajouter des ressources à votre canal à partir de l’éditeur. L’aperçu ci-dessous montre les images dans un modèle personnalisé.

   ![image](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Insertion d’une image comme calque d’arrière-plan  {#inserting-image}

Vous pouvez insérer une image en tant que calque d’arrière-plan dans la disposition :

Vous pouvez ajuster la règle CSS pour utiliser « data-uri » et insérer directement l’image (`Base64` encodée) dans le fichier CSS que vous avez créé à l’étape 13, *static.css*.

Cela se fait comme suit :
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Vous pouvez également suivre les étapes ci-dessous :

1. Assurez-vous que l’image est incluse d’une manière ou d’une autre dans la configuration hors ligne pour le canal.
1. Utilisez un lien direct vers l’image dans le CSS ci-dessus, au lieu de la variante « data-uri ».


## Mise à jour de la couleur d’arrière-plan {#updating-color}

Pour modifier la couleur d’arrière-plan, ajoutez le code suivant au fichier xml (étape 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`

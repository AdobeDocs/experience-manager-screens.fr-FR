---
title: Création de modèles personnalisés dans des dispositions multizones
seo-title: Création de modèles personnalisés dans des dispositions multizones
description: Suivez cette page pour en savoir plus sur la création de modèles personnalisés dans des dispositions multizones.
seo-description: Suivez cette page pour en savoir plus sur la création de modèles personnalisés dans des dispositions multizones.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 90d3d91f127432d8783748f00440bc6949262826

---


# Creating Custom Templates for MultiZone Layouts {#creating-custom-templates-multizone}

Cette page explique comment créer un modèle personnalisé pour une mise en page à plusieurs zones.

## Points importants {#considerations}

Vous devez tenir compte de deux points importants avant de créer un modèle personnalisé dans une disposition multi-zone :

1. **Taille ou pourcentages** de pixels fixes :

   Vous devez décider d’utiliser une taille de pixel fixe pour différentes zones de votre mise en page personnalisée ou de créer une mise en page personnalisée à l’aide de pourcentages.

   > [!NOTE]
   > L’utilisation du pourcentage pour définir des zones pour votre mise en page personnalisée vous permet de réutiliser le modèle sur diverses tailles d’écran.

1. **Convention d’affectation de nom**:

   Avant de comprendre comment créer des modèles multi-zone personnalisés à utiliser dans un projet AEM Screens, il est recommandé de comprendre le verbe des modèles que vous souhaitez créer.

   | **Nom de la disposition** | **Description** |
   |---|---|
   | Left20-LandscapeHD3Zone | Fait référence à une disposition paysage à 3 zones, avec une zone 1 qui couvre 20 % de l’écran horizontal et vertical à partir de la gauche, une zone 2 qui couvre 80 % de l’écran horizontal et 20 % de l’écran vertical justifié à droite, ainsi qu’une zone 3 qui couvre 100 % de l’écran horizontal et 80 % de l’écran vertical avec un format 16:9. |
   | Upper20-PortraitHD2Zone | Fait référence à un modèle portrait à 2 zones qui couvre 20 % de l’écran à partir du haut, avec un format 16:9. |
   | Right20-LandscapeSD3Zone | Fait référence à un modèle à 3 zones qui couvre 20 % de l’écran à partir de la droite, avec un format 4:3. |

   > [!IMPORTANT]
   > Les zones définies dans la mise en page personnalisée peuvent ne pas correspondre aux proportions globales de la mise en page entière. La convention d’affectation de nom suivie dans ce document spécifie les proportions de la disposition personnalisée dans son ensemble.

## Exemple de cas d’utilisation avec la disposition Left20-LandscapeHD3Zone {#custom-template-one}

Suivez la section ci-dessous pour créer un modèle personnalisé *Left20-LandscapeHD3Zone* avec la configuration suivante :

* **Left20** fait référence à la zone supérieure sur la gauche qui couvre 20 % de l’écran horizontal et vertical.
* **Landscape** fait référence à l’orientation de l’écran.
* **HD** fait référence au format 16:9.
* **3Zone** fait référence à trois zones de l’affichage.

## Représentation visuelle de la disposition multizone {#multi-layout-visual-one}

La disposition Left20-LandscapeHD3Zone vous permet de créer la disposition multizone suivante dans votre projet :

![image](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Création d’une disposition Left20-LandscapeHD3Zone {#landscape-layout-one}

Suivez les étapes ci-dessous pour créer une mise en page Left20-LandscapeHD3Zone pour un projet AEM Screens :

1. Create an AEM Screens project titled as **customtemplate**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Accédez à **CRXDE Lite** à partir de votre instance AEM —> Outils —> **CRXDE Lite**.

1. Créez un dossier sous **Applications** intitulé **modèlepersonnalisé**. De même, créez un autre dossier intitulé **modèle** sous **modèle** personnalisé, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/custom-multizone/custom-template1.png)

   > [!NOTE]
   > Il est recommandé de cliquer sur **Enregistrer tout** à partir de la barre d’action de CRXDE Lite chaque fois que vous créez, modifiez ou copiez du contenu sur l’un des noeuds, sans quoi vous ne pourrez pas valider les mises à jour.

1. Copiez le modèle de la barre de gauche `/libs/screens/core/templates/splitscreenchannel/lbar-left` vers `/apps/customtemplate/template`.

1. Renommez la **barre gauche** copiée (`/apps/customtemplate/template`) en **ma disposition**personnalisée.
   ![image](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Accédez aux propriétés `/apps/customtemplate/template/my-custom-layout` jcr:description **et mettez à jour les propriétés** jcr:description *en* Template for Left20-LandscapeHD3Zone **et** jcr:titleen Left20-LandscapeHD3Zone.**

   ![image](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Accédez au noeud **offline-config** depuis `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` et mettez à jour **jcr:title** vers *Left20-LandscapeHD3Zone*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Accédez à la propriété *jcr:content* de **my-custom-template** à partir de `/apps/customtemplate/template/my-custom-layout/jcr:content` et mettez à jour la propriété **cq:cssClass** pour aem-Layout my-custom-layout.****

   ![image](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. En vous référant à l’étape (4), au cours de laquelle vous avez copié le modèle de barre gauche, vous verrez 3 grilles réactives sous `my-custom-layout/jcr:content`la section. Ajoutez la classe css personnalisée à chacune des grilles réactives dans la propriété *cq:cssClass* , par exemple *my-custom-layout—top-left* pour le noeud *r1c1* .

   ![image](/help/user-guide/assets/custom-multizone/custom-template7.png)

   De même, ajoutez *my-custom-layout—top-right* pour *r1c2* et *my-custom-layout—bottom* pour le noeud *r2c1.*

   >[!NOTE]
   >Ces classes personnalisées seront utilisées dans le CSS pour définir la largeur/hauteur de ces grilles réactives.

   >[!NOTE]
   > Vous pouvez ajouter ou supprimer des grilles réactives en fonction du nombre total de grilles souhaité. Dans cet exemple, nous présentons 2 grilles dans la première ligne et 1 grille dans la deuxième ligne. Il y a donc un total de 3 grilles réactives (r1c1, r1c2, r2c1).

1. Copiez `/libs/settings/wcm/designs/screens` vers `/apps/settings/wcm/designs/` et renommez la conception copiée en tant que conceptions **de modèle** personnalisé.

1. Accédez à la propriété `/apps/settings/wcm/designs/custom-template-designs` jcr:title *de conceptions* -modèles **** personnalisées et mettez-la à jour pour **personnaliser la conception**-modèle.

1. Accédez à `/apps/settings/wcm/designs/custom-template-designs` et créez un fichier static.css.

1. Copiez le contenu dans le fichier static.css :

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
   > Vous pouvez mettre à jour les pourcentages pour qu’ils correspondent aux exigences de votre modèle personnalisé.

1. Accédez à la propriété `/apps/<project>/templates/my-custom-layout/jcr:content` cq:designPath *et mettez-la à jour pour* `/apps/settings/wcm/designs/customtemplate-designs` charger les styles configurés dans static.css.

   >[!NOTE]
   > Il est recommandé de taper tous les styles plutôt que de copier ou coller, ce qui peut entraîner des espaces blancs et des problèmes de style CSS.

## Affichage du résultat {#viewing-result}

Suivez les étapes ci-dessous pour utiliser le modèle personnalisé ci-dessus dans votre projet AEM Screens :

1. Accédez au projet d’écrans que vous avez créé à l’étape (1) et sélectionnez le dossier **Canaux** .

   ![image](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Cliquez sur **Créer** dans la barre d’actions et sélectionnez le modèle **Left20-LandscapeHD3Zone** dans l’assistant **Créer** .

   ![image](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Une fois que vous avez créé un canal avec le modèle personnalisé, vous pouvez ajouter des ressources à votre canal à partir de l’éditeur. L’aperçu suivant présente les images dans un modèle personnalisé.

   ![image](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Insertion d’une image en tant que calque d’arrière-plan {#inserting-image}

Vous pouvez insérer une image en tant que calque d’arrière-plan dans la mise en page :

You can adjust the CSS rule to use what is called “data-uri” and directly inline the image (Base64 encoded) in the CSS file, you created in (step 13), *static.css*.

Cela se fait comme suit :
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Vous pouvez également suivre les étapes ci-dessous :

1. Vérifiez que l’image est incluse d’une manière ou d’une autre dans la configuration hors ligne du canal.
1. Utilisez un lien direct vers l’image dans le fichier CSS ci-dessus, au lieu de la variante « data-uri ».


## Mise à jour de la couleur d’arrière-plan {#updating-color}

To change the background color, add the following code to the xml file (step 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`




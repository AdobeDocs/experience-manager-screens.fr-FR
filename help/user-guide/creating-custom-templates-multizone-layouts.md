---
title: Création de modèles personnalisés dans des dispositions multizones
seo-title: Création de modèles personnalisés dans des dispositions multizones
description: Suivez cette page pour en savoir plus sur la création de modèles personnalisés dans des dispositions multizones.
seo-description: Suivez cette page pour en savoir plus sur la création de modèles personnalisés dans des dispositions multizones.
contentOwner: Jyotika Syal
translation-type: ht
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: ht
source-wordcount: '947'
ht-degree: 100%

---


# Création de modèles personnalisés pour des dispositions multizone {#creating-custom-templates-multizone}

Cette page explique comment créer un modèle personnalisé dans une disposition multizone.

## Points importants {#considerations}

Avant de créer un modèle personnalisé dans une disposition multizone, vous devez tenir compte de deux points importants :

1. **Taille fixe en pixels ou taille en pourcentages** :

   Vous devez décider d’utiliser une taille fixe en pixels pour différentes zones d’une disposition personnalisée ou de la créer à l’aide de pourcentages.

   >[!NOTE]
   >Les pourcentages employés pour définir les zones d’une disposition personnalisée permettent de réutiliser le modèle pour différentes tailles d’écran.

1. **Convention d’affectation de noms** :

   Pour savoir comment créer des modèles multizone personnalisés à utiliser dans un projet AEM Screens, il est recommandé de comprendre la terminologie des modèles que vous souhaitez créer.

   | **Nom de la disposition** | **Description** |
   |---|---|
   | Left20-LandscapeHD3Zone | Fait référence à une disposition paysage à 3 zones, avec une zone 1 qui couvre 20 % de l’écran horizontal et vertical à partir de la gauche, une zone 2 qui couvre 80 % de l’écran horizontal et 20 % de l’écran vertical justifié à droite, ainsi qu’une zone 3 qui couvre 100 % de l’écran horizontal et 80 % de l’écran vertical avec un format 16:9. |
   | Upper20-PortraitHD2Zone | Fait référence à un modèle portrait à 2 zones qui couvre 20 % de l’écran à partir du haut, avec un format 16:9. |
   | Right20-LandscapeSD3Zone | Fait référence à un modèle à 3 zones qui couvre 20 % de l’écran à partir de la droite, avec un format 4:3. |

   >[!IMPORTANT]
   >Les zones définies dans la disposition personnalisée ne correspondent pas nécessairement aux proportions globales de l’ensemble de la disposition. La convention d’affectation de noms appliquée dans ce document définit les proportions de l’ensemble de la disposition personnalisée.

## Exemple de cas d’utilisation avec la disposition Left20-LandscapeHD3Zone {#custom-template-one}

Appliquez la procédure décrite dans la section ci-dessous pour créer un modèle personnalisé *Left20-LandscapeHD3Zone* avec la configuration suivante :

* **Left20** fait référence à la zone supérieure sur la gauche qui couvre 20 % de l’écran horizontal et vertical.
* **Landscape** fait référence à l’orientation de l’écran.
* **HD** fait référence au format 16:9.
* **3Zone** fait référence à trois zones de l’affichage.

## Représentation visuelle de la disposition multizone {#multi-layout-visual-one}

La disposition Left20-LandscapeHD3Zone vous permet de créer la disposition multizone suivante dans votre projet :

![image](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Création d’une disposition Left20-LandscapeHD3Zone {#landscape-layout-one}

Appliquez la procédure suivante pour créer une disposition Left20-LandscapeHD3Zone pour un projet AEM Screens :

1. Créez un projet AEM Screens intitulé **customtemplate**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Accédez à **CRXDE Lite** à partir de votre instance AEM --> Outils --> **CRXDE Lite**.

1. Créez un dossier sous **apps** intitulé **customtemplate**. De même, créez un autre dossier intitulé **template** sous **customtemplate**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >Il est recommandé de cliquer sur **Enregistrer tout** dans la barre d’actions de CRXDE Lite chaque fois que vous créez, modifiez ou copiez du contenu sur l’un des nœuds, faute de quoi vous ne pourrez pas valider les mises à jour.

1. Copiez le modèle de la barre de gauche depuis `/libs/screens/core/templates/splitscreenchannel/lbar-left` vers `/apps/customtemplate/template`.

1. Renommez la **barre de gauche** copiée (`/apps/customtemplate/template`) en indiquant **my-custom-layout**.
   ![image](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Accédez à `/apps/customtemplate/template/my-custom-layout` et mettez à jour les propriétés **jcr:description** en indiquant *Template for Left20-LandscapeHD3Zone* et **jcr:title** en indiquant *Left20-LandscapeHD3Zone*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Accédez au nœud **offline-config** depuis `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` et mettez à jour **jcr:title** en indiquant *Left20-LandscapeHD3Zone*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Accédez à la propriété *jcr:content* de **my-custom-template** depuis `/apps/customtemplate/template/my-custom-layout/jcr:content` et mettez à jour la propriété **cq:cssClass** en indiquant **aem-Layout my-custom-layout**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. En vous référant à l’étape (4), au cours de laquelle vous avez copié le modèle de la barre de gauche, vous voyez apparaître 3 grilles réactives sous `my-custom-layout/jcr:content`. Ajoutez la classe css personnalisée à chacune des grilles réactives dans la propriété *cq:cssClass*, par exemple *my-custom-layout--top-left* pour le nœud *r1c1*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template7.png)

   De même, ajoutez *my-custom-layout--top-right* pour *r1c2* et *my-custom-layout--bottom* pour le nœud *r2c1*.

   >[!NOTE]
   >Ces classes personnalisées seront utilisées dans le CSS pour définir la largeur et la hauteur de ces grilles réactives.

   >[!NOTE]
   >Vous pouvez ajouter ou supprimer les grilles réactives en fonction du nombre total de grilles souhaité. Dans cet exemple, nous présentons 2 grilles dans la première ligne et 1 grille dans la deuxième ligne. Il y a donc un total de 3 grilles réactives (r1c1, r1c2, r2c1).

1. Copiez `/libs/settings/wcm/designs/screens` dans `/apps/settings/wcm/designs/` et renommez la conception copiée **custom-template-designs**.

1. Accédez à `/apps/settings/wcm/designs/custom-template-designs` et mettez à jour la propriété *jcr:title* de **custom-template-designs** en indiquant **customtemplate-design**.

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

1. Accédez à `/apps/<project>/templates/my-custom-layout/jcr:content` et mettez à jour la propriété *cq:designPath* en indiquant `/apps/settings/wcm/designs/customtemplate-designs` afin de charger les styles configurés dans static.css.

   >[!NOTE]
   >Il est recommandé de saisir tous les styles plutôt que de les copier ou coller, ce qui peut entraîner des espaces blancs et par conséquent des problèmes de styles CSS.

## Affichage du résultat {#viewing-result}

Suivez les étapes ci-dessous pour utiliser le modèle personnalisé ci-dessus dans votre projet AEM Screens :

1. Accédez au projet Screens que vous avez créé à l’étape (1) et sélectionnez le dossier **Canaux**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Cliquez sur **Créer** dans la barre d’actions et sélectionnez le modèle **Left20-LandscapeHD3Zone** dans l’assistant **Créer**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Une fois un canal créé avec le modèle personnalisé, vous pouvez lui ajouter des ressources à partir de l’éditeur. L’aperçu ci-dessous montre les images dans un modèle personnalisé.

   ![image](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Insertion d’une image en tant que calque d’arrière-plan {#inserting-image}

Vous pouvez insérer une image en tant que calque d’arrière-plan dans la disposition :

Vous pouvez ajuster la règle CSS pour utiliser un « data-uri » et intégrer directement l’image (codée en base 64) dans le fichier *static.css* créé à l’étape 13.

Cela se fait comme suit :
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Vous pouvez également suivre les étapes ci-dessous :

1. Vérifiez que l’image est incluse d’une manière ou d’une autre dans la configuration hors ligne du canal.
1. Utilisez un lien direct vers l’image dans le fichier CSS ci-dessus, au lieu de la variante « data-uri ».


## Mise à jour de la couleur d’arrière-plan {#updating-color}

Pour modifier la couleur d’arrière-plan, ajoutez le code suivant au fichier xml (étape 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`




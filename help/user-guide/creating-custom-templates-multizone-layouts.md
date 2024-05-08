---
title: Création de modèles personnalisés dans des dispositions multizones
description: Découvrez comment créer des modèles personnalisés dans des dispositions multizones pour AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 28%

---

# Création de modèles personnalisés pour des dispositions multizones {#creating-custom-templates-multizone}

Cette page explique comment créer un modèle personnalisé dans une disposition multizone.

## Points importants {#considerations}

Avant de créer un modèle personnalisé dans une disposition multizone, vous devez tenir compte de deux points importants :

1. **Taille fixe en pixels ou taille en pourcentages** :

   Choisissez d’utiliser une taille fixe en pixels pour différentes zones de votre disposition personnalisée ou de créer une disposition personnalisée à l’aide de pourcentages.

   >[!NOTE]
   >L’utilisation du pourcentage pour définir des zones pour votre disposition personnalisée vous permet de réutiliser le modèle sur différentes tailles d’écran.

1. **Convention d’affectation de noms** :

   Avant de comprendre comment créer des modèles multizone personnalisés à utiliser dans un projet AEM Screens, vous devez connaître la terminologie des modèles que vous souhaitez créer.

   | **Nom de la disposition** | **Description** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | Une disposition paysage à trois zones qui permet de créer trois zones :<br>* Zone 1 : 20 % de l’écran horizontal et vertical à partir de la gauche<br>* Zone 2 : 80 % de l’écran horizontal et 20 % de l’écran vertical justifié à droite<br>* Zone 3 : 100 % d’horizontal et 80 % de l’écran vertical avec un format 16:9 |
   | `Upper20-PortraitHD2Zone` | Un modèle portrait à deux zones qui couvre 20 % de l’écran à partir du haut, avec un format de 16:9. |
   | `Right20-LandscapeSD3Zone` | Un modèle à trois zones qui couvre 20 % de l’écran à partir de la droite, avec un format de 4:3 |

   >[!IMPORTANT]
   >Les zones définies dans la disposition personnalisée ne correspondent pas nécessairement aux proportions globales de l’ensemble de la disposition. La convention d’affectation de noms appliquée dans ce document définit les proportions de l’ensemble de la disposition personnalisée.

## Exemple de cas d’utilisation `Left20-LandscapeHD3Zone` Disposition {#custom-template-one}

Suivez la section ci-dessous pour créer un modèle personnalisé. *`Left20-LandscapeHD3Zone`* avec la configuration suivante :

* **`Left20`** - Zone supérieure sur la gauche recouvrant 20 % de la taille de l’écran horizontal et vertical.
* **`Landscape`** - Orientation de l’écran.
* **`HD`** - Le rapport d’aspect est de 16:9.
* **`3Zone`** - Trois zones de l’affichage.

## Représentation visuelle de la disposition multizone {#multi-layout-visual-one}

La variable `Left20-LandscapeHD3Zone` La disposition vous permet de créer la disposition multizone suivante dans votre projet :

![image](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Création d’un `Left20-LandscapeHD3Zone` Disposition {#landscape-layout-one}

Pour créer un `Left20-LandscapeHD3Zone` Mise en page d’un projet AEM Screens.

1. Créez un projet AEM Screens intitulé **`customtemplate`**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Accédez à **CRXDE Lite** à partir de votre instance AEM > Outils > **CRXDE Lite**.

1. Créez un dossier sous **apps** intitulé **`customtemplate`**. De même, créez un autre dossier intitulé **modèle** under **`customtemplate`**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >Cliquez sur **Enregistrer tout** à partir de la barre d’actions de CRXDE Lite chaque fois que vous créez, modifiez ou copiez du contenu sur l’un des noeuds. Sinon, vous ne pouvez pas valider les mises à jour.

1. Copiez le modèle de la barre de gauche depuis `/libs/screens/core/templates/splitscreenchannel/lbar-left` vers `/apps/customtemplate/template`.

1. Renommez la **barre de gauche** copiée (`/apps/customtemplate/template`) en indiquant **my-custom-layout**.
   ![image](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Accédez à `/apps/customtemplate/template/my-custom-layout` et mettre à jour les propriétés **`jcr:description`** to *Modèle pour`Left20-LandscapeHD3Zone`* et **`jcr:title`** to *`Left20-LandscapeHD3Zone`*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Accédez au **`offline-config`** noeud à partir de `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` et mettre à jour la variable **`jcr:title`** to *`Left20-LandscapeHD3Zone`*.

   ![image](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Accédez au *`jcr:content`* de **my-custom-template** de `/apps/customtemplate/template/my-custom-layout/jcr:content` et mettre à jour la variable **`cq:cssClass`** pour pouvoir utiliser **aem-Layout my-custom-layout**.

   ![image](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. En vous référant à l’étape (4) au cours de laquelle vous avez copié le modèle de la barre de gauche, vous pouvez afficher trois grilles réactives sous `my-custom-layout/jcr:content`. Ajoutez une classe CSS personnalisée à chacune des grilles réactives dans la *`cq:cssClass`* par exemple, *my-custom-layout—top left* pour *r1c1* noeud .

   ![image](/help/user-guide/assets/custom-multizone/custom-template7.png)

   De même, ajoutez *my-custom-layout--top-right* pour *r1c2* et *my-custom-layout--bottom* pour le nœud *r2c1*.

   >[!NOTE]
   >Ces classes personnalisées sont utilisées dans le CSS pour définir la largeur/hauteur de ces grilles réactives.

   >[!NOTE]
   >Vous pouvez ajouter ou supprimer les grilles réactives en fonction du nombre total de grilles souhaité. Dans cet exemple, deux grilles de la première ligne et une grille de la deuxième ligne sont présentées. Il existe donc un total de trois grilles réactives (r1c1, r1c2, r2c1).

1. Copiez `/libs/settings/wcm/designs/screens` dans `/apps/settings/wcm/designs/` et renommez la conception copiée **custom-template-designs**.

1. Accédez à `/apps/settings/wcm/designs/custom-template-designs` et mettre à jour la propriété *`jcr:title`* de **custom-template-designs** to **customtemplate-design**.

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

1. Accédez à `/apps/<project>/templates/my-custom-layout/jcr:content` et mettre à jour la propriété *`cq:designPath`* to `/apps/settings/wcm/designs/customtemplate-designs` vous pouvez donc charger les styles configurés dans static.css.

   >[!NOTE]
   >Saisissez tous les styles plutôt que de les copier ou coller, ce qui peut entraîner des espaces blancs et des problèmes de style CSS.

## Affichage du résultat {#viewing-result}

Suivez les étapes ci-dessous pour utiliser le modèle personnalisé ci-dessus dans votre projet AEM Screens :

1. Accédez au projet Screens que vous avez créé à l’étape (1) et cliquez sur le bouton **Canaux** dossier.

   ![image](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Cliquez sur **Créer** dans la barre d’actions et cliquez sur le modèle **`Left20-LandscapeHD3Zone`** de la **Créer** assistant.

   ![image](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Après avoir créé un canal avec le modèle personnalisé, vous pouvez ajouter des ressources à votre canal à partir de l’éditeur. L’aperçu ci-dessous montre les images dans un modèle personnalisé.

   ![image](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Insertion d’une image comme calque d’arrière-plan  {#inserting-image}

Vous pouvez insérer une image en tant que calque d’arrière-plan dans la disposition :

Vous pouvez ajuster la règle CSS pour utiliser &quot;data-uri&quot; et intégrer directement l’image (`Base64` codé) dans le fichier CSS que vous avez créé à l’ (étape 13), *static.css*.

Cela se fait comme suit :
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Vous pouvez également suivre les étapes ci-dessous :

1. Assurez-vous que l’image est d’une manière ou d’une autre incluse dans la configuration hors ligne du canal.
1. Utilisez un lien direct vers l’image dans le CSS ci-dessus, au lieu de la variante &quot;data-uri&quot;.


## Mise à jour de la couleur d’arrière-plan {#updating-color}

Pour modifier la couleur d’arrière-plan, ajoutez le code suivant au fichier xml (étape 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`

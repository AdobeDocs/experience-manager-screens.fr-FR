---
title: Création de modèles personnalisés dans des mises en page multi-zones
seo-title: Création de modèles personnalisés dans des mises en page multi-zones
description: Suivez cette page pour en savoir plus sur la création de modèles personnalisés dans les mises en page MultiZone.
seo-description: Suivez cette page pour en savoir plus sur la création de modèles personnalisés dans les mises en page MultiZone.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Création de modèles personnalisés dans des mises en page multi-zones {#creating-custom-templates-multizone}

L’exemple suivant montre comment créer des modèles personnalisés dans des mises en page multiZone.

Par exemple, la section ci-dessous illustre la création d’un modèle personnalisé dans une disposition multizone avec les configurations suivantes :

![image](assets/custom-template1.png)


## Création d’un modèle personnalisé avec une configuration spécifique {#basic-flow-setting}

Suivez les étapes ci-dessous pour créer un modèle personnalisé.

1. Créez le modèle dans `/apps/<project>/templates/my-custom-layout`

```shell
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
    jcr:description="My Custom 3-zones layout "
    jcr:primaryType="cq:Template"
    jcr:title="3-zones layout"
    allowedParents="[/libs/screens/core/templates/channelfolder]"
    allowedPaths="[/content/screens(/.*)?]"
    ranking="{Long}20000">
    <jcr:content
        cq:cssClass="aem-Layout aem-Layout--3x1 my-CustomLayout"
        cq:designPath="/apps/settings/wcm/designs/<project>"
        cq:deviceGroups="[mobile/groups/responsive]"
        jcr:primaryType="cq:PageContent"
        sling:resourceSuperType="screens/core/components/channel"
        sling:resourceType="screens/core/components/multiscreenchannel">
        <r1c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-top"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r2c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-middle"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r3c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-bottom"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <cq:responsive jcr:primaryType="nt:unstructured">
            <breakpoints jcr:primaryType="nt:unstructured"/>
        </cq:responsive>
        <offline-config/>
    </jcr:content>
</jcr:root>
```

1. Créez une conception de page dans `/apps/settings/wcm/designs/<project>`.

   >[!NOTE]
   >
   >Assurez-vous que le `cq:designPath` code ci-dessus correspond au chemin.

1. Mettez à jour le noeud **offline-config** pour que la conception pointe également vers le nouveau chemin.

1. Ajoutez un fichier **static.css** dans le `/apps/settings/wcm/designs/<project>` dossier et définissez son contenu sur

```shell
.cq-Screens-channel--multizone.my-CustomLayout {}
.cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-top { height: 150px; }
.cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-middle { height: 1470px; }
.cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-bottom { height: 300px; }
```

## Insertion d’une image en tant que calque d’arrière-plan {#inserting-image}

Vous pouvez définir une image comme calque d’arrière-plan sur la disposition :

Vous pouvez ajuster la règle CSS pour utiliser ce qui est appelé "data-uri" et directement dans l’image (codée en base 64) du fichier CSS.

Cela se fait comme suit :
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Vous pouvez également suivre les étapes ci-dessous :

1. Assurez-vous que l’image est en quelque sorte incluse dans la configuration hors ligne du canal.
1. Utilisez un lien direct vers l’image dans le fichier CSS ci-dessus, au lieu de la variante "uri de données".


## Mise à jour de la couleur d’arrière-plan {#updating-color}

Pour modifier la couleur d’arrière-plan, ajoutez le code suivant au fichier xml :

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`

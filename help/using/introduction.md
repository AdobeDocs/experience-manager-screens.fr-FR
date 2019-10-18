---
title: Présentation d’ [!UICONTROL AEM Screens]
seo-title: Guide des meilleures pratiques pour les projets [!UICONTROL AEM Screens]
description: Cette page est une section d’introduction aux écrans AEM
seo-description: Cette page présente AEM Screens
translation-type: tm+mt
source-git-commit: 55999ae9ead7ab8986f4dcb69b0bbaa46933c9ec

---


# Présentation d’AEM Screens {#introduction}

**Les écrans** d’AEM (Adobe Experience Manager) sont une solution Digital Signage qui vous permet de créer, de publier et de lire des expériences numériques dynamiques et interactives impliquant différents types d’écrans sur place, de concert avec une stratégie de marketing numérique intégrée.

AEM Screens vous permet de créer les éléments suivants :

* **panoramas numériques dédiés**
* **recommandations de produit**
* **imagerie du mode de vie de fond**

En outre, les écrans fournissent de nombreuses applications uniques aux clients et aux employés en fonction du domaine dans lequel ils sont déployés, par exemple :

* **affichage interactif**
* **wayfinding**
* **marque**
* **ajout d’ambiance à votre environnement**

La création et la gestion d’un réseau de signalisation numérique à l’aide d’AEM Screens est simple et intuitive. Une application de lecteur héberge des canaux de contenu conçus pour AEM Screens par des clients ou des partenaires d’implémentation. *Les emplacements* gèrent une hiérarchie d’emplacements prédéfinie et contient des affichages. Each *display* has a dashboard that shows different devices and screens attached. Le contenu d’AEM Screens est géré dans des *canaux*. *AEM Screens Player effectue le rendu du contenu figurant dans les canaux sur les affichages.*



>[!NOTE]
>
>Pour en savoir plus sur les différentes fonctionnalités d’un projet de développement et de gestion d’AEM Screens, consultez le Guide **[de l’utilisateur d’](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html)** AEM Screens.

## Sites AEM par rapport aux écrans AEM {#aem-sites-screens}

> [!NOTE]
>
> Si votre équipe d’implémentation a l’expérience de l’utilisation des applications de sites AEM, il est important de comprendre la différence entre les sites AEM et les écrans AEM.

AEM Screens fournit une plateforme de création/lecture unifiée pour le déploiement de contenu sur des périphériques de signature numérique dans des espaces publics. Bien que l’auteur de l’expérience s’efforce de maintenir la cohérence sur le Web et sur les canaux locaux, il convient de noter certaines différences.

* **Temps** d'arrêt : Généralement, les pages Web sont conçues pour fournir une mine d’informations qui peuvent être consommées sur une période relativement longue. En revanche, les expériences numériques sur place doivent anticiper les besoins du lecteur et fournir des orientations claires et concises sur la manière et les raisons pour lesquelles l’utilisateur doit s’engager. Les expériences sont ainsi mieux ciblées, mieux organisées et plus contextuelles.

* **Distance d'affichage**: Les distances d’affichage sont généralement plus longues ou plus éloignées que ce que les utilisateurs expérimentent habituellement avec un site Web. Par conséquent, la taille du texte devrait normalement être plus grande et l’espacement entre le texte, les images et d’autres contenus complémentaires devrait être testé en fonction de la taille d’écran prévue et de l’emplacement dans l’espace physique.

* **Persistance**: L’état connecté du périphérique du lecteur ne doit jamais être autorisé à influencer la diffusion ou non d’expériences numériques à l’utilisateur. Le lecteur doit être conçu de manière à ce qu’une ou plusieurs expériences persistent toujours et puissent être diffusées quel que soit l’état connecté du périphérique du lecteur.

* **Segmentation** en boucle multimédia : La configuration de chaque périphérique du lecteur pour disposer de son propre segment de boucle garantit que le contenu localisé peut être facilement créé, publié et lu dans l’ensemble de l’expérience numérique. Les ressources multimédia contenues dans les canaux de séquence incorporés sont ajoutées au segment de boucle précédent et offrent la possibilité de cibler un segment de boucle multimédia pour chaque regroupement d’emplacements.

* **Expériences** interactives : Une application tactile de kiosque peut être créée et diffusée dans un canal d’écrans à l’aide d’AEM et de l’éditeur d’application d’une seule page. Il est recommandé d’appliquer des propriétés de conception omnichannel cohérentes, un minuteur d’inactivité pour réinitialiser l’expérience et un appel à l’action clair pour les tâches que l’application peut exécuter. La page d’entrée doit être composée d’éléments numériques clés conçus pour transmettre de la valeur, attirer l’utilisateur à l’écran et l’inviter à s’engager.

AEM Screens fournit une structure permettant de déployer du contenu sur des périphériques physiques. Le contenu est affecté aux canaux dans les écrans, qui peuvent contenir du contenu multimédia ou des applications d’écran tactile. Dans cette structure, une application de site AEM peut être diffusée sous forme de contenu via un canal.

Avant d’être déposé sur un canal dans les écrans, un site AEM doit être formaté pour être utilisé aux dimensions du périphérique d’affichage auquel il est destiné.

> [!NOTE]
>
> De nombreux composants de sites AEM ne sont pas compatibles avec les écrans AEM. Les écrans AEM sont fournis avec de nombreux composants prêts à l’emploi qui vous permettent de créer des expériences numériques sans nécessiter de personnalisation. Si les exigences du projet le permettent, utilisez la fonctionnalité intégrée d’AEM Screens lorsque cela est possible.

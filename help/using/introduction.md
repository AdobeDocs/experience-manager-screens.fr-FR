---
title: Présentation d’AEM Screens
description: Découvrez AEM Screens et ce qu’il peut vous apporter.
exl-id: 11781e0b-0aca-4d08-aaad-87a7aaf28c24
source-git-commit: ba5327077e4a2d30cc7b77f02123da5a240c67ae
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 95%

---

# Présentation d’AEM Screens {#introduction}

**AEM Screens** est une solution d’affichage numérique qui vous permet de créer, de publier et de lire des expériences numériques dynamiques et interactives. Elle implique différents types d’écrans sur site, de concert avec une stratégie de marketing numérique omnicanal exhaustive.

AEM Screens vous permet de créer ce qui suit :

* **Panneaux de menus numériques dédiés**
* **Systèmes de recommandation de produits**
* **Images de style de vie en arrière-plan**

AEM Screens fournit, en outre, de nombreuses applications exclusives pour sa clientèle et son personnel, en fonction du domaine dans lequel elles sont déployées. Voici quelques exemples :

* **Affichages interactifs**
* **Orientation**
* **Valorisation de la marque**
* **Ajout d’ambiance à votre environnement**

Avec AEM Screens, la création et la gestion d’un réseau de signalétique digitale s’avèrent à la fois simples et intuitives. Une application de lecture héberge des canaux de contenu créés pour AEM Screens par des clients ou des partenaires de mise en œuvre. Les *emplacements* gèrent une hiérarchie d’emplacements prédéfinie et contiennent des affichages. Chaque *affichage* comprend un tableau de bord, auquel sont associés différents appareils et écrans. Le contenu d’AEM Screens est géré dans des *canaux*. *AEM Screens Player* effectue le rendu du contenu figurant dans les canaux sur des dispositifs d’affichage.



>[!NOTE]
>
>Pour en savoir plus sur les différentes fonctionnalités relatives à la gestion et au développement de projets AEM Screens, consultez le **[Guide d’utilisation d’AEM Screens](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/aem-screens-introduction)**.

## AEM Sites par rapport à AEM Screens {#aem-sites-screens}

>[!NOTE]
>
>Si votre équipe en charge de la mise en œuvre a déjà travaillé avec des applications AEM Sites, il est important de comprendre la différence entre AEM Sites et AEM Screens.

AEM Screens fournit une plateforme de création/lecture unifiée pour le déploiement de contenu sur des appareils de signalétique digitale installés dans l’espace public. Bien que le créateur de l’expérience s’efforce de maintenir la cohérence entre le contenu présenté sur le web et sur site, il convient de noter quelques différences.

* **Durée d’arrêt** : en règle générale, les pages web sont conçues pour fournir une grande quantité d’informations pouvant être exploitées sur une période relativement longue. À l’inverse, les expériences digitales sur site doivent anticiper les besoins de l’utilisateur, ou de l’utilisatrice et fournir des informations claires et concises quant à l’intérêt que présente une interaction pour ceux-ci. Cela se traduit par des expériences plus ciblées, mieux étudiées et plus pertinentes.

* **Distance d’affichage** : les distances d’affichage sont généralement supérieures à celles auxquelles les personnes sont habituées avec un site web. Par conséquent, la taille du texte doit normalement être plus grande, et l’espacement entre le texte, les images et d’autres contenus doit être testé en fonction de la taille d’écran prévue et de la position dans l’espace physique.

* **Persistance** : la possibilité de diffuser ou non des expériences numériques à l’utilisateur ou l’utilisatrice ne doit jamais être influencée par l’état de connexion de l’appareil de lecture. Le lecteur doit être conçu de manière à ce qu’une ou plusieurs expériences persistent toujours et puissent être diffusées quel que soit l’état de connexion.

* **Segmentation de boucle multimédia** : en configurant chaque appareil de lecture de sorte qu’il dispose de son propre segment de boucle, vous avez la garantie que le contenu localisé peut être facilement créé, publié et lu dans l’ensemble de l’expérience digitale. Les ressources multimédias contenues dans les canaux de séquence incorporés sont ajoutées au segment de boucle précédent et offrent la possibilité de cibler un segment de boucle multimédia pour chaque regroupement d’emplacements.

* **Expériences interactives** : une application kiosque tactile peut être créée et diffusée dans un canal Screens à l’aide d’AEM et de l’éditeur de SPA. Il est recommandé d’appliquer des propriétés de conception omnicanal cohérentes, un minuteur d’inactivité pour réinitialiser l’expérience, ainsi qu’un appel à l’action clair pour les tâches que l’application peut exécuter. La page de destination doit se composer d’éléments numériques clés, conçus pour transmettre la valeur du contenu, attirer l’utilisateur vers l’écran et susciter son engagement.

AEM Screens fournit une structure permettant de déployer du contenu sur des appareils physiques. Le contenu est affecté à des canaux dans Screens et les écrans peuvent proposer du contenu multimédia ou des applications tactiles. Dans cette structure, une application AEM Sites peut être diffusée sous la forme de contenu par le biais d’un canal.

Avant d’être déposé dans un canal d’AEM Screens, un site AEM doit être formaté en vue d’être utilisé aux dimensions de l’appareil d’affichage auquel il est destiné.

>[!NOTE]
>De nombreux composants AEM Sites ne sont pas compatibles avec AEM Screens. AEM Screens s’accompagne d’un grand nombre de composants prêts à l’emploi qui vous permettent de créer des expériences digitales sans nécessiter de personnalisation. Si cela est autorisé dans le projet, utilisez la fonctionnalité intégrée d’AEM Screens lorsque cela s’avère possible.

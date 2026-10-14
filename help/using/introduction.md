---
title: Présentation d’AEM Screens
description: Découvrez AEM Screens et son utilité.
exl-id: 11781e0b-0aca-4d08-aaad-87a7aaf28c24
TQID: https://experienceleague.adobe.com/UticeR0hdyxXrG1P5qrwzrJLhZ3h5BRCfjamUzzu-XE
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
    internal-label: Experience Manager Screens
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 93%
---
# Présentation d’AEM Screens {#introduction}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

**AEM Screens** est une solution de signalétique numérique qui vous permet de créer, de publier et de lire des expériences numériques dynamiques et interactives. Elle implique différents types d’écrans sur site, de concert avec une stratégie de marketing numérique omnicanal exhaustive.

AEM Screens vous permet de créer :

* **Panneaux de menus numériques dédiés**
* **Systèmes de recommandation de produits**
* **Images de style de vie en arrière-plan**

AEM Screens fournit également de nombreuses applications uniques pour les clientes et clients et les employés, en fonction du domaine dans lequel les applications sont déployées, par exemple :

* **Affichages interactifs**
* **Orientation**
* **Valorisation de la marque**
* **Ajout d’ambiance à votre environnement**

Avec AEM Screens, la création et la gestion d’un réseau daffichage  s’avèrent à la fois simples et intuitives. Une application de lecture héberge des canaux de contenu créés pour AEM Screens par des clientes ou clients ou des partenaires de mise en œuvre. Les *emplacements* gèrent une hiérarchie d’emplacements prédéfinie et contiennent des affichages. Chaque *affichage* comprend un tableau de bord, auquel sont associés différents appareils et écrans. Le contenu d’AEM Screens est géré dans des *canaux*. *AEM Screens Player* effectue le rendu du contenu figurant dans les canaux sur des dispositifs d’affichage.

>[!NOTE]
>
>Pour en savoir plus sur les différentes fonctionnalités relatives à la gestion et au développement de projets AEM Screens, consultez le **[Guide d’utilisation d’AEM Screens](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/aem-screens-introduction)**.

## AEM Sites par rapport à AEM Screens {#aem-sites-screens}

>[!NOTE]
>
>Si votre équipe de mise en œuvre a déjà de l’expérience avec des applications AEM Sites, il est important de comprendre la différence entre AEM Sites et AEM Screens.

AEM Screens fournit une plateforme de création/lecture unifiée pour le déploiement de contenu sur des appareils daffichage  installés dans l’espace public. Bien que le créateur de l’expérience s’efforce de maintenir la cohérence entre le contenu présenté sur le Web et sur site, il convient de noter quelques différences.

* **Durée d’arrêt** : en règle générale, les pages web sont conçues pour fournir une grande quantité d’informations pouvant être exploitées sur une période relativement longue. À l’inverse, les expériences numériques sur site doivent anticiper les besoins de l’observateur ou de l’observatrice et fournir des informations claires et concises sur la manière et les raisons de son engagement. Cette attention se traduit par des expériences plus ciblées, mieux étudiées et plus contextuelles.

* **Distance d’affichage** : les distances d’affichage sont généralement supérieures à celles auxquelles les personnes sont habituées avec un site web. Par conséquent, la taille du texte doit normalement être plus grande, et l’espacement entre le texte, les images et les autres contenus doit être testé en fonction de la taille d’écran prévue et de l’emplacement dans l’espace physique.

* **Persistance** : la possibilité de diffuser ou non des expériences numériques à l’utilisateur ou l’utilisatrice ne doit jamais être influencée par l’état de connexion de l’appareil de lecture. Le lecteur doit être conçu de manière à ce qu’une ou plusieurs expériences persistent toujours et puissent être diffusées quel que soit l’état de connexion de l’appareil lecteur.

* **Segmentation de boucle multimédia** : en configurant chaque appareil de lecture de sorte qu’il dispose de son propre segment de boucle, vous avez la garantie que le contenu localisé peut être facilement créé, publié et lu dans l’ensemble de l’expérience digitale. Les ressources multimédias contenues dans les canaux de séquence incorporés sont ajoutées au segment de boucle précédent et offrent la possibilité de cibler un segment de boucle multimédia pour chaque regroupement d’emplacements.

* **Expériences interactives** : une application kiosque tactile peut être créée et diffusée dans un canal Screens à l’aide d’AEM et de l’éditeur de SPA. Il est considéré comme une bonne pratique d’appliquer des propriétés de conception omnicanal cohérentes, un temporisateur d’inactivité pour réinitialiser l’expérience, ainsi qu’un CTA clair pour les tâches que l’application peut exécuter. La page de destination doit se composer d’éléments numériques clés, conçus pour transmettre la valeur du contenu, attirer l’utilisateur vers l’écran et susciter son engagement.

AEM Screens fournit un framework permettant de déployer du contenu sur des appareils physiques. Le contenu est affecté à des canaux dans Screens, qui peuvent contenir du contenu multimédia ou des applications pour écran tactile. Dans ce framework, une application AEM Sites peut être diffusée sous la forme de contenu par le biais d’un canal.

Un site AEM doit être formaté pour être utilisé avec les dimensions de l’appareil d’affichage auquel il est destiné. Cela doit être fait avant d’être déposé dans un canal de Screens.

>[!NOTE]
>De nombreux composants AEM Sites ne sont pas compatibles avec AEM Screens. AEM Screens s’accompagne d’un grand nombre de composants standard qui vous permettent de créer des expériences numériques sans nécessiter de personnalisation. Si les exigences du projet le permettent, utilisez autant que possible la fonctionnalité intégrée d’AEM Screens.


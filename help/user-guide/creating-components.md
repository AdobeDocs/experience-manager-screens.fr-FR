---
title: Création de composants
description: Découvrez comment les composants d’AEM sont utilisés pour contenir, formater et générer le rendu du contenu mis à disposition sur vos pages web.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 40%

---

# Création de composants {#creating-components}

Les composants AEM servent à stocker, mettre en forme et générer le rendu du contenu diffusé dans vos pages web.

>[!NOTE]
>
>Pour en savoir plus sur la création de composants AEM, voir Développement de composants AEM.

## Création de canaux {#authoring-channels}

Le canal est l’objet central du contenu diffusé à un ensemble d’affichages. Par conséquent, un auteur de contenu ouvre généralement un canal dans l’éditeur pour ajouter ou modifier du contenu. Parce que le canal est un ***`cq:Page`***, il suit le même schéma UX traditionnel pour ajouter et modifier des composants sur le canal.

Cependant, comme les composants d’un canal sont généralement rendus en plein écran, l’expérience de création en pâtit lors de la tentative de modification de composants uniques ou de composition de nouvelles commandes. Par conséquent, le canal s’appuie sur des sélecteurs pour effectuer le rendu de différentes vues des composants. L’environnement de création utilise le sélecteur de modification pour activer le rendu de canal personnalisé.

Par exemple, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

L’utilisateur ne doit pas se charger de l’ajout du sélecteur à l’URL au cours de l’édition. Une logique côté client écoute l’événement de changement de calque et ajoute le sélecteur si le canal possède le type de ressource dédié. *screens/core/components/channel*.

## Rendu des composants {#rendering-components}

Pour permettre une création correcte, les composants doivent fournir les deux rendus suivants :

| **Component** | **Rendus** |
|---|---|
| *my-component/my-component.html* | rendu de production |
| *my-component/edit.html* | modification du rendu dans une vue plus petite |

Les composants intégrés utilisent les catégories de bibliothèques clientes suivantes :

| **Component** | **Bibliothèque cliente** |
|---|---|
| *cq.screens.components.edit* | CSS et JS devant être chargés lors de la création |
| *cq.screens.components.production* | CSS et JS devant être chargés lorsque le canal est en cours d’exécution |
| *cq.screens.components* | CSS et JS partagés |

>[!NOTE]
>
>Pour développer des composants personnalisés, utilisez le ***[modèle d’exemple de composant AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.

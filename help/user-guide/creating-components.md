---
title: Création de composants
seo-title: Création de composants
description: Les composants AEM servent à stocker, mettre en forme et générer le rendu du contenu diffusé dans vos pages web. Suivez cette page pour en savoir plus sur la création de canaux et le rendu de composants.
seo-description: Les composants AEM servent à stocker, mettre en forme et générer le rendu du contenu diffusé dans vos pages web. Suivez cette page pour en savoir plus sur la création de canaux et le rendu de composants.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
translation-type: ht
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: ht
source-wordcount: '331'
ht-degree: 100%

---


# Création de composants {#creating-components}

Les composants AEM servent à stocker, mettre en forme et générer le rendu du contenu diffusé dans vos pages web.

>[!NOTE]
>
>Pour plus d’informations sur la création de composants AEM, voir Développement de composants AEM.

## Création de canaux {#authoring-channels}

Le canal est l’objet central du contenu qui est diffusé à un ensemble d’écrans. Par conséquent, un auteur de contenu ouvre généralement un canal dans l’éditeur pour ajouter ou modifier du contenu. Étant donné que le canal est un nœud ***cq:Page***, il applique le même schéma UX traditionnel pour ajouter et modifier des composants dans le canal.

Cependant, dans la mesure où les composants d’un canal sont généralement rendus en mode Plein écran, l’expérience de création est dégradée lorsque vous essayez de modifier des composants uniques ou de composer de nouvelles séquences. Par conséquent, le canal dépend des sélecteurs pour effectuer le rendu des différentes vues des composants. L’environnement de création met à profit le sélecteur de modification pour activer le rendu de canal personnalisé.

Par exemple, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

L’utilisateur ne doit pas se charger de l’ajout du sélecteur à l’URL au cours de l’édition. Une logique côté client écoute l’événement de changement de calque et ajoute le sélecteur si le canal présente le type de ressource dédié *screens/core/components/channel.*

## Rendu des composants {#rendering-components}

Pour garantir une création correcte, les composants doivent fournir les deux rendus suivants :

| **Component** | **Rendus** |
|---|---|
| *my-component/my-component.html* | rendu de production |
| *my-component/edit.html* | modification du rendu dans une vue plus petite |

Les composants intégrés tirent parti des catégories de bibliothèques clientes suivantes :

| **Component** | **Bibliothèque cliente** |
|---|---|
| *cq.screens.components.edit* | CSS et JS devant être chargés lors de la création |
| *cq.screens.components.production* | CSS et JS devant être chargés lorsque le canal est en cours d’exécution |
| *cq.screens.components* | CSS et JS partagés |

>[!NOTE]
>
>Pour développer des composants personnalisés, utilisez le ***[modèle d’exemple de composant AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.


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
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Création de composants {#creating-components}

Les composants AEM servent à stocker, mettre en forme et générer le rendu du contenu diffusé dans vos pages web.

>[!NOTE]
>
>Pour en savoir plus sur la création de composants AEM, voir Développement de composants AEM.

## Création de canaux {#authoring-channels}

Le canal est l’objet central du contenu qui est diffusé à un ensemble d’écrans. Par conséquent, un auteur de contenu ouvre généralement un canal dans l’éditeur pour ajouter ou modifier du contenu. Since the Channel is a ***cq:Page*** it will follow the same traditional UX pattern to add and change components on the channel.

Cependant, dans la mesure où les composants d’un canal sont généralement rendus en mode plein écran, l’expérience de création est dégradée lorsque vous essayez de modifier des composants uniques ou de composer de nouvelles séquences. Par conséquent, le canal dépend des sélecteurs pour effectuer le rendu des différentes vues des composants. L’environnement de création utilisera le sélecteur d’édition pour activer le rendu personnalisé du canal.

Par exemple, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

L’utilisateur ne doit pas se charger de l’ajout du sélecteur à l’URL au cours de l’édition. A client side logic is listening to the layer switch event and adds the selector if a the channel has the dedicated resource type *screens/core/components/channel.*

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
| *cq.screens.components* | CSS partagés et JS |

>[!NOTE]
>
>To develop custom components, use the *** [AEM Screens sample component template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.


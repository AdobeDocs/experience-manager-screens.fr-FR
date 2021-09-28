---
title: Utilisation de rendus adaptatifs dans AEM Screens
description: Cette page décrit comment utiliser les rendus adaptatifs dans AEM Screens.
source-git-commit: 68e7a47d7a9b10d1d3fecb7a7f7d96bbbde1c48a
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---


# Utilisation de rendus adaptatifs dans AEM Screens {#adaptive-renditions}

## Présentation {#introduction}

Les rendus adaptatifs permettent aux appareils de sélectionner automatiquement le meilleur rendu pour un appareil en fonction des règles définies par le client. Les périphériques téléchargent et lisent automatiquement le rendu le plus approprié d’une ressource en fonction de ces règles, ce qui permet aux clients de se concentrer uniquement sur la conception de l’expérience *main*.

## Objectif {#objective}

En tant qu’auteur de contenu AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques à l’appareil pour qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu.
Une fois qu’un développeur ajoute les propriétés et les règles de mappage de rendu, vous êtes prêt à appliquer le mappage de rendu aux ressources et à les inclure ensuite dans un canal AEM Screens.

>[!IMPORTANT]
>Avant de commencer à utiliser les rendus adaptatifs, dans un canal AEM Screens, il est recommandé d’en savoir plus sur la présentation et la configuration de l’architecture de cette fonctionnalité. Voir [Rendus adaptatifs : Présentation et configurations de l’architecture ](/help/user-guide/adaptive-renditions.md) pour plus d’informations.

## Utilisation de rendus adaptatifs dans les canaux {#using-adaptive-renditions}

>[!NOTE]
>Une fois que vous avez ajouté la [propriété de mappage de rendu au projet Screens](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) et les [règles de mappage de rendu](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules), en tant qu’auteur de contenu, vous êtes prêt à appliquer les rendus à vos ressources.

### Application de rendus aux ressources {#apply-renditions-assets}

Suivez les étapes ci-dessous pour appliquer des rendus aux ressources, que vous souhaitez utiliser dans le canal Screens :

1. Accédez au dossier **Ressources** dans votre instance AEM.

1. Créez une version de la ressource qui convient le mieux à l’affichage de la signalétique, par exemple `seahorse.jpg`.

1. Choisissez le modèle de dénomination du rendu, par exemple`landscape`, similaire à ce qui a été défini dans la propriété **pattern** dans **CRXDE Lite**. Pour plus d’informations, voir [Ajout de règles de mappage de rendu](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) .

1. Renommez le fichier de ressource afin qu’il contienne le modèle (défini à l’étape 3), par exemple `seahorse-landscape.png`.

1. Cliquez sur **Ajouter le rendu** pour télécharger le rendu, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/adaptive-renditions/add-rendition.png)

1. Une fois la ressource ajoutée, sélectionnez-la et cliquez sur **Gérer la publication** dans la barre d’actions pour la publier.

   ![image](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >Pour en savoir plus sur la gestion de la publication et la diffusion de mises à jour de contenu de l’auteur à la publication sur le périphérique, voir [Mise à jour de contenu à la demande](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content.html?lang=en) .


## Stratégie de migration {#migration-strategy}

>[!IMPORTANT]
>Pour les réseaux volumineux, il est recommandé d’effectuer la migration graduellement afin d’atténuer les risques, car la fonctionnalité introduira des modifications dans le format de stockage de manifeste et de fichier. L’ajout de `sling:configRef` à l’ensemble du projet implique la mise à jour de tous les lecteurs vers le Feature Pack 6.5.9. Si vous avez mis à jour certains lecteurs, vous devez ajouter `sling:configRef` uniquement aux dossiers d’affichages, d’emplacements ou de canaux dont tous les lecteurs ont été mis à jour vers le Feature Pack 6.5.9.

Le diagramme suivant illustre la stratégie de migration pour les réseaux volumineux :

![image](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Pour activer la fonction, ajoutez au moins une règle de mappage et assurez-vous que la configuration du mappage de rendu peut être résolue dans le contexte des affichages et des canaux. Pour migrer, procédez comme suit :

1. Ajoutez [Règles de mappage de rendu](/help/user-guide/adaptive-renditions.md).
1. Créez un dossier pour les nouveaux canaux et ajoutez une référence pointant vers la configuration du mappage de rendu.
1. Créez des canaux qui remplacent les anciens et téléchargez des rendus.
1. Réaffecter les affichages aux nouveaux canaux.
1. Ajoutez une référence aux affichages ou emplacements migrés pointant vers la configuration du mappage de rendu.
1. Répétez les étapes 3, 4 et 5 pour tous les autres canaux et affichages.

   >[!NOTE]
   >Une fois la migration terminée, veillez à supprimer toutes les références de configuration des canaux, affichages et emplacements, et à en ajouter une seule au noeud de contenu du projet.


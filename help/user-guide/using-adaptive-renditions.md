---
title: Utilisation des rendus adaptatifs dans AEM Screens
description: Découvrez comment utiliser les rendus adaptatifs dans AEM Screens.
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: ba5327077e4a2d30cc7b77f02123da5a240c67ae
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 36%

---

# Utilisation des rendus adaptatifs dans AEM Screens {#adaptive-renditions}

## Présentation {#introduction}

Les rendus adaptatifs permettent aux appareils de sélectionner automatiquement le meilleur rendu pour un appareil en fonction des règles définies par le client. Les périphériques téléchargent et lisent automatiquement le rendu le plus approprié d’une ressource en fonction de ces règles, ce qui permet aux clients de se concentrer uniquement sur la conception de la *main* expérience.

## Objectif {#objective}

En tant qu’auteur de contenu AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques pour un appareil afin qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu.
Une fois que le développeur a ajouté les propriétés et les règles de mappage de rendu, vous êtes prêt à appliquer le mappage de rendu aux ressources, puis à les inclure dans un canal AEM Screens.

>[!IMPORTANT]
>Avant de commencer à utiliser les rendus adaptatifs dans un canal AEM Screens, Adobe vous recommande d’en savoir plus sur la présentation et la configuration de l’architecture de cette fonctionnalité. Voir [Rendus adaptatifs : présentation et configurations de l’architecture](/help/user-guide/adaptive-renditions.md).

## Utilisation de rendus adaptatifs dans les canaux {#using-adaptive-renditions}

>[!NOTE]
>Une fois que vous avez ajouté [Propriété de mappage de rendu au projet Screens](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) et [règles de mappage de rendu](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules), en tant qu’auteur de contenu, vous êtes maintenant prêt à appliquer les rendus à vos ressources.

### Application de rendu aux ressources {#apply-renditions-assets}

Pour appliquer des rendus aux ressources que vous souhaitez utiliser dans le canal Screens, procédez comme suit.

1. Accédez au dossier **Ressources** dans votre instance AEM.
1. Créez une version de la ressource qui convient le mieux à l’affichage de la signalétique, par exemple `seahorse.jpg`.
1. Choisissez le modèle de dénomination du rendu, par exemple `landscape`, similaire à ce qui a été défini dans la propriété **motif** dans **CRXDE Lite**. Voir [Ajout de règles de mappage de rendu](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) pour plus d’informations.
1. Cliquez sur **Ajouter un rendu** pour charger le rendu, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. Sélectionnez le fichier de ressource renommé. Le rendu que vous ajoutez doit contenir le modèle (défini à l’étape 3), par exemple `seahorse-landscape.png`.
1. Une fois la ressource ajoutée, sélectionnez-la, puis cliquez sur **Gérer la publication** à partir de la barre d’actions pour publier la ressource.

   ![image](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >Voir [Mise à jour du contenu On-Demand](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content) pour en savoir plus sur la gestion de la publication et la diffusion de mises à jour de contenu de l’auteur à la publication sur le périphérique.

## Stratégie de migration {#migration-strategy}

>[!IMPORTANT]
>Pour les réseaux volumineux, Adobe recommande que la migration soit réalisée progressivement afin d’atténuer les risques. Cela est dû au fait que la fonction peut introduire des modifications dans le format de stockage de manifeste et de fichier. Ajouter le `sling:configRef` à l’ensemble du projet implique la mise à jour de tous les lecteurs vers le Feature Pack 6.5.9. Si vous avez mis à jour certains lecteurs, ajoutez la variable `sling:configRef` uniquement aux dossiers d’affichages, d’emplacements ou de canaux pour lesquels tous les lecteurs ont été mis à jour vers le Feature Pack 6.5.9.

Le diagramme suivant illustre la stratégie de migration pour les réseaux de taille importante :

![image](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Pour activer la fonctionnalité, ajoutez au moins une règle de mappage et assurez-vous que la configuration de mappage de rendu peut être résolue dans le contexte des affichages et des canaux. Pour réaliser la migration, procédez comme suit :

1. Ajoutez les [Règles de mappage de rendu](/help/user-guide/adaptive-renditions.md).
1. Créez un dossier pour les nouveaux canaux et ajoutez une référence pointant vers la configuration de mappage de rendu.
1. Créez des canaux qui remplacent les anciens et téléchargez des rendus.
1. Réaffectez les affichages aux nouveaux canaux.
1. Ajoutez une référence aux affichages ou emplacements migrés pointant vers la configuration de mappage de rendu.
1. Répétez les étapes 3, 4 et 5 pour tous les autres canaux et affichages.

   >[!NOTE]
   >Une fois la migration terminée, veillez à supprimer toutes les références de configuration des canaux, affichages et emplacements, et à en ajouter une seule au nœud de contenu du projet.

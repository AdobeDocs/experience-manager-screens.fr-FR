---
title: Analyses avec AEM Screens
seo-title: Analyses avec AEM Screens
description: La page décrit Analytics avec les écrans AEM
seo-description: La page décrit les analyses avec les écrans AEM.
translation-type: tm+mt
source-git-commit: f01b69b860a3862e2b46f11b2d9b95dede742d9c

---


# Analytics avec AEM Screens {#analytics-screens}

>[!NOTE]
>
>Les parties prenantes habituelles de cette activité sont les responsables du marketing et des stratégies commerciales.

AEM Screens permet de capturer localement chaque événement pouvant faire l’objet d’un suivi exécuté par chaque périphérique du lecteur. Ces données seront stockées localement jusqu’à ce qu’elles puissent être téléchargées dans le cloud pour traitement. Outre toutes les données d’événement, un deviceID et un horodatage sont également ajoutés. Ainsi, les données d’un lecteur peuvent être distinguées d’un autre lecteur et les données exécutées à des moments différents de la journée peuvent être évaluées séparément, si nécessaire.

Il y a deux raisons fondamentales pour lesquelles nous pouvons vouloir capturer ces données.

La première implique des boucles de **rétroaction et un apprentissage** automatique, tandis que la seconde implique la **création de graphiques, de tableaux de bord et de rapports** destinés à la consommation humaine.

Dans le cas de l’utilisation de la boucle de commentaire, nous ne nous soucions pas des rapports visuels ou des tableaux de bord, mais plutôt de définir des règles sur lesquelles AEM peut s’exécuter pour la modification du contenu. En consommant et en traitant toutes les données d’événement du lecteur d’écran à partir d’une certaine période, nous pouvons définir une règle qui évalue l’efficacité d’image1 par rapport à image2. En combinant les données de ventes aux données de lecture, AEM peut déterminer que l’image1 a un impact bien plus important sur les ventes et demander automatiquement à tous les lecteurs d’utiliser image1.

Le deuxième cas d’utilisation d’Analytics consiste à traiter les événements de lecture et les données d’utilisation pour la consommation humaine au moyen de rapports et de tableaux de bord.
Nous pouvons utiliser ces données pour créer une carte d’une expérience interactive afin de déterminer la carte de parcours préférée dans notre application. Nous pouvons également choisir de créer un tableau de bord qui fournit une interprétation graphique du nombre de fois où les consommateurs interagissent avec notre application.


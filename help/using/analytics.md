---
title: Analyses avec AEM Screens
description: Découvrez Adobe Analytics avec Adobe Experience Manager Screens.
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 20%

---

# Analyses avec AEM Screens {#analytics-screens}

>[!NOTE]
>
>Les parties prenantes standard de cette activité sont les stratèges marketing/métier.

AEM Screens permet de capturer, en local, tous les événements pouvant faire l’objet d’un suivi qui sont exécutés par chaque appareil de lecture. Ces données sont stockées localement jusqu’à ce qu’elles puissent être chargées dans le cloud en vue de leur traitement. Outre toutes les données d’événement, un deviceID et un horodatage sont ajoutés. Cela permet de s’assurer que les données d’un lecteur peuvent être distinguées d’un autre lecteur et que les données exécutées à différents moments de la journée peuvent être évaluées séparément, si nécessaire.

Il existe deux raisons fondamentales à la capture de ces données.

Le premier implique **boucles de rétroaction et apprentissage automatique** tandis que la seconde implique la **création de graphiques, de tableaux de bord et de rapports** qui sont destinés à la consommation humaine.

Dans le cas de l’utilisation de la feedback loop, il n’est pas nécessaire de se préoccuper des rapports visuels ou des tableaux de bord, mais plutôt de définir des règles sur lesquelles AEM peut s’exécuter pour la modification du contenu. En consommant et en traitant toutes les données d’événement du lecteur Screens d’une période donnée, vous pouvez définir une règle qui évalue l’efficacité d’image1 par rapport à image2. En combinant les données de ventes aux données de lecture, AEM peut déterminer qu’image1 a un plus grand impact sur les ventes et demande automatiquement à tous les lecteurs d’utiliser image1.

Le deuxième cas d’utilisation consiste à traiter les événements de lecture et les données d’utilisation compréhensibles par un humain au moyen de rapports et de tableaux de bord.
Vous pouvez utiliser ces données pour créer une carte thermique d’une expérience interactive afin de déterminer la carte de parcours préférée dans l’application. Vous pouvez également choisir de créer un tableau de bord qui donne une représentation graphique du nombre de fois où les consommateurs interagissent avec l’application.

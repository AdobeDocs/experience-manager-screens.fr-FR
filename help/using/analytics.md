---
title: Analytics avec AEM Screens
description: Découvrez Adobe Analytics avec Adobe Experience Manager Screens.
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 92%

---

# Analytics avec AEM Screens {#analytics-screens}

>[!NOTE]
>
>Cette activité est généralement réalisée par des personnes spécialisées dans la stratégie opérationnelle/marketing.

AEM Screens permet de capturer, en local, tous les événements pouvant faire l’objet d’un suivi qui sont exécutés par chaque appareil de lecture. Ces données sont stockées en local jusqu’à ce qu’elles puissent être téléchargées dans le cloud en vue de leur traitement. Outre toutes les données d’événement, un deviceID et un horodatage sont ajoutés. Ainsi, il est possible de distinguer les données d’un lecteur de celles d’un autre lecteur et, au besoin, les données exécutées à différents moments de la journée peuvent être évaluées séparément.

Il y a deux raisons fondamentales à la capture de ces données.

La première a trait aux **boucles de rétroaction et au machine learning**, tandis que la seconde implique la **création de graphiques, de tableaux de bord et de rapports** compréhensibles par un humain.

S’agissant de la boucle de rétroaction, les rapports visuels et les tableaux de bord ne constituent pas votre sujet de préoccupation principal. L’objectif est plutôt de définir des règles sur lesquelles AEM peut s’exécuter pour la modification de contenu. L’exploitation et le traitement de toutes les données d’événement de lecture Screens d’une période donnée vous permettent de définir une règle qui évalue l’efficacité d’image1 par rapport à image2. En combinant les données de ventes aux données de lecture, AEM peut déterminer qu’image1 a un impact plus important sur les ventes et demande automatiquement à tous les lecteurs de l’utiliser.

Le deuxième cas d’utilisation d’Analytics consiste à traiter les événements de lecture et les données d’utilisation pour la consommation humaine au moyen de rapports et de tableaux de bord.
Vous pouvez utiliser ces données pour créer une carte de fréquentation (heatmap) d’une expérience interactive afin de déterminer le cheminement préféré dans votre application. Vous pouvez également choisir de créer un tableau de bord qui représente, sous forme graphique, le nombre de fois où les consommateurs et consommatrices interagissent avec votre application.

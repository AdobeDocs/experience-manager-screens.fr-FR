---
title: Analyses avec AEM Screens
seo-title: Analyses avec AEM Screens
description: Cette page décrit les analyses avec AEM Screens
seo-description: Cette page décrit les analyses avec AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 100%

---


# Analyses avec AEM Screens {#analytics-screens}

>[!NOTE]
>
>Cette activité est généralement réalisée par un stratège opérationnel/marketing.

AEM Screens permet de capturer, en local, tous les événements pouvant faire l’objet d’un suivi qui sont exécutés par chaque appareil de lecture. Ces données sont stockées en local jusqu’à ce qu’elles puissent être téléchargées dans le cloud en vue de leur traitement. Outre toutes les données d’événement, un deviceID et un horodatage sont ajoutés. Ainsi, il est possible de distinguer les données d’un lecteur de celles d’un autre lecteur et, au besoin, les données exécutées à différents moments de la journée peuvent être évaluées séparément.

Il y a deux raisons fondamentales à la capture de ces données.

La première a trait aux **boucles de rétroaction et à l’apprentissage automatique**, tandis que la seconde implique la **création de graphiques, de tableaux de bord et de rapports** compréhensibles par un humain.

S’agissant de la boucle de rétroaction, les rapports visuels et les tableaux de bord ne constituent pas notre sujet de préoccupation principal. L’objectif est plutôt de définir des règles sur lesquelles AEM peut s’exécuter pour la modification de contenu. L’exploitation et le traitement de toutes les données d’événement de lecture Screens d’une période donnée nous permettent de définir une règle qui évalue l’efficacité d’image1 par rapport à image2. En combinant les données de ventes aux données de lecture, AEM peut déterminer qu’image1 a un impact bien plus important sur les ventes et demande automatiquement à tous les lecteurs de l’utiliser.

Le deuxième cas d’utilisation consiste à traiter les événements de lecture et les données d’utilisation compréhensibles par un humain au moyen de rapports et de tableaux de bord.
Nous pouvons utiliser ces données pour créer une carte de fréquentation (heatmap) d’une expérience interactive afin de déterminer le cheminement préféré dans notre application. Nous pouvons également choisir de créer un tableau de bord qui représente, sous forme graphique, le nombre de fois où les consommateurs interagissent avec notre application.


---
title: Approche recommandée
description: Découvrez l’approche recommandée dans un projet AEM Screens.
exl-id: 28aacffa-e9c9-4ccb-8038-720bb3e02a3f
TQID: https://experienceleague.adobe.com/r0WE0DQZx3dtGGlNaX9DUX3ckvu2ZdseJLy8-sDJZXQ
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: ae478996-b206-4712-9b0c-dc78a2644453
  - id: f18e6c98-d21a-4444-b84b-f327ce464de4
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: fc314d1d-7cb9-4a38-8dbd-8f9b6478f40d
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 482
ht-degree: 47%

---

# Approche recommandée {#recommended-approach}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

La bonne pratique consiste à considérer tout projet AEM Screens au niveau de l’entreprise comme une activité sur le long terme. Il est probable que le projet s’étende sur une ou plusieurs années, notamment si la solution permet des interactions complexes avec les utilisateurs et utilisatrices ou si elle est déployée sur divers appareils et emplacements.

## Consignes pour le développement d’une stratégie de signalétique numérique {#signage-strategy}

Voici quelques recommandations dont vous devez tenir compte avant de développer et de déployer un projet de signalétique numérique :

* **Contrôle de l’étendue** :
Si la solution souhaitée est ambitieuse, il est recommandé de diviser les éléments livrables en phases discrètes pour contrôler la portée du projet.

* **Cas D’Utilisation Définis** :
Les phases de projet doivent fournir des cas d’utilisation clairement définis avec des critères de réussite clairement identifiés.

* **Éléments livrables incrémentiels** :
Concentrez-vous sur la diffusion progressive des fonctionnalités.

* **Estimation du résultat souhaité** :
Commencez par utiliser les fonctionnalités AEM Screens prêtes à l’emploi avant de créer des composants et des intégrations personnalisés. Examinez avec les autres membres du projet s’il est possible d’atteindre le résultat souhaité à l’aide des composants et des fonctionnalités standard fournis avec les AEM Screens.

* **définition des pilotes, des déploiements et des POC** :
Développez une preuve de concept (PDC) et adaptez-la si nécessaire au moyen d’un pilote et d’un déploiement.

* **Prédéfinition de la stratégie de contenu** :
Établissez une stratégie de contenu, y compris des objectifs à court et à long terme. Alignez également les objectifs et KPI de la marque sur les améliorations de fonctionnalités.

  >[!NOTE]
  >
  > Les coûts initiaux sont souvent plus élevés sur un projet AEM Screens en raison de la nécessité d’investir dans du matériel, des installations et des conceptions de site. Par conséquent, le fait de simplifier les solutions de contenu initiales peut aider à gérer les attentes de budget.

* **Estimation des livrables à grande échelle** :
Si la solution est diffusée à grande échelle, déployez les composants de l’application vers des emplacements pilotes soigneusement choisis pour une utilisation à titre d’essai. Une fois l’application validée, vous pouvez la déployer sur de nouveaux appareils et à d’autres emplacements.

  >[!NOTE]
  >
  > Commencez à collecter des données d’analyse pendant le projet pilote afin que les équipes commerciales puissent valider le succès de la solution par rapport aux mesures spécifiques qu’elles se sont fixées. Le fait de connaître les performances du projet pilote aide les équipes commerciales à identifier les améliorations à apporter.

* **Diviser les livrables en tâches mesurables** :
La division de la diffusion des fonctionnalités en tâches mesurables permet de recueillir des commentaires, de fournir des objectifs plus réalisables et de réduire les risques globaux du projet.

* **Élaboration d’une feuille de route** :
Si votre client souhaite un produit riche en fonctionnalités, proposez une tranche des fonctionnalités prévues au début du projet et planifiez d’autres fonctionnalités pour les phases ultérieures. Proposer un premier livrable comportant de nombreuses fonctionnalités entraîne des risques accrus et est plus difficile à valider auprès du client ou de la cliente.

* **Présentation de la portée des intégrations personnalisées** :
Les composants interactifs avec interaction écran tactile, capteur de mouvement ou RFID nécessitent un développement personnalisé important dans la méthode d’implémentation. Un diaporama, une publicité vidéo ou un menu statique peuvent être diffusés sous la forme de contenu graphique ou HTML sur un canal Screens.

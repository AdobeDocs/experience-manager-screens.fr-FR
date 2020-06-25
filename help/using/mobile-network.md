---
title: Réseau mobile direct
description: La page décrit la configuration réseau de Direct Mobile
translation-type: tm+mt
source-git-commit: d12de8de2b7bb29d85ebb0e046f2d1fd5051e928
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 2%

---


# Réseau mobile direct {#mobile-network-setup}

Les joueurs AEM Screens peuvent également être connectés à l&#39;aide de réseaux mobiles ou cellulaires s&#39;exécutant au moins sur un réseau 3G.

Dans les AEM Screens, le contenu requis est physiquement téléchargé sur le contrôleur du lecteur ou sur l’ordinateur et correctement stocké dans le système d’exploitation sous-jacent. Par conséquent, la bande passante donnée n’a d’incidence que sur les temps de téléchargement initiaux et n’influence pas les performances des écrans.

La connexion des lecteurs AEM Screens avec une connexion 3/4/5G cellulaire à votre fournisseur de données de service mobile permet de placer le routeur mobile dans un emplacement optimisé afin d&#39;assurer la meilleure couverture réseau disponible. Il s&#39;agit généralement d&#39;une position élevée et ouverte avec le plus de béton ou de métal environnant de construction optimale possible.

Cette configuration offre aux utilisateurs d’AEM Screen une grande flexibilité car aucune connexion fixe n’est requise pour se connecter aux AEM Screens.

Le diagramme suivant présente la configuration réseau mobile directe et se compose d&#39;un segment de connexion réseau unique et de la connexion de chaque lecteur au réseau de données mobile ou cellulaire.

![](/help/using/assets/direct-mobile-1.png)

## Connexion d&#39;un lecteur AEM Screens à un réseau mobile direct {#connecting-aem-screens-players}

Suivez les étapes ci-dessous pour vous assurer que les lecteurs d’écran AEM sont correctement connectés dans cette configuration :

1. Assurez-vous que chacun des lecteurs d’écran AEM est connecté au réseau des routeurs.

1. Testez la connexion Internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si vous recevez un message d&#39;erreur, vérifiez les paramètres réseau et vérifiez s&#39;il existe une liaison réseau suffisante et si le pare-feu du système d&#39;exploitation est configuré pour autoriser l&#39;accès au réseau à l&#39;aide des ports de communication AEM Screens configurés.

1. Si l’appel d’URL aboutit, vous pouvez continuer à installer les AEM Screens et à vous enregistrer. AEM Screens Débuts.

## Configuration d&#39;un réseau mobile direct {#requirements-direct}

La configuration réseau peut être logiquement séparée en deux blocs :

* Connexion Internet mobile

* Réseau local

### Connexion Internet mobile {#mobile-internet-connection}

Les performances de la connexion Internet en plus de l&#39;accessibilité au réseau fournissent une bande passante suffisante pour fonctionner en AEM Screens en douceur.

Dans Direct Mobile Network, chaque lecteur est connecté avec une carte de données mobile unique au réseau de données des fournisseurs.

Le tableau suivant présente les réseaux de données avec leur bande passante standard :

| Réseau de données | Bande passante |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1 000 à 1 000 Mbit/s |

Tout en envisageant le réseau de données à utiliser, il est recommandé de répondre aux questions suivantes :

La vitesse réseau disponible dépend du plan spécifique du fournisseur de données mobiles et de la couverture disponible qui est atteinte à l&#39;emplacement du contrôleur AEM Screens.
Tout en suivant cette configuration, il faut également tenir compte du fait que, outre la bande passante disponible, certains plans de fournisseurs de données mobiles limitent la quantité de données disponibles qui se connectent à la connexion au cours d&#39;une période donnée. Il faut s&#39;assurer qu&#39;il y a suffisamment de capacité en quantité de données et de bande passante.
Pour assurer le suivi, le Package de données nécessaire doit au moins être :

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Pour le téléchargement initial des fichiers multimédia, par exemple, lors de l&#39;intégration de nouveaux lecteurs, une plus grande quantité de données et une durée de téléchargement accrue doivent être attendues et être reflétées dans les hypothèses ci-dessus.Un réseau 4G avec une *bonne* couverture et des données *illimitées* doivent correspondre aux installations les plus courantes de cette configuration réseau.

>[!NOTE]
>Un plan minimum 3G avec une bonne couverture réseau devrait permettre d&#39;obtenir des performances de téléchargement acceptables pour un lecteur AEM Screens. S&#39;il n&#39;y a qu&#39;une couverture équitable disponible à un emplacement spécifique, il faut prendre en compte la possibilité de basculer la configuration réseau globale vers le réseau [mobile avec routeur de données mobiles et composants](/help/using/mobile-network-router.md)réseau actifs.


### Réseau local {#lan-connection}

En plus de la connectivité réseau, la performance du réseau local (LAN) est de fournir une bande passante suffisante pour fonctionner en AEM Screens en douceur. Le réseau LAN correspond généralement à un réseau de 100 Mbit/s, de sorte qu&#39;il y a suffisamment de bande passante pour connecter de nombreux périphériques avec de bonnes performances au système.

Lors de l&#39;utilisation d&#39;autres composants réseau actifs, il est obligatoire que tous ces composants correspondent aux exigences de bande passante du réseau. Par exemple, les composants réseau doivent correspondre au moins à la norme 100 Mbit/s et à la bande passante fournie par la spécification d&#39;accès Internet ou de routeur.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre localement tous les fichiers multimédias nécessaires, tels que les images et les vidéos. Le trafic réseau majeur survient lorsqu’un nouveau contenu doit être affiché sur un affichage spécifique.

Pour les opérations normales, par exemple, une liste de lecture définie qui se met à jour fréquemment au cours de la journée - offre une opération indépendante de la proximité du réseau, une fois que tous les fichiers ont été enregistrés sur le lecteur.

Dans le cas de scénarios où il y a davantage d&#39;interactions avec des capteurs ou des déclencheurs et du contenu dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d&#39;écran immédiate afin d&#39;assurer une meilleure expérience client possible.

Le tableau suivant présente un aperçu des données clés de connectivité réseau.

>[!NOTE]
>Toutes les informations font référence à la consommation de chaque périphérique du réseau demandant et téléchargeant une source Internet. Chacune de ces requêtes additionne et étend le temps de téléchargement.

![](/help/using/assets/download-times-mobile.png)




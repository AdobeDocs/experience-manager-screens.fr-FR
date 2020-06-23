---
title: Réseau mobile direct
description: La page décrit la configuration réseau de Direct Mobile
translation-type: tm+mt
source-git-commit: 6d6637d5222e861fa9a83f555baf0699f56f150a
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 16%

---


# Réseau mobile direct {#mobile-network-setup}

Les joueurs AEM Screens peuvent également être connectés à l&#39;aide de réseaux mobiles ou cellulaires exécutant au moins un réseau 3G.

Dans les AEM Screens, le contenu requis est physiquement téléchargé sur le contrôleur du lecteur ou sur l’ordinateur et correctement stocké dans le système d’exploitation sous-jacent. Par conséquent, la bande passante donnée n’a d’incidence que sur les temps de téléchargement initiaux et n’influence pas les performances des écrans.

Connexion des lecteurs AEM Screens avec une connexion cellulaire 3/4/5G à votre fournisseur de données de service mobile. L&#39;avantage de cette configuration est que le routeur mobile peut être placé dans un emplacement optimisé pour garantir la meilleure couverture réseau disponible. Il s&#39;agit généralement d&#39;une position élevée et ouverte, avec le plus de béton ou de métal environnant le moins possible.

Cette configuration offre aux utilisateurs d’écran AEM une grande flexibilité car aucune connexion fixe n’est requise pour connecter les AEM Screens.

![](/help/using/assets/direct-mobile-1.png)

## Connexion d&#39;un lecteur AEM Screens à un réseau mobile direct {#connecting-aem-screens-players}

Suivez les étapes ci-dessous pour vous connecter aux lecteurs d’écran AEM dans cette configuration :

1. Assurez-vous que chacun des lecteurs d’écran AEM est connecté au réseau des routeurs.

1. Testez la connexion Internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si vous recevez un message d&#39;erreur, vérifiez les paramètres réseau.Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle


1. Assurez-vous que le paramètre de carte réseau correspond à votre paramètre de routeur.
1. Vérifiez si le routeur est correctement connecté au réseau étendu du fournisseur de services Internet (lien Internet). Il peut également être identifié à l&#39;aide d&#39;une DEL de signal sur les routeurs standard.

1. Si l’appel d’URL aboutit, vous pouvez continuer à installer les AEM Screens et à les enregistrer en conséquence. AEM Screens Débuts.

   >[!NOTE]
   >**Conseil de dépannage**
   >Si le AEM Screens ne se connecte pas correctement et n’affiche pas le contenu attendu :
   >
   >1. Vérifiez dans le pare-feu de votre routeur Internet s’il existe des restrictions concernant `TCP/IP Port 80/443`.
   >1. Assurez-vous que tous les ports nécessaires sont autorisés.



## Configuration requise pour la configuration de la configuration réseau mobile {#requirements-direct}

La configuration réseau peut être logiquement séparée en deux blocs :

* Connexion Internet mobile

* Réseau local

### Connexion Internet mobile {#mobile-internet-connection}

Les performances de la connexion Internet en plus de l&#39;accessibilité au réseau fournissent une bande passante suffisante pour opérer en AEM Screens en douceur et en douceur.

*Suffisamment* dépend de la quantité d&#39;écrans AEM connectés et de l&#39;utilisation d&#39;autres consommateurs dans le réseau, tels que les smartphones, les tablettes, les caissiers, les ordinateurs ou les réseaux WIFI invités.
Gardez à l’esprit que tous les appareils ont un accès simultané à la connexion Internet et que la bande passante diminue généralement de façon linéaire à mesure que des appareils gourmands/ordinateurs sont ajoutés au réseau.
En plus de la connexion réseau théorique spécifique, il doit être assuré, que la couverture du routeur mobile est au moins &quot;bonne&quot; (veuillez consulter le manuel de votre routeur mobile). De plus, le plan mensuel sous-jacent doit couvrir suffisamment de capacité de données et de bande passante pour desservir tous les clients connectés au sein du réseau local connecté.

Les réseaux de données offrent une bande passante standard avec :

**3G**
* 42 Mbit/s

**4G**
* 150 Mbit/s

**5G**
* 1 000 Mbit/s à 1 000 Mbit/s

Tout en envisageant le réseau de données à utiliser, il est recommandé de répondre aux questions suivantes :

* Combien de clients sont connectés au routeur ?

* Combien de changements de contenu sont attendus et quelles sont ces tailles de fichier moyennes ?

>[!NOTE]
>Le Package de données nécessaire doit être au moins :
`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>Assurez-vous qu’il y a suffisamment de tampon.
>Pour le téléchargement initial des fichiers multimédia, par exemple, lors de l&#39;intégration de nouveaux lecteurs, une plus grande quantité de données et une durée de téléchargement accrue doivent être attendues et être reflétées dans les hypothèses ci-dessus.Un réseau 4G avec une *bonne* couverture et des données *illimitées* doivent correspondre aux installations les plus courantes de cette configuration réseau.


### Réseau local {#lan-connection}

En plus de l’accessibilité réseau déjà décrite, le réseau local doit fournir suffisamment de bande passante pour qu’AEM Screens fonctionne correctement et de manière fluide. En ce moment, le réseau LAN correspond généralement à un réseau 100 Mbit/s, de sorte qu&#39;il devrait y avoir suffisamment de bande passante pour connecter de nombreux périphériques avec de bonnes performances au système. Si vous utilisez d’autres composants réseau actifs, il est obligatoire qu’ils correspondent aux exigences de bande passante réseau. Par exemple, les composants réseau doivent correspondre au moins à la norme 100 Mbit/s et à la bande passante fournie par la spécification d&#39;accès Internet/routeur.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre localement tous les fichiers multimédia nécessaires, tels que les images et les vidéos. En raison de ce concept, le trafic réseau majeur se produit au cas où un nouveau contenu s’afficherait sur un écran spécifique.
Pour un fonctionnement normal, par exemple, une liste de lecture définie qui n&#39;est pas changée très souvent pendant la journée, cela offre une opération indépendante du réseau proche, une fois tous les fichiers enregistrés sur le lecteur.
Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Le tableau suivant présente un aperçu des données clés de connectivité réseau pour les performances prévisibles et les temps d&#39;attente potentiels.
>[!NOTE]
>Toutes les informations font référence à la consommation de chaque périphérique du réseau demandant et téléchargeant une source Internet. Chacune de ces requêtes additionne et étend le temps de téléchargement.

![](/help/using/assets/download-times-mobile.png)




---
title: Configuration du réseau mobile
description: La page décrit la configuration du réseau mobile.
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 44%

---


# Configurations de réseau mobile {#mobile-network-setup}

Les lecteurs AEM Screens Adobe peuvent également être connectés à l&#39;aide de réseaux mobiles/cellulaires exécutant au moins un réseau 3G.
Dans les AEM Screens, le contenu nécessaire est physiquement téléchargé sur le contrôleur/ordinateur du lecteur et correctement stocké dans le système d&#39;exploitation sous-jacent. Par conséquent, la bande passante donnée n’a qu’une incidence sur les temps de téléchargement initiaux et n’a aucune incidence sur les performances des systèmes d’affichage.
Connexion des lecteurs AEM Screens avec une connexion cellulaire 3/4/5G à votre fournisseur de données de service mobile. L&#39;avantage de cette configuration est que le routeur mobile peut être placé dans un emplacement optimisé pour garantir la meilleure couverture réseau disponible. Il s&#39;agit généralement d&#39;une position élevée et ouverte, avec le plus de béton ou de métal environnant le moins possible.
Cette configuration offre aux utilisateurs d’écran AEM une grande flexibilité car aucune ligne fixe n’est nécessaire pour connecter les AEM Screens.


## Configuration d’un réseau d’accès direct {#requirements-direct}

La configuration réseau décrite dans la version 5.5 peut être logiquement séparée en trois blocs. Le bloc de connexion WAN/External World/Internet (ici Connexion aux données mobiles), le réseau local/local interne et les sous-sections facultatives du réseau local séparées par des composants réseau actifs.
Pour fournir le meilleur rendement possible, il faut s&#39;assurer que les deux sections respectent les normes minimales recommandées.
Que signifie &quot;bonne performance&quot; dans l&#39;Environnement AEM Screens ?
AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, la majorité du trafic réseau a lieu lorsqu’un nouveau contenu s’affiche sur un écran spécifique.
Pour le fonctionnement normal, par exemple, si vous avez défini une liste de lecture qui ne change pas très souvent au cours de la journée, cela permet d’opérer de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.
Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.
Les tableaux ci-dessous offrent une bonne vue d’ensemble des données clés de connectivité réseau en ce qui concerne les performances prévisibles et les temps d’attente potentiels.
Toutes ces informations doivent être considérées comme la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.


### WAN/connexion Internet {#wan-connection}

En plus de l’accessibilité réseau déjà décrite, la connexion Internet doit fournir suffisamment de bande passante pour qu’AEM Screens fonctionne correctement et de manière fluide. En détail, &quot;suffisant&quot; dépend de la quantité d’écrans AEM connectés et de l’utilisation d’autres consommateurs du réseau, tels que les Smartphones, les Tablettes, les Caissiers, les Ordinateurs ou les réseaux Wifi invités.
Gardez à l’esprit que tous les appareils ont un accès simultané à la connexion Internet et que la bande passante diminue généralement de façon linéaire à mesure que des appareils gourmands/ordinateurs sont ajoutés au réseau.
En plus de la connexion réseau théorique spécifique, il doit être assuré, que la couverture du routeur mobile est au moins &quot;bonne&quot; (veuillez consulter le manuel de votre routeur mobile). De plus, le plan mensuel sous-jacent doit couvrir suffisamment de capacité de données et de bande passante pour desservir tous les clients connectés au sein du réseau local connecté.
Les réseaux de données fournissent une bande passante standard d&#39;environ.. jusqu&#39;à :
・ 3Go 42Mbit/s ・ 4Go 150Mbit/s ・ 5Go 1000Mbit/s-10000Mbit/sEn considérant quel réseau de données doit être utilisé, il est recommandé de répondre aux questions suivantes :
・ Combien de clients sont connectés au routeur ?
・ Combien de changements de contenu dois-je attendre et quelles sont ces tailles de fichier moyennes ?
Pour donner suite, le Package de données nécessaire doit au moins être :
Capacité du Package de données = Nombre de clients * ( Nombre de fichiers de contenu * Taille moyenne du fichier) Assurez-vous qu&#39;il y a suffisamment de mémoire tampon.
Attention : Pour le téléchargement initial des fichiers multimédia, par exemple, lors de l’intégration de nouveaux lecteurs, une plus grande quantité de données et une durée de téléchargement accrue doivent être attendues et être reflétées dans les hypothèses ci-dessus.
En règle générale, un réseau 4G avec une &quot;bonne&quot; couverture et des données illimitées doit correspondre aux installations les plus courantes de cette configuration réseau.


### Connexion de réseau local {#lan-connection}

En plus de l’accessibilité réseau déjà décrite, le réseau local doit fournir suffisamment de bande passante pour qu’AEM Screens fonctionne correctement et de manière fluide. Actuellement, le réseau LAN atteint généralement un débit de 100 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances. Si vous utilisez d’autres composants réseau actifs, il est obligatoire qu’ils correspondent aux exigences de bande passante réseau. Par exemple, les composants réseau doivent correspondre au moins à la norme 100 Mbit/s et à la bande passante fournie par la spécification d&#39;accès Internet/routeur.
Si une solution Wi-Fi est envisagée pour connecter l’écran à Internet, il est recommandé d’utiliser au minimum les standards Wi-Fi modernes tels que IEEE 802.11g. Cette norme prend en charge les connexions jusqu’à 54 Mbit. Toute nouvelle norme telle que 802.11h-n est de meilleure qualité. Si un répéteur Wifi est nécessaire, nous recommandons fortement les technologies de point d&#39;accès Mesh Wifi, comme Google Nest Mesh Wifi ou d&#39;autres technologies similaires.
D’autres technologies qui répètent le signal Wi-Fi finissent par provoquer une perte massive de bande passante dans l’ensemble du réseau.

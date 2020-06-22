---
title: Présentation des serveurs proxy
seo-title: Présentation des serveurs proxy
description: La page décrit les serveurs proxy.
seo-description: La page décrit les serveurs proxy.
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 58%

---


# Présentation des configurations réseau standard {#intro-standard-networks}

Une configuration réseau peut avoir différentes structures. Cette section présente un aperçu des structures réseau déployées dans un environnement. Il existe différentes configurations qui sont parfois mises en oeuvre à partir de rien.

Cette section présente les serveurs proxy, suivis des différentes structures réseau configurées au sein de différentes organisations.

## Serveurs proxy {#proxy-servers}

Un serveur proxy est un ordinateur dédié ou un système logiciel s’exécutant sur un ordinateur qui agit comme intermédiaire entre un terminal de point d’entrée, tel qu’un ordinateur, et un autre serveur à partir duquel un utilisateur ou un client demande un service. Le serveur proxy peut exister sur la même machine qu’un serveur de pare-feu ou sur un serveur distinct qui transfère les demandes par le biais du pare-feu.

L’un des avantages du serveur proxy est que son cache peut servir tous les utilisateurs. Si un ou plusieurs sites Internet sont fréquemment demandés, ils sont susceptibles de se trouver dans le cache du proxy, ce qui réduira le temps de réponse pour l’utilisateur. Un proxy peut également consigner ses interactions, ce qui peut s’avérer utile pour le dépannage.

## Présentation des configurations réseau {#network-setups}

Pour mettre en œuvre une configuration réseau, vous devez vous référer aux scénarios suivants avec leurs avantages et inconvénients respectifs.

Il existe trois types principaux de configuration réseau :

1. Accès Internet Configuration
1. Configuration du réseau mobile
1. Configuration du réseau d&#39;entreprise enfermée

Le tableau suivant décrit les différents types de configuration réseau avec des avantages et des inconvénients :

<table>
 <tbody>
  <tr>
   <td><strong>Configuration réseau</strong></td>
   <td><strong>Avantages</strong></td>
   <td><strong>Inconvénients</strong></td>
  </tr>
  <tr>
   <td><strong>Configuration de l'accès Internet</strong></td>
   <td>Installation<br>Un bon choix pour les installations<br><br>dédiées de taille moyenne ou supérieure peut être encapsulé<br>Quelques points de panne<br>Relativement peu onéreuxUne bonne évolutivité</td>
   <td>Plan de données Internet approprié obligatoire</td>
  </tr>
    <tr>
   <td><strong>Configuration du réseau mobile</strong></td>
   <td>Configuration<br>Facile et directe Un bon choix pour les installations<br>de taille moyenne ou de grande taille Réseau dédié peut être encapsulé<br>Quelques points de défaillance<br>Relativement peu onéreux<br>Une bonne évolutivité</br></td>
   <td>Connexion Internet appropriée obligatoire</td>
  </tr>
    <tr>
   <td><strong>Réseau d’entreprise fermé</strong></td>
   <td>Haute flexibilité et évolutivité<br>Haute sécurité en raison des différents réseaux<br><br>encapsulés des lignes de défense<br>Facilité de surveillance et de maintenanceFiabilité</td>
   <td>Spécialistes<br>du réseau ou intégrateur système complexes et onéreux recommandés</td>
  </tr>
  </tr>
 </tbody>
</table>



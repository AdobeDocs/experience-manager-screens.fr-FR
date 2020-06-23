---
title: Présentation des configurations réseau standard
seo-title: Présentation des configurations réseau standard
description: La page décrit les configurations réseau standard.
seo-description: La page décrit les configurations réseau standard.
translation-type: tm+mt
source-git-commit: 77cf87cbce39a00528b2690d9689861b91e61fc5
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 13%

---


# Gestion du trafic réseau {#managing-network-traffic}

Une configuration réseau peut avoir différentes structures. Cette section décrit les configurations réseau les plus courantes de la configuration réseau d&#39;une entreprise.

Ce guide présente les serveurs proxy, suivis des différentes structures réseau configurées au sein de différentes organisations.

>[!NOTE]
>**Configuration requise pour le réseau AEM Screens **>Les AEM Screens communiquent directement avec AEM en tant que Cloud Service. Il est donc nécessaire d’établir une connexion stable entre les deux noeuds. Les pare-feu sont absolument obligatoires pour l&#39;accès à Internet commercial et, en tant que client, vous devez comprendre quels ports de communication doivent être ouverts dans les pare-feu et autres composants réseau liés à la sécurité informatique.

## Présentation des serveurs proxy {#proxy-servers}

Une connexion Internet repose sur l&#39;utilisation d&#39;un serveur proxy. Un serveur proxy est un ordinateur dédié ou un système logiciel s&#39;exécutant sur un ordinateur qui agit comme intermédiaire entre un périphérique de point de terminaison, tel qu&#39;un ordinateur, et un autre serveur à partir duquel un utilisateur ou un client demande un service. Le serveur proxy peut exister sur la même machine qu’un serveur de pare-feu ou sur un serveur distinct qui transfère les demandes par le biais du pare-feu.

L’un des avantages du serveur proxy est que son cache peut servir tous les utilisateurs. Si un ou plusieurs sites Internet sont fréquemment demandés, ils risquent d’être dans le cache du proxy, ce qui améliore le temps de réponse de l’utilisateur. Un proxy peut également consigner ses interactions dans un journal, qui est utilisé pour le dépannage.

## Understanding the Standard Network Setups {#network-setups}

Pour mettre en oeuvre une configuration réseau, vous devez vous référer aux scénarios suivants avec leurs points forts et leurs détails de déploiement.

Il existe quatre principaux types de configuration réseau :

1. [Réseau Internet direct (câblé/sans fil)](/help/using/direct-internet-network.md)
1. [Réseau mobile direct](/help/using/mobile-network.md)
1. [Réseau mobile avec routeur de données mobile et composants réseau actifs](/help/using/mobile-network-router.md)
1. [Réseau d&#39;entreprise fermé (câblé/sans fil)](/help/using/enclosed-corporate-network.md)

Le tableau suivant décrit les différents types de configuration réseau avec des avantages et des inconvénients :

<table>
 <tbody>
  <tr>
   <td><strong>Configuration réseau</strong></td>
   <td><strong>Avantages</strong></td>
   <td><strong>Inconvénients</strong></td>
  </tr>
  <tr>
   <td><strong>Réseau Internet direct (câblé/sans fil)</strong></td>
   <td>Installation<br>Un bon choix pour les installations<br><br>de taille moyenne ou plus importantes Un réseau dédié peut être encapsulé<br>Quelques points de panne<br>Relativement peu cherBonne évolutivité</td>
   <td>Plan de données Internet obligatoire </td>
  </tr>
    <tr>
   <td><strong>Réseau mobile direct</strong></td>
   <td>Facile à configurer<br>Bon choix pour les installations<br>de taille moyenne ou plus grande Évolutivité<br>Écrans encapsulés
</td>
   <td>Connexion Internet obligatoire</td>
  </tr>
    <tr>
<tr>
   <td><strong>Réseau mobile avec routeur de données mobile et composants réseau actifs</strong></td>
   <td>Facile à configurer<br>Bon choix pour les installations<br><br>dédiées de taille moyenne ou plus grandes Le réseau peut être encapsulé<br>Quelques points de panne<br>relativement peu coûteuxBonne évolutivité</br></td>
   <td>Plan de données Internet obligatoire</td>
  </tr>
    <tr>

<td><strong>Réseau d'entreprise fermé (câblé/sans fil)</strong></td>
   <td>Une flexibilité et une évolutivité<br>très sécurisées en raison des différentes lignes de défense<br><br>des réseaux<br>encapsulés Facilité de surveillance et de maintenanceFiables</td>
   <td>Compliqué et coûteux<br>recommandé pour les spécialistes du réseau ou les intégrateurs de systèmes</td>
  </tr>
  </tr>
 </tbody>
</table>



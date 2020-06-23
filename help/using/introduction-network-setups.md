---
title: Présentation des configurations réseau standard
seo-title: Présentation des configurations réseau standard
description: La page décrit les configurations réseau standard.
seo-description: La page décrit les configurations réseau standard.
translation-type: tm+mt
source-git-commit: 0be82fcc46166ec0613bd658a0caeab83bd72551
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 36%

---


# Gestion du trafic réseau {#managing-network-traffic}

Une configuration réseau peut avoir différentes structures. Cette section présente un aperçu des structures réseau déployées dans un environnement. Il existe différentes configurations qui sont parfois mises en oeuvre à partir de rien.

Cette section présente les serveurs proxy, suivis des différentes structures réseau configurées au sein de différentes organisations.

>[!NOTE]
>**Configuration requise pour le réseau AEM Screens **>Les AEM Screens communiquent directement avec le Cloud Service AEM. Il est donc nécessaire d’établir une connexion stable entre ces deux noeuds. Les pare-feu sont absolument obligatoires pour l&#39;accès Internet commercial et le Client doit savoir quels ports de communication doivent être ouverts dans les pare-feu et les autres composants réseau liés à la sécurité informatique qui sont sous le contrôle du Client.

## Serveurs proxy {#proxy-servers}

Un serveur proxy est un ordinateur dédié ou un système logiciel s’exécutant sur un ordinateur qui agit comme intermédiaire entre un terminal de point d’entrée, tel qu’un ordinateur, et un autre serveur à partir duquel un utilisateur ou un client demande un service. Le serveur proxy peut exister sur la même machine qu’un serveur de pare-feu ou sur un serveur distinct qui transfère les demandes par le biais du pare-feu.

L’un des avantages du serveur proxy est que son cache peut servir tous les utilisateurs. Si un ou plusieurs sites Internet sont fréquemment demandés, ils sont susceptibles de se trouver dans le cache du proxy, ce qui réduira le temps de réponse pour l’utilisateur. Un proxy peut également consigner ses interactions, ce qui peut s’avérer utile pour le dépannage.

## Understanding the Standard Network Setups {#network-setups}

Pour mettre en oeuvre une configuration réseau, vous devez vous référer aux scénarios suivants avec les points forts et les détails de déploiement.

Il existe trois types principaux de configuration réseau :

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
   <td><strong>Accès direct à Internet</strong></td>
   <td>Installation<br>Un bon choix pour les installations<br><br>dédiées de taille moyenne ou supérieure peut être encapsulé<br>Quelques points de panne<br>Relativement peu onéreuxUne bonne évolutivité</td>
   <td>Plan de données Internet approprié obligatoire</td>
  </tr>
    <tr>
   <td><strong>Réseau mobile direct</strong></td>
   <td>Configuration<br>Optimisée pour les installations<br>de taille moyenne ou de grande taille<br>Bonne évolutivitéÉcrans encapsulés
</td>
   <td>Connexion Internet appropriée obligatoire</td>
  </tr>
    <tr>
<tr>
   <td><strong>Réseau mobile avec routeur de données mobile et composants réseau actifs</strong></td>
   <td>Configuration<br>Facile et directe Un bon choix pour les installations<br>de taille moyenne ou de grande taille Réseau dédié peut être encapsulé<br>Quelques points de défaillance<br>Relativement peu onéreux<br>Une bonne évolutivité</br></td>
   <td>Plan de données Internet approprié obligatoire</td>
  </tr>
    <tr>

<td><strong>Réseau d’entreprise fermé</strong></td>
   <td>Haute flexibilité et évolutivité<br>Haute sécurité en raison des différents réseaux<br><br>encapsulés des lignes de défense<br>Facilité de surveillance et de maintenanceFiabilité</td>
   <td>Spécialistes<br>du réseau ou intégrateur système complexes et onéreux recommandés</td>
  </tr>
  </tr>
 </tbody>
</table>



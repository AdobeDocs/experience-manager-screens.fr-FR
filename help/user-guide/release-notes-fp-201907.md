---
title: Notes de mise à jour du Feature Pack 201907
description: Découvrez le Feature Pack 201907 d’AEM Screens, publié le 31 juillet 2019.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: release-notes
content-type: reference
docset: aem65
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 6a05a014-aedf-4261-849d-abf1ce070964
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 44%

---

# Notes de mise à jour du Feature Pack 201907 {#release-notes-for-feature-pack}

>[!CAUTION]
>
>Adobe vous recommande d’effectuer la mise à niveau vers la dernière version de Adobe Experience Manager (AEM). AEM Screens assure la prise en charge de la maintenance de la plateforme AEM 6.3 Screens.

AEM Screens a publié AEM 6.4.5 Feature Pack 5 et AEM 6.5.1 Feature Pack 1 avec les détails suivants.

## Date de publication {#release-date}

La date de publication d’AEM Screens Feature Pack 201907 est le mercredi 31 juillet 2019.

### Nouveautés {#what-s-new}

* **Le Déclencheur de données entraîne la modification des ressources dans un canal AEM Screens**

Le lecteur passe à un canal qui affiche les informations d’urgence. Le système d’urgence envoie ces informations lorsqu’il reçoit un événement. Ce canal est le seul lu jusqu’à la fin de la situation d’urgence.


Voir [Canal d’urgence](emergency-channel.md) cas d’utilisation pour la mise en oeuvre.

* Ciblage activé pour les composants asynchrones

Le ciblage peut désormais être activé pour les ressources utilisées dans le projet AEM Screens.

Pour en savoir plus sur la manière d’activer le ciblage des ressources dans le projet AEM Screens, voir [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md).

Après avoir configuré ContextHub pour votre projet AEM Screens, consultez différents cas d’utilisation pour comprendre le rôle essentiel des ressources déclenchées par les données dans différents secteurs :

**[Activation ciblée du stock de vente au détail](retail-inventory-activation.md)**

**[Activation de la température de l’agence de voyages](local-temperature-activation.md)**

**[Activation de la réservation d’hébergements](hospitality-reservation-activation.md)**

* **Améliorations des gestionnaires de mise à jour**

Le gestionnaire de mise à jour analyse désormais les fragments d’expérience et collecte toute image, vidéo ou produit qui y est associé.

* **Lancements**

Les lancements permettent aux auteurs de contenu de créer des versions ultérieures des canaux. Grâce aux lancements, les auteurs peuvent prévisualiser chaque canal du lancement et doivent pouvoir lancer une demande de révision. Le groupe des approbateurs reçoit une notification et peut approuver ou rejeter la demande. Lorsque la date d’activation est atteinte, le contenu est lu sur les appareils.
Voir [Lancements](launches.md) pour plus d’informations.

* **Configurations hors ligne dans les fragments d’expérience**

Vous pouvez désormais ajouter des configurations hors ligne (bibliothèques côté client et fichiers statiques) lors de la configuration du fragment d’expérience Screens. Voir [Utilisation de fragments d’expérience](experience-fragments-in-screens.md) pour plus d’informations.

### Lecteurs AEM Screens publiés

Les lecteurs AEM Screens suivants sont publiés pour AEM 6.4.5 Feature Pack 5 et AEM 6.5.1 Feature Pack 1 :

* ChromeOS
* Windows
* Android™

#### Téléchargements du lecteur AEM Screens

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, voir [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/).

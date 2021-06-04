---
title: 'Notes de mise à jour du Feature Pack 202105 '
description: '"Consultez cette page pour obtenir des informations sur AEM Screens Feature Pack 202105, publié le 4 juin 2021."'
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: 7fa4207be0d89a6c7d0d9d9a04722cd40d035634
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 43%

---

# Notes de mise à jour du Feature Pack 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>Il est recommandé d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager (AEM). Screens fournit une prise en charge de maintenance pour la plate-forme AEM 6.3 Screens.

## Disponibilité {#availability}

AEM Screens inclus dans le Feature Pack 8 d’AEM 6.5.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.8 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack appelé **AEM 6.5 Screens FP8**.

## Date de publication {#release-date}

La date de publication du Feature Pack 202105 d’AEM Screens est le 4 juin 2021.

### Nouveautés {#what-is-new}

* **Verrouillage d’une page dans un canal AEM Screens**

   AEM Screens prend désormais en charge la fonction *Verrouillage d’une page*, comme déjà implémenté dans AEM Sites. Adobe Experience Manager (AEM) vous permet de verrouiller une page, de sorte que personne d’autre ne puisse en modifier le contenu. Cela s’avère utile lorsque vous apportez de nombreuses modifications à une page spécifique ou lorsque vous devez figer une page pendant quelque temps.

* **Attribution d’un nom au périphérique du lecteur AEM Screens**

   Les lecteurs AEM Screens incluent désormais la possibilité d’envoyer un nom de périphérique à Adobe Experience Manager (AEM).
Par défaut, lorsque l’enregistrement en masse est utilisé pour enregistrer un périphérique, un nom d’utilisateur généré par le système est saisi dans le champ du titre. Un client peut également utiliser une balise de ressource ou un autre nom convivial afin qu’il soit visible dans AEM et plus facile d’attribuer le contenu approprié.

   Reportez-vous à la documentation suivante pour savoir comment configurer le nom dans chaque système d’exploitation pris en charge :

       * [Android](/help/user-guide/implementing-android-player.md#name-android)
       * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
       * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
       * [Chrome OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)
   
* **Génération de manifeste**

   Génération plus rapide de manifeste de canal avec de meilleures performances, comme l’allocation de ressources moindres sur le serveur.

### Correctifs {#bug-fixes}

* Le lecteur affichait un écran noir lors du passage à un canal contenant une séquence incorporée dynamique.
* Les lecteurs Screens bloquent désormais le passage à un canal rompu, ce qui permet d’éviter une erreur 404 ou une page contenant un message d’erreur.

### Lecteurs AEM Screens publiés {#released-aem-screens-players}

Les lecteurs AEM Screens suivants sont publiés pour AEM 6.5 Feature Pack 8 :

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Téléchargements du lecteur AEM Screens {#aem-screens-player-downloads}

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, reportez-vous à la section **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.

---
title: Notes de mise à jour du Feature Pack 202105
description: Découvrez le Feature Pack 202105 d’AEM Screens, publié le 4 juin 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 62%

---

# Notes de mise à jour du Feature Pack 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe vous recommande d’effectuer la mise à niveau vers la dernière version de Adobe Experience Manager (AEM). AEM Screens assure la prise en charge de la maintenance de la plateforme AEM 6.3 Screens.

## Disponibilité {#availability}

Le Feature Pack 8 d’AEM 6.5 a été publié pour AEM Screens.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.8 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack appelé **AEM 6.5 Screens FP8**.

>[!IMPORTANT]
>Installez la version minimale d’AEM 6.5 Feature Pack 8 pour que le connecteur AMS fonctionne après avoir installé les packages. `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16`, et la variable `screens core bundles`.

## Date de publication {#release-date}

La date de publication du Feature Pack 202105 d’AEM Screens est le 4 juin 2021.

### Nouveautés {#what-is-new}

* **Verrouillage d’une page dans un canal AEM Screens**

  AEM Screens prend désormais en charge la fonction *Verrouillage d’une page*, déjà implémentée dans AEM Sites. Adobe Experience Manager (AEM) permet de verrouiller une page, de sorte que personne d’autre ne puisse en modifier le contenu. Cela s’avère utile lorsque vous apportez de nombreuses modifications à une page spécifique ou lorsque vous devez figer une page pendant quelque temps.

* **Nommage d’un appareil de lecteur AEM Screens**

  Les lecteurs AEM Screens comprennent désormais la possibilité d’envoyer un nom d’appareil à Adobe Experience Manager (AEM).
Par défaut, lorsque l’enregistrement en masse est utilisé pour enregistrer un périphérique, un nom d’utilisateur généré par le système est saisi dans le champ du titre. Un client peut également utiliser une balise de ressource ou un autre nom convivial afin qu’il soit visible dans AEM et qu’il soit plus facile d’attribuer le contenu approprié.

  Consultez la documentation suivante pour plus d’informations sur la configuration du nom dans chaque système d’exploitation pris en charge :

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Génération de manifeste**

  Génération plus rapide de manifeste de canal avec de meilleures performances, comme l’allocation de moins de ressources sur le serveur.

### Correctifs {#bug-fixes}

* Le lecteur affichait un écran noir lors du passage à un canal contenant une séquence incorporée dynamique.
* Les lecteurs Screens bloquent désormais le passage vers un canal rompu, ce qui permet d’éviter une erreur 404 ou une page contenant un message d’erreur.

### Lecteurs AEM Screens publiés

Les lecteurs AEM Screens suivants sont publiés pour AEM 6.5 Feature Pack 8 :

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### Téléchargements du lecteur AEM Screens

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, voir **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.

---
title: Nouvel importateur de projet à partir d’un fichier
description: Cette fonctionnalité vous permet d’importer en bloc un ensemble d’emplacements d’une feuille de calcul CSV/XLS dans votre projet AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 50%

---

# Nouvel importateur de projet à partir d’un fichier {#new-project-importer-from-file}

Cette section décrit une fonctionnalité permettant d’importer en bloc un ensemble d’emplacements depuis une feuille de calcul CSV/XLS dans votre projet AEM Screens.

## Présentation {#introduction}

Lorsque vous configurez un projet AEM Screens pour la première fois au sein de votre organisation, vous devez également créer tous les emplacements. Si votre projet implique de nombreux emplacements, il s’ensuit une tâche fastidieuse qui implique de nombreux clics et attentes dans l’interface utilisateur.

Cette fonctionnalité a pour objectif de réduire le temps nécessaire à la configuration du projet et de résoudre ainsi des problèmes de budgétisation.

En permettant à l’auteur de fournir une feuille de calcul en tant que fichier d’entrée et en laissant le système créer automatiquement l’arborescence de l’emplacement dans le serveur principal, cette fonction :

* *offre de bien meilleures performances qu’un clic manuel dans l’interface utilisateur*
* *permet aux clients d’exporter leurs emplacements depuis leur propre système et de les importer directement dans AEM*

Cela permet d’économiser du temps et de l’argent lors de la configuration initiale du projet ou lors de l’extension d’AEM Screens à de nouveaux emplacements.

## Présentation de l’architecture {#architectural-overview}

Le diagramme suivant offre un aperçu de l’architecture de la fonction Importateur de projet :

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### Modèle de données {#data-model}

Le modèle de données de l’Importateur de projet est décrit ci-dessous :

>[!NOTE]
>
>La version actuelle ne prend en charge que les emplacements d’importation.

| **Propriété** | **Description** |
|---|---|
| ***`path {string*}`*** | Chemin des ressources de l’emplacement |
| ***`[./jcr:title] {string*}`*** | Nom du modèle à utiliser (emplacement des *écrans/du noyau/des modèles/de l’emplacement*) |
| ***`template {string}`*** | Titre facultatif à utiliser pour la page |
| ***`[./jcr:description] {string}`*** | Description facultative à utiliser pour la page |

Le fichier de feuille de calcul (CSV/XLS) nécessite donc les colonnes suivantes :

* **chemin {string}** - Chemin d’accès de l’emplacement à importer, où la racine du chemin d’accès est le dossier d’emplacement du projet (en d’autres termes, *`/foo`* est importé dans *`/content/screens/<project>/locations/foo`*)
* **modèle {string}** - Modèle à utiliser pour le nouvel emplacement. Pour l’instant, la seule valeur autorisée est « location », mais cela sera étendu à tous les modèles Screens à l’avenir (`display`, `sequencechannel`, etc.)
* **[./*] {string}** - Toute propriété facultative à définir à l’emplacement (à savoir, `./jcr:title`, `./jcr:description`, `./foo, ./bar`). La version actuelle ne permet aucun filtrage.

>[!NOTE]
>
>Toute colonne qui ne correspond pas aux conditions ci-dessus est ignorée. Par exemple, si votre fichier de feuille (CSV/XLS) contient une autre colonne que : **chemin**, **modèle**, **titre**, et **description** dans votre fichier , ces champs sont ignorés. Et, **Importateur de projet** ne valide pas ces champs supplémentaires pour l’importation de votre projet dans votre projet AEM Screens.

## Utilisation de l’importateur de projet {#using-project-importer}

La section suivante décrit l’utilisation de l’importateur de projets dans un projet AEM Screens.

>[!CAUTION]
>
>Restrictions :
>
>* Les fichiers possédant une extension autre que CSV/XLS/XLSX ne sont pas pris en charge dans la version actuelle.
>* Il n’existe aucun filtrage des propriétés pour les fichiers importés et tout élément commençant par &quot;./ » est importé.
>

### Conditions préalables {#prerequisites}

* Créez un projet intitulé **DemoProjectImport**

* Utilisez un exemple de fichier CSV ou Excel que vous devez importer.

A des fins de démonstration, vous pouvez télécharger un fichier Excel depuis la section ci-dessous.

[Obtenir le fichier](assets/minimal-file.xls)

### Importation du fichier avec un minimum de champs obligatoires {#importing-the-file-with-minimum-required-fields}

Suivez les étapes ci-dessous pour importer un fichier dans un dossier d’emplacement avec le minimum de champs requis :

>[!NOTE]
>
>L’exemple suivant présente les quatre champs minimum requis pour importer votre projet :

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Accédez à votre projet AEM Screens (**DemoProjectImport**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Sélectionnez le projet, ** DemoProjectImporter **>** Créer **>** Importer les emplacements ** à partir de la barre latérale.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. Le **Importer** L’assistant s’affiche. Sélectionnez le fichier pour votre projet avec des emplacements ou sélectionnez le fichier (***minimal-file.xls***) téléchargé à partir du *Conditions préalables* section.

   Une fois le fichier sélectionné, cliquez sur **Suivant**.

   ![Screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Vérifiez le contenu du fichier (emplacements) dans l’assistant d’importation, puis cliquez sur **Importer**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Par conséquent, vous pouvez désormais afficher tous les emplacements importés dans votre projet.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)

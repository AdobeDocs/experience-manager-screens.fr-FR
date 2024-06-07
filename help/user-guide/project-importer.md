---
title: Nouvel importateur de projet à partir d’un fichier
description: Cette fonctionnalité permet d’importer en bloc un ensemble d’emplacements dans votre projet AEM Screens depuis une feuille de calcul CSV/XLS.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: ht
source-wordcount: '623'
ht-degree: 100%

---

# Nouvel importateur de projet à partir d’un fichier {#new-project-importer-from-file}

Cette section décrit une fonctionnalité permettant d’importer en bloc un ensemble d’emplacements depuis une feuille de calcul CSV/XLS dans votre projet AEM Screens.

## Présentation {#introduction}

Lorsque vous configurez un projet AEM Screens pour la première fois pour votre entreprise, créez également tous les emplacements. Si votre projet implique un grand nombre d’emplacements, cela entraîne une tâche fastidieuse qui implique beaucoup de sélections et d’attente dans l’interface d’utilisation.

Cette fonctionnalité a pour objectif de réduire le temps nécessaire à la configuration du projet et de résoudre ainsi des problèmes de budgétisation.

En permettant à l’auteur de fournir une feuille de calcul en tant que fichier d’entrée et en laissant le système créer automatiquement l’arborescence de l’emplacement dans le serveur principal, cette fonction :

* *présente de meilleures performances par rapport à la sélection manuelle dans l’interface d’utilisation ;*
* *permet aux clientes et clients d’exporter leurs emplacements depuis leur propre système et de les importer directement dans AEM.*

Ce processus permet d’économiser du temps et de l’argent lors de la configuration initiale du projet ou lors de l’extension d’AEM Screens à de nouveaux emplacements.

## Vue d’ensemble de l’architecture {#architectural-overview}

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
| ***`[./jcr:title] {string*}`*** | Nom du modèle à utiliser (emplacement *screens/core/templates/location*) |
| ***`template {string}`*** | Titre facultatif à utiliser pour la page |
| ***`[./jcr:description] {string}`*** | Description facultative à utiliser pour la page |

La feuille de calcul (fichier CSV/XLS) requiert donc les colonnes suivantes :

* **path {string}** : chemin d’accès de l’emplacement à importer, où la racine du chemin d’accès correspond au dossier d’emplacement du projet (c’est-à-dire *`/foo`* est importé dans *`/content/screens/<project>/locations/foo`*).
* **template {string}** : modèle à utiliser pour le nouvel emplacement, pour l’instant la seule valeur autorisée est « location », mais cette valeur sera étendue ultérieurement à tous les modèles Screens (`display`, `sequencechannel`, etc.).
* **[./*] {string}** : toute propriété facultative à définir sur l’emplacement (c’est-à-dire, `./jcr:title`, `./jcr:description`, `./foo, ./bar`). La version actuelle ne permet aucun filtrage.

>[!NOTE]
>
>Toute colonne qui ne correspond pas aux conditions ci-dessus est simplement ignorée. Par exemple, si une autre colonne est définie dans votre feuille (fichier CSV/XLS) autre que **path**, **template**, **title** et **description** dans votre fichier, ces champs sont ignorés. Par ailleurs, l’**Importateur de projet** ne valide pas ces champs supplémentaires pour l’importation de votre projet dans votre projet AEM Screens.

## Utilisation de l’importateur de projet {#using-project-importer}

La section suivante décrit l’utilisation de l’importateur de projets dans un projet AEM Screens.

>[!CAUTION]
>
>Restrictions :
>
>* Les fichiers possédant une extension autre que CSV/XLS/XLSX ne sont pas pris en charge dans la version actuelle.
>* Il n’existe aucun filtrage des propriétés pour les fichiers importés et tout élément commençant par &quot;./&quot; est importé.
>

### Conditions préalables {#prerequisites}

* Créez un projet intitulé **DemoProjectImport**.

* Utilisez en exemple un fichier CSV ou Excel que vous devez importer.

A des fins de démonstration, vous pouvez télécharger un fichier Excel depuis la section ci-dessous.

[Obtenir le fichier](assets/minimal-file.xls)

### Importation du fichier avec un minimum de champs obligatoires {#importing-the-file-with-minimum-required-fields}

Pour importer un fichier dans un dossier d’emplacement avec un minimum de champs obligatoires, procédez comme suit :

>[!NOTE]
>
>L’exemple suivant présente les quatre champs minimum requis pour importer votre projet :

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Accédez à votre projet AEM Screens (**DemoProjectImport**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Cliquez sur le projet, ** DemoProjectImporter **>** Créer **>** Importer des emplacements** depuis la barre latérale.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. L’assistant **Importation** s’affiche. Cliquez sur le fichier de votre projet contenant des emplacements ou sur le fichier (***minimal-file.xls***) que vous avez téléchargé dans la section *Conditions préalables*.

   Une fois le fichier sélectionné, cliquez sur **Suivant**.

   ![Screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Vérifiez le contenu du fichier (emplacements) dans l’assistant d’importation, puis cliquez sur **Importer**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Par conséquent, vous pouvez maintenant afficher tous les emplacements importés dans votre projet.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)

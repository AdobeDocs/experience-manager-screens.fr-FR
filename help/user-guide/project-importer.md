---
title: Nouvel importateur de projets à partir du fichier
seo-title: Nouvel importateur de projets à partir du fichier
description: Cette fonctionnalité vous permet d’importer en bloc un ensemble d’emplacements d’une feuille de calcul CSV/XLS dans votre projet AEM Screens.
seo-description: Cette fonctionnalité vous permet d’importer en bloc un ensemble d’emplacements d’une feuille de calcul CSV/XLS dans votre projet AEM Screens.
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Nouvel importateur de projets à partir du fichier {#new-project-importer-from-file}

Cette section décrit une fonctionnalité d’importation en bloc d’un ensemble d’emplacements d’une feuille de calcul CSV/XLS vers votre projet AEM Screens.

## Présentation {#introduction}

Lorsque vous configurez un projet AEM Screens, pour la première fois dans votre entreprise, vous devez également créer tous les emplacements. Si votre projet implique un grand nombre d’emplacements, cela entraîne une tâche fastidieuse qui implique beaucoup de clics et d’attente dans l’interface utilisateur.

Cette fonction a pour objectif de réduire le temps nécessaire à la mise en place du projet et de résoudre ainsi les problèmes de budgétisation.

En laissant l’auteur fournir une feuille de calcul sous forme de fichier d’entrée et en laissant le système créer automatiquement l’arborescence de l’emplacement dans le serveur principal, cette fonction :

* *améliore nettement les performances au lieu de cliquer manuellement dans l’interface utilisateur*
* *permet aux clients d’exporter les emplacements qu’ils ont depuis leur propre système et de les importer directement dans AEM*

Cela permet de gagner du temps et de l’argent lors de la configuration initiale du projet ou lors de l’extension des écrans AEM aux nouveaux emplacements.

## Présentation architecturale {#architectural-overview}

Le diagramme suivant présente la présentation architecturale de la fonction d’importateur de projets :

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### Modèle de données {#data-model}

Le modèle de données pour Project Importer est décrit ci-dessous :

>[!NOTE]
>
>La version actuelle ne prend en charge que les emplacements d’importation.

| **Propriété** | **Description** |
|---|---|
| ***chemin {string*}** | Le chemin de ressource de l'emplacement |
| ***[./jcr:title]{string*}** | Nom du modèle à utiliser (emplacement des *écrans/du noyau/des modèles/de l’emplacement*) |
| ***template {string}*** | Titre facultatif à utiliser pour la page |
| ***[./jcr:description]{string}*** | Description facultative à utiliser pour la page |

Le fichier de feuille de calcul (CSV/XLS) requiert donc les colonnes suivantes :

* **chemin {string}** Chemin d’accès de l’emplacement à importer, où la racine du chemin d’accès correspond au dossier d’emplacement du projet (c’est-à-dire */foo* sera importé dans */content/screens/&lt;project&gt;/locations/foo*)

* **template {string}** Le modèle à utiliser pour le nouvel emplacement, pour l’instant la seule valeur autorisée est "location", mais il sera étendu ultérieurement à tous les modèles d’écrans ("display", "séquencechannel, etc.)
* [**./*] {string}** Toute propriété facultative à définir sur l’emplacement (c’est-à-dire, ./jcr:title, ./jcr:description, ./foo, ./bar). La version actuelle n’autorise aucun filtrage pour le moment.

>[!NOTE]
>
>Toute colonne qui ne correspond pas aux conditions ci-dessus sera simplement ignorée. Par exemple, si une autre colonne est définie dans votre fichier de feuille (CSV/XLS) autre que **chemin**,**modèle**,**titre** et **description, ces champs seront ignorés et Project Importer ne valide pas ces champs supplémentaires pour l’importation de votre projet dans votre projet AEM Screens.******

## Utilisation de Project Importer {#using-project-importer}

La section suivante décrit l’utilisation de l’importateur de projets dans un projet AEM Screens.

>[!CAUTION]
>
>Restrictions:
>
>* Les fichiers autres que les extensions CSV/XLS/XLSX ne sont pas pris en charge dans la version actuelle.
>* Il n’existe aucun filtrage des propriétés pour les fichiers importés et tout élément commençant par "./" sera importé.
>



### Conditions préalables {#prerequisites}

* Création d’un projet intitulé **DemoProjectImport**

* Utilisez un exemple de fichier CSV ou Excel que vous devez importer.

A des fins de démonstration, vous pouvez télécharger un fichier Excel à partir de la section ci-dessous.

[Obtenir un fichier](assets/minimal-file.xls)

### Importation du fichier avec un minimum de champs obligatoires {#importing-the-file-with-minimum-required-fields}

Suivez les étapes ci-dessous pour importer un fichier dans un dossier d’emplacements avec un minimum de champs obligatoires :

>[!NOTE]
>
>L’exemple suivant présente les quatre champs minimum requis pour importer votre projet :

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Accédez à votre projet AEM Screens (**DemoProjectImport**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Sélectionnez le projet,** DemoProjectImporter **—&gt;** Créer **—&gt;** Importer des emplacements** depuis la barre latérale.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. L'assistant **Importer** s'ouvre. Sélectionnez le fichier dont vous disposez pour votre projet avec des emplacements ou sélectionnez le fichier (***minimal-file.xls***) que vous avez téléchargé dans la section *Conditions préalables* .

   Une fois le fichier sélectionné, cliquez sur **Suivant**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Vérifiez le contenu du fichier (emplacements) dans l’assistant d’importation, puis cliquez sur **Importer**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Par conséquent, vous pourrez désormais afficher tous les emplacements importés dans votre projet.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)


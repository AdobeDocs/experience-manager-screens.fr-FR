---
title: Configuration de l’auteur et de la publication dans les écrans AEM
seo-title: Configuration de l’auteur et de la publication dans les écrans AEM
description: L’architecture des écrans AEM ressemble à une architecture traditionnelle des sites AEM. Le contenu est créé sur une instance d’auteur AEM, puis répliqué par la suite sur plusieurs instances de publication. Suivez cette page pour savoir comment configurer l’auteur et la publication pour AEM Screens.
seo-description: L’architecture des écrans AEM ressemble à une architecture traditionnelle des sites AEM. Le contenu est créé sur une instance d’auteur AEM, puis répliqué par la suite sur plusieurs instances de publication. Suivez cette page pour savoir comment configurer l’auteur et la publication pour AEM Screens.
uuid: 0a6e87e7-0018-42ef-b484-9a3da61c636a
contentOwner: jsyal
content-type: reference
topic-tags: authoring
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: f2397d11-a18b-4779-b77b-5f99b797f40c
docset: aem65
translation-type: tm+mt
source-git-commit: 221243c537e708aac44145c8d5d5a181ea80a293

---


# Configuration de l’auteur et de la publication dans les écrans AEM {#configuring-author-and-publish-in-aem-screens}

Cette page aborde les sujets suivants :

* **Configuration des instances d’auteur et de publication**
* **Configuration de la topologie de publication**
* **Gestion de la publication : Diffusion des mises à jour de contenu de l’auteur à la publication sur le périphérique**

## Conditions préalables {#prerequisites}

Avant de vous familiariser avec les serveurs d’auteur et de publication, vous devez connaître au préalable :

* **Topologie AEM**
* **Création et gestion du projet AEM Screens**
* **Processus d'enregistrement de périphérique**

>[!NOTE]
>
>Cette fonctionnalité d’AEM Screens n’est disponible que si vous avez installé AEM 6.4 Screens Feature Pack 2. Pour accéder à ce Feature Pack, vous devez contacter l’assistance d’Adobe et demander à y accéder. Une fois que vous disposez des autorisations, vous pouvez le télécharger à partir de Package Share.

## Configuration des instances d’auteur et de publication {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Pour en savoir plus sur l’aperçu de l’architecture de création et de publication et sur la manière dont le contenu est créé sur une instance d’auteur AEM, puis répliqué par la suite sur plusieurs instances de publication, voir Présentation [de l’architecture de](author-publish-architecture-overview.md)création et de publication.

La section suivante explique comment configurer les agents de réplication sur la topologie de création et de publication.

Vous pouvez configurer un exemple simple, où vous hébergez un auteur et deux instances de publication :

* Auteur —&gt; localhost:4502
* Publier 1 (pub1) —&gt; hôte local:4503
* Publier (pub2) —&gt; hôte local:4504

## Configuration des agents de réplication sur l’auteur {#setting-replication-agents}

Pour créer des agents de réplication, vous devez apprendre à créer un agent de réplication standard.

Trois agents de réplication sont nécessaires pour les écrans :

1. **Agent de réplication par défaut ***(spécifié comme ***agent** de réplication standard)
1. **Agent de réplication des écrans**
1. **Agent de réplication inverse**

### Étape 1 : Création d'un agent de réplication par défaut {#step-creating-a-default-replication-agent}

Pour créer un agent de réplication par défaut, procédez comme suit :

1. Accédez à votre instance AEM —&gt; icône marteau —&gt; **Opérations** —&gt; **Configuration**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Sélectionnez la **réplication** dans l'arborescence de navigation de gauche.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Sélectionnez les **agents sur l'auteur** dans le dossier **Replication** et cliquez sur **New** pour créer un agent de réplication standard.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Entrez le **Titre** et le **Nom** pour créer l'agent de réplication, puis cliquez sur **Créer**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Cliquez avec le bouton droit sur l'agent de réplication et cliquez sur **Ouvrir** pour modifier les paramètres.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Cliquez sur **Modifier** pour ouvrir la boîte de dialogue Paramètres **de l’** agent afin d’entrer les détails.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Accédez à l’onglet **Transport** et saisissez l’ **URI**, l’ **utilisateur** et le **mot de passe.**

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >Vous pouvez également copier et renommer un agent de réplication par défaut existant.


#### Création d’agents de réplication standard {#creating-standard-replication-agents}

1. Créer un agent de réplication standard pour pub1 (l’agent par défaut prêt à l’emploi doit déjà être configuré) (par exemple, *https://&lt;nom_hôte&gt;:4503/bin/receive?sling:authRequestLogin=1*)
1. Créez un agent de réplication standard pour pub2. Vous pouvez copier l'agent rep pour pub1 et mettre à jour le transport à utiliser pour pub2 en modifiant le port dans la configuration du transport. (par exemple, *https://&lt;nom_hôte&gt;:4504/bin/receive?sling:authRequestLogin=1*)

#### Création d'agents de réplication d'écrans {#creating-screens-replication-agents}

1. Créez l’agent de réplication AEM Screens pour pub1. En standard, il existe un agent de réplication Screens qui pointe vers le port 4503. Cette fonction doit être activée.
1. Créez l’agent de réplication AEM Screens pour pub2. Copiez l’agent de réplication Screens pour pub1 et modifiez le port pour qu’il pointe sur 4504 pour pub2.

#### Création d'écrans et d'agents de réplication inverse {#creating-screens-reverse-replication-agents}

1. Créez un agent de réplication inverse standard pour pub1.
1. Créez un agent de réplication inverse standard pour pub2. Vous pouvez copier l'agent de représentation inversée pour pub1 et mettre à jour le transport à utiliser pour pub2 en modifiant le port dans la configuration du transport.

## Configuration de la topologie de publication {#setting-up-publish-topology}

### Étape 1 : Configuration De La Détection Apache Sling Basée Sur Le Chêne {#step-configure-apache-sling-oak-based-discovery}

Configuration d’Apache Sling Oak-Based Discovery pour toutes les instances de publication dans la topologie

Pour chaque instance de publication :

1. Accéder à `https://<host>:<port>/system/console/configMgr`
1. Sélectionnez **Apache Sling Oak-Based Discovery Service** Configuration.
1. Mettre à jour les URL des connecteurs de topologie : ajouter des URL de toutes les instances de publication participantes qui sont, `https://localhost:4502/libs/sling/topology/connector`
1. Liste blanche du connecteur de topologie : s’adapter aux adresses IP ou aux sous-réseaux couvrant les instances de publication
1. Activer les boucles locales d’arrêt **automatique**

La configuration doit être identique pour chaque instance de publication et la boucle locale d’arrêt automatique empêche une boucle infinie.

#### Étape 2 : Vérifier la topologie de publication {#step-verify-publish-topology}

Pour toutes les instances de publication, accédez à `https://<host>:<port>/system/console/topology`. Chaque instance de publication doit être représentée dans la topologie.

#### Étape 3 : Configuration d’une grappe Artémis ActiveMQ {#step-setup-activemq-artemis-cluster}

Cette étape vous permet de créer un mot de passe chiffré pour la grappe ActiveMQ Artémis.
L’utilisateur de la grappe et le mot de passe de toutes les instances de publication dans la topologie doivent être identiques. Le mot de passe de la configuration ActiveMQ Artémis doit être chiffré. Chaque instance ayant sa propre clé de chiffrement, il est nécessaire d’utiliser la prise en charge de Crypto pour créer une chaîne de mot de passe chiffrée. Ensuite, le mot de passe chiffré sera utilisé dans la configuration OSGi pour ActiveMQ.

Sur chaque instance de publication :

1. Dans la console OSGi, accédez à **MAIN** —&gt; **Crypto Support** (*https://&lt;hôte&gt;:&lt;port&gt;/system/console/crypto*).
1. Entrez le mot de passe en texte brut (identique pour toutes les instances) dans Texte **brut.**
1. Cliquez sur **Protéger**.
1. Copiez la valeur Texte **** protégé dans le bloc-notes ou l’éditeur de texte. Cette valeur sera utilisée dans la configuration OSGi pour ActiveMQ.

Comme chaque instance de publication possède par défaut des clés de chiffrement uniques, vous devez exécuter cette étape sur chaque instance de pub et enregistrer la clé unique pour la configuration suivante.

*Par exemple*,

Pub1 - `{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`Pub2 - `{8d3d113c834cc4f52c2daee0da3cb0a21122a31f0138bfe4b70c9ead79415f41}`

#### Étape 4 : Activer la grappe d'artéfacts ActiveMQ {#step-activate-activemq-artemis-cluster}

Sur chaque instance de publication :

1. Accédez au gestionnaire de configuration OSGi *https://&lt;hôte&gt;:&lt;port&gt;/system/console/configMgr*
1. Sélectionnez **Apache ActiveMQ Artemis JMS Provider** Configuration
1. Mettez à jour les éléments suivants :

* ***Mot de passe*** de cluster : (utilisez la valeur chiffrée de l’étape précédente par instance respective)
* ***Rubriques***: {name: 'commandes', adresse: 'com.adobe.cq.screens.orders', maxConsumers: 50}

#### Vérification de la grappe d’artéfacts ActiveMQ {#verify-activemq-artemis-cluster}

Suivez les étapes ci-dessous sur chaque instance de publication :

1. Accédez à la console OSGi -&gt; Main &gt; Artémis ActiveMQ `[https://localhost:4505/system/console/mq`.
1. Vérifiez et vérifiez pour afficher les ports des autres instances sous Informations sur le cluster &gt; Topologie &gt; noeuds=2, membres=2.
1. Envoyer un message de test (en haut de l'écran sous Informations sur le courtier)
1. Entrez les modifications suivantes dans les champs :

   1. **Destination**: /com.adobe.cq.screens/devTestTopic
   1. **Texte**: Hello World
   1. Affichez le fichier error.log de chaque instance pour vérifier que le message a été envoyé et reçu dans la grappe.

>[!NOTE]
>
>La navigation vers la console OSGI peut prendre quelques secondes après l’enregistrement de la configuration à l’étape précédente. Vous pouvez également consulter le fichier error.log pour plus de détails.

Par exemple, l’image suivante s’affiche sur la configuration réussie d’ActiveMQ Artemis Server.

Si vous ne voyez pas la configuration suivante de */system/console/mq*, accédez à */system/console/mq* et cliquez sur **Redémarrer** pour redémarrer le courtier.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Suppression des exigences d’en-tête de référent {#remove-referrer-header-requirement}

Suivez les étapes de chaque instance de publication :

1. Accédez à la console **** OSGi &gt; **Configuration Manager**
1. Select **Apache Sling Referrer Filter**
1. Mettre à jour la configuration et **vérifier Autoriser les champs vides**

### Configuring Author and Publish Instance {#configuring-author-and-publish-instance}

Une fois que vous avez configuré la stratégie de publication, vous devez configurer les instances d’auteur et de publication pour afficher les résultats pratiques de l’implémentation :

>[!NOTE]
>
>**Conditions préalables**
>
>Pour commencer avec cet exemple, créez un projet AEM Screens, puis créez un emplacement, un affichage et un canal dans votre projet. Ajoutez du contenu à votre canal et affectez-le à un affichage.

#### Étape 1 : Démarrage d’un lecteur AEM Screens (périphérique) {#step-starting-an-aem-screens-player-device}

1. Lancez une fenêtre du navigateur distincte.
1. Go to Screens player using the *web browser*, that is,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` or launch the AEM Screens app. Lorsque vous ouvrez le périphérique, vous remarquez que son état est non enregistré. 

>[!NOTE]
>
>Vous pouvez ouvrir un lecteur AEM Screens à l’aide de l’application AEM Screens que vous avez téléchargée ou du navigateur Web.

#### Étape 2 : Enregistrement d’un périphérique sur l’auteur {#step-registering-a-device-on-author}

1. Accédez à `https://localhost:4502/screens.html/content/screens/we-retail` ou sélectionnez votre projet et accédez à Périphériques &gt; Gestionnaire de périphériques.
1. Sélectionnez **Enregistrer le périphérique**.
1. Cliquez sur Enregistrement **du** périphérique pour afficher le périphérique.
1. Sélectionnez le périphérique que vous voulez enregistrer et cliquez ensuite sur **Enregistrer le périphérique**.
1. Vérifiez le code d’enregistrement et cliquez sur **Valider**.
1. Saisissez un titre pour votre périphérique et cliquez sur **S’enregistrer**.

#### Step 3: Assigning the Device to Display {#step-assigning-the-device-to-display}

1. Cliquez sur **Attribuer l’affichage** dans la boîte de dialogue de l’étape précédente.
1. Sélectionnez le chemin d’affichage de votre canal dans le dossier **Emplacements** .
1. Cliquez sur **Attribuer**.
1. Click **Finish** to complete the process, and now the device is assigned.

Vérifiez votre lecteur et vous verrez le contenu que vous avez ajouté à votre canal.

#### Étape 4 : Configuration du périphérique de publication pour publier des instances {#step-publishing-device-configuration-to-publish-instances}

**Vérification du périphérique**

Avant d’effectuer les étapes ci-dessous, vérifiez l’ID de périphérique. Pour vérifier, recherchez l’ID de périphérique dans CRXDELite, avec le chemin d’accès comme */accueil/utilisateurs/screens/{project}/devices*.

Pour répliquer l’utilisateur du périphérique, procédez comme suit :

1. Accédez à la page d’administration utilisateur (par ex. : `https://localhost:4502/useradmin`
1. Recherchez le groupe **screens-devices-master** .
1. Cliquez avec le bouton droit sur le groupe, puis cliquez sur **Activer.**

>[!CAUTION]
>
>N’activez pas le service author-publish-screens-service, car il s’agit d’un utilisateur système utilisé par la tâche d’auteur.

Vous pouvez également activer le périphérique à partir de la console de gestion des périphériques. Suivez les étapes ci-dessous :

1. Accédez à votre projet Screens —&gt; **Devices**.
1. Cliquez sur **Gestionnaire de périphériques **dans la barre d'actions.
1. Sélectionnez le périphérique et cliquez sur **Activer** dans la barre d’actions, comme illustré dans la figure ci-dessous.

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>Une fois que vous avez activé le périphérique, vous pouvez également modifier ou mettre à jour l’URL du serveur en cliquant sur **Modifier l’URL du serveur **dans la barre d’actions, comme illustré dans la figure ci-dessous, et vos modifications seront propagées au lecteur AEM Screens.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Liste de vérification de publication {#publishing-check-list}

Les points suivants résument la liste de vérification de publication :

* *Ecrans Utilisateur* de périphérique : stocké en tant qu’utilisateur AEM, il est activé à partir des **outils** &gt; **Sécurité** &gt; **Utilisateurs**. L’utilisateur sera préfixé par le préfixe "screens" avec une longue chaîne sérialisée.

* *Projet* - Projet AEM Screens.
* *Emplacement* - Emplacement auquel le périphérique est connecté.
* *Canal(s)* - un ou plusieurs canaux affichés à l'emplacement
* *Planification* - si vous utilisez une planification, assurez-vous que celle-ci est publiée.
* *Emplacement, calendriers et dossier* Canal - si les ressources correspondantes se trouvent dans un dossier.

Une fois la liste de contrôle vérifiée, vous devez vérifier les changements/comportements suivants dans votre canal :

* Après avoir publié la configuration du périphérique, ouvrez la configuration du lecteur d’écrans et pointez-la vers l’instance de publication. Vous pouvez également activer le périphérique à partir de la console de gestion des périphériques.
* Mettez à jour le contenu d’un canal sur l’auteur, puis publiez-le et vérifiez que le canal mis à jour s’affiche désormais sur le lecteur AEM Screens.
* Connectez le lecteur d’écrans à une autre instance de publication et vérifiez le comportement ci-dessus.

#### Étape 5 : Pointage du périphérique vers l’instance de publication dans le panneau d’administration {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Affichez l’interface utilisateur d’administration à partir du lecteur d’écrans, appuyez longuement sur le coin supérieur gauche pour ouvrir le menu Admin, sur votre lecteur AEM Screens tactile ou à l’aide de la souris.
1. Cliquez sur l’option **Configuration** dans le panneau latéral.
1. Modifiez l’instance d’auteur en instance de publication sur **le serveur**.

Affichez les modifications dans votre lecteur AEM Screens.

Vous pouvez également mettre à jour/modifier l’URL du serveur à partir de la console de gestion des périphériques en procédant comme suit :

1. Accédez à votre projet AEM Screens et sélectionnez le dossier **Devices** .
1. Cliquez sur **Gestionnaire de périphériques** dans la barre d’actions.
1. Sélectionnez le périphérique et cliquez sur **Modifier l’URL du serveur **dans la barre d’actions, comme illustré dans la figure ci-dessous. Vos modifications seront propagées au lecteur AEM Screens.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)



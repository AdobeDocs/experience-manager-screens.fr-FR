---
title: Développement d’un composant personnalisé pour les écrans AEM
seo-title: Développement d’un composant personnalisé pour les écrans AEM
description: Le didacticiel suivant décrit les étapes à suivre pour créer un composant personnalisé pour AEM Screens. AEM Screens réutilise de nombreux modèles de conception et technologies existants d’autres produits AEM. Ce didacticiel met en évidence les différences et les considérations spéciales lors du développement pour AEM Screens.
seo-description: Didacticiel d’introduction pour créer un composant "Hello World" simple pour AEM Screens. AEM Screens réutilise de nombreux modèles de conception et technologies existants d’autres produits AEM. Le didacticiel suivant a pour but de mettre en évidence les différences et les considérations spécifiques lors du développement pour AEM Screens.
uuid: 8ec8be5a-6348-48f2-9cb7-75b2bad555a6
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 24eb937f-ab51-4883-8236-8ebe6243f6e3
targetaudience: target-audience new
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Développement d’un composant personnalisé pour les écrans AEM {#developing-a-custom-component-for-aem-screens}

Le didacticiel suivant décrit les étapes à suivre pour créer un composant personnalisé pour AEM Screens. AEM Screens réutilise de nombreux modèles de conception et technologies existants d’autres produits AEM. Ce didacticiel met en évidence les différences et les considérations spéciales lors du développement pour AEM Screens.

## Présentation {#overview}

Ce didacticiel est destiné aux développeurs qui découvrent AEM Screens. Dans ce didacticiel, un simple composant "Hello World" est créé pour un canal de séquence dans AEM Screens. Une boîte de dialogue permet aux auteurs de mettre à jour le texte affiché.

![overviewwhellow](assets/overviewhellow.png)

## Conditions préalables {#prerequisites}

Pour terminer ce didacticiel, vous devez :

1. [AEM 6.5](https://helpx.adobe.com/experience-manager/6-4/release-notes.html) ou [AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html) + dernier écran Feature Pack

1. [Lecteur AEM Screens](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-screens-introduction.html)
1. Environnement de développement local

Les étapes du didacticiel et les captures d’écran sont effectuées à l’aide de **CRXDE-Lite**. Vous pouvez également utiliser des IDE pour compléter le didacticiel. Vous trouverez plus d’informations sur l’utilisation d’un IDE pour le développement [avec AEM ici.](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#eclipse-ide)


## Project Setup {#project-setup}

Le code source d’un projet Screens est généralement géré sous la forme d’un projet Maven multimodule. Pour accélérer le didacticiel, un projet a été prégénéré à l’aide de l’archétype de projet [AEM 13](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype). Vous trouverez plus de détails sur la [création d’un projet avec l’archétype de projet Maven AEM ici](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#maven-multimodule).

1. Téléchargez et installez les packages suivants à l’aide du gestionnaire [de packages](http://localhost:4502/crx/packmgr/index.jsp)CRX :

   [Obtenir un fichier](assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [Obtenir un fichier](assets/base-screens-weretail-runuicontent-001-snapshot.zip)
   **Si vous travaillez avec Eclipse ou un autre IDE, vous pouvez** télécharger le package source ci-dessous. Déployez le projet sur une instance AEM locale à l’aide de la commande expert :

   **`mvn -PautoInstallPackage clean install`**

   Démarrage du projet HelloWorld SRC Screens We.Retail Run

   [Obtenir un fichier](assets/src-screens-weretail-run.zip)

1. Dans [CRX Package Manager](http://localhost:4502/crx/packmgr/index.jsp) , vérifiez que les deux packages suivants sont installés :

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**
   ![Screens We.Retail Run Ui.Apps et Ui.Content packages installés via CRX Package Manager](assets/crx-packages.png)

   Screens We.Retail Run Ui.Apps et Ui.Content packages installés via CRX Package Manager

1. Le **package screens-weretail-run.ui.apps** installe le code en dessous `/apps/weretail-run`.

   Ce package contient le code responsable du rendu des composants personnalisés du projet. Ce package comprend le code de composant et tout code JavaScript ou CSS nécessaire. Ce paquet incorpore également **screens-weretail-run.core-0.0.1-SNAPSHOT.jar** qui contient tout code Java requis par le projet.

   >[!NOTE]
   >
   >Dans ce didacticiel, aucun code Java n’est écrit. Si une logique métier plus complexe est nécessaire, Java principal peut être créé et déployé à l’aide du lot Java principal.

   ![Représentation du code ui.apps dans CRXDE Lite](assets/uipps-contents.png)

   Représentation du code ui.apps dans CRXDE Lite

   Le composant **helloworld** n’est actuellement qu’un espace réservé. Au cours du didacticiel, une fonctionnalité sera ajoutée pour permettre à un auteur de mettre à jour le message affiché par le composant.

1. Le **package screens-weretail-run.ui.content** installe le code sous :

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`
   Ce paquet contient le contenu de départ et la structure de configuration nécessaire pour le projet. **`/conf/we-retail-run`** contient toutes les configurations pour le projet Exécuter We.Retail. **`/content/dam/we-retail-run`** inclut le démarrage des ressources numériques pour le projet. **`/content/screens/we-retail-run`** contient la structure de contenu Ecrans. Le contenu sous tous ces chemins est principalement mis à jour dans AEM. Pour assurer la cohérence entre les environnements (local, Dev, Stage, Prod), une structure de contenu de base est souvent enregistrée dans le contrôle de code source.

1. **Accédez au projet AEM Screens &gt; We.Retail Run :**

   Dans le menu Démarrer d’AEM &gt; Cliquez sur l’icône Ecrans. Vérifiez que le projet d’exécution We.Retail est visible.

   ![we-retaiul-run-starter](assets/we-retaiul-run-starter.png)

## Création du composant Hello World {#hello-world-cmp}

Le composant Hello World est un composant simple qui permet à un utilisateur de saisir un message à afficher à l’écran. Le composant est basé sur le modèle de composant [AEM Screens : https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template).

Les écrans AEM présentent des contraintes intéressantes qui ne sont pas nécessairement vraies pour les composants des sites WCM traditionnels.

* La plupart des composants Screens doivent s’exécuter en mode plein écran sur les périphériques de signalisation numérique cible.
* La plupart des composants d’écran doivent être incorporables dans les canaux de séquence pour générer des diaporamas.
* La création doit permettre de modifier des composants individuels dans un canal de séquence, de sorte que le rendu en mode plein écran est hors de question.

1. Dans **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (ou IDE de choix), accédez à `/apps/weretail-run/components/content/helloworld.`

   Add the following properties to the `helloworld` component:

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![Propriétés de /apps/weretail-run/components/content/helloworld](assets/2018-04-28_at_4_23pm.png)

   Propriétés de /apps/weretail-run/components/content/helloworld

   Le composant **helloworld** étend le composant **fondation/composants/parbase** afin qu’il puisse être correctement utilisé dans un canal de séquence.

1. Créez un fichier sous le `/apps/weretail-run/components/content/helloworld` nom `helloworld.html.`

   Renseignez le fichier avec ce qui suit :

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/helloworld.html
   
   */-->
   
   <!--/* production: preview authoring mode + unspecified mode (i.e. on publish) */-->
   <sly data-sly-test.production="${wcmmode.preview || wcmmode.disabled}" data-sly-include="production.html" />
   
   <!--/* edit: any other authoring mode, i.e. edit, design, scaffolding, etc. */-->
   <sly data-sly-test="${!production}" data-sly-include="edit.html" />
   ```

   Les composants d’écran nécessitent deux rendus différents selon le mode [de](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/author-environment-tools.html#PageModes) création utilisé :

   1. **Production**: Mode Aperçu ou Publication (wcmmode=disabled)
   1. **Modifier**: utilisé pour tous les autres modes de création, c'est-à-dire éditer, concevoir, échafauder, développeur...
   `helloworld.html`agit comme un commutateur, en vérifiant quel mode de création est actuellement actif et en redirigeant vers un autre script HTML. Une convention commune utilisée par les composants d’écrans consiste à disposer d’un `edit.html` script pour le mode Edition et d’un `production.html` script pour le mode Production.

1. Créez un fichier sous le `/apps/weretail-run/components/content/helloworld` nom `production.html.`

   Renseignez le fichier avec ce qui suit :

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   Ci-dessus se trouve l’annotation de production du composant Hello World. Un `data-duration` attribut est inclus, car le composant est utilisé sur un canal de séquence. L’ `data-duration` attribut est utilisé par le canal de séquence pour savoir pendant combien de temps un élément de séquence doit être affiché.

   Le composant effectue le rendu d’une balise `div` et d’une `h1` balise avec du texte. `${properties.message}` est une partie du script HTML qui génère le contenu d’une propriété JCR nommée `message`. Une boîte de dialogue est créée ultérieurement pour permettre à l’utilisateur de saisir une valeur pour le texte de la `message` propriété.

   Notez également que la notation BEM (Modificateur d’élément de bloc) est utilisée avec le composant. BEM est une convention de codage CSS qui facilite la création de composants réutilisables. BEM est la notation utilisée par les composants [principaux d’](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)AEM. Pour plus d'informations, consultez : [https://getbem.com/](https://getbem.com/)

1. Créez un fichier sous le `/apps/weretail-run/components/content/helloworld` nom `edit.html.`

   Renseignez le fichier avec ce qui suit :

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/edit.html
   
   */-->
   
   <!--/* if message populated */-->
   <div
    data-sly-test.message="${properties.message}"
    class="aem-Screens-editWrapper cmp-hello-world">
    <p class="cmp-hello-world__message">${message}</p>
   </div>
   
   <!--/* empty place holder */-->
   <div data-sly-test="${!message}"
        class="aem-Screens-editWrapper cq-placeholder cmp-hello-world"
        data-emptytext="${'Hello World' @ i18n, locale=request.locale}">
   </div>
   ```

   Ci-dessus se trouve l’annotation de modification du composant Hello World. Le premier bloc affiche une version de modification du composant si le message de boîte de dialogue a été renseigné.

   Le second bloc est rendu si aucun message de boîte de dialogue n’a été saisi. Dans ce cas, le libellé `cq-placeholder` Hello World `data-emptytext` est défini comme espace réservé ***et*** est rendu. La chaîne du libellé peut être internationalisée à l’aide de l’i18n afin de prendre en charge la création dans plusieurs paramètres régionaux.

1. **Boîte de dialogue Copier l’image d’écran à utiliser pour le composant Hello World.**

   Il est plus facile de commencer à partir d’une boîte de dialogue existante, puis d’effectuer des modifications.

   1. Copiez la boîte de dialogue depuis : `/libs/screens/core/components/content/image/cq:dialog`
   1. Collez la boîte de dialogue sous `/apps/weretail-run/components/content/helloworld`
   ![copy-image-dialog](assets/copy-image-dialog.gif)

1. **Mettre à jour la boîte de dialogue Hello World pour inclure un onglet pour le message.**

   Mettez à jour la boîte de dialogue afin qu’elle corresponde à ce qui suit. La structure de noeud JCR de la boîte de dialogue finale est présentée ci-dessous en XML :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Hello World"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/coral/foundation/tabs"
           size="L">
           <items jcr:primaryType="nt:unstructured">
               <message
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Message"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <message
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/textfield"
                                   fieldDescription="Message for component to display"
                                   fieldLabel="Message"
                                   name="./message"/>
                           </items>
                       </column>
                   </items>
               </message>
               <sequence
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Sequence"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <duration
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield"
                                   defaultValue=""
                                   fieldDescription="Amount of time the image will be shown in the sequence, in milliseconds"
                                   fieldLabel="Duration (ms)"
                                   min="0"
                                   name="./duration"/>
                           </items>
                       </column>
                   </items>
               </sequence>
           </items>
       </content>
   </jcr:root>
   ```

   Le champ de texte du message est enregistré dans une propriété nommée `message` et le champ de nombre de la durée dans une propriété nommée `duration`. Ces deux propriétés sont toutes deux référencées dans `/apps/weretail-run/components/content/helloworld/production.html` HTL en tant que `${properties.message}` et `${properties.duration}`.

   ![Hello World - Boîte de dialogue terminée](assets/2018-04-29_at_5_21pm.png)

   Hello World - Boîte de dialogue terminée

## Création de bibliothèques côté client {#clientlibs}

Les bibliothèques côté client offrent un mécanisme d’organisation et de gestion des fichiers CSS et JavaScript nécessaires à une implémentation d’AEM.

Les composants d’AEM Screens sont rendus différemment en mode Edition et en mode Aperçu/Production. Deux bibliothèques clientes seront créées, une pour le mode Edition et une autre pour l’aperçu/production.

1. Créez un dossier pour les bibliothèques côté client pour le composant Hello World.

   Sous- `/apps/weretail-run/components/content/helloworld`créer un nouveau dossier nommé `clientlibs`.

   ![2018-04-30_at_1046am](assets/2018-04-30_at_1046am.png)

1. Sous le `clientlibs` dossier, créez un noeud nommé `shared` de type `cq:ClientLibraryFolder.`

   ![2018-04-30_at_1115am](assets/2018-04-30_at_1115am.png)

1. Ajoutez les propriétés suivantes à la bibliothèque cliente partagée :

   * `allowProxy` | Booléen | `true`

   * `categories`| Chaîne[] | `cq.screens.components`
   ![Propriétés de /apps/weretail-run/components/content/helloworld/clientlibs/shared](assets/2018-05-03_at_1026pm.png)

   Propriétés de /apps/weretail-run/components/content/helloworld/clientlibs/shared

   La propriété categories est une chaîne qui identifie la bibliothèque cliente. cq.screens.components.nuage est utilisé en mode Edition et Aperçu/Production. Par conséquent, tout fichier CSS/JS défini dans la bibliothèque sharedclientlib est chargé dans tous les modes.

   Il est recommandé de ne jamais exposer directement les chemins d’accès à /apps dans un environnement de production. La propriété allowProxy garantit que la bibliothèque cliente CSS et JS sont référencées par le biais d’un préfixe of/etc.clientlibs.

1. Créez un fichier nommé `css.txt` sous le dossier partagé.

   Renseignez le fichier avec ce qui suit :

   ```
   #base=css
   
   styles.less
   ```

1. Créez un dossier nommé `css` sous le `shared` dossier. Ajoutez un fichier nommé `style.less` sous le `css` dossier. La structure des bibliothèques clientes doit maintenant ressembler à ceci :

   ![2018-04-30_at_3_11pm](assets/2018-04-30_at_3_11pm.png)

   Au lieu d’écrire des CSS directement, ce didacticiel utilise LESS. [LESS](https://lesscss.org/) est un précompilateur CSS populaire qui prend en charge les variables, mixins et fonctions CSS. Les bibliothèques clientes AEM prennent en charge la compilation LESS de manière native. Sass ou d’autres précompilateurs peuvent être utilisés mais doivent être compilés en dehors d’AEM.

1. Populate `/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less` with the following:

   ```css
   /**
       Shared Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less
   
   **/
   
   .cmp-hello-world {
       background-color: #fff;
   
    &__message {
     color: #000;
     font-family: Helvetica;
     text-align:center;
    }
   }
   ```

1. Copiez et collez le dossier de bibliothèque `shared` client pour créer une nouvelle bibliothèque cliente nommée `production`.

   ![Copier la bibliothèque cliente partagée pour créer une nouvelle bibliothèque cliente de production](assets/copy-clientlib.gif)

   Copier la bibliothèque cliente partagée pour créer une nouvelle bibliothèque cliente de production

1. Mettez à jour la `categories` propriété de la bibliothèque cliente de production pour qu’elle soit `cq.screens.components.production.`

   Cela permet de s’assurer que les styles sont chargés uniquement en mode Aperçu/Production.

   ![Propriétés de /apps/weretail-run/components/content/helloworld/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Propriétés de /apps/weretail-run/components/content/helloworld/clientlibs/production

1. Populate `/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less` with the following:

   ```css
   /**
       Production Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less
   
   **/
   .cmp-hello-world {
   
       height: 100%;
       width: 100%;
       position: fixed;
   
    &__message {
   
     position: relative;
     font-size: 5rem;
     top:25%;
    }
   }
   ```

   Les styles ci-dessus affichent le message centré au milieu de l’écran, mais uniquement en mode de production.

Troisième catégorie de bibliothèque cliente : peut `cq.screens.components.edit` être utilisé pour ajouter des styles spécifiques à Edition uniquement au composant.

| Catégorie Clientlib | Utilisation |
|---|---|
| `cq.screens.components` | Styles et scripts partagés entre les modes de modification et de production |
| `cq.screens.components.edit` | Styles et scripts utilisés uniquement en mode d’édition |
| `cq.screens.components.production` | Styles et scripts utilisés uniquement en mode de production |

## Création d’une page de conception {#design-page}

Les écrans AEM utilisent des modèles [de page](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/page-templates-static.html) statiques et des configurations [de](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/default-components-designmode.html) conception pour les modifications globales. Les configurations de conception sont fréquemment utilisées pour configurer les composants autorisés pour Parsys sur un canal. Il est recommandé de stocker ces configurations d’une manière spécifique à l’application.

Une page de conception d’exécution We.Retail est créée ci-dessous pour stocker toutes les configurations spécifiques au projet d’exécution We.Retail.

1. Dans **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs` , accédez à `/apps/settings/wcm/designs`
1. Créez un noeud sous le dossier designs, nommé `we-retail-run` avec un type de `cq:Page`.
1. Sous la `we-retail-run` page, ajoutez un autre noeud nommé `jcr:content` de type `nt:unstructured`. Add the following properties to the `jcr:content` node:

   | Nom | Type | Valeur |
   |---|---|---|
   | jcr:title | Chaîne | Exécution We.Retail |
   | sling:resourceType | Chaîne | wcm/core/components/designer |
   | cq:doctype | Chaîne | html_5 |

   ![Page de conception à /apps/settings/wcm/designs/we-détaillant-run](assets/2018-05-07_at_1219pm.png)

   Page de conception à /apps/settings/wcm/designs/we-détaillant-run

## Création d’un canal de séquence {#create-sequence-channel}

Le composant Hello World est destiné à être utilisé sur un canal de séquence. Pour tester le composant, un nouveau canal de séquence est créé.

1. Dans le menu Démarrer d’AEM, accédez à **Écrans** &gt; **We.Retail** Run &gt; et sélectionnez **Canaux**.

1. Click the **Create** button

   1. Choisir **Créer une entité**
   ![2018-04-30_at_5_18pm](assets/2018-04-30_at_5_18pm.png)

1. Dans l’assistant de création :

1. Étape du modèle - choisissez** Canal de la séquence**

   1. Étape des propriétés
   * Onglet de base &gt; Titre = Canal **inactif**
   * Onglet Canal &gt; **Activer le canal en ligne**
   ![idle-channel](assets/idle-channel.gif)

1. Ouvrez les propriétés de la page pour le canal inactif. Mettez à jour le champ Conception pour qu’il pointe vers `/apps/settings/wcm/designs/we-retail-run,`la page de conception créée dans la section précédente.

   ![Configuration de conception /apps/settings/wcm/designs/we-détaillant-run](assets/2018-05-07_at_1240pm.png)

   Configuration de conception pointant vers /apps/settings/wcm/designs/we-détaillant-run

1. Modifiez le canal inactif nouvellement créé pour l’ouvrir.

1. Basculer le mode Page vers le mode **Design**

   1. Cliquez sur l’icône de clé à **molette** dans les paramètres pour configurer les composants autorisés.

   1. Sélectionnez le groupe **Ecrans** et le groupe **Nous.Exécution au détail - Contenu** .
   ![2018-04-30_at_5_43pm](assets/2018-04-30_at_5_43pm.png)

1. Passez en mode **Modifier**. Le composant Hello World peut désormais être ajouté à la page et combiné avec d’autres composants de canal de séquence.

   ![2018-04-30_at_5_53pm](assets/2018-04-30_at_5_53pm.png)

1. Dans **CRXDE-Lite** , accédez à `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par` `/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par`. Notez que la `components` propriété inclut désormais `group:Screens`, `group:We.Retail Run - Content`.

   ![Configuration de la conception sous /apps/settings/wcm/designs/we-détaillant-run](assets/2018-05-07_at_1_14pm.png)

   Configuration de la conception sous /apps/settings/wcm/designs/we-détaillant-run

## Assemblage {#putting-it-all-together}

La vidéo ci-dessous montre le composant terminé et comment il peut être ajouté à un canal de séquence. Le canal est ensuite ajouté à un affichage Emplacement et finalement affecté à un lecteur d’écran.

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9&captions=fre_fr)

## Code terminé {#finished-code}

Vous trouverez ci-dessous le code final du didacticiel. Les **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** et **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** sont les packages AEM compilés. **SRC-screens-weretail-run-0.0.1.zip **est le code source non compilé qui peut être déployé à l’aide de Maven.

[Obtenir un fichier](assets/screens-weretail-runuiapps-001-snapshot.zip)

[Obtenir un fichier](assets/screens-weretail-runuicontent-001-snapshot.zip)

[Obtenir un fichier](assets/screens-weretail-run.zip)

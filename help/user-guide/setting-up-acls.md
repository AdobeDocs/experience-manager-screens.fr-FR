---
title: Configuration des listes de contrôle d’accès
description: Découvrez comment séparer les projets à l’aide des listes de contrôle d’accès (ACL) afin que chaque personne ou équipe gère son propre projet.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 85%

---

# Configuration des listes de contrôle d’accès (ACL) {#setting-up-acls}

La section suivante explique comment séparer les projets à l’aide de listes de contrôle d’accès (ACL) afin que chaque personne ou équipe gère son propre projet.

En tant qu’administrateur ou administratrice d’AEM, vous devez vous assurer que les personnes membres de l’équipe d’un projet n’interfèrent pas avec les autres projets. Chaque utilisateur ou utilisatrice doit avoir des rôles spécifiques en fonction des exigences du projet.

## Configuration des autorisations {#setting-up-permissions}

Les étapes suivantes résument le processus de configuration de listes de contrôle d’accès pour un projet :

1. Connectez-vous à AEM et accédez à **Outils** > **Sécurité**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Cliquez sur **Groupes**, puis saisissez un ID (par exemple, Acme).

   Vous pouvez également utiliser ce lien `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Cliquez ensuite sur **Enregistrer**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Cliquez sur **Contributeurs ou contributrices** dans la liste et double-cliquez dessus.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Ajoutez le projet **Acme** (le projet que vous avez créé) pour **Ajouter des personnes membres au groupe**. Cliquez sur **Enregistrer**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Si vous souhaitez que les membres de l’équipe de projet enregistrent les lecteurs (ce qui implique de créer un utilisateur pour chaque lecteur), recherchez le groupe administrateurs-utilisateurs et ajoutez le groupe ACME aux administrateurs-utilisateurs.

1. Ajoutez tous les utilisateurs et toutes les utilisatrices qui travaillent sur le projet **Acme** au groupe **Acme**.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Configurez les autorisations du groupe **Acme** à l’aide de ce `(http://localhost:4502/useradmin)`.

   Cliquez sur le groupe **Acme** et sur les **autorisations**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Autorisations {#permissions}

Le tableau ci-dessous résume le chemin avec les autorisations au niveau du projet :

| **Chemin** | **Autorisation** | **Description** |
|---|---|---|
| `/apps/<project>` | READ | Permet d’accéder aux fichiers du projet, le cas échéant. |
| `/content/dam/<project>` | ALL | Permet un accès pour stocker les ressources du projet telles que les images ou les vidéos dans la gestion des ressources numériques (DAM). |
| `/content/screens/<project>` | ALL | Supprime l’accès à tous les autres projets sous /content/screens. |
| `/content/screens/svc` | READ | Permet d’accéder au service d’enregistrement. |
| `/libs/screens` | READ | Permet d’accéder à DCC. |
| `/var/contentsync/content/screens/` | ALL | Aide à mettre à jour le contenu hors ligne du projet. |

>[!NOTE]
>
>Vous pouvez parfois séparer les fonctions de création (telles que la gestion des ressources et la création de canaux) des fonctions d’administration (telles que l’enregistrement des lecteurs). Dans un tel scénario, créez deux groupes et ajoutez le groupe de l’auteur aux contributeurs et le groupe d’administrateurs aux contributeurs et aux administrateurs-utilisateurs.

### Création de groupes {#creating-groups}

La création d’un projet doit également créer des groupes d’utilisateurs et d’utilisatrices par défaut avec un ensemble élémentaire d’autorisations affectées. Étendez les autorisations aux rôles classiques définis dans AEM Screens.

Par exemple, vous pouvez créer les groupes spécifiques aux projets suivants :

* Administrateurs de projet Screens
* Opérateurs de projet Screens (enregistrement des lecteurs et gestion des emplacements et des appareils)
* Utilisateurs et utilisatrices de projet Screens (utilisation des canaux, plannings et affectations de canaux)

Le tableau ci-dessous résume les groupes avec la description et les autorisations pour un projet AEM Screens :

<table>
 <tbody>
  <tr>
   <td><strong>Nom du groupe</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Autorisations</strong></td>
  </tr>
  <tr>
   <td>Administrateurs et administratrices de Screens<br /> <em><code>screens-admins</code></em></td>
   <td>Accès au niveau administrateur pour les fonctionnalités AEM Screens</td>
   <td>
    <ul>
     <li>Membre des contributeurs et contributrices</li>
     <li>Membre des utilisateurs-administrateurs et utilisatrices-administratrices</li>
     <li>ALL /content/screens</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Utilisateurs et utilisatrices de Screens<br /> <em><code>screens-users</code></em></td>
   <td>Créer et mettre à jour des canaux et des plannings et les affecter à des emplacements dans AEM Screens</td>
   <td>
    <ul>
     <li>Membre des contributeurs et contributrices</li>
     <li><code>&lt;project&gt; /content/screens</code></li>
     <li><code>&lt;project&gt; /content/dam</code></li>
     <li><code>&lt;project&gt; /content/experience-fragments</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Opérateurs et opératrices de Screens<br /> <em><code>screens-operators</code></em></td>
   <td>Créer et mettre à jour la structure des emplacements et enregistrer des lecteurs dans AEM Screens</td>
   <td>
    <ul>
     <li>Membre des contributeurs et contributrices</li>
     <li><code>jcr:all /home/users/screens</code></li>
     <li><code>jcr:all /home/groups/screens</code></li>
     <li><code>&lt;project&gt; /content/screens</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Lecteurs Screens<br /> <em><code>screens-&lt;project&gt;-devices</code></em></td>
   <td>Tous les lecteurs et tous les lecteurs/appareils sont automatiquement membres des contributeurs et contributrices.</td>
   <td><p> Membre des contributeurs et contributrices</p> </td>
  </tr>
 </tbody>
</table>

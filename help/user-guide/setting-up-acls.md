---
title: Configuration des listes de contrôle d’accès
description: Découvrez comment séparer les projets à l’aide des listes de contrôle d’accès afin que chaque personne ou équipe gère son propre projet.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: 2b865165793b1c0f90f1351518e41096a57ea2ff
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 29%

---

# Configuration des listes de contrôle d’accès {#setting-up-acls}

La section suivante explique comment séparer les projets à l’aide des listes de contrôle d’accès de sorte que chacune des personnes ou équipes gère son propre projet.

En tant qu’administrateur d’AEM, vous souhaitez vous assurer que les membres de l’équipe d’un projet n’interfèrent pas avec les autres projets et que chacun des utilisateurs se voit attribuer des rôles spécifiques en fonction des exigences du projet.

## Configuration des autorisations {#setting-up-permissions}

Les étapes suivantes résument le processus de configuration de listes de contrôle d’accès pour un projet :

1. Connectez-vous à AEM et accédez à **Outils** > **Sécurité**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Cliquez sur **Groupes**, puis saisissez un ID (par exemple, Acme).

   Vous pouvez également utiliser ce lien `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Ensuite, sélectionnez **Enregistrer**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Sélectionner **Contributeurs** dans la liste et double-cliquez dessus.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Ajoutez la variable **Acme** (projet que vous avez créé) **Ajouter des membres au groupe**. Cliquez sur **Enregistrer**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Si vous souhaitez que les membres de l’équipe de projet enregistrent les lecteurs (ce qui implique de créer un utilisateur pour chaque lecteur), recherchez le groupe administrateurs-utilisateurs et ajoutez le groupe ACME aux administrateurs-utilisateurs.

1. Ajoutez tous les utilisateurs qui travaillent sur la **Acme** Projet vers **Acme** groupe.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Configuration des autorisations pour le groupe **Acme** en utilisant ceci `(http://localhost:4502/useradmin)`.

   Sélectionnez le groupe **Acme** et cliquez sur les **autorisations**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Autorisations {#permissions}

Le tableau suivant résume le chemin avec les autorisations au niveau du projet :

| **Chemin** | **Autorisation** | **Description** |
|---|---|---|
| `/apps/<project>` | LECTURE | Permet d’accéder aux fichiers du projet, le cas échéant. |
| `/content/dam/<project>` | ALL | Permet d’accéder au stockage des ressources du projet telles que les images ou la vidéo dans la gestion des ressources numériques. |
| `/content/screens/<project>` | ALL | Supprime l’accès à tous les autres projets sous /content/screens. |
| `/content/screens/svc` | LECTURE | Permet d’accéder au service d’enregistrement. |
| `/libs/screens` | LECTURE | Permet d’accéder à DCC. |
| `/var/contentsync/content/screens/` | ALL | Permet de mettre à jour le contenu hors ligne du projet. |

>[!NOTE]
>
>Parfois, vous pouvez séparer les fonctions de création (telles que la gestion des ressources et la création de canaux) des fonctions d’administration (telles que l’enregistrement des lecteurs). Dans un tel scénario, créez deux groupes et ajoutez le groupe d’auteurs aux contributeurs et le groupe d’administrateurs aux contributeurs et aux administrateurs-utilisateurs.

### Création de groupes {#creating-groups}

La création d’un projet doit également créer des groupes d’utilisateurs par défaut avec un ensemble de base d’autorisations attribuées. Étendez les autorisations aux rôles typiques définis dans AEM Screens.

Vous pouvez par exemple créer les groupes spécifiques aux projets suivants :

* Administrateurs de projet Screens
* Opérateurs de projet Screens (enregistrement des lecteurs et gestion des emplacements et des appareils)
* Utilisateurs de projet Screens (utilisation des canaux, des plannings et des affectations de canal)

Le tableau suivant récapitule les groupes avec une description et des autorisations pour un projet AEM Screens :

<table>
 <tbody>
  <tr>
   <td><strong>Nom du groupe</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Autorisations</strong></td>
  </tr>
  <tr>
   <td>Administrateurs Screens<br /> <em>screens-administrateurs</em></td>
   <td>Accès au niveau administrateur pour les fonctionnalités AEM Screens</td>
   <td>
    <ul>
     <li>Membre des contributeurs</li>
     <li>Membre des utilisateurs-administrateurs</li>
     <li>ALL /content/screens</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Utilisateurs de Screens<br /> <em>screens-users</em></td>
   <td>Créer et mettre à jour des canaux et des plannings et les affecter à des emplacements dans AEM Screens</td>
   <td>
    <ul>
     <li>Membre des contributeurs</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Opérateurs Screens<br /> <em>screens-opérateurs</em></td>
   <td>Création et mise à jour de la structure des emplacements et enregistrement des lecteurs dans AEM Screens</td>
   <td>
    <ul>
     <li>Membre des contributeurs</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Lecteurs Screens<br /> <em>screens-&lt;projet&gt;-devices</em></td>
   <td>Les groupes de tous les lecteurs et de tous les lecteurs/périphériques sont automatiquement membres des contributeurs.</td>
   <td><p> Membre des contributeurs</p> </td>
  </tr>
 </tbody>
</table>

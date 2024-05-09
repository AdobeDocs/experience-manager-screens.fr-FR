---
title: Configuration d’Adobe Analytics avec AEM Screens
description: Découvrez le séquencement et l’envoi d’événements personnalisés à l’aide d’Adobe Analytics hors ligne.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 4ecc1fb1-2437-449a-a085-66b2a85f4053
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 80%

---

# Configuration d’Adobe Analytics avec AEM Screens {#configuring-adobe-analytics-with-aem-screens}

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available if you have installed AEM 6.4.2 Feature Pack 2 and AEM 6.3.3 Feature Pack 4.
>
>To get access to either of these Feature Packs, contact Adobe Support and request access. When you have permissions, download it from Package Share. -->

Cette section couvre les sujets suivants :

* **Séquencement dans Adobe Analytics avec AEM Screens**
* **Envoi d’événements personnalisés à l’aide d’Adobe Analytics hors ligne**

## Séquencement dans Adobe Analytics avec AEM Screens {#sequencing-in-adobe-analytics-with-aem-screens}

La variable ***processus de séquencement*** commence par un service de stockage de données qui active le service Adobe Analytics. Le contenu du canal envoie les événements Adobe Analytics avec la paie, c’est-à-dire que la capture des tests de données vers les E/S Windows et les événements de séjour sont déclenchés. Les événements sont enregistrés dans la base de données de l’index et sont ensuite placés dans la banque d’objets. Selon le planning défini par l’administrateur, il coupe les données de la banque d’objets et les transfère ensuite dans la banque de blocs. Il tente d’envoyer le maximum de données lorsqu’il est connecté.

### Diagramme de séquencement {#sequencing-diagram}

Le diagramme de séquencement suivant explique l’intégration d’Adobe Analytics avec AEM Screens :

![analytics_chunking](assets/analytics_chunking.png)

## Envoi d’événements personnalisés à l’aide d’Adobe Analytics hors ligne {#sending-custom-events-using-offline-adobe-analytics}

Le tableau suivant résume le modèle de données standard pour les événements. Il répertorie tous les champs envoyés à Adobe Analytics :

<table>
 <tbody>
  <tr>
   <td><strong>Section</strong></td> 
   <td><strong>Libellé de propriété</strong></td> 
   <td><strong>Nom/clé de propriété</strong></td> 
   <td><strong>Requis</strong></td> 
   <td><strong>Type de données</strong></td> 
   <td><strong>Type de propriété</strong><br /> </td> 
   <td><strong>Description</strong></td> 
  </tr>
  <tr>
   <td><strong><em>Noyau/événement</em></strong></td> 
   <td>GUID d’événement</td> 
   <td>event.guid</td> 
   <td>recommandé</td> 
   <td>chaîne</td> 
   <td>UUID</td> 
   <td>Identifiant unique qui identifie une instance d’un événement</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Date et heure de la collecte de l’événement</td> 
   <td>event.coll_dts</td> 
   <td>facultatif</td> 
   <td>chaîne</td> 
   <td>Horodatage - UTC</td> 
   <td>Date et heure de collecte</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Date et heure de l’événement (début)</td> 
   <td>event.dts_start</td> 
   <td>recommandé</td> 
   <td>chaîne</td> 
   <td>Horodatage - UTC</td> 
   <td>Date et heure de début de l’événement. Si vous n’avez pas spécifié cette heure, l’heure de début de l’événement est considérée comme l’heure par le serveur lorsqu’elle a été reçue.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Date et heure de l’événement (fin)</td> 
   <td>event.dts_end</td> 
   <td>facultatif</td> 
   <td>chaîne</td> 
   <td>Horodatage - UTC</td> 
   <td>Date et heure de fin de l’événement</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Workflow</td> 
   <td>event.workflow</td> 
   <td>recommandé</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Nom du workflow (Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Principale catégorie DMe</td> 
   <td>event.category</td> 
   <td>requis</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Catégorie principale (BUREAU, MOBILE, WEB, PROCESSUS, SDK, SERVICE, RÉSEAU) - Regroupement des types d’événements - <strong>Lecteur envoyé</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Sous-catégorie</td> 
   <td>event.subcategory</td> 
   <td>recommandé</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Sous-catégorie - Section d’un processus, d’une zone d’un écran, etc. (Fichiers récents, fichiers CC, créations mobiles, etc.)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Type d’événement/d’action</td> 
   <td>event.type</td> 
   <td>requis</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Type d’événement (rendu, clic, pincement, zoom) - Action de l’utilisateur principal</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Sous-type</td> 
   <td>event.subtype</td> 
   <td>recommandé</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Sous-type d’événement (création, mise à jour, suppression, publication, etc.) : plus de détails sur l’action de l’utilisateur ou l’utilisatrice</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Hors ligne</td> 
   <td>event.offline</td> 
   <td>facultatif</td> 
   <td>booléen</td> 
   <td> </td> 
   <td>L’événement a été généré alors que l’action était hors ligne/en ligne (true/false).</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Agent utilisateur</td> 
   <td>event.user_agent</td> 
   <td>recommandé (propriétés web)</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Agent utilisateur</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Langue/Paramètres régionaux</td> 
   <td>event.language</td> 
   <td>recommandé</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Les paramètres régionaux de l’utilisateur sont une chaîne basée sur les conventions d’identification linguistiques RFC 3066 (par exemple, en-US, fr-FR ou es-ES).</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>GUID de l’appareil</td> 
   <td>event.device_guid</td> 
   <td>facultatif</td> 
   <td>chaîne<br /> </td> 
   <td>UUID</td> 
   <td>Identifie le GUID de l’appareil (par exemple, ID d’ordinateur ou hachage de l’adresse IP + masque de sous-réseau + ID réseau + agent utilisateur) - Ici, le nom d’utilisateur du lecteur généré au moment de l’enregistrement est envoyé.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Décompte</td> 
   <td>event.count</td> 
   <td>facultatif</td> 
   <td>nombre</td> 
   <td> </td> 
   <td>Nombre de fois où l’événement s’est produit - La durée de la vidéo est envoyée.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Valeur</td> 
   <td>event.value</td> 
   <td>facultatif</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Valeur de l’événement (par exemple, paramètres activés/désactivés)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Nom de page</td> 
   <td>event.pagename</td> 
   <td>Requis pour AA</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Prise en charge d’Adobe Analytics pour le nom de page personnalisé</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>facultatif</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>URL de la propriété web ou du schéma mobile - doit inclure une URL complète</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Code d’erreur</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Code d’échec</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Type d’erreur</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Type d’échec</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Description de l’erreur</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Description de l’échec<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>Produit source/d’origine</em></strong></td> 
   <td>Nom</td> 
   <td>source.name</td> 
   <td>requis</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Nom de l’application (AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Version</td> 
   <td>source.version</td> 
   <td>requis</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Version du micrologiciel</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Plateforme</td> 
   <td>source.platform</td> 
   <td>requis</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Appareil</td> 
   <td>source.device</td> 
   <td>requis avec exceptions</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Nom du lecteur</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Version du SE</td> 
   <td>source.os_version</td> 
   <td>requis avec exceptions</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Version du S/E</td> 
  </tr>
  <tr>
   <td><strong><em>Contenu</em></strong></td> 
   <td>Action</td> 
   <td>content.action</td> 
   <td>requis</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>URL de la ressource, dont le rendu lu</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Type Mime</td> 
   <td>content.mimetype</td> 
   <td>facultatif</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Type MIME du contenu</td> 
  </tr>
  <tr>
   <td><strong><em>Transaction</em></strong></td> 
   <td>Numéro de transaction</td> 
   <td>trn.number</td> 
   <td>requis</td> 
   <td>chaîne</td> 
   <td>UUID</td> 
   <td>Identifiant unique de préférence conforme à la norme UUID v4</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Description du produit</td> 
   <td>trn.product</td> 
   <td>requis</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>L’URL du fichier (à l’exclusion du rendu)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Quantité</td> 
   <td>trn.quantity</td> 
   <td>requis</td> 
   <td>chaîne</td> 
   <td> </td> 
   <td>Durée de lecture</td> 
  </tr>
 </tbody>
</table>

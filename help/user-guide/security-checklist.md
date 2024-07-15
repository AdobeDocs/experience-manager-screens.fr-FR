---
title: Liste de contrôle de sécurité
description: Découvrez les principaux aspects d’AEM Screens en matière de sécurité avec une liste de questions et d’éléments à prendre en compte.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 100%

---

# Liste de contrôle de sécurité d’AEM Screens {#security-checklist}

La page Liste de contrôle de sécurité d’AEM Screens décrit les principaux aspects en matière de sécurité avec une liste de questions et d’éléments à prendre en compte.

## Tableau de liste de contrôle {#checklist-table}

| **Aspect de sécurité** | **Liste de contrôle** | **Oui/Non/ND** |
|---|---|---|
| **Mises à jour des logiciels AEM et Screens** | **a.** *Le dernier Service Pack d’Adobe Experience Manager (AEM) a-t-il été appliqué ?* <br>**b.** *Le dernier pack de fonctionnalités AEM Screens a-t-il été appliqué ?* <br>**c.** *Utilisez-vous la dernière version d’AEM Screens disponible dans [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/) ?* |
| **Sécurité physique** | **a.** *Avez-vous désactivé tous les ports inutiles ?* <br>**b.** *Avez-vous sécurisé les câbles et le matériel ?* <br>**c.** *Utilisez-vous des conteneurs, le cas échéant ?* |
| **Sécurité réseau** | **a.** *Utilisez-vous un sous-réseau isolé pour vos appareils de signalétique ?* <br>**b.** *Le sous-réseau isolé permet-il d’accéder aux points d’entrée requis, notamment AEM, Adobe Analytics ou les autres services requis ?* <br>**c.** *Avez-vous sécurisé votre Wi-Fi en utilisant les bonnes pratiques de l’entreprise ?* <br>**d.** *Si vous utilisez la lecture synchronisée, avez-vous autorisé TCP 24503 pour WebSocket uniquement pour le ou les appareils principaux ?* <br>**e.** *Avez-vous débloqué les plages d’adresses IP des appareils de lecture afin que seuls les appareils autorisés puissent accéder au service d’enregistrement sur l’instance de création ?* |
| **Sécurité du système d’exploitation** | **a.** *Avez-vous effectué la mise à niveau vers la dernière version du système d’exploitation et appliqué tous les correctifs de sécurité nécessaires ?* <br>**b.** *Avez-vous désactivé tous les services inutiles et supprimé les applications inutiles ?* <br>**c.** *Avez-vous inscrit l’appareil dans la gestion des appareils afin d’appliquer les stratégies d’entreprise ?* <br>**d.** *Avez-vous verrouillé l’appareil à une borne à application (lecteur) unique ?* <br>**e.** *Disposez-vous de procédures d’exploitation standard (SOP) pour installer les mises à jour de sécurité du système d’exploitation au fil du temps ?*<br>**f.***Avez-vous suivi les bonnes pratiques en matière de sécurité pour le système d’exploitation utilisé, telles que l’utilisation de logiciels anti-malware et d’utilisateurs et d’utilisatrices non administrateurs et administratrices ?* |
| **Sécurité des applications** | **a.** *Avez-vous désactivé l’interface d’administration, le sélecteur de canal et l’interface d’utilisation des activités pour la production ?* <br>**b.** *Avez-vous minimisé le niveau de journal pour la production ?* <br>**c.** *Utilisez-vous https pour vous connecter à AEM ?* <br>**d.** *Utilisez-vous un certificat signé par une autorité de certification ou un indicateur de performance clé d’entreprise ? (au lieu de certificats auto-signés)*<br>**e.** *Utilisez-vous TLS et non SSL v3 ?*<br>**f.** *Validez-vous le jeton d’enregistrement sur l’appareil et sur AEM lors de l’enregistrement ?*<br> **g.** *Avez-vous classé les données utilisées et vérifié qu’il n’existe pas d’informations d’identification personnelle ni d’informations médicales protégées sur l’appareil ?*<br> **h.** *Avez-vous classé les données utilisées et vérifié qu’il n’existe pas d’informations d’identification personnelle ni d’informations médicales protégées sur l’appareil ?*<br> **i.** *Avez-vous configuré la surveillance des e-mails ? Disposez-vous d’une SOP pour gérer la surveillance des e-mails et pour gérer les appareils dont le ping reste sans réponse ?* |
| **Contrôle d’accès** | **a.** *Disposez-vous d’un contrôle d’accès basé sur des rôles (RBAC) identifié et géré en interne ?* <br>**b.** *Avez-vous suivi le principe du moindre privilège et les bonnes pratiques d’Adobe en accordant les accès aux auteurs, aux autrices, aux administrateurs, aux administratrices, et aux lecteurs ?* |

### Téléchargement de la liste de contrôle de sécurité {#download-checklist}

Pour télécharger la liste de contrôle de sécurité d’AEM Screens, cliquez [ici](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).

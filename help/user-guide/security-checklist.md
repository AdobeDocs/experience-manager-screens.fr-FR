---
title: Liste de contrôle de sécurité
description: Découvrez les principaux aspects de sécurité d’AEM Screens avec une liste de questions et de considérations à prendre en compte.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 36%

---

# Liste de contrôle de sécurité d’AEM Screens {#security-checklist}

La page Liste de contrôle de sécurité d’AEM Screens décrit les principaux domaines de sécurité avec une liste de questions et de considérations à prendre en compte.

## Tableau de liste de contrôle {#checklist-table}

| **Aspect de sécurité** | **Liste de contrôle** | **Oui/Non/ND** |
|---|---|---|
| **Mises à jour des logiciels AEM et Screens** | **a.** *Le dernier Service Pack d’Adobe Experience Manager (AEM) a-t-il été appliqué ?* <br>**b.** *Le dernier Feature Pack AEM Screens a-t-il été appliqué ?* <br>**c.** *Utilisez-vous la dernière version d’AEM Screens disponible dans [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/) ?* |
| **Sécurité physique** | **a.** *Avez-vous désactivé tous les ports inutiles ?* <br>**b.** *Avez-vous sécurisé le câblage et le matériel ?* <br>**c.** *Utilisez-vous des conteneurs, le cas échéant ?* |
| **Sécurité réseau** | **a.** *Utilisez-vous un sous-réseau isolé pour vos appareils de signalétique ?* <br>**b.** *Le sous-réseau isolé permet-il d’accéder aux points de terminaison requis, y compris AEM, Adobe Analytics ou d’autres services requis ?* <br>**c.** *Avez-vous sécurisé votre Wi-Fi en utilisant les bonnes pratiques de l’entreprise ?* <br>**d.** *Si vous utilisez la lecture synchronisée, avez-vous autorisé TCP 24503 pour WebSocket uniquement sur les appareils principaux ?* <br>**e.** *Avez-vous débloqué la plage d’adresses IP des appareils du lecteur afin que seuls les appareils autorisés puissent accéder au service d’enregistrement sur l’instance de création ?* |
| **Sécurité du système d’exploitation** | **a.** *Avez-vous effectué la mise à niveau vers la dernière version du système d’exploitation et appliqué tous les correctifs de sécurité nécessaires ?* <br>**b.** *Avez-vous désactivé tous les services inutiles et supprimé les applications inutiles ?* <br>**c.** *Avez-vous inscrit l’appareil dans la gestion des appareils afin d’appliquer les stratégies d’entreprise ?* <br>**d.** *Avez-vous verrouillé l’appareil sur une borne d’application unique (lecteur) ?* <br>**e.** *Disposez-vous de procédures d’exploitation standard (SOP) pour installer les mises à jour de sécurité du système d’exploitation au fil du temps ?*<br>**f.***Avez-vous suivi les bonnes pratiques de sécurité pour le système d’exploitation utilisé, telles que les logiciels anti-malware et les utilisateurs non administrateurs ?* |
| **Sécurité des applications** | **a.** *Avez-vous désactivé l’interface utilisateur d’administration, le sélecteur de canal et l’interface utilisateur d’activité pour la production ?* <br>**b.** *Avez-vous minimisé le niveau de journal pour la production ?* <br>**c.** *Utilisez-vous https pour vous connecter à AEM ?* <br>**d.** *Utilisez-vous un certificat signé par une autorité de certification ou un ICP d’entreprise ? (et non les certificats auto-signés)*<br>**e.***Utilisez-vous TLS et non SSL v3 ?*<br>**f.** *Validez-vous le jeton d’enregistrement sur le périphérique et AEM lors de l’enregistrement ?*<br> **g.** *Avez-vous classifié les données utilisées et vérifié qu’il n’existe aucune information d’identification personnelle ou d’identification personnelle sur l’appareil ?*<br> **h.** *Avez-vous classifié les données utilisées et vérifié qu’il n’existe aucune information d’identification personnelle (PII) ou d’information sanitaire protégée (PHI) sur l’appareil ?*<br> **i.** *Avez-vous configuré la surveillance des emails ? Disposez-vous d’une SOP pour répondre à la surveillance des emails et pour gérer les périphériques qui ne font pas l’objet d’un ping ?* |
| **Contrôle d’accès** | **a.** *Disposez-vous d’un contrôle d’accès en fonction du rôle (RBAC) identifié et géré en interne ?* <br>**b.** *Avez-vous suivi le principe du moindre privilège en fournissant l’accès aux auteurs, administrateurs et lecteurs à l’aide des bonnes pratiques d’Adobe ?* |

### Téléchargement de la liste de contrôle de sécurité {#download-checklist}

Pour télécharger la liste de contrôle de sécurité AEM Screens, cliquez sur [here](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).

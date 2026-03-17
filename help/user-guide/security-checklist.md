---
title: Liste de contrôle de sécurité
description: Découvrez les principaux aspects d’AEM Screens en matière de sécurité avec une liste de questions et d’éléments à prendre en compte.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: ad8509deaff9f90df5f6b50947f587a74e420661
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 18%

---

# Liste de contrôle de sécurité d’AEM Screens {#security-checklist}

La page Liste de contrôle de sécurité d’AEM Screens décrit les principaux aspects en matière de sécurité avec une liste de questions et d’éléments à prendre en compte.

## Tableau de liste de contrôle {#checklist-table}

| **Aspect de sécurité** | **Liste de contrôle** | **Oui/Non/ND** |
|---|---|---|
| **Mises à jour des logiciels AEM et Screens** | **a.** *Le dernier pack de services Adobe Experience Manager (AEM) a-t-il été appliqué ?* <br>**b.** *Le dernier Feature Pack AEM Screens a-t-il été appliqué ?* <br>**c.** *Utilisez-vous le dernier logiciel AEM Screens Player disponible dans les [téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/) ?* | |
| **Sécurité physique** | **a.** *Avez-vous désactivé tous les ports inutiles ?* <br>**b.** *Avez-vous sécurisé le câblage et le matériel ?* <br>**c.** *Utilisez-vous des conteneurs, le cas échéant ?* | |
| **Sécurité réseau** | **a.** *Utilisez-vous un sous-réseau isolé pour vos appareils de signalétique ?* <br>**b.** *Le sous-réseau isolé permet-il d’accéder aux points d’entrée requis, y compris AEM, Adobe Analytics ou d’autres services requis ?* <br>**c.** *Avez-vous sécurisé votre réseau Wi-Fi en utilisant les bonnes pratiques d&#39;entreprise ?* <br>**d.** *Si vous utilisez la lecture synchronisée, avez-vous autorisé les 24503 TCP pour WebSocket uniquement sur les appareils principaux ?* <br>**par** *Avez-vous débloqué la plage d’adresses IP des appareils du lecteur afin que seuls les appareils autorisés puissent accéder au service d’enregistrement sur l’instance de création ?* | |
| **Sécurité du système d’exploitation** | **a.** *Avez-vous effectué la mise à niveau vers la dernière version du système d&#39;exploitation et appliqué tous les correctifs de sécurité nécessaires ?* <br>**b.** *Avez-vous désactivé tous les services inutiles et supprimé les applications inutiles ?* <br>**c.** *Avez-vous inscrit l’appareil dans la gestion des appareils pour appliquer les politiques d’entreprise ?* <br>**d.** *Avez-vous verrouillé l’appareil sur un kiosque à application unique (lecteur) ?* <br>**par** *Avez-vous mis en place des procédures d&#39;exploitation standard (SOP) pour installer les mises à jour de sécurité du système d&#39;exploitation au fil du temps ?*<br>**f.***Avez-vous suivi les bonnes pratiques de sécurité pour le système d&#39;exploitation utilisé, telles que les logiciels anti-malware, les utilisateurs non-administrateurs ?* | |
| **Sécurité des applications** | **a.** *Avez-vous désactivé l’interface utilisateur d’administration, le sélecteur de canaux et l’interface utilisateur d’activité pour la production ?* <br>**b.** *Avez-vous réduit le niveau de journalisation pour la production ?* <br>**c.** *Utilisez-vous https pour vous connecter à AEM ?* <br>**d.** *Utilisez-vous un certificat signé par une autorité de certification ou une ICP d’entreprise ? (non des certificats auto-signés)*<br>**par &#x200B;***Utilisez-vous TLS et non SSL v3 ?*<br>**f.** *Validez-vous le jeton d’enregistrement sur l’appareil et AEM lors de l’enregistrement ?*<br> **par ex.** *Avez-vous classé les données en cours d’utilisation et qu’il n’existe aucune PII ou IPS sur l’appareil ?*<br> **h.** *Avez-vous classé les données en cours d&#39;utilisation et qu&#39;il n&#39;existe aucune information d&#39;identification personnelle (PII) ou information de santé protégée (ISP) sur l&#39;appareil ?*<br> **i.** *Avez-vous configuré la surveillance des e-mails ? Disposez-vous d’une SOP pour gérer la surveillance des e-mails et pour gérer les appareils dont le ping reste sans réponse ?* | |
| **Contrôle d’accès** | **a.** *Avez-vous un contrôle d’accès basé sur les rôles (RBAC) identifié et géré en interne ?* <br>**b.** *Avez-vous suivi le principe de moindre privilège pour fournir l’accès aux auteurs, administrateurs et lecteurs en utilisant les bonnes pratiques d’Adobe ?* | |

### Télécharger la liste de contrôle de sécurité {#download-checklist}

Pour télécharger la liste de contrôle de sécurité d’AEM Screens, cliquez [ici](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).

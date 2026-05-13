---
title: Liste de contrôle de sécurité
description: Découvrez les principaux aspects d’AEM Screens en matière de sécurité avec une liste de questions et d’éléments à prendre en compte.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
TQID: https://experienceleague.adobe.com/ES-ciW55PF5Zzh9zqRYGu-kWbOym8XkLInXmmqga524
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 490
ht-degree: 18%

---

# Liste de contrôle de sécurité d’AEM Screens {#security-checklist}

La page Liste de contrôle de sécurité d’AEM Screens décrit les principaux aspects en matière de sécurité avec une liste de questions et d’éléments à prendre en compte.

## Tableau de liste de contrôle {#checklist-table}

| **Aspect de sécurité** | **Liste de contrôle** | **Oui/Non/ND** |
|---|---|---|
| **Mises à jour des logiciels AEM et Screens** | **a.** *Le dernier pack de services Adobe Experience Manager (AEM) a-t-il été appliqué ?* <br>**b.** *Le dernier Feature Pack AEM Screens a-t-il été appliqué ?* <br>**c.** *Utilisez-vous le dernier logiciel AEM Screens Player disponible dans [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/) ?* | |
| **Sécurité physique** | **a.** *Avez-vous désactivé tous les ports inutiles ?* <br>**b.** *Avez-vous sécurisé le câblage et le matériel ?* <br>**c.** *Utilisez-vous des conteneurs, le cas échéant ?* | |
| **Sécurité réseau** | **a.** *Utilisez-vous un sous-réseau isolé pour vos appareils de signalétique ?* <br>**b.** *Le sous-réseau isolé permet-il d’accéder aux points d’entrée requis, y compris AEM, Adobe Analytics ou d’autres services requis ?* <br>**c.** *Avez-vous sécurisé votre connexion Wi-Fi en utilisant les bonnes pratiques d&#39;entreprise ?* <br>**j.** *Si vous utilisez la lecture synchronisée, avez-vous autorisé les 24503 TCP pour WebSocket uniquement sur les appareils principaux ?* <br>**par ex.** *Avez-vous débloqué la plage d’adresses IP des appareils du lecteur afin que seuls les appareils autorisés puissent accéder au service d’enregistrement sur l’instance de création ?* | |
| **Sécurité du système d’exploitation** | **a.** *Avez-vous effectué une mise à niveau vers la dernière version du système d&#39;exploitation et appliqué tous les correctifs de sécurité nécessaires ?* <br>**b.** *Avez-vous désactivé tous les services inutiles et supprimé les applications inutiles ?* <br>**c.** *Avez-vous inscrit l’appareil dans la gestion des appareils pour appliquer les politiques d’entreprise ?* <br>**j.** *Avez-vous verrouillé l’appareil sur un kiosque à application unique (lecteur) ?* <br>**par ex.** *Avez-vous mis en place des procédures d’exploitation standard (SOP) pour installer les mises à jour de sécurité du système d’exploitation au fil du temps ?*<br>**f.***Avez-vous suivi les bonnes pratiques de sécurité pour le système d’exploitation utilisé, telles que les logiciels anti-programmes malveillants, les utilisateurs non administrateurs ?* | |
| **Sécurité des applications** | **a.** *Avez-vous désactivé l’interface utilisateur d’administration, le sélecteur de canaux et l’interface utilisateur d’activité pour la production ?* <br>**b.** *Avez-vous réduit le niveau de journalisation pour la production ?* <br>**c.** *Utilisez-vous https pour vous connecter à AEM ?* <br>**j.** *Utilisez-vous un certificat signé par une autorité de certification ou une ICP d’entreprise ? (non des certificats auto-signés)*<br>**par ex ***Utilisez-vous TLS et non SSL v3 ?*<br>**f.** *Validez-vous le jeton d’enregistrement sur l’appareil et AEM lors de l’enregistrement ?*<br> **par ex.** *Avez-vous classé les données en cours d’utilisation et qu’il n’existe aucune PII ou IPS sur l’appareil ?*<br> **h.** *Avez-vous classé les données en cours d’utilisation et qu’il n’existe aucune information d’identification personnelle (PII) ou information de santé protégée (ISP) sur l’appareil ?*<br> **i.** *Avez-vous configuré la surveillance des e-mails ? Disposez-vous d’une SOP pour gérer la surveillance des e-mails et pour gérer les appareils dont le ping reste sans réponse ?* | |
| **Contrôle d’accès** | **a.** *Disposez-vous d’un contrôle d’accès basé sur les rôles (RBAC) identifié et géré en interne ?* <br>**b.** *Avez-vous appliqué le principe de moindre privilège pour permettre aux auteurs, administrateurs et lecteurs d’accéder aux ressources à l’aide des bonnes pratiques d’Adobe ?* | |

### Télécharger la liste de contrôle de sécurité {#download-checklist}

Pour télécharger la liste de contrôle de sécurité d’AEM Screens, cliquez [ici](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).

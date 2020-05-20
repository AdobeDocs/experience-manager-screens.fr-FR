---
title: Liste de contrôle de sécurité
seo-title: Liste de contrôle de sécurité
description: La page décrit la liste de contrôle de sécurité
seo-description: La page décrit la liste de contrôle de sécurité
translation-type: tm+mt
source-git-commit: aade9071cebddf147dfad51d7319fb6f0e1c22bf
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 2%

---


# Liste de contrôle de sécurité des écrans AEM  {#security-checklist}

La page Liste de contrôle de sécurité d’AEM Screens décrit les principales zones de sécurité avec une liste de questions et de considérations à prendre en compte.

## Tableau Liste de contrôle {#checklist-table}

| **Zone de sécurité** | **Liste de contrôle** | **Oui/Non/NA** |
|---|---|---|
| **Mises à jour du logiciel AEM et Screens** | ***a.*** *Le dernier Service Pack d’Adobe Experience Manager (AEM) a-t-il été appliqué ?* <br>***b.****Le dernier pack de fonctionnalités d’AEM Screens a-t-il été appliqué ?*<br>***c.*** Utilisez-vous le dernier logiciel AEM Screens Player disponible dans les téléchargements *d’[](https://download.macromedia.com/screens/)AEM Screens Player ?* |
| **Sécurité physique** | ***a.*** *Avez-vous désactivé tous les ports inutiles ?* <br>***b.****Avez-vous sécurisé le câblage et le matériel ?*<br>***c.*** *Utilisez-vous des conteneurs, le cas échéant ?* |
| **Sécurité réseau** | ***a.*** *Utilisez-vous un sous-réseau isolé pour vos périphériques de signalisation ?* <br>***b.****Le sous-réseau isolé permet-il d’accéder aux points de terminaison requis, notamment AEM, Adobe Analytics ou d’autres services requis ?*<br>***c.*** Avez-vous *sécurisé votre Wi-Fi en utilisant les meilleures pratiques de l&#39;entreprise ?* <br>***d.****Si vous utilisez la lecture synchronisée, avez-vous autorisé TCP 24503 pour WebSocket uniquement sur le ou les périphériques principaux ?*<br>***e.*** *Avez-vous placé en liste blanche les plages d’adresses IP des périphériques du lecteur afin que seuls les périphériques autorisés puissent accéder au service d’enregistrement sur l’ordinateur de l’auteur ?* |
| **Sécurité du système d’exploitation** | ***a.*** *Avez-vous effectué la mise à niveau vers la dernière version du système d&#39;exploitation et appliqué tous les correctifs de sécurité nécessaires ?* <br>***b.****Avez-vous désactivé tous les services inutiles et supprimé les applications inutiles ?*<br>***c.*** Avez-vous *inscrit le périphérique à la gestion des périphériques pour appliquer les stratégies d’entreprise ?* <br>***d.****Avez-vous verrouillé le périphérique sur le kiosque d&#39;application unique (lecteur) ?*<br>***e.*** *Disposez-vous de procédures d&#39;exploitation standard (SOP) pour installer les mises à jour de sécurité du système d&#39;exploitation au fil du temps ?*<br>***f.****Avez-vous suivi les meilleures pratiques de sécurité pour le système d&#39;exploitation en cours d&#39;utilisation, telles que les logiciels anti-malware, les utilisateurs non-administrateurs ?* |
| **Sécurité des applications** | ***a.*** *Avez-vous désactivé l’interface utilisateur d’administration, le commutateur de Canaux et l’interface utilisateur d’Activité pour la production ?* <br>***b.****Avez-vous minimisé le niveau de journal pour la production ?*<br>***c.*** *Utilisez-vous https pour vous connecter à AEM ?* <br>***d.****Utilisez-vous un certificat signé par une autorité de certification ou une ICP d’entreprise ? (non les certificats autosignés)*<br>***e.**** Utilisez-vous TLS et non SSL v3 ?*<br>*** f.****Validez-vous le jeton d’enregistrement sur le périphérique et AEM lors de l’enregistrement ?*<br> ***g.*** *Avez-vous classifié les données utilisées et qu’il n’existe pas d’IIP ou d’IIP sur l’appareil ?*<br> ***h.*** *Avez-vous classifié les données utilisées et qu’il n’existe aucune information d’identification personnelle ou d’information sur la santé protégée sur l’appareil ?*<br> ***i.*** *Avez-vous configuré la surveillance des courriels et avez-vous mis en place une SOP pour répondre à la surveillance des courriels et gérer les périphériques non-Ping ?* |
| **Contrôle d’accès** | ***a.*** *Disposez-vous d&#39;un Contrôle d&#39;accès basé sur le rôle (CGRR) identifié et géré en interne ?* <br>***b.****Avez-vous suivi le principe du moindre privilège en fournissant l’accès aux auteurs, administrateurs et lecteurs en utilisant les meilleures pratiques d’Adobe ?* |

### Téléchargement de la liste de contrôle de sécurité {#download-checklist}

Pour télécharger la liste de contrôle de sécurité d’AEM Screens, cliquez [ici](/help/user-guide/assets/Screens-Security-Checklist.pdf).




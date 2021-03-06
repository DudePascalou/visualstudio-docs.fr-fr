---
title: Guide pratique pour attacher les outils d’analyse des performances à des processus en cours d’exécution ou les en détacher | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c53dcbec5d41b6aa93eef115bba966076fcfda2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Guide pratique pour attacher les outils d’analyse des performances à des processus en cours d’exécution ou les en détacher
Le profileur peut être utilisé pour attacher ou détacher des outils du processus en cours afin de faciliter l’échantillonnage et la collecte des données de performances. Vous pouvez utiliser cette méthode pour profiler un processus lorsque vous voulez éviter de collecter des données sur le temps de chargement de l’application ou pour surveiller les performances d’un processus après qu’il a atteint un certain état.  
  
> [!NOTE]
>  Les étapes suivantes concernent l’attachement et le détachement de processus à partir de l’environnement de développement intégré (IDE) de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Pour plus d’informations sur l’utilisation des outils en ligne de commande, consultez [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md). Pour plus d’informations sur le profilage de services, consultez [Profilage de services](../profiling/command-line-profiling-of-services.md).  
  
 Les processus qui peuvent être profilés dépendent des autorisations d’accès utilisateur définies par l’administrateur de l’ordinateur. Un compte d’utilisateur peut, par exemple, disposer d’autorisations pour ce qui suit :  
  
-   Fonctionnalités de profilage avancées quand l’administrateur a défini le démarrage du pilote et du service  
  
-   Profilage d’échantillons uniquement (utilisateurs du domaine)  
  
-   Refuser à tout le monde l’accès au profilage  
  
 Pour plus d’informations, consultez [Profilage et sécurité Windows Vista](../profiling/profiling-and-windows-vista-security.md), ainsi que les options d’administration dans [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Pour établir un attachement à un processus en cours d'exécution  
  
1.  Dans le menu **Débogage**, pointez sur **Profileur**, puis sur **Explorateur de performances** et cliquez sur **Attacher**.    
  
     La boîte de dialogue **Attacher le profileur au processus** s’affiche.  
  
2.  Cliquez sur le nom du processus que vous voulez attacher.  
  
3.  Cliquez sur **Attacher**.  
  
### <a name="to-detach-from-a-running-process"></a>Pour détacher d’un processus en cours d’exécution  
  
1.  Dans le menu **Débogage**, pointez sur **Profileur**, puis sur **Explorateur de performances** et cliquez sur **Détacher**. 
  
     La boîte de dialogue **Attacher le profileur au processus** s’affiche.  
  
2.  Cliquez sur le nom de l’image de laquelle se détacher.  
  
3.  Cliquez sur **Détacher**.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de la collecte de données](../profiling/controlling-data-collection.md)   
 [Vue d’ensemble des sessions de performance](../profiling/performance-session-overview.md)   
 [Guide pratique pour démarrer et terminer la collecte des données de performances](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilage et sécurité Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)
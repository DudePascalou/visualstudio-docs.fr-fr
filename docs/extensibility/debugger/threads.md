---
title: Threads | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a2754d3b1b15771f876855e7ca7d1dc510748308
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="threads"></a>Threads
En termes de l’architecture du débogueur, une **thread**:  
  
-   Est l’unité fondamentale de calcul. Un thread exécute séquentiellement les instructions dans le contexte d’une seule pile d’appels, déplacement à partir du contexte d’un code à l’autre.  
  
-   Peut identifier lui-même et le programme est en cours d’exécution et peut être nommé, suspendu et repris. Un thread peut également énumérer ses frames de pile associée et, sous certaines conditions, peut être déplacé vers un autre frame de pile. Étant donné le contexte d’un frame de pile, un thread peut retourner son thread logique associé, le cas échéant. Un thread possède des propriétés, par exemple un nombre suspend, qui peuvent être affichés dans la fenêtre Threads de l’IDE.  
  
-   Est représenté par un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interface, généralement créé par un moteur de débogage (DE) ou un ordinateur virtuel en raison de l’exécution d’un programme.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmes](../../extensibility/debugger/programs.md)   
 [Frames de pile](../../extensibility/debugger/stack-frames.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Gestionnaire du débogage de session](../../extensibility/debugger/session-debug-manager.md)
---
title: Concepts du débogueur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c157e570179da1e1f16ed5c2c12af63b95b0b61d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="debugger-concepts"></a>Concepts du débogueur
Pour générer sur le package de débogage de Visual Studio, vous devez être familiarisé avec les concepts d’architecture utilisées lors de la conception du package.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Session de débogage](../../extensibility/debugger/debug-session.md)  
 Explique le rôle d’une session de l’architecture du débogage.  
  
 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Définit un serveur est en termes d’architecture, le débogage en termes à la fois abstract et physiques.  
  
 [Fournisseurs de ports](../../extensibility/debugger/port-suppliers.md)  
 Définit ce qu’un fournisseur de port est en termes d’architecture de débogage.  
  
 [Ports](../../extensibility/debugger/ports.md)  
 Définit quelles un port est en termes d’architecture de débogage.  
  
 [Processus](../../extensibility/debugger/processes.md)  
 Définit un processus est en termes d’architecture de débogage.  
  
 [Nœuds de programme](../../extensibility/debugger/program-nodes.md)  
 Définit un nœud de programme en termes d’architecture, y compris comment il peut identifier lui-même et le processus, dans qu'il est en cours d’exécution le débogage.  
  
 [Programmes](../../extensibility/debugger/programs.md)  
 Définit un programme en termes d’architecture de débogage.  
  
 [Threads](../../extensibility/debugger/threads.md)  
 Définit les caractéristiques de threads en termes d’architecture de débogage.  
  
 [Frames de pile](../../extensibility/debugger/stack-frames.md)  
 Définit un frame de pile en termes d’architecture de débogage. Un frame de pile est une abstraction d’une pile qui fournit le contexte d’exécution d’un thread.  
  
 [Modules](../../extensibility/debugger/modules.md)  
 Définit un module, en termes d’architecture, de débogage comme un conteneur physique de code, par exemple un fichier exécutable ou une DLL.  
  
 [Points d’arrêt](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Définit les trois types de points d’arrêt, en attente, la limite et d’erreur, en termes d’architecture de débogage.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le moteur de débogage (DE) fonctionne simultanément dans le code, la documentation et les contextes d’expression d’évaluation. Décrit, pour chacun des trois contextes, emplacement, position ou d’évaluation appropriée à ce dernier.  
  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble des composants de débogage de Visual Studio, y compris le moteur de débogage (DE), évaluateur d’expression (EE) et le Gestionnaire de symboles (es).  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.
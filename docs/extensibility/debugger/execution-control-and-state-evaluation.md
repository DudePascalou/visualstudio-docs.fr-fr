---
title: Contrôle de l’exécution et l’état d’évaluation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d306ffe484605a081afa81afdcdcaa1a70339c84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="execution-control-and-state-evaluation"></a>Contrôle de l’exécution et l’état d’évaluation
Débogage d’une application requiert en implémentant des fonctionnalités de contrôle de l’exécution pas à pas détaillé dans des fonctions, stopper aux points d’arrêt et continuer l’exécution. Bases de débogage Visual Studio son contrôle de l’exécution sur les événements envoyés entre les composants du débogueur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contrôle du programme](../../extensibility/debugger/program-control.md)  
 Répertorie les routines suivantes qui se produisent au niveau du programme : définir l’instruction suivante, l’exécution, exécution pas à pas, continuer, la suspension et la reprise.  
  
 [Méthodes liées au point d’arrêt](../../extensibility/debugger/breakpoint-related-methods.md)  
 Définit la limite, en attente de types de points d’arrêt qui prend en charge de Visual Studio.  
  
 [Évaluation de la pile des appels](../../extensibility/debugger/call-stack-evaluation.md)  
 Aborde l’implémentation des méthodes qui permettent d’afficher les frames de pile de la pile des appels en mode arrêt.  
  
 [Évaluation des expressions](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Explique comment le moteur de débogage (DE), Gestionnaire d’expression d’évaluation (EE) et la session de débogage sont impliqués dans l’analyse et évaluation d’une expression entrée dans un des fenêtres de l’IDE.  
  
 [Événements de contrôle](../../extensibility/debugger/control-events.md)  
 Décrit l’interface utilisée pour envoyer des événements pendant l’exécution contrôlée du programme.
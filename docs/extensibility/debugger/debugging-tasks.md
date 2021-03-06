---
title: Tâches de débogage | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77cc933c49e15786221fd1cd3eb7e242118527a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-tasks"></a>Tâches de débogage
Pour déboguer un programme, il doit être lancé et un moteur de débogage (DE) doit être attaché à ce dernier, sans quoi le DE doit être attaché à un programme précédemment exécuté. Une fois attaché, le DE doit générer certains événements de démarrage. En réponse, le package de débogage tente de lier les points d’arrêt définis dans l’IDE. Lorsque le programme atteint un point d’arrêt lié, il s’arrête et attend l’entrée d’utilisateur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Problèmes de sécurité](../../extensibility/debugger/security-issues.md)  
 Décrit les étapes de sécurité qui sont nécessaires pour déboguer un programme.  
  
 [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)  
 Fournit des instructions détaillées sur la spécification DE, ce qui appelle le système d’exploitation pour lancer le programme.  
  
 [Attachement directement à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Décrit le processus utilisé pour déboguer un programme dans un processus qui est déjà en cours d’exécution.  
  
 [Envoi d’événements de démarrage après un lancement](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Répertorie les événements qui ont lieu une fois le D’est attaché au programme, jusqu'à ce que le programme est à son point d’entrée principal et est prêt pour le débogage.  
  
 [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)  
 Explique comment le D’envoie généralement un événement de point d’entrée, un événement de fin de charge ou un événement d’arrêt, selon les circonstances.  
  
 [Liaison de points d’arrêt](../../extensibility/debugger/binding-breakpoints.md)  
 Décrit comment, si l’utilisateur définit un point d’arrêt, l’IDE formule la demande et vous invite à entrer la session de débogage pour créer le point d’arrêt.  
  
 [Évaluation des expressions](../../extensibility/debugger/evaluating-expressions.md)  
 Explique comment les expressions sont créées et que se passe-t-il quand une expression est évaluée.  
  
 [Visualisation et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Explique comment les visualiseurs de types et des visionneuses personnalisées sont prises en charge par l’évaluateur d’expression (EE).  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts d’architecture débogage.  
  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble des composants de débogage Visual Studio, y compris le DE, EE et le Gestionnaire de symboles (es).  
  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le DE fonctionne simultanément dans le code, la documentation et les contextes d’expression d’évaluation. Décrit, pour chacun des trois contextes, emplacement, position ou d’évaluation appropriée à ce dernier.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
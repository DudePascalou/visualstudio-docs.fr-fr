---
title: Implémentation d’un évaluateur d’Expression | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed1df74c187b3f0a93e1a1ec84e8803bc164d223
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-an-expression-evaluator"></a>Implémentation d’un évaluateur d’Expression
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L’évaluation d’une expression est une interaction complexe entre le moteur de débogage (DE), le fournisseur de symboles (SP), l’objet de classeur et l’évaluateur d’expression (EE) lui-même. Ces quatre composants sont connectés par les interfaces qui sont implémentées par un composant et consommés par un autre.  
  
 Le EE prend une expression à partir de la DE sous la forme d’une chaîne et analyse ou évalue. Le EE implémente les interfaces suivantes, qui sont consommés par le DE :  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 Le EE appelle l’objet de classeur, fourni par le DE, pour obtenir la valeur des symboles et des objets. Le EE consomme les interfaces suivantes, qui sont implémentées par le DE :  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 Le EE implémente [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` fournit le mécanisme permettant de décrire le résultat d’une évaluation d’expression, comme une variable locale, un type primitif ou un objet, pour Visual Studio, qui affiche ensuite les informations appropriées dans le **variables locales**,  **Espion**, ou **exécution** fenêtre.  
  
 La procédure stockée est fournie pour le EE par le DE lorsqu’il demande des informations. La procédure stockée implémente des interfaces qui décrivent des adresses et des champs, tels que les interfaces suivantes et leurs dérivés :  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 Le EE consomme toutes ces interfaces.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Stratégie d’implémentation d’un évaluateur d’expression](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Définit un processus en trois étapes pour la stratégie d’implémentation expression évaluateur (Java EE).  
  
## <a name="see-also"></a>Voir aussi  
 [L’écriture d’un évaluateur d’Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
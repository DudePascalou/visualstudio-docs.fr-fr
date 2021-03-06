---
title: IEEVisualizerDataProvider | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8e37561957d592ecd9ae855f2816c860f84e7b20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface fournit la capacité de modifier la valeur d’un objet via un visualiseur de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 L’évaluateur d’expression implémente cette interface pour prendre en charge la modification des données sur un objet de propriété via un visualiseur de type.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est utilisée pour la création du [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objet via un appel à [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Consultez [Visualizing et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus d’informations.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Détermine s’il est possible de mettre à jour l’objet (et par la suite, sa valeur) qui est représentant ce visualiseur.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Force une nouvelle évaluation de l’objet pour le visualiseur.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Obtient un objet existant de ce visualiseur (aucune évaluation n’est effectuée).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Met à jour l’objet pour le visualiseur, modifiant ainsi la valeur que présente du visualiseur.|  
  
## <a name="remarks"></a>Notes  
 Le service de visualiseur (telle que représentée par le [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) de l’interface et retournée par [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) conserve une référence à l’objet qui implémente le `IEEVisualizerDataProvider` interface . Par conséquent, le `IEEVisualizerDataProvider` interface ne doit pas être implémenté sur le même objet qui implémente le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) si cet objet conserve une référence à la `IEEVisualizerService` objet : résultats de la référence circulaire et une un blocage se produit lorsque les objets sont détruits. L’approche recommandée consiste à implémenter `IEEVisualizerDataProvider` sur un objet distinct dans lequel le `IDebugProperty2` sans appeler les délégués de l’objet `IUnknown::AddRef` dessus.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)
---
title: IDebugBreakpointRequest3 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f369b193b69ef1a08c2ad3d451ff989caae8939f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Cette interface représente les informations nécessaires pour créer et lier n’importe quel type de point d’arrêt. Il s’agit d’une extension de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 En général, le Gestionnaire de session de débogage (SDM) implémente cette interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le moteur de débogage (DE) accède à cette interface en appelant [QueryInterface](/cpp/atl/queryinterface) sur l’interface IDebugBreakpointRequest2 reçu dans un appel à [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), le `IDebugBreakpointRequest3` interface expose la méthode suivante.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Obtient les informations de demande de point d’arrêt qui décrit cette demande de point d’arrêt.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est utilisée pour fournir des informations supplémentaires pour le DE via le [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structure. Ces informations supplémentaires incluent l’ID de fournisseur de la DE (sous la forme d’un GUID), le nom d’un point de trace et le nom d’une contrainte de point d’arrêt.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
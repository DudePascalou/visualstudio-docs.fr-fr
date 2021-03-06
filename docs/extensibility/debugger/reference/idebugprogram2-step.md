---
title: IDebugProgram2::Step | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10685adb27c9bf2e962beccb7e68f19ce5c27eeb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Effectue une étape.  
  
> [!NOTE]
>  Cette méthode est déconseillée. Utilisez le [étape](../../../extensibility/debugger/reference/idebugprocess3-step.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objet qui représente le thread en cours en retrait.  
  
 `sk`  
 [in] Une valeur à partir de la [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) énumération qui spécifie le type d’étape.  
  
 `step`  
 [in] Une valeur à partir de la [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) énumération qui spécifie l’unité d’étape (par exemple, par l’instruction ou l’instruction).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En cas de toute synchronisation de threads ou de la communication entre les threads, les autres threads dans le programme doivent s’exécuter lorsqu’un thread particulier est exécution pas à pas.  
  
> [!WARNING]
>  Ne pas envoyer un événement d’arrêt ou un événement (synchrone) immédiat [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lors du traitement de cet appel ; sinon, le débogueur peut se bloquer.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
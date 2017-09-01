---
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 26a44b7c1449e767bca10793bd4602ea472a8a48
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Creates a pending breakpoint in the debug engine (DE).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pBPRequest`  
 [in] An [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) object that describes the pending breakpoint to create.  
  
 `ppPendingBP`  
 [out] Returns an [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) object that represents the pending breakpoint.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code. Typically returns `E_FAIL` if the `pBPRequest` parameter does not match any language supported by the DE of if the `pBPRequest` parameter is invalid or incomplete.  
  
## <a name="remarks"></a>Remarks  
 A pending breakpoint is essentially a collection of all the information needed to bind a breakpoint to code. The pending breakpoint returned from this method is not bound to code until the [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) method is called.  
  
 For each pending breakpoint the user sets, the session debug manager (SDM) calls this method in each attached DE. It is up to the DE to verify that the breakpoint is valid for programs running in that DE.  
  
 When the user sets a breakpoint on a line of code, the DE is free to bind the breakpoint to the closest line in the document that corresponds to this code. This makes it possible for the user to set a breakpoint on the first line of a multi-line statement, but bind it on the last line (where all the code is attributed in the debug information).  
  
## <a name="example"></a>Example  
 The following example shows how to implement this method for a simple `CProgram` object. The DE's implementation of the `IDebugEngine2::CreatePendingBreakpoint` could then forward all calls to this implementation of the method in each program.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>See Also  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
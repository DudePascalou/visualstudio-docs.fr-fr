---
title: IDebugComPlusSymbolProvider2::FunctionHasLineInfo | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- FunctionHasLineInfo
- IDebugComPlusSymbolProvider2::FunctionHasLineInfo
ms.assetid: e1b508f1-6521-492f-b110-ab957744a037
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8175946e7d4c01a2013e31ff39ba7d1ea4161f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcomplussymbolprovider2functionhaslineinfo"></a>IDebugComPlusSymbolProvider2::FunctionHasLineInfo
Détermine si la méthode spécifiée a des informations de ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FunctionHasLineInfo(  
   IDebugAddress* pAddress  
);  
```  
  
```csharp  
int FunctionHasLineInfo(  
   IDebugAddress pAddress  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAddress`  
 [in] L’adresse de débogage qui est représenté par un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Cette adresse doit être un METHOD_ADDRESS.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugSymbolProvider** objet qui expose la [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interface.  
  
```cpp  
HRESULT CDebugSymbolProvider::FunctionHasLineInfo(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );  
  
    IfFalseGo( pAddress, E_INVALIDARG );  
  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->FunctionHasLineInfo( address.addr.addr.addrMethod.tokMethod,  
                                       address.addr.addr.addrMethod.dwVersion))  
    {  
  
        // S_FALSE indicates this method does not have line info  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
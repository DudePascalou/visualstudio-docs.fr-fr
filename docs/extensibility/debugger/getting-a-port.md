---
title: Obtention d’un Port | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c20b3e3bdc2644e7af7d9a35de06af7f96d7680
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getting-a-port"></a>Obtention d’un Port
Un port représente une connexion à un ordinateur sur lequel les processus sont en cours d’exécution. Cet ordinateur peut être l’ordinateur local ou un ordinateur distant (ce qui peut éventuellement être qui exécute un système d’exploitation non basé sur Windows, consultez [Ports](../../extensibility/debugger/ports.md) pour plus d’informations).  
  
 Un port est représenté par le [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface. Il est utilisé pour obtenir des informations sur les processus en cours d’exécution sur l’ordinateur que le port est connecté à.  
  
 Un moteur de débogage a besoin d’accéder à un port afin d’inscrire des nœuds de programme avec le port et de satisfaire les demandes d’informations sur les processus. Par exemple, si le moteur de débogage implémente la [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) de l’interface, l’implémentation pour la [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) méthode peut demander le port pour le processus nécessaire informations à retourner.  
  
 Visual Studio fournit le port nécessaire pour le moteur de débogage, et il obtient ce port à partir d’un fournisseur de port. Si un programme est attaché à (ou à partir de dans le débogueur en raison d’une exception est levée, ce qui déclenche la boîte de dialogue juste-à-temps [JIT]), l’utilisateur se voit proposer de transport (un autre nom pour un fournisseur de port) à utiliser. Sinon, si l’utilisateur lance le programme à partir du débogueur, le système de projet spécifie le fournisseur de port à utiliser. Dans les deux cas, Visual Studio instancie le fournisseur de port, représenté par un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) de l’interface et demande un nouveau port en appelant [ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) avec un [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) interface. Ce port est ensuite transmis le moteur de débogage dans un formulaire ou un autre.  
  
## <a name="example"></a>Exemple  
 Ce fragment de code montre comment utiliser le port fourni à [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) pour inscrire un nœud de programme dans [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Pas directement liées à ce concept de paramètres ont été omis par souci de clarté.  
  
> [!NOTE]
>  Cet exemple utilise le port à lancer et reprendre le processus et suppose que le [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) interface est implémentée sur le port. Il s’agit en aucun cas la seule façon d’effectuer ces tâches, et il est possible que le port peut ne même impliqué autre que le programme de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) lui donné.  
  
```cpp  
// This is an IDebugEngineLaunch2 method.  
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                      IDebugPort2 *pPort,  
                                      /* omitted parameters */,  
                                      IDebugProcess2**ppDebugProcess)  
{  
    // do stuff here to set up for a launch (such as handling the other parameters)  
    ...  
  
    // Now get the IPortNotify2 interface so we can register a program node  
    // in CDebugEngine::ResumeProcess.  
    CComPtr<IDebugDefaultPort2> spDefaultPort;  
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
    if (SUCCEEDED(hr))  
    {  
        CComPtr<IDebugPortNotify2> spPortNotify;  
        hr = spDefaultPort->GetPortNotify(&spPortNotify);  
        if (SUCCEEDED(hr))  
        {  
            // Remember the port notify so we can use it in ResumeProcess.  
            m_spPortNotify = spPortNotify;  
  
            // Now launch the process in a suspended state and return the  
            // IDebugProcess2 interface  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = pPort->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                // pass on the parameters we were given (omitted here)  
                hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
            }  
        }  
    }  
    return(hr);  
}  
  
HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
{  
    // Make a program node for this process  
    HRESULT hr;  
    CComPtr<IDebugProgramNode2> spProgramNode;  
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
    if (SUCCEEDED(hr))  
    {  
        hr = m_spPortNotify->AddProgramNode(spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            // resume execution of the process using the port given to us earlier.  
           // (Querying for the IDebugPortEx2 interface is valid here since  
           // that's how we got the IDebugPortNotify2 interface in the first place.)  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = m_spPortNotify->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrement du programme](../../extensibility/debugger/registering-the-program.md)   
 [L’activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)   
 [Ports](../../extensibility/debugger/ports.md)
---
title: 'Comment : configurer la sécurité de la liste d’Inclusion | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f8995e95ed1a35841aab945daa1ea35854946b56
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-inclusion-list-security"></a>Comment : configurer la sécurité de la liste d'inclusion
  Si vous disposez des autorisations d’administrateur, vous pouvez configurer le [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation pour contrôler si les utilisateurs finaux sont fournies à l’option d’installation des solutions Office en enregistrant une décision d’approbation à la liste d’inclusion. Pour plus d’informations sur les listes d’inclusion, consultez [faire confiance à des Solutions Office à l’utilisation de listes d’Inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Pour les solutions qui se trouvent dans chacune des cinq zones, vous pouvez définir les options suivantes :  
  
-   Activer la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation et de la liste d’inclusion. Vous pouvez autoriser les utilisateurs finaux d’approuver des solutions Office qui sont signés avec n’importe quel certificat.  
  
-   Restreindre la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation et de la liste d’inclusion. Vous pouvez autoriser les utilisateurs à installer des solutions Office signées avec un certificat qui identifie le serveur de publication, mais qui n’est pas approuvé.  
  
-   Désactiver la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation et de la liste d’inclusion. Vous pouvez empêcher les utilisateurs finaux à partir de l’installation des solutions Office qui ne sont pas signée avec un certificat explicitement approuvé.  
  
## <a name="enabling-the-inclusion-list"></a>L’activation de la liste d’Inclusion  
 Activer la liste d’inclusion d’une zone lorsque vous souhaitez que les utilisateurs finaux aient la possibilité d’installer et exécuter les solutions Office provenant de cette zone.  
  
#### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Pour activer la liste d’inclusion à l’aide de l’Éditeur du Registre  
  
1.  Ouvrez l’Éditeur du Registre :  
  
    1.  Cliquez sur **Démarrer**, puis cliquez sur **exécuter**.  
  
    2.  Dans le **ouvrir** , tapez **regedt32.exe**, puis cliquez sur **OK**.  
  
2.  Recherchez la clé de Registre suivante :  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Si la clé n’existe pas, créez-le.  
  
3.  Ajoutez les sous-clés suivantes en tant que **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées.  
  
    |Sous-clé valeur chaîne|Value|  
    |-------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Désactivé**|  
    |**Poste de travail**|**Activé**|  
    |**LocalIntranet**|**Activé**|  
    |**TrustedSites**|**Activé**|  
  
     Par défaut, **Internet** a la valeur **AuthenticodeRequired** et **UntrustedSites** a la valeur **désactivé**.  
  
#### <a name="to-enable-the-inclusion-list-programmatically"></a>Pour activer la liste d’inclusion par programmation  
  
1.  Créez une application console Visual Basic ou Visual c#.  
  
2.  Ouvrez le fichier Program.vb ou Program.cs à modifier et ajoutez le code suivant.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Générez et exécutez l’application.  
  
## <a name="restricting-the-inclusion-list"></a>Restreindre la liste d’Inclusion  
 Limiter la liste d’inclusion afin que les solutions doivent être signées avec des certificats Authenticode dont l’identité est connue avant que les utilisateurs sont invités à une décision d’approbation.  
  
#### <a name="to-restrict-the-inclusion-list"></a>Pour restreindre la liste d’inclusion  
  
1.  Ouvrez l’Éditeur du Registre :  
  
    1.  Cliquez sur **Démarrer**, puis cliquez sur **exécuter**.  
  
    2.  Dans le **ouvrir** , tapez **regedt32.exe**, puis cliquez sur **OK**.  
  
2.  Recherchez la clé de Registre suivante :  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Si la clé n’existe pas, créez-le.  
  
3.  Ajoutez les sous-clés suivantes en tant que **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées.  
  
    |Sous-clé valeur chaîne|Value|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Désactivé**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**Poste de travail**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     Par défaut, **Internet** a la valeur **AuthenticodeRequired** et **UntrustedSites** a la valeur **désactivé**.  
  
#### <a name="to-restrict-the-inclusion-list-programmatically"></a>Pour restreindre la liste d’inclusion par programmation  
  
1.  Créez une application console Visual Basic ou Visual c#.  
  
2.  Ouvrez le fichier Program.vb ou Program.cs à modifier et ajoutez le code suivant.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Générez et exécutez l’application.  
  
## <a name="disabling-the-inclusion-list"></a>La désactivation de la liste d’Inclusion  
 Vous pouvez désactiver la liste d’inclusion afin que les utilisateurs finaux peuvent installer uniquement les solutions qui sont signées avec un certificat approuvé et connu.  
  
#### <a name="to-disable-the-inclusion-list"></a>Pour désactiver la liste d’inclusion  
  
1.  Ouvrez l’Éditeur du Registre :  
  
    1.  Cliquez sur **Démarrer**, puis cliquez sur **exécuter**.  
  
    2.  Dans le **ouvrir** , tapez **regedt32.exe**, puis cliquez sur **OK**.  
  
2.  Créer la clé de Registre suivante, si cela n’existe pas déjà :  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  Ajoutez les sous-clés suivantes en tant que **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées.  
  
    |Sous-clé valeur chaîne|Value|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Désactivé**|  
    |**Internet**|**Désactivé**|  
    |**Poste de travail**|**Désactivé**|  
    |**LocalIntranet**|**Désactivé**|  
    |**TrustedSites**|**Désactivé**|  
  
#### <a name="to-disable-the-inclusion-list-programmatically"></a>Pour désactiver la liste d’inclusion par programmation  
  
1.  Créez une application console Visual Basic ou Visual c#.  
  
2.  Ouvrez le fichier Program.vb ou Program.cs à modifier et ajoutez le code suivant.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  Générez et exécutez l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Approbation des Solutions Office à l’aide des listes d’Inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Sécurisation de solutions Office](../vsto/securing-office-solutions.md)  
  
  
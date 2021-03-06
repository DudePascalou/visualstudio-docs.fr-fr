---
title: 'Comment : ajouter un éditeur approuvé à un ordinateur Client pour les Applications ClickOnce | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c9d718eba01a35c1f6991ab50d217c8b5f63065
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Comment : ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce
Avec le déploiement d’applications approuvées, vous pouvez configurer les ordinateurs clients pour que vos applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] s’exécutent avec un niveau de confiance supérieur sans solliciter l’utilisateur. Les procédures suivantes montrent comment utiliser l’outil en ligne de commande CertMgr.exe pour ajouter le certificat d’un éditeur au magasin d’éditeurs approuvés sur un ordinateur client.  
  
 Les commandes que vous utilisez varient légèrement selon que l’autorité de certification qui a émis votre certificat fait partie ou non de la racine de confiance d’un client. Si un ordinateur client Windows fait partie d’un domaine, il contient, dans une liste, les autorités de certification considérées comme des racines de confiance. Cette liste est généralement configurée par l’administrateur système. Si votre certificat a été émis par l’une de ces racines de confiance, ou par une autorité de certification liée à l’une de ces racines de confiance, vous pouvez ajouter le certificat au magasin racine approuvé du client. Si, en revanche, votre certificat n’a pas été émis par l’une de ces racines de confiance, vous devez ajouter le certificat au magasin racine approuvé du client et au magasin d’éditeurs approuvés.  
  
> [!NOTE]
>  Vous devez ajouter les certificats de cette façon sur chaque ordinateur client sur lequel vous envisagez de déployer une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] qui nécessite des autorisations élevées. Vous ajoutez les certificats manuellement ou par le biais d’une application que vous déployez sur vos clients. Vous ne devez configurer ces ordinateurs qu’une seule fois, après quoi vous pouvez déployer une quantité quelconque d’applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] signées avec le même certificat.  
  
 Vous pouvez aussi ajouter un certificat à un magasin par programmation en utilisant la classe <xref:System.Security.Cryptography.X509Certificates.X509Store> .  
  
 Pour obtenir une vue d’ensemble du déploiement d’applications approuvées, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Pour ajouter un certificat au magasin d’éditeurs approuvés sous la racine de confiance  
  
1.  Obtenez un certificat numérique à partir d’une autorité de certification.  
  
2.  Exportez le certificat au format Base64 X.509 (.cer). Pour plus d’informations sur les formats de certificats, consultez [Exporter un certificat](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  À partir de l’invite de commandes sur les ordinateurs clients, exécutez la commande suivante :  
  
     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Pour ajouter un certificat au magasin d’éditeurs approuvés sous une autre racine  
  
1.  Obtenez un certificat numérique à partir d’une autorité de certification.  
  
2.  Exportez le certificat au format Base64 X.509 (.cer). Pour plus d’informations sur les formats de certificats, consultez [Exporter un certificat](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  À partir de l’invite de commandes sur les ordinateurs clients, exécutez la commande suivante :  
  
     **certmgr.exe -add good.cer -c -s -r localMachine Root**  
  
     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md)   
 [Guide pratique pour activer les paramètres de sécurité ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Guide pratique pour définir une zone de sécurité pour une application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Guide pratique pour définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Guide pratique pour déboguer une application ClickOnce avec des autorisations restreintes](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Comment : ajouter un éditeur approuvé à un ordinateur Client pour les Applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Comment : signer de nouveau les manifestes de déploiement et d’Application](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Guide pratique pour configurer le comportement de l’invite d’approbation ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
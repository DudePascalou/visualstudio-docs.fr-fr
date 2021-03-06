---
title: Meilleures pratiques de développement pour COM, VSTO et VBA compléments dans Office
ms.custom: ''
ms.date: 07/25/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 020faeb330348049dcf12431fadfa6ab099d1584
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Meilleures pratiques de développement pour COM, VSTO et VBA compléments dans Office
  Si vous développez des Compléments VSTO COM ou de VBA pour Office, suivez les meilleures pratiques de développement décrits dans cet article.   Cela aide à vérifier :

-  Compatibilité de vos compléments entre différentes versions et les déploiements de Microsoft Office.
-  Réduction de la complexité du déploiement de compléments pour vos utilisateurs et les administrateurs informatiques.
-  Échecs d’installation ou d’exécution involontaires de votre complément ne se produisent pas.

>Remarque : L’utilisation de la [bureau pont](/windows/uwp/porting/desktop-to-uwp-root) pour préparer votre COM, VSTO VBA complément ou pour le Windows Store n’est pas pris en charge. Compléments COM, VSTO et VBA ne peut pas être distribués dans le Windows Store ou Office Store. 
  
## <a name="do-not-check-for-office-during-installation"></a>Ne pas vérifier Office pendant l’installation  
 Nous ne recommandons pas avoir votre complément détecter si Office est installé pendant l’installation du complément. Si Office n’est pas installé, vous pouvez installer le complément et l’utilisateur sera en mesure d’y accéder après l’installation d’Office. 
  
## <a name="use-embedded-interop-types-nopia"></a>Utilisez des Types Interop incorporés (NoPIA)  
Si votre solution utilise .NET 4.0 ou version ultérieure, utilisez des types interop incorporés (NoPIA) au lieu de selon l’Office assemblys PIA (Primary Interop) redistribuable. À l’aide de l’incorporation de type réduit la taille de l’installation de votre solution et garantit la compatibilité future. Office 2010 était la dernière version d’Office fourni l’assembly PIA redistribuable. Pour plus d’informations, consultez [procédure pas à pas : incorporation des informations de type provenant d’assemblys Microsoft Office](https://msdn.microsoft.com/en-us/library/ee317478.aspx) et [équivalence de Type et types interop incorporés](/windows/uwp/porting/desktop-to-uwp-root).

Si votre solution utilise une version antérieure de .NET, nous recommandons que vous mettez à jour votre solution pour utiliser .NET 4.0 ou version ultérieure. À l’aide de .NET 4.0 ou version ultérieure réduit les conditions préalables d’exécution sur des versions plus récentes de Windows.
  
## <a name="avoid-depending-on-specific-office-versions"></a>Évitez d’en fonction des versions d’Office  
Si votre solution utilise une fonctionnalité qui est disponible uniquement dans les versions plus récentes d’Office, vérifiez que la capacité existe (si possible, au niveau des fonctionnalités) lors de l’exécution (par exemple, l’utilisation de gestion des exceptions ou en vérifiant la version des exceptions). Valider la version minimale, au lieu des versions spécifiques, à l’aide d’API prises en charge dans le modèle objet, telles que la [Application.Version propriété](https://msdn.microsoft.com/en-us/library/office/microsoft.office.interop.excel._application.version.aspx). Nous ne recommandons pas s’appuient sur les métadonnées binaires, les chemins d’installation ou les clés de Registre Office car ils peuvent changer entre les versions, les environnements et les installations.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Activer l’utilisation de Office 32 bits et 64 bits   
Votre cible de build par défaut doit prendre en charge les (x86) 32 bits et 64 bits (x64), sauf si votre solution dépend des bibliothèques qui sont uniquement disponibles pour un nombre de bits spécifique. L’augmentation de la version 64 bits d’Office à l’adoption, notamment dans les environnements de données volumineuses. Prise en charge 32 bits et 64 bits rend plus facile pour vos utilisateurs pour effectuer la transition entre les versions 32 bits et 64 bits d’Office.

Lorsque vous écrivez du code VBA, utilisez 64 bits safe instructions declare et convertir des variables comme il convient. En outre, assurez-vous que les documents peuvent être partagées entre les utilisateurs qui exécutent des versions 32 bits ou 64 bits d’Office en fournissant le code pour chaque nombre de bits. Pour plus d’informations, consultez [64 bits de Visual Basic pour une vue d’ensemble des applications](https://msdn.microsoft.com/en-us/library/office/gg264421.aspx).

## <a name="support-restricted-environments"></a>Prend en charge des environnements restreints   
Votre solution ne doit pas nécessiter de privilèges d’élévation du compte d’utilisateur ou administrateur. En outre, la solution ne doit pas s’appuyer sur la définition ou la modification :

- Le répertoire de travail actuel.
- Répertoires de chargement DLL.
- La variable de chemin d’accès.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Modifier l’emplacement de données partagées et des paramètres
Si la solution se compose d’un complément et un processus externe à Office, n’utilisez pas le dossier application data de l’utilisateur ou du Registre pour échanger des données ou des paramètres entre le complément et le processus externe. Envisagez plutôt d’utiliser le dossier temporaire de l’utilisateur, le dossier de documents ou répertoire d’installation de votre solution.

## <a name="increment-the-version-number-with-each-update"></a>Incrémenter le numéro de version avec chaque mise à jour
Définir le numéro de version des fichiers binaires dans votre solution et incrémenter avec chaque mise à jour. Cela rend plus facile pour les utilisateurs à identifier les modifications apportées entre les versions et évaluer la compatibilité.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Fournir des instructions de prise en charge pour les versions plus récentes d’Office
Les clients demandent des éditeurs de logiciels pour fournir des instructions de prise en charge pour leurs COM, VSTO et VBA les compléments qui s’exécutent dans Office. Liste de vos clients permet des instructions de prise en charge explicite à l’aide d’Office 365 ProPlus outils comprennent votre prise en charge. 

Pour fournir des instructions de prise en charge pour les applications clientes Office (par exemple, Word ou Excel), commencez par vérifier que vos compléments s’exécutent dans la version actuelle d’Office, puis validez à fournir des mises à jour si votre complément s’arrête dans une version ultérieure. Il est inutile de tester vos compléments lorsque Microsoft publie une nouvelle build ou une mise à jour Office. Microsoft change rarement la plateforme d’extensibilité COM, VSTO et VBA dans Office, et ces modifications seront documentées.

>Important : Microsoft gère une liste des compléments pris en charge pour les rapports de compatibilité et les informations de contact d’éditeurs de logiciels. Pour obtenir votre complément répertorié, consultez [ https://aka.ms/readyforwindows ](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Utiliser Process Monitor pour vous aider à déboguer l’installation ou le chargement des problèmes
Si votre complément présente des problèmes de compatibilité pendant l’installation ou de la charge, il peuvent être liées à des problèmes avec un accès de fichier ou du Registre. Utilisez [Process Monitor](/sysinternals/downloads/procmon) ou un outil de débogage similaire pour vous connecter et de comparer le comportement par rapport à un environnement de travail pour aider à identifier le problème.

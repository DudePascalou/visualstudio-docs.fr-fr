---
title: Élément hôte de feuille de calcul | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c89fa79a73393afa2919554de790c307b2ea68b5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="worksheet-host-item"></a>Élément hôte de feuille de calcul
  L’élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> est un type qui étend le type <xref:Microsoft.Office.Interop.Excel.Worksheet> à partir de l’assembly PIA (Primary Interop Assembly) pour Excel. L’élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> fournit les mêmes propriétés, méthodes et événements qu’un objet <xref:Microsoft.Office.Interop.Excel.Worksheet> , mais il expose également des événements supplémentaires et agit comme conteneur pour les contrôles hôtes et les contrôles Windows Forms.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Dans les projets au niveau du document, vous pouvez ajouter des éléments hôtes <xref:Microsoft.Office.Tools.Excel.Worksheet> à votre projet au moment du design. Dans les projets de compléments VSTO, vous pouvez générer des éléments hôtes <xref:Microsoft.Office.Tools.Excel.Worksheet> au moment de l'exécution.  
  
## <a name="understanding-worksheet-host-items-in-document-level-projects"></a>Présentation des éléments hôtes Worksheet dans les projets au niveau du document  
 Quand vous créez un projet au niveau du document pour Excel, Visual Studio crée automatiquement trois éléments hôtes <xref:Microsoft.Office.Tools.Excel.Worksheet> dans le projet. Les noms par défaut des feuilles de calcul sont `Sheet1`, `Sheet2`et `Sheet3`. Si vous créez un projet basé sur un classeur existant, le nombre d’éléments hôtes dépend du nombre de feuilles de calcul dans le classeur.  
  
 Ces classes de feuille de calcul vous donnent accès aux membres de l’élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> pour effectuer des tâches de base dans votre personnalisation, telles que la modification du contenu d’une feuille de calcul. Vous pouvez aussi utiliser ces classes pour ajouter des contrôles à des feuilles de calcul. En combinant plusieurs jeux de contrôles et en écrivant du code, vous pouvez lier les contrôles à des données, recueillir des informations de l’utilisateur et répondre à des actions utilisateur. Pour plus d'informations, consultez [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 Les classes de feuille de calcul fournissent un emplacement dans lequel vous pouvez commencer à écrire du code dans votre projet. Étant donné que la classe fournit les mêmes propriétés, méthodes et événements que l’objet <xref:Microsoft.Office.Interop.Excel.Worksheet> dans l’assembly PIA pour Excel, vous pouvez aussi utiliser ces classes pour accéder au modèle objet d’Excel. Pour plus d'informations, consultez [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
 Dans les projets au niveau du document, vous pouvez ajouter des éléments hôtes <xref:Microsoft.Office.Tools.Excel.Worksheet> supplémentaires au projet au moment du design en ajoutant une nouvelle feuille de calcul au classeur dans le concepteur.  
  
### <a name="renaming-worksheets"></a>Modification du nom des feuilles de calcul  
 Dans un projet au niveau du document, vous pouvez renommer les feuilles de calcul dans le concepteur Visual Studio, mais cela modifie uniquement le nom d’affichage de la feuille de calcul. Le nom de programmation est encore le nom par défaut de la feuille de calcul. Si vous renommez la feuille de calcul dans la fenêtre **Propriétés** , seul le nom de programmation est modifié.  
  
### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Limitations de l’élément hôte Worksheet dans les projets au niveau du document  
 Vous ne pouvez pas créer d’éléments hôtes <xref:Microsoft.Office.Tools.Excel.Worksheet> au moment de l’exécution dans un projet au niveau du document. Si vous créez une feuille de calcul Excel au moment de l’exécution, elle sera de type <xref:Microsoft.Office.Interop.Excel.Worksheet>. Comme il ne s’agit pas d’un élément hôte, elle ne peut pas contenir de contrôles hôtes ni de contrôles Windows Forms. Pour plus d’informations sur la création de documents au moment de l’exécution, consultez [Comment : par programme ajouter des feuilles de calcul à des classeurs](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
## <a name="understanding-worksheet-host-items-in-vsto-add-in-projects"></a>Présentation des éléments hôtes Worksheet dans les projets de complément VSTO  
 Dans les projets de niveau application, vous pouvez générer un élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> au moment de l’exécution pour toute feuille de calcul ouverte dans Excel. Vous pouvez utiliser l’élément hôte <xref:Microsoft.Office.Tools.Excel.Worksheet> pour ajouter des contrôles à la feuille de calcul associée ou pour gérer des événements qui ne sont pas disponibles sur des objets <xref:Microsoft.Office.Interop.Excel.Worksheet> .  
  
 Pour générer un <xref:Microsoft.Office.Tools.Excel.Worksheet> élément hôte, utilisez la méthode GetVstoObject. Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Élément hôte de classeur](../vsto/workbook-host-item.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  
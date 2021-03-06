---
title: Ajouter des contrôles aux documents Office au moment de l’exécution
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at runtime
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at runtime
- helper methods [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af280d407a8453b66658ee5395a88d2b91b991b7
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="add-controls-to-office-documents-at-runtime"></a>Ajouter des contrôles aux documents Office au moment de l’exécution
  Vous pouvez ajouter des contrôles à un document Microsoft Office Word et un classeur Microsoft Office Excel au moment de l’exécution. Vous pouvez également les supprimer lors de l’exécution. Contrôles que vous ajoutez ou supprimez lors de l’exécution sont appelés *des contrôles dynamiques*.  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 Cette rubrique décrit les tâches suivantes :  

-   [Gérer des contrôles au moment de l’exécution à l’aide de collections de contrôle](#ControlsCollection).  

-   [Ajouter des contrôles hôtes aux documents](#HostControls).  

-   [Ajouter des contrôles Windows Forms aux documents](#WindowsForms).  

 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment exposer les faire : ajouter des contrôles à un document lors de l’exécution ?](http://go.microsoft.com/fwlink/?LinkId=132782).  

##  <a name="ControlsCollection"></a> Gérer des contrôles au moment de l’exécution à l’aide de collections de contrôle  
 Pour ajouter, obtenir ou supprimer des contrôles au moment de l’exécution, utilisez les méthodes d’assistance de <xref:Microsoft.Office.Tools.Excel.ControlCollection> et <xref:Microsoft.Office.Tools.Word.ControlCollection> objets.  

 La façon dont vous accédez à ces objets dépend du type de projet que vous développez :  

-   Dans un projet au niveau du document pour Excel, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> des classes `Sheet1`, `Sheet2`et `Sheet3` . Pour plus d’informations sur ces classes, consultez [élément hôte de feuille de calcul](../vsto/worksheet-host-item.md).  

-   Dans un projet au niveau du document pour Word, utilisez la propriété <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de la classe `ThisDocument` . Pour plus d’informations sur cette classe, consultez [élément hôte de Document](../vsto/document-host-item.md).  

-   Dans un projet de complément VSTO pour Excel ou Word, utilisez le `Controls` propriété d’un <xref:Microsoft.Office.Tools.Excel.Worksheet> ou <xref:Microsoft.Office.Tools.Word.Document> que vous générez au moment de l’exécution. Pour plus d’informations sur la génération de ces objets lors de l’exécution, consultez [documents Word d’étendre et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  

### <a name="add-controls"></a>Ajouter des contrôles  
 Les types <xref:Microsoft.Office.Tools.Excel.ControlCollection> et <xref:Microsoft.Office.Tools.Word.ControlCollection> incluent des méthodes d’assistance que vous pouvez utiliser pour ajouter des contrôles hôtes et des contrôles Windows Forms communs aux documents et aux feuilles de calcul. Chaque nom de méthode est au format `Add`*control class*où *control class* correspond au nom de la classe du contrôle que vous souhaitez ajouter. Par exemple, pour ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à votre document, utilisez la méthode <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> .  

 L’exemple de code suivant montre comment ajouter <xref:Microsoft.Office.Tools.Excel.NamedRange> à `Sheet1` dans un projet au niveau du document pour Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="access-and-delete-controls"></a>Contrôles d’accès et de suppression  
 Vous pouvez utiliser la `Controls` propriété d’un <xref:Microsoft.Office.Tools.Excel.Worksheet> ou <xref:Microsoft.Office.Tools.Word.Document> pour parcourir tous les contrôles dans votre document, y compris les contrôles ajoutés au moment du design. Les contrôles que vous avez ajoutés au moment de la conception sont également appelés *contrôles statiques*.  

 Vous pouvez supprimer des contrôles dynamiques en appelant le `Delete` méthode du contrôle, ou en appelant le `Remove` méthode de chaque collection de contrôles. L’exemple de code suivant utilise la méthode <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> pour supprimer une <xref:Microsoft.Office.Tools.Excel.NamedRange> de `Sheet1` dans un projet au niveau du document pour Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 Impossible de supprimer les contrôles statiques lors de l’exécution. Si vous essayez d’utiliser le `Delete` ou `Remove` méthode pour supprimer un contrôle statique, un <xref:Microsoft.Office.Tools.CannotRemoveControlException> sera levée.  

> [!NOTE]  
>  Ne supprimez pas les contrôles par programmation dans le gestionnaire d’événements `Shutdown` du document. Les éléments d’interface utilisateur du document ne sont plus disponibles quand l’événement `Shutdown` est déclenché. Si vous souhaitez supprimer les contrôles avant la fermeture du document, ajoutez votre code au gestionnaire d’événements pour un autre événement, tel que <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> ou <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> pour Word, ou <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>ou <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> pour Excel.  

##  <a name="HostControls"></a> Ajouter des contrôles hôtes aux documents  
 Lorsque vous ajoutez par programmation des contrôles hôtes aux documents, vous devez fournir un nom qui identifie de façon unique le contrôle. Vous devez également spécifier où le contrôle doit être ajouté dans le document. Pour obtenir des instructions spécifiques, consultez les rubriques suivantes :  

-   [Comment : ajouter des contrôles ListObject aux feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

-   [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

-   [Comment : ajouter des contrôles Chart aux feuilles de calcul](../vsto/how-to-add-chart-controls-to-worksheets.md)  

-   [Comment : ajouter du contenu des contrôles à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)  

-   [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

 Pour plus d’informations sur les contrôles hôtes, consultez [éléments hôtes et héberger la vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).  

 Lorsqu’un document est enregistré puis fermé, tous les contrôles hôtes créés dynamiquement sont déconnectés de leurs événements et perdent leur fonctionnalité de liaison de données. Vous pouvez ajouter du code à votre solution pour recréer les contrôles hôtes lorsque le document est de nouveau ouvert. Pour plus d’informations, consultez [conserver des contrôles dynamiques persistants dans des documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Les méthodes d’assistance ne sont pas fournies pour les contrôles hôtes suivants, car ceux-ci ne peuvent pas être ajoutés par programmation aux documents : <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>et <xref:Microsoft.Office.Tools.Word.XMLNodes>.  

##  <a name="WindowsForms"></a> Ajouter des contrôles Windows Forms à des documents  
 Lorsque vous ajoutez par programmation un contrôle Windows Forms à un document, vous devez fournir l’emplacement du contrôle et un nom qui identifie de façon unique le contrôle. Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fournit des méthodes d’assistance pour chaque contrôle. Ces méthodes sont surchargées afin que vous puissiez transmettre une plage ou des coordonnées spécifiques pour l’emplacement du contrôle.  

 Lorsqu’un document est enregistré puis fermé, tous les contrôles Windows Forms créés dynamiquement sont supprimés du document. Vous pouvez ajouter du code à votre solution pour recréer les contrôles lorsque le document est de nouveau ouvert. Si vous créez des contrôles Windows Forms dynamiques en utilisant un complément VSTO, les wrappers ActiveX des contrôles sont laissés dans le document. Pour plus d’informations, consultez [conserver des contrôles dynamiques persistants dans des documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Les contrôles Windows Forms ne peuvent pas être ajoutés par programmation aux documents protégés. Si vous déprotégez par programmation un document Word ou une feuille de calcul Excel pour ajouter un contrôle, vous devez écrire le code supplémentaire pour supprimer le wrapper ActiveX du contrôle lorsque le document est fermé. Le wrapper ActiveX du contrôle n’est pas supprimé automatiquement des documents protégés.  

### <a name="add-custom-controls"></a>Ajouter des contrôles personnalisés  
 Si vous souhaitez ajouter un <xref:System.Windows.Forms.Control> qui n’est pas pris en charge par les méthodes d’assistance disponibles, tel qu’un contrôle utilisateur personnalisé, utilisez les méthodes suivantes :  

-   Pour Excel, utilisez l’une des méthodes <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> d’un objet <xref:Microsoft.Office.Tools.Excel.ControlCollection> .  

-   Pour Word, utilisez l’une des méthodes <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> d’un objet <xref:Microsoft.Office.Tools.Word.ControlCollection> .  

 Pour ajouter le contrôle, transmettez la <xref:System.Windows.Forms.Control>, un emplacement pour le contrôle et un nom qui identifie de façon unique le contrôle à la `AddControl` (méthode). Le `AddControl` méthode retourne un objet qui définit la façon dont le contrôle interagit avec la feuille de calcul ou le document. Le `AddControl` méthode retourne un <xref:Microsoft.Office.Tools.Excel.ControlSite> (pour Excel) ou un <xref:Microsoft.Office.Tools.Word.ControlSite> objet (pour Word).  

 L’exemple de code suivant montre comment utiliser la méthode <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> pour ajouter dynamiquement un contrôle utilisateur personnalisé à une feuille de calcul dans un projet Excel au niveau du document. Dans cet exemple, le contrôle utilisateur est nommé `UserControl1`, et la <xref:Microsoft.Office.Interop.Excel.Range> est nommée `range1`. Pour utiliser cet exemple, exécutez-le à partir d’une classe `Sheet`*n* dans le projet.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="use-members-of-custom-controls"></a>Utilisez les membres de contrôles personnalisés  
 Après l’utilisation d’un de le `AddControl` les méthodes pour ajouter un contrôle à une feuille de calcul ou d’un document, vous pouvez maintenant avoir deux objets de contrôle différents :  

-   Le <xref:System.Windows.Forms.Control> qui représente le contrôle personnalisé.  

-   Le `ControlSite`, `OLEObject`, ou `OLEControl` objet qui représente le contrôle après qu’il a été ajouté à la feuille de calcul ou le document.  

 De nombreuses propriétés et méthodes sont partagées entre ces contrôles. Il est important que vous accédiez à ces membres via le contrôle approprié :  

-   Pour accéder aux membres qui appartiennent uniquement au contrôle personnalisé, utilisez le <xref:System.Windows.Forms.Control>.  

-   Pour accéder aux membres qui sont partagés par les contrôles, utilisez le `ControlSite`, `OLEObject`, ou `OLEControl` objet.  

 Si vous accédez à un membre partagé à partir du <xref:System.Windows.Forms.Control>, un échec peut survenir sans que vous soyez averti ou notifié, ou des résultats non valides peuvent être générés. Utilisez toujours les méthodes ou propriétés de la `ControlSite`, `OLEObject`, ou `OLEControl` objet, sauf si la méthode ou propriété nécessaire n’est pas disponible ; ensuite seulement vous devez référencez le <xref:System.Windows.Forms.Control>.  

 Par exemple, les deux le <xref:Microsoft.Office.Tools.Excel.ControlSite> classe et le <xref:System.Windows.Forms.Control> classe a un `Top` propriété. Pour obtenir ou définir la distance entre le haut du contrôle et le haut du document, utilisez la propriété <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> du <xref:Microsoft.Office.Tools.Excel.ControlSite>, et non la propriété <xref:System.Windows.Forms.Control.Top%2A> du <xref:System.Windows.Forms.Control>.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>Voir aussi  
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Conserver les contrôles dynamiques persistants dans des documents Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Comment : ajouter des contrôles ListObject aux feuilles de calcul](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Comment : ajouter des contrôles NamedRange aux feuilles de calcul](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Comment : ajouter des contrôles Chart aux feuilles de calcul](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Contrôles Windows Forms sur une vue d’ensemble des documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   

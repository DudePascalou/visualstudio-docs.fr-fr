---
title: 'Procédure pas à pas : Liaison de données à partir d’un Service dans un VSTO complément projet | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a89b9455051031b3faa0a44102f2fe97dca97d89
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project"></a>Procédure pas à pas : Liaison à des données de service dans un projet de complément VSTO
  Vous pouvez lier des données à des contrôles hôtes dans les projets de complément VSTO. Cette procédure pas à pas montre comment ajouter des contrôles à un document Microsoft Office Word, comment lier les contrôles aux données extraites du service de contenu MSDN et comment répondre aux événements au moment de l’exécution.  
  
 **S’applique à :** les informations contenues dans cette rubrique s’appliquent aux projets au niveau de l’application pour Word 2010. Pour plus d’informations, consultez [Fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Ajout d’un contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> à un document au moment du design.  
  
-   Liaison du contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> aux données à partir d’un service web.  
  
-   Réponse à l’événement <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> d’un contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> .  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] ou [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-a-new-project"></a>Création d'un projet  
 La première étape consiste à créer un projet de complément VSTO Word.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créez un projet de complément VSTO Word portant le nom **MTPS Content Service**, en Visual Basic ou C#.  
  
     Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio ouvre le fichier `ThisAddIn.vb` ou `ThisAddIn.cs` et ajoute le projet à l’ **Explorateur de solutions**.  
  
## <a name="adding-a-web-service"></a>Ajout d’un service web  
 Pour cette procédure pas à pas, utilisez un service web appelé MTPS Content Service. Ce service web retourne les informations d’un article MSDN spécifié sous la forme d’une chaîne XML ou de texte brut. Une étape ultérieure indique comment afficher les informations retournées dans un contrôle de contenu.  
  
#### <a name="to-add-the-mtps-content-service-to-the-project"></a>Pour ajouter MTPS Content Service au projet  
  
1.  Dans le menu **Données** , cliquez sur **Ajouter une nouvelle source de données**.  
  
2.  Dans l’ **Assistant Configuration de source de données**, cliquez sur **Service**, puis sur **Suivant**.  
  
3.  Dans le champ **Adresse** , tapez l’URL suivante :  
  
     **http://services.msdn.microsoft.com/ContentServices/ContentService.asmx**  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le champ **Espace de noms** , tapez **ContentService**, puis cliquez sur **OK**.  
  
6.  Dans la boîte de dialogue **Assistant Ajout de référence** , cliquez sur **Terminer**.  
  
## <a name="adding-a-content-control-and-binding-to-data-at-run-time"></a>Ajout d’un contrôle de contenu et liaison de données au moment de l’exécution  
 Dans les projets de complément VSTO, vous ajoutez et liez des contrôles au moment de l’exécution. Pour cette procédure pas à pas, configurez le contrôle de contenu pour extraire des données du service web quand un utilisateur clique sur le contrôle.  
  
#### <a name="to-add-a-content-control-and-bind-to-data"></a>Pour ajouter un contrôle de contenu et le lier à des données  
  
1.  Dans la classe `ThisAddIn` , déclarez les variables de MTPS Content Service, du contrôle de contenu et de la liaison de données.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]  
  
2.  Ajoutez la méthode suivante à la classe `ThisAddIn` . Cette méthode crée un contrôle de contenu au début du document actif.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]  
  
3.  Ajoutez la méthode suivante à la classe `ThisAddIn` . Cette méthode initialise les objets requis pour créer et envoyer une requête au service web.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]  
  
4.  Créez un gestionnaire d’événements pour extraire le document de la Bibliothèque MSDN sur les contrôles de contenu quand un utilisateur clique sur le contrôle de contenu et liez les données au contrôle de contenu.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]  
  
5.  Appelez les méthodes `AddRichTextControlAtRange` et `InitializeServiceObjects` à partir de la méthode `ThisAddIn_Startup` . Programmeurs C#, ajoutez un gestionnaire d’événements.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]  
  
## <a name="testing-the-add-in"></a>Test du complément  
 Quand vous ouvrez Word, le contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> apparaît. Le texte du contrôle change quand vous cliquez dessus.  
  
#### <a name="to-test-the-vsto-add-in"></a>Pour tester le complément VSTO  
  
1.  Appuyez sur **F5**.  
  
2.  Cliquez à l’intérieur du contrôle de contenu.  
  
     Les informations sont téléchargées depuis MTPS Content Service et elles s’affichent dans le contrôle de contenu.  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  
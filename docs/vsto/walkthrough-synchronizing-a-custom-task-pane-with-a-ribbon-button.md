---
title: 'Procédure pas à pas : Synchronisation d’un volet Office personnalisé avec un bouton de ruban | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom task panes [Office development in Visual Studio], showing and hiding
- showing custom task panes
- Ribbon [Office development in Visual Studio], custom task panes
- toggle buttons [Office development in Visual Studio]
- custom task panes [Office development in Visual Studio], synchronizing with Ribbon button
- user interfaces [Office development in Visual Studio], custom task panes
- synchronization [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], showing and hiding
- custom task panes [Office development in Visual Studio], creating
- hiding custom task panes
- task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio], synchronizing with Ribbon button
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ff3252a1ae234615cc4d4ed83a07d98a15092bee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button"></a>Procédure pas à pas : synchronisation d'un volet de tâches personnalisé avec un bouton dans le ruban
  Cette procédure pas à pas indique comment créer un volet Office personnalisé que les utilisateurs peuvent masquer ou afficher en cliquant sur un bouton bascule du ruban. Vous devez toujours créer un élément d’interface utilisateur, comme un bouton, sur lequel les utilisateurs peuvent cliquer pour afficher ou masquer le volet Office personnalisé. En effet, les applications Microsoft Office ne proposent aucune méthode par défaut permettant aux utilisateurs d’afficher ou de masquer des volets Office personnalisés.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Cette procédure pas à pas utilise spécifiquement Excel. Toutefois, les concepts qui y sont présentés sont applicables à toutes les applications susmentionnées.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Conception de l’interface utilisateur du volet Office personnalisé.  
  
-   Ajout d’un bouton bascule au ruban.  
  
-   Synchronisation du bouton bascule avec le volet Office personnalisé.  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel ou Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)].  
  
## <a name="creating-the-add-in-project"></a>Création du projet de complément  
 Dans cette étape, vous allez créer un projet de complément VSTO pour Excel.  
  
#### <a name="to-create-a-new-project"></a>Pour créer un projet  
  
1.  Créez un projet de complément Excel nommé **SynchroniserVoletOfficeEtRuban**à l’aide du modèle de projet de complément Excel. Pour plus d'informations, consultez [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le fichier de code **ThisAddIn.cs** ou **ThisAddIn.vb** et ajoute le projet **SynchroniserVoletOfficeEtRuban** dans l’ **Explorateur de solutions**.  
  
## <a name="adding-a-toggle-button-to-the-ribbon"></a>Ajout d’un bouton bascule au ruban.  
 L'une des règles de conception d'une application Office stipule que les utilisateurs doivent toujours avoir le contrôle de l'interface utilisateur de l'application Office. Pour permettre aux utilisateurs de contrôler le volet Office personnalisé, vous pouvez ajouter un bouton bascule au ruban permettant d’afficher et de masquer le volet Office. Pour créer un bouton bascule, ajoutez un élément **Ruban (Concepteur visuel)** au projet. Le concepteur vous permet d'ajouter et de position des contrôles, de définir les propriétés des contrôles et de gérer les événements de contrôle. Pour plus d'informations, consultez [Ribbon Designer](../vsto/ribbon-designer.md).  
  
#### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Pour ajouter un bouton bascule au ruban  
  
1.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Ruban (Concepteur visuel)**.  
  
3.  Remplacez le nom du nouveau ruban par **ManageTaskPaneRibbon**, puis cliquez sur **Ajouter**.  
  
     Le fichier **ManageTaskPaneRibbon.cs** ou **ManageTaskPaneRibbon.vb** s’ouvre dans le Concepteur de ruban et affiche un onglet et un groupe par défaut.  
  
4.  Dans le Concepteur de ruban, cliquez sur **group1**.  
  
5.  Dans la fenêtre **Propriétés** , définissez la propriété **Label** sur la valeur **Gestionnaire de volets Office**.  
  
6.  Sous l’onglet **Contrôles de ruban Office** de la **boîte à outils**, faites glisser un contrôle **ToggleButton** dans le groupe **Gestionnaire de volets Office** .  
  
7.  Cliquez sur **toggleButton1**.  
  
8.  Dans la fenêtre **Propriétés** , affectez à la propriété **Label** la valeur **Afficher le Volet Office**.  
  
## <a name="designing-the-user-interface-of-the-custom-task-pane"></a>Conception de l’interface utilisateur du volet Office personnalisé  
 Il n’existe aucun concepteur visuel pour les volets Office personnalisés. Toutefois, vous pouvez concevoir un contrôle utilisateur avec la disposition de votre choix. Ultérieurement dans cette procédure, vous ajouterez le contrôle utilisateur au volet Office personnalisé.  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Pour concevoir l’interface utilisateur du volet Office personnalisé  
  
1.  Dans le menu **Projet** , cliquez sur **Ajouter un contrôle utilisateur**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , remplacez le nom du nouveau contrôle utilisateur par **ContrôleVoletOffice**, puis cliquez sur **Ajouter**.  
  
     Le contrôle utilisateur s'ouvre dans le concepteur.  
  
3.  Sous l’onglet **Contrôles communs** de la **boîte à outils**, faites glisser un contrôle **TextBox** vers le contrôle utilisateur.  
  
## <a name="creating-the-custom-task-pane"></a>Création du volet Office personnalisé  
 Pour créer le volet Office personnalisé au démarrage du complément VSTO, ajoutez le contrôle utilisateur au volet Office dans le gestionnaire d’événements <xref:Microsoft.Office.Tools.AddIn.Startup> du complément VSTO. Par défaut, le volet Office personnalisé n’est pas visible. Ultérieurement dans cette procédure, vous ajouterez un code pour afficher ou masquer le volet Office lorsque l’utilisateur clique sur le bouton bascule ajouté au ruban.  
  
#### <a name="to-create-the-custom-task-pane"></a>Pour créer le volet Office personnalisé  
  
1.  Dans l' **Explorateur de solutions**, développez **Excel**.  
  
2.  Cliquez avec le bouton droit sur **ThisAddIn.cs** ou **ThisAddIn.vb** , puis cliquez sur **Afficher le code**.  
  
3.  Ajoutez le code suivant à la classe `ThisAddIn` . Ce code déclare une instance de `TaskPaneControl` en tant que membre de `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]  
  
4.  Remplacez le gestionnaire d'événements `ThisAddIn_Startup` par le code suivant. Ce code ajoute l’objet `TaskPaneControl` au champ `CustomTaskPanes` , mais il n’affiche pas le volet Office personnalisé (par défaut, la propriété <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> de la classe <xref:Microsoft.Office.Tools.CustomTaskPane> a la valeur **false**). Le code Visual C# attache un gestionnaire d’événements à l’événement <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> .  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]  
  
5.  Ajoutez la méthode suivante à la classe `ThisAddIn` . Cette méthode gère l’événement <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> . Lorsque l’utilisateur ferme le volet Office en cliquant sur le bouton **Fermer** (X), cette méthode met à jour l’état du bouton bascule sur le ruban.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]  
  
6.  Ajoutez la propriété suivante à la classe `ThisAddIn` . Cette propriété expose l’objet privé `myCustomTaskPane1` à d’autres classes. Ultérieurement dans cette procédure, vous ajouterez du code à la classe `MyRibbon` qui utilise cette propriété.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]  
  
## <a name="hiding-and-showing-the-custom-task-pane-by-using-the-toggle-button"></a>Masquage et affichage du volet Office personnalisé à l’aide du bouton bascule  
 La dernière étape consiste à ajouter du code permettant d’afficher ou masquer le volet Office personnalisé lorsque l’utilisateur clique sur le bouton bascule du ruban.  
  
#### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>Pour afficher et masquer le volet Office personnalisé à l’aide du bouton bascule  
  
1.  Dans le Concepteur de ruban, double-cliquez sur le bouton bascule **Afficher le Volet Office** .  
  
     Visual Studio génère automatiquement un gestionnaire d’événements nommé `toggleButton1_Click`, qui gère l’événement <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> du bouton bascule. Visual Studio ouvre également le fichier **MyRibbon.cs** ou **MyRibbon.vb** dans l’éditeur de code  
  
2.  Remplacez le gestionnaire d'événements `toggleButton1_Click` par le code suivant. Lorsque l’utilisateur clique sur le bouton bascule, ce code affiche ou masque le volet Office personnalisé, selon l’état du bouton bascule (activé ou désactivé).  
  
     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]  
  
## <a name="testing-the-add-in"></a>Test du complément  
 Lorsque vous exécutez le projet, Excel s’ouvre sans afficher le volet Office personnalisé. Cliquez sur le bouton bascule du ruban pour tester le code.  
  
#### <a name="to-test-your-vsto-add-in"></a>Pour tester votre complément VSTO  
  
1.  Appuyez sur F5 pour exécuter votre projet.  
  
     Vérifiez qu’Excel s’ouvre et que l’onglet **Compléments** figure sur le ruban.  
  
2.  Cliquez sur l'onglet **Compléments** du ruban.  
  
3.  Dans le groupe **Gestionnaire de volets de tâches** , cliquez sur le bouton bascule **Afficher le Volet Office** .  
  
     Vérifiez que le volet Office est alternativement affiché et masqué lorsque vous cliquez sur le bouton bascule.  
  
4.  Lorsque le volet Office est visible, cliquez sur le bouton **Fermer** (X) dans le coin du volet Office.  
  
     Vérifiez que le bouton bascule n’est pas enfoncé.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour en savoir plus sur la création de volets Office personnalisés, consultez les rubriques suivantes :  
  
-   Créer un volet Office personnalisé dans un complément VSTO pour une autre application. Pour plus d’informations sur les applications qui prennent en charge les volets de tâches personnalisés, consultez [les volets de tâches personnalisés](../vsto/custom-task-panes.md).  
  
-   Automatiser une application à partir d’un volet Office personnalisé Pour plus d'informations, consultez [Procédure pas à pas : automatisation d'une application à partir d'un volet de tâches personnalisé](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Créer un volet Office personnalisé pour chaque message électronique ouvert dans Outlook. Pour plus d'informations, consultez [Procédure pas à pas : affichage de volets des tâches personnalisés avec des messages électroniques dans Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Volets de tâches personnalisés](../vsto/custom-task-panes.md)   
 [Comment : ajouter un volet Office personnalisé à une Application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Procédure pas à pas : Automatisation d’une Application à partir d’un volet Office personnalisé](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Procédure pas à pas : Affichage de volets de tâches personnalisés avec des Messages électroniques dans Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)   
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)  
  
  
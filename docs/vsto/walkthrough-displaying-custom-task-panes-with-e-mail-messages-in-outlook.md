---
title: 'Walkthrough: Displaying Custom Task Panes with E-Mail Messages in Outlook | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
ms.assetid: 04943967-a7ef-4876-9584-84ada427e3f3
caps.latest.revision: 59
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 0487a8842e8e5ec2fed0006937fd9d5b38e051cf
ms.contentlocale: fr-fr
ms.lasthandoff: 08/30/2017

---
# <a name="walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook"></a>Walkthrough: Displaying Custom Task Panes with E-Mail Messages in Outlook
  This walkthrough demonstrates how to display a unique instance of a custom task pane with each e-mail message that is created or opened. Users can display or hide the custom task pane by using a button on the Ribbon of each e-mail message.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 To display a custom task pane with multiple Explorer or Inspector windows, you must create an instance of the custom task pane for every window that is opened. For more information about the behavior of custom task panes in Outlook windows, see [Custom Task Panes](../vsto/custom-task-panes.md).  
  
> [!NOTE]  
>  This walkthrough presents the VSTO Add-in code in small sections to make it easier to discuss the logic behind the code.  
  
 This walkthrough illustrates the following tasks:  
  
-   Designing the user interface (UI) of the custom task pane.  
  
-   Creating a custom Ribbon UI.  
  
-   Displaying the custom Ribbon UI with e-mail messages.  
  
-   Creating a class to manage Inspector windows and custom task panes.  
  
-   Initializing and cleaning up resources used by the VSTO Add-in.  
  
-   Synchronizing the Ribbon toggle button with the custom task pane.  
  
> [!NOTE]  
>  Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions. The Visual Studio edition that you have and the settings that you use determine these elements. For more information, see [Personalize the Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisites  
 You need the following components to complete this walkthrough:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] or Microsoft Outlook 2010.  
  
 ![link to video](../vsto/media/playvideo.gif "link to video") For a related video demonstration, see [How Do I: Use Task Panes in Outlook?](http://go.microsoft.com/fwlink/?LinkID=130309).  
  
## <a name="creating-the-project"></a>Creating the Project  
 Custom task panes are implemented in VSTO Add-ins. Start by creating an VSTO Add-in project for Outlook.  
  
#### <a name="to-create-a-new-project"></a>To create a new project  
  
1.  Create an **Outlook Add-in** project with the name **OutlookMailItemTaskPane**. Use the **Outlook Add-in** project template. For more information, see [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] opens the **ThisAddIn.cs** or **ThisAddIn.vb** code file and adds the **OutlookMailItemTaskPane** project to **Solution Explorer**.  
  
## <a name="designing-the-user-interface-of-the-custom-task-pane"></a>Designing the User Interface of the Custom Task Pane  
 There is no visual designer for custom task panes, but you can design a user control with the UI you want. The custom task pane in this VSTO Add-in has a simple UI that contains a <xref:System.Windows.Forms.TextBox> control. Later in this walkthrough, you will add the user control to the custom task pane.  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>To design the user interface of the custom task pane  
  
1.  In **Solution Explorer**, click the **OutlookMailItemTaskPane** project.  
  
2.  On the **Project** menu, click **Add User Control**.  
  
3.  In the **Add New Item** dialog box, change the name of the user control to **TaskPaneControl**, and then click **Add**.  
  
     The user control opens in the designer.  
  
4.  From the **Common Controls** tab of the **Toolbox**, drag a **TextBox** control to the user control.  
  
## <a name="designing-the-user-interface-of-the-ribbon"></a>Designing the User Interface of the Ribbon  
 One of the goals for this VSTO Add-in is to give users a way to hide or display the custom task pane from the Ribbon of each e-mail message. To provide the user interface, create a custom Ribbon UI that displays a toggle button that users can click to display or hide the custom task pane.  
  
#### <a name="to-create-a-custom-ribbon-ui"></a>To create a custom Ribbon UI  
  
1.  On the **Project** menu, click **Add New Item**.  
  
2.  In the **Add New Item** dialog box, select **Ribbon (Visual Designer)**.  
  
3.  Change the name of the new Ribbon to **ManageTaskPaneRibbon**, and click **Add**.  
  
     The **ManageTaskPaneRibbon.cs** or **ManageTaskPaneRibbon.vb** file opens in the Ribbon Designer and displays a default tab and group.  
  
4.  In the Ribbon Designer, click **group1**.  
  
5.  In the **Properties** window, set the **Label** property to **Task Pane Manager**.  
  
6.  From the **Office Ribbon Controls** tab of the **Toolbox**, drag a ToggleButton control onto the **Task Pane Manager** group.  
  
7.  Click **toggleButton1**.  
  
8.  In the **Properties** window, set the **Label** property to **Show Task Pane**.  
  
## <a name="display-the-custom-ribbon-user-interface-with-e-mail-messages"></a>Display the Custom Ribbon User Interface with E-Mail Messages  
 The custom task pane that you create in this walkthrough is designed to appear only with Inspector windows that contain e-mail messages. Therefore, set the properties to display your custom Ribbon UI only with these windows.  
  
#### <a name="to-display-the-custom-ribbon-ui-with-e-mail-messages"></a>To display the custom Ribbon UI with e-mail messages  
  
1.  In the Ribbon Designer, click the **ManageTaskPaneRibbon** Ribbon.  
  
2.  In the **Properties** window, click the drop-down list next to **RibbonType**, and select **Microsoft.Outlook.Mail.Compose** and **Microsoft.Outlook.Mail.Read**.  
  
## <a name="creating-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Creating a Class to Manage Inspector Windows and Custom Task Panes  
 There are several cases in which the VSTO Add-in must identify which custom task pane is associated with a specific e-mail message. These cases include the following:  
  
-   When the user closes an e-mail message. In this case, the VSTO Add-in must remove the corresponding custom task pane to ensure that resources used by the VSTO Add-in are cleaned up correctly.  
  
-   When the user closes the custom task pane. In this case, the VSTO Add-in must update the state of the toggle button on the Ribbon of the e-mail message.  
  
-   When the user clicks the toggle button on the Ribbon. In this case, the VSTO Add-in must hide or display the corresponding task pane.  
  
 To enable the VSTO Add-in to keep track of which custom task pane is associated with each open e-mail message, create a custom class that wraps pairs of <xref:Microsoft.Office.Interop.Outlook.Inspector> and <xref:Microsoft.Office.Tools.CustomTaskPane> objects. This class creates a new custom task pane object for each e-mail message, and it deletes the custom task pane when the corresponding e-mail message is closed.  
  
#### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>To create a class to manage Inspector windows and custom task panes  
  
1.  In **Solution Explorer**, right-click the **ThisAddIn.cs** or **ThisAddIn.vb** file, and then click **View Code**.  
  
2.  Add the following statements to the top of the file.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]  [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]  
  
3.  Add the following code to the **ThisAddIn.cs** or **ThisAddIn.vb** file, outside the `ThisAddIn` class (for Visual C#, add this code inside the `OutlookMailItemTaskPane` namespace). The `InspectorWrapper` class manages a pair of <xref:Microsoft.Office.Interop.Outlook.Inspector> and <xref:Microsoft.Office.Tools.CustomTaskPane> objects. You will complete the definition of this class in the following steps.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]  [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]  
  
4.  Add the following constructor after the code that you added in the previous step. This constructor creates and initializes a new custom task pane that is associated with the <xref:Microsoft.Office.Interop.Outlook.Inspector> object that is passed in. In C#, the constructor also attaches event handlers to the <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> event of the <xref:Microsoft.Office.Interop.Outlook.Inspector> object and to the <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> event of the <xref:Microsoft.Office.Tools.CustomTaskPane> object.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]  [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]  
  
5.  Add the following method after the code that you added in the previous step. This method is an event handler for the <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> event of the <xref:Microsoft.Office.Tools.CustomTaskPane> object that is contained in the `InspectorWrapper` class. This code updates the state of the toggle button whenever the user opens or closes the custom task pane.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]  [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]  
  
6.  Add the following method after the code that you added in the previous step. This method is an event handler for the <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> event of the <xref:Microsoft.Office.Interop.Outlook.Inspector> object that contains the current e-mail message. The event handler frees resources when the e-mail message is closed. The event handler also removes the current custom task pane from the `CustomTaskPanes` collection. This helps prevent multiple instances of the custom task pane when the next e-mail message is opened.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]  [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]  
  
7.  Add the following code after the code that you added in the previous step. Later in this walkthrough, you will call this property from a method in the custom Ribbon UI to display or hide the custom task pane.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]  [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]  
  
## <a name="initializing-and-cleaning-up-resources-used-by-the-add-in"></a>Initializing and Cleaning Up Resources Used by the Add-In  
 Add code to the `ThisAddIn` class to initialize the VSTO Add-in when it is loaded, and to clean up resources used by the VSTO Add-in when it is unloaded. You initialize the VSTO Add-in by setting up an event handler for the <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> event and by passing all existing e-mail messages to this event handler. When the VSTO Add-in is unloaded, detach the event handler and clean up objects used by the VSTO Add-in.  
  
#### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>To initialize and clean up resources used by the VSTO Add-in  
  
1.  In the **ThisAddIn.cs** or **ThisAddIn.vb** file, locate the definition of the `ThisAddIn` class.  
  
2.  Add the following declarations to the `ThisAddIn` class:  
  
    -   The `inspectorWrappersValue` field contains all the <xref:Microsoft.Office.Interop.Outlook.Inspector> and `InspectorWrapper` objects that are managed by the VSTO Add-in.  
  
    -   The `inspectors` field maintains a reference to the collection of Inspector windows in the current Outlook instance. This reference prevents the garbage collector from freeing the memory that contains the event handler for the <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> event, which you will declare in the next step.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)] [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]  
  
3.  Replace the `ThisAddIn_Startup` method with the following code. This code attaches an event handler to the <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> event, and it passes every existing <xref:Microsoft.Office.Interop.Outlook.Inspector> object to the event handler. If the user loads the VSTO Add-in after Outlook is already running, the VSTO Add-in uses this information to create custom task panes for all e-mail messages that are already open.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]  [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]  
  
4.  Replace the `ThisAddIn_ShutDown` method with the following code. This code detaches the <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> event handler and cleans up objects used by the VSTO Add-in.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]  [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]  
  
5.  Add the following <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> event handler to the `ThisAddIn` class. If a new <xref:Microsoft.Office.Interop.Outlook.Inspector> contains an e-mail message, the method creates an instance of a new `InspectorWrapper` object to manage the relationship between the e-mail message and the corresponding task pane.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]  [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]  
  
6.  Add the following property to the `ThisAddIn` class. This property exposes the private `inspectorWrappersValue` field to code outside the `ThisAddIn` class.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]  [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Build your project to ensure that it compiles without errors.  
  
#### <a name="to-build-your-project"></a>To build your project  
  
1.  In **Solution Explorer**, right-click the **OutlookMailItemTaskPane** project and then click **Build**. Verify that the project compiles without errors.  
  
## <a name="synchronizing-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Synchronizing the Ribbon Toggle Button with the Custom Task Pane  
 The toggle button will appear to be pressed in when the task pane is visible, and it will appear to be not pressed in when the task pane is hidden. To synchronize the state of the button with the custom task pane, modify the <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> event handler of the toggle button.  
  
#### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>To synchronize the custom task pane with the toggle button  
  
1.  In the Ribbon Designer, double-click the **Show Task Pane** toggle button.  
  
     Visual Studio automatically generates an event handler named `toggleButton1_Click`, which handles the <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> event of the toggle button. Visual Studio also opens the **ManageTaskPaneRibbon.cs** or **ManageTaskPaneRibbon.vb** file in the Code Editor.  
  
2.  Add the following statements to the top of the **ManageTaskPaneRibbon.cs** or **ManageTaskPaneRibbon.vb** file.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]  [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]  
  
3.  Replace the `toggleButton1_Click` event handler with the following code. When the user clicks the toggle button, this method hides or displays the custom task pane that is associated with the current Inspector window.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]  [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]  
  
## <a name="testing-the-project"></a>Testing the Project  
 When you start debugging the project, Outlook opens and the VSTO Add-in is loaded. The VSTO Add-in displays a unique instance of the custom task pane with each e-mail message that is opened. Create several new e-mail messages to test the code.  
  
#### <a name="to-test-the-vsto-add-in"></a>To test the VSTO Add-in  
  
1.  Press F5.  
  
2.  In Outlook, click **New** to create a new e-mail message.  
  
3.  On the Ribbon of the e-mail message, click the **Add-Ins** tab, and then click the **Show Task Pane** button.  
  
     Verify that a task pane with the title **My task pane** is displayed with the e-mail message.  
  
4.  In the task pane, type **First task pane** in the text box.  
  
5.  Close the task pane.  
  
     Verify that the state of the **Show Task Pane** button changes so that it is no longer pressed.  
  
6.  Click the **Show Task Pane** button again.  
  
     Verify that the task pane opens, and that the text box still contains the string **First task pane**.  
  
7.  In Outlook, click **New** to create a second e-mail message.  
  
8.  On the Ribbon of the e-mail message, click the **Add-Ins** tab, and then click the **Show Task Pane** button.  
  
     Verify that a task pane with the title **My task pane** is displayed with the e-mail message, and the text box in this task pane is empty.  
  
9. In the task pane, type **Second task pane** in the text box.  
  
10. Change focus to the first e-mail message.  
  
     Verify that the task pane that is associated with this e-mail message still displays **First task pane** in the text box.  
  
 This VSTO Add-in also handles more advanced scenarios that you can try. For example, you can test the behavior when viewing e-mails by using the **Next Item** and **Previous Item** buttons. You can also test the behavior when you unload the VSTO Add-in, open several e-mail messages, and then reload the VSTO Add-in.  
  
## <a name="next-steps"></a>Next Steps  
 You can learn more about how to create custom task panes from these topics:  
  
-   Create a custom task pane in an VSTO Add-in for a different application. For more information about the applications that support custom task panes, see [Custom Task Panes](../vsto/custom-task-panes.md).  
  
-   Automate a Microsoft Office application by using a custom task pane. For more information, see [Walkthrough: Automating an Application from a Custom Task Pane](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Create a Ribbon button in Excel that can be used to hide or display a custom task pane. For more information, see [Walkthrough: Synchronizing a Custom Task Pane with a Ribbon Button](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
## <a name="see-also"></a>See Also  
 [Custom Task Panes](../vsto/custom-task-panes.md)   
 [How to: Add a Custom Task Pane to an Application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Walkthrough: Automating an Application from a Custom Task Pane](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Walkthrough: Synchronizing a Custom Task Pane with a Ribbon Button](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Ribbon Overview](../vsto/ribbon-overview.md)   
 [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)   
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  
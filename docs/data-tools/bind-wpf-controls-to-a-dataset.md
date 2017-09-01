---
title: Bind WPF controls to a dataset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 32
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 9b510e4bc3bee3eb7585a93cc643a2ea0da62900
ms.contentlocale: fr-fr
ms.lasthandoff: 08/30/2017

---
# <a name="bind-wpf-controls-to-a-dataset"></a>Bind WPF controls to a dataset
In this walkthrough, you will create a WPF application that contains data-bound controls. The controls are bound to product records that are encapsulated in a dataset. You will also add buttons to browse through products and save changes to product records.  
  
This walkthrough illustrates the following tasks:  
  
- Creating a WPF application and a dataset that is generated from data in the AdventureWorksLT sample database.  
  
- Creating a set of data-bound controls by dragging a data table from the **Data Sources** window to a window in the WPF Designer.  
  
- Creating buttons that navigate forward and backward through product records.  
  
- Creating a button that saves changes that users make to the product records to the data table and the underlying data source.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Prerequisites  
You need the following components to complete this walkthrough:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorksLT sample database attached to it. You can download the AdventureWorksLT database from the [CodePlex Web site](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 Prior knowledge of the following concepts is also helpful, but not required to complete the walkthrough:  
  
-   Datasets and TableAdapters. For more information, see [Dataset tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) and [TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
-   Working with the WPF Designer. For more information, see [WPF and Silverlight Designer Overview](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   WPF data binding. For more information, see [Data Binding Overview](/dotnet/framework/wpf/data/data-binding-overview).  
  
## <a name="create-the-project"></a>Create the project  
 Create a new WPF project. The project will display product records.  
  
#### <a name="to-create-the-project"></a>To create the project  
  
1.  Start Visual Studio.  
  
2.  On the **File** menu, point to **New**, and then click **Project**.  
  
3.  Expand **Visual Basic** or **Visual C#**, and then select **Windows**.  
  
4.  Select the **WPF Application** project template.  
  
5.  In the **Name** box, type `AdventureWorksProductsEditor` and click **OK**.  
  
     Visual Studio creates the `AdventureWorksProductsEditor` project.  
  
## <a name="create-a-dataset-for-the-application"></a>Create a dataset for the application  
 Before you can create data-bound controls, you must define a data model for your application and add it to the **Data Sources** window. In this walkthrough, you create a dataset to use as the data model.  
  
#### <a name="to-create-a-dataset"></a>To create a dataset  
  
1.  On the **Data** menu, click **Show Data Sources**.  
  
     The **Data Sources** window opens.  
  
2.  In the **Data Sources** window, click **Add New Data Source**.  
  
     The **Data Source Configuration** wizard opens.  
  
3.  On the **Choose a Data Source Type** page, select **Database**, and then click **Next**.  
  
4.  On the **Choose a Database Model** page, select **Dataset**, and then click **Next**.  
  
5.  On the **Choose Your Data Connection** page, select one of the following options:  
  
    -   If a data connection to the AdventureWorksLT sample database is available in the drop-down list, select it and then click **Next**.  
  
    -   Click **New Connection**, and create a connection to the AdventureWorksLT database.  
  
6.  On the **Save the Connection String to the Application Configure File** page, select the **Yes, save the connection as** check box, and then click **Next**.  
  
7.  On the **Choose Your Database Objects** page, expand **Tables**, and then select the **Product (SalesLT)** table.  
  
8.  Click **Finish**.  
  
     Visual Studio adds a new `AdventureWorksLTDataSet.xsd` file to the project, and it adds a corresponding **AdventureWorksLTDataSet** item to the **Data Sources** window. The `AdventureWorksLTDataSet.xsd` file defines a typed dataset named `AdventureWorksLTDataSet` and a TableAdapter named `ProductTableAdapter`. Later in this walkthrough, you will use the `ProductTableAdapter` to fill the dataset with data and save changes back to the database.  
  
9. Build the project.  
  
## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Edit the default fill method of the TableAdapter  
 To fill the dataset with data, use the `Fill` method of the `ProductTableAdapter`. By default, the `Fill` method fills the `ProductDataTable` in the `AdventureWorksLTDataSet` with all rows of data from the Product table. You can modify this method to return only a subset of the rows. For this walkthrough, modify the `Fill` method to return only rows for products that have photos.  
  
#### <a name="to-load-product-rows-that-have-photos"></a>To load product rows that have photos  
  
1.  In **Solution Explorer**, double-click the `AdventureWorksLTDataSet.xsd` file.  
  
     The Dataset designer opens.  
  
2.  In the designer, right-click the **Fill, GetData()** query and select **Configure**.  
  
     The **TableAdapter Configuration** wizard opens.  
  
3.  In the **Enter a SQL Statement** page, add the following WHERE clause after the `SELECT` statement in the text box.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  Click **Finish**.  
  
## <a name="define-the-user-interface"></a>Define the user interface  
 Add several buttons to the window by modifying the XAML in the WPF Designer. Later in this walkthrough, you will add code that enables users to scroll through and save changes to products records by using these buttons.  
  
#### <a name="to-define-the-user-interface-of-the-window"></a>To define the user interface of the window  
  
1.  In **Solution Explorer**, double-click MainWindow.xaml.  
  
     The window opens in the WPF Designer.  
  
2.  In the [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] view of the designer, add the following code between the `<Grid>` tags:  
  
    ```xaml  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Build the project.  
  
## <a name="create-data-bound-controls"></a>Create data-bound controls  
 Create controls that display customer records by dragging the `Product` table from the **Data Sources** window to the WPF Designer.  
  
#### <a name="to-create-data-bound-controls"></a>To create data-bound controls  
  
1.  In the **Data Sources** window, click the drop-down menu for the **Product** node and select **Details**.  
  
2.  Expand the **Product** node.  
  
3.  For this example, some fields will not be displayed, so click the drop-down menu next to the following nodes and select **None**:  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   rowguid  
  
    -   ModifiedDate  
  
4.  Click the drop-down menu next to the **ThumbNailPhoto** node and select **Image**.  
  
    > [!NOTE]
    >  By default, items in the **Data Sources** window that represent pictures have their default control set to **None**. This is because pictures are stored as byte arrays in databases, and byte arrays can contain anything from a simple array of bytes to the executable file of a large application.  
  
5.  From the **Data Sources** window, drag the **Product** node to the grid row under the row that contains the buttons.  
  
     Visual Studio generates XAML that defines a set of controls that are bound to data in the **Products** table. It also generates code that loads the data. For more information about the generated XAML and code, see [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
6.  In the designer, click the text box next to the **Product ID** label.  
  
7.  In the **Properties** window, select the check box next to the **IsReadOnly** property.  
  
## <a name="navigating-product-records"></a>Navigating product records  
 Add code that enables users to scroll through product records by using the **\<** and **>** buttons.  
  
#### <a name="to-enable-users-to-navigate-product-records"></a>To enable users to navigate product records  
  
1.  In the designer, double-click the **<** button on the window surface.  
  
     Visual Studio opens the code-behind file, and creates a new `backButton_Click` event handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.  
  
2.  Modify the `Window_Loaded` event handler, so the `ProductViewSource`, `AdventureWorksLTDataSet`, and `AdventureWorksLTDataSetProductTableAdapter` are outside of the method and accessible to the entire form. Declare only these to be global to the form, and assign them within the `Window_Loaded` event handler similar to the following:  
  
     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]  [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]  
  
3.  Add the following code to the `backButton_Click` event handler:  
  
     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]  [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]  
  
4.  Return to the designer and double-click the **>** button.  
  
5.  Add the following code to the `nextButton_Click` event handler:  
  
     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]  [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]  
  
## <a name="save-changes-to-product-records"></a>Save changes to product records  
Add code that enables users to save changes to product records by using the **Save changes** button.  
  
#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>To add the ability to save changes to product records  
  
1.  In the designer, double-click the **Save changes** button.  
  
     Visual Studio opens the code-behind file, and creates a new `saveButton_Click` event handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.  
  
2.  Add the following code to the `saveButton_Click` event handler:  
  
     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]  [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]  
  
    > [!NOTE]
    >  This example uses the `Save` method of the `TableAdapter` to save the changes. This is appropriate in this walkthrough, because only one data table is being changed. If you need to save changes to multiple data tables, you can alternatively use the `UpdateAll` method of the `TableAdapterManager` that Visual Studio generates with your dataset. For more information, see [TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
## <a name="test-the-application"></a>Test the application  
 Build and run the application. Verify that you can view and update product records.  
  
#### <a name="to-test-the-application"></a>To test the application  
  
1.  Press **F5**.  
  
     The application builds and runs. Verify the following:  
  
    -   The text boxes display data from the first product record that has a photo. This product has the product ID 713, and the name **Long-Sleeve Logo Jersey, S**.  
  
    -   You can click the **>** or **<** buttons to navigate through other product records.  
  
2.  In one of the product records, change the **Size** value, and then click **Save changes**.  
  
3.  Close the application, and then restart the application by pressing **F5** in Visual Studio.  
  
4.  Navigate to the product record you changed, and verify that the change persisted.  
  
5.  Close the application.  
  
## <a name="next-steps"></a>Next Steps  
 After completing this walkthrough, you can perform the following related tasks:  
  
-   Learn how to use the **Data Sources** window in Visual Studio to bind WPF controls to other types of data sources. For more information, see [Bind WPF controls to a WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
-   Learn how to use the **Data Sources** window in Visual Studio to display related data (that is, data in a parent-child relationship) in WPF controls. For more information, see [Walkthrough: Displaying Related Data in a WPF Application](../data-tools/display-related-data-in-wpf-applications.md).  
  
## <a name="see-also"></a>See Also  
 [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
 [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
 [Dataset tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [WPF and Silverlight Designer Overview](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Data Binding Overview](/dotnet/framework/wpf/data/data-binding-overview)
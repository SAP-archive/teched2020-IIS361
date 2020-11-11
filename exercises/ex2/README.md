Exercise 2 - Configure Content Area in Analytical List Page
============================================================

In this exercise, you will define the content area of the Analytical List Page with Fiori Guided Development. For this, you first have to open the Guided Development tool.

![](media/image1.png)

(1) Click **View**.

![](media/image2.png)

(2) Click **Find Command...**

![](media/image3.png)

(3) Type a few characters to filter out the list, for example **gu**.

![](media/image4.png)

(4) Click **Fiori: Open Guided Development**.

Guided development tool opens for your project as long as this is the only project in your workspace. If you already have multiple projects in your workspace, you will be asked to choose one. In this case, choose application project you have created in the previous exercise.

Exercise 2.1 Configuring Table
------------------------------

In this exercise, you will configure the columns displayed in the table of the Analytical List Page. UI annotation 'LineItem' is used to represent the table, with DataField records representing the columns. As you will use the Guided Development tool, you do not need to add this annotation manually, just follow the steps below to configure the table and the respective annotation will be added to or updated in the local annotation file when you choose apply.

![](media/image5.png)

(5) To find the guides related to tables, type **table** in the search field

![](media/image6.png)

(6) Scroll to the Analytical List Page guides and expand the guide  **Add a new column to a table** ![](media/image7.png) .

![](media/image8.png)

(7) Read the description and click **Start Guide**.

This simple guide contains just one step adding a column (DataField record) to your table (LineItem). You can repeat this step as many times as needed to add all the columns to the table. If the table (LineItem) is not yet defined in your app, it will be created along with the first column.

![](media/image9.png)

(8)  In the Entity Type field, choose your main entity type **Z_SEPMRA_SO_SALESORDERANALYSIS**.

![](media/image10.png)

(9) In the **Property** field, choose **Delivery Calendar Year** as your first column content. The code snippet will be adjusted accordingly

![](media/image11.png)

(10) Click **Apply**.

![](media/image12.png)

Annotation UI.LineItem is added to your local annotation file as configured in the code snippet. This file gets open next to the Guided Development tool.

Note: if you need more horizontal space, double-click on the **Guided Development** tab.

Now repeat steps (9) and (10) to add the records (columns) for following properties:

-   DeliveryCalendarMonth

-   SalesOrder

-   SalesOrderItem

-   Product

-   MainProductCategory

-   SoldToParty

-   Quantity

-   NetAmount

![](media/image13.png)

(11) When the records for all property are added to your LineItem, click **Exit Guide** to get back to the list of available guides.

Exercise 2.2 Configuring Chart 
------------------------------

In this exercise, you will configure the chart to be displayed in the Analytical List Page. Annotation Term /"UI.Chart\" is used to visualize the data in the chart format. As you will use the Guided Development tool, you do not need to add this annotation manually, just follow the steps below to configure the chart and the respective annotation will be added to or updated in the local annotation file when you choose apply.

![](media/image14.png)

(12) Filter by chart in the search field and expand the guide **Add an interactive chart** ![](media/image15.png) in the **Analytical List Page** group.

![](media/image16.png)

(13) Click **Start Guide**.

![](media/image17.png)

(14) Enter the following values:
| **Field**           | **Value** 
| ------------------- | ------------- 
| Entity Type         | SEPMRA_SO_SALESORDERANALYSISType  
| Chart Title         | Revenue by Customer
| Chart Description   | Net Revenue by Customer 
| ChartType           | Column  
| Measure property    | NetAmount
| Dimensions Property | SoldToParty
| Dimensions Property | DeliveryCalendarYear


![](media/image18.png)

(15) Click **Apply**. UI.Chart annotation is added to your local annotation file as configured in the code snippet.

**Exercise 2.3 Configuring Presentation Variant**
-------------------------------------------------

In this exercise, you will configure a UI.PresentationVariant annotation that is used to display the main content of the Analytical List Page. Here you will assign the chart and table created earlier in this exercise as visualization artifacts and define the sorting order. To do so, you will use the step 2 of the Add interactive chart guide.

![](media/image19.png)

(16) Click **Step 2: Configure a UI.PresentationVariant annotation term**

![](media/image20.png)

(17) Enter the following values:

  **Field**                 **Value**
  ------------------------- ----------------------------------
  Entity Type               SEPMRA_SO_SALESORDERANALYSISType
  Sort Order Property       NetAmount
  Sort Order Descending?    true
  Include Grand Total?      false
  Initial Expansion Level   1

![](media/image21.png)

(18) Click **Apply**. UI.PresentationVariant annotation is added to your local annotation file as configured in the code snippet.

![](media/image22.png)

(19)  Click **Exit Guide**.

Exercise 2.4 Start the Application Preview
------------------------------------------

In this exercise, you will start the preview of the Analytical List Page to view the content you just configured. Before you perform the steps below, make sure that the pop-ups from the SAP Business Application Studio are allowed in your browser.

![](media/image23.png)

(20) In the Explorer pane, right-click on the webapp folder.

**Note**: if the Explorer pane is hidden, double-click on the Guided Development tab to unhide it.

![](media\image24.png)

(21) Click **Preview Application**. Application preview will open in the next tab.

![](media/image25.png)

(22) in the Adapt Filters pop-up, enter **EUR** in the **Currency** field

![](media/image26.png)

(23) Click **Go**. The content area of the page displays the chart and table you created. They displayed the data pre-filtered by the currency value you entered in the pop-up with the required filter field.

The filter bar area is empty as at this point no visual filters are defined, you will specify them in one of the next exercises.

![](media/image27.png)

(24) You can click the button **Compact Filter** ![](media/image28.png) to view the compact filter bar with the only required field. You will add more in the next exercise.

![](media/image29.png)

Summary
-------

You have successfuly annotated the main entity type of your app with UI.LineItem, UI.Chart and UI.PresentationVariant annotations required to display content area of Analytical List Page. In the next exercise, you will configure the filters in the Alalytical List Page. 

Continue to [Exercise 3 - Configuring Filters in Analytical List Page](../ex3/README.md)

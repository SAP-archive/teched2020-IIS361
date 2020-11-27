Exercise 3 -- Configuring Filters in Analytical List Page
=========================================================

In this exercise, you will define the filter area of the Analytical List
Page.

Exercise 3.1 Configuring Comact Filter 
--------------------------------------

In this exercise, you will configure a UI.SelectionFields annotation that is used to display the filter fields in the compact filter bar of of the Analytical List Page.

![](media/image1.png)

(1) In the Guided Development Tab of SAP Business Application Studio, enter **filter** in the search field.

(2) Expand the guide **Add a new filter field to the Smart Filter Bar** ![](media/image2.png) under the Analytical List Page group.

![](media/image3.png)

(3) Click **Start Guide**.

![](media/image4.png)

(4) In the **Entity Type** field, select **Z_SEPMRA_SO_SALESORDERANALYSISType**.

![](media/image5.png)

(4) in the **Property** field, select **DeliveryCalendarDate**.

![](media/image6.png)

(5) In the **Property** field, select **DeliveryCalendarDate**.

![](media/image7.png)

(6) Click **Apply**. Annotation UI.SelectionFields is added to your local annotation file as configured in the code snippet.

![](media/image8.png)

(7) Now repeat steps (5) and (6) to add the filter ields for the following properties:

-   SoldToParty
-   Product
-   MainProductCategory
-   DeliveryCalendarQuarter

![](media/image9.png)

(8) When the fields for all properties are added to your UI.SelectionFields annotation, click **Exit Guide** to get back to the list of available guides.

You can now switch to the tab containing the running app to view the result. If you already stopped the preview after the previous exercise, you can start it again as described in [Exercise 2.4 Starting the Application Preview](../ex2#exercise-24-starting-the-application-preview)

**Note**: Do not forget to click the **Compact Filter** button ![](media/image10.png) to view the updated filter bar

Exercise 3.2 Configuring Visual Filter with Line Chart 
------------------------------------------------------

In this exercise, you will configure a UI.Chart, UI.PresentationVariant and Common.ValueList annotations that are used to display the visual filters. For this you will use the guide Add Visual Filter that consists of 3 steps.

Fiori user experiance recommends the filters to be displayed in a Visual format for better drill down and analysis. Visual Filters can be used by an end user as an alternate option to the more conventional compact filters. Visual Filters show the top outliers with respect to measures and thus provide hints to users what are the interesting filter selections. You need to have a ValueHelp entity set to configure a Visual Filter

![](media/image11.png)

(9) In Guided Development, open the guide **Add a new visual filter** ![](media/image12.png).

![](media/image13.png)

(10) Click **Start Guide**.

![](media/image14.png)

(11) In the first step, you define a chart to be displayed in the filter
bar, using a \'UI.Chart\' annotation. Enter the following values:

  |**Field**             |**Value**
  ---------------------  |--------------------------------
  |Entity Type           |SEPMRA_SO_ALP_SLDORDERITEMType
  |Chart Qualifier       |FilterQuantityByDate
  |Chart Title           |Quantity by Delivery Date
  |Chart Description     |Item Quantity by Delivery Date
  |Chart Type            |Line
  |Dimensions Property   |DeliveryDate
  |Measures Property     |Quantity


**Note**: The data displayed in the chart is more aggregated than what is shown in the main content of the page. In our case we display the sum of all sales order amounts by day. Therefore, you **use an entity type that is different** from the entity type used in the main content of the page

(12) Click **Apply**. UI.Chart annotation is added to the local annotation file.

![](media/image15.png)

(13) Click **Step 2**

**Note:** You can also click **Next** at the bottom of the guide to go to the next step.

![](media/image16.png)

(14) Enter the following values:

  |**Field**                        |**Value**
  |-------------------------------- |----------------------------------
  |Entity Type                      |SEPMRA_SO_ALP_SLDORDERITEMType
  |Presentation Variant Qualifier   |FilterQuantityByDate
  |Chart Qualifier                  |\@UI.Chart\#FilterQuantityByDate

**Note**: Here you use the same entity type as in the previous step.

(15) Click **Apply**.

![](media/image17.png)

(16) Click **Step 3.**

In that step, you will define the mapping between dimensions in the visual filter and properties in the objects displayed in the main content, so that clicking on a dimension value the visual filter will filter the main content accordingly. In this case, you have to map the date property in **SEPMRA_SO_ALP_SLDORDERITEMType** to the date in **Z_SEPMRA_SO_SALESORDERANALYSIS** for the visual filter to work properly. For this, we use the Common.ValueList annotation.

![](media/image18.png)

(17) Enter the following values:

  |**Field**                        |**Value**
  |-------------------------------- |------------------------------------
  |Entity Type                      |Z_SEPMRA_SO_SALESORDERANALYSISType
  |Entity Type Property             |DeliveryCalendarDate
  |Collection Path                  |SEPMRA_SO_ALP_SLDORDERITEM
  |Presentation Variant Qualifier   |FilterQuantityByDate
  |Local Data Property              |DeliveryCalendarDate
  |Value List Property              |DeliveryDate

**Note**: Here you annotate the property of your main entity type.

**Note**: Value list Property must contain the property you used as dimension in the chart configured in step 1 of the guide.

(18) Click **Apply**.

![](media/image19.png)

(19) Click **Exit Guide**.

At this point your visual filter is configured and you can start the application preview as described in [Exercise 2.4 Starting the Application Preview](../ex2#exercise-24-starting-the-application-preview). The visual filter is displayed. You can filter the content by selecting any of the points in the line chart and clicking **Go**.

![](media/image20.png)

Exercise 3.3 Configuring Visual Filter with Bar Chart 
-----------------------------------------------------

In this exercise, you will go through the similar steps to create one more visual filter, this time as a bar chart.

To start, repeat the steps (9) and (10) above to start the guide **Add a new visual filter**.

![](media/image21.png)

(20)In **step 1** of the guide, use the following values to create a chart as described in [Exercise 
Configuring Visual Filter with Line Chart](#exercise-32-configuring-visual-filter-with-line-chart) steps
(11)-(13).

  |**Field**             |**Value**
  |--------------------- |--------------------------------
  |Entity Type           |SEPMRA_SO_ALP_SLDORDERITEMType
  |Chart Qualifier       |FilterQuantityByProduct
  |Chart Title           |Quantity by Product
  |Chart Description     |Item Quantity by Product
  |Chart Type            |Bar
  |Dimensions Property   |Product
  |Measures Property     |Quantity

![](media/image22.png)

(21) In **step 2** of the guide, use the following values to reference that chart in a presentation variant as in steps (14) - (16) above.

  |**Field**                        |**Value**
  |-------------------------------- |-------------------------------------
  |Entity Type                      |SEPMRA_SO_ALP_SLDORDERITEMType
  |Presentation Variant Qualifier   |FilterQuantityByProduct
  |Chart Qualifier                  |\@UI.Chart\#FilterQuantityByProduct

**Note**: Here you use the same entity type as in the previous step.

![](media/image23.png)

(22) In **step 3** of the guide, use the following values to map the dimensions in the chart to the respective property of your main entity type in the annotation Common.ValueList as in steps (16) - (18) above.

  |**Field**                        |**Value**
  |-------------------------------- |--------------------------------
  |Entity Type                      |Z_SEPMRA_SO_SALESORDERANALYSIS
  |Entity Type Property             |Product
  |Collection Path                  |SEPMRA_SO_ALP_SLDORDERITEM
  |Presentation Variant Qualifier   |FilterQuantityByProduct
  |Local Data Property              |Product
  |Value List Property              |Product

**Note**: Here you annotate the property of your main entity type.

**Note**: Value list Property must contain the property you used as dimension in the chart configured in step 1 of the guide.

When you are done with all three steps, your second visual filter is configured and you can start the application preview as described in [Exercise 2.4 Starting the Application Preview](../ex2#exercise-24-starting-the-application-preview). Enter **EUR** as a currency in the pop up and click **Go** to view the result. The second
visual filter in is displayed as a bar chart.

![](media/image24.png)

Exercise 3.4 Configuring Semantic Coloring
------------------------------------------

In this step, you will define the criticality coloring to the visual filter bar based on the sales order items. Criticality annotations allows you to define the improvement direction by specifying different ranges and when the actual values cross those boundaries specified application, Visual Filterbar charts displays criticality coloring to display the situation

![](media/image25.png)

(23) In Guidede Development, expand the guide **Add semantic coloring for visual filter** ![](media/image26.png)

![](media/image27.png)

(24) Click **Start Guide**.

![](media/image28.png)

(25) In the step 1, configure the DataPoint annotation using the following values:

  |**Field**                |**Value**
  |------------------------ |--------------------------------
  |Entity Type              |SEPMRA_SO_ALP_SLDORDERITEMType
  |Data Point Qualifier     |Quantity
  |Data Point Value         |Quantity
  |Improvement Direction    |Maximize
  |ToleranceRangeLowValue   |5
  |DeviationRangeLowValue   |4

(26) Click **Apply**.

![](media/image29.png)

(27) Click **Step 2**.


**Note**: You can also click **Next** at the bottom of the guide to go to the next step.

![](media/image30.png)

(28) In **Step 2**, update the chart you defined for the visual filter in [Exercise 
Configuring Visual Filter with Line
Chart](../ex3#exercise-32-configuring-visual-filter-with-line-chart) as follows:

  |**Field**                                |**Value**
  |---------------------------------------- |--------------------------------
  |Entity Type                              |SEPMRA_SO_ALP_SLDORDERITEMType
  |Chart Qualifier                          |FilterQuantityByDate
  |Chart Title                              |Quantity by Delivery Date
  |Chart Description                        |Item Quantity by Delivery Date
  |Chart Type                               |Line
  |Dimensions Property                      |DeliveryDate
  |Measures Property                        |Quantity
  |**Chart Measures Attributes Property**   |**Quantity**
  |**Data Point Qualifier**                 |**\@UI.DataPoint\#Quantity**

**Note**: Here you update the already existing UI.Chart annotation used to display your visual filter with the reference to the Data Point annotation defiled in the previous step. For your convenience, the new fields and values are marked bold in this table.

(29) Click **Apply**.

 
At this point you have configured the semantic coloring for the visual filter with the Line chart. Start the preview to see the changes in your visual filter based on the line chart. The data points are highlighted with semantic colors.

![](media/image31.png)

Summary
-------

You have learned how to create Visual Filters and define the semantic coloring for its elements. In the next exercise, you will configure the Object Page.

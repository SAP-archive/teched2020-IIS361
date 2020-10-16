# Configuration of Content for Analytical List Page
In this exercise, we will create the main page for the application based on Analytical List Page floorplan

## Steps for creating UI annotations

### Modify the annotation.xml
1. To start, double click on the 'annotation.xml' file in the 'annotations' folder under 'webapp' to open

2. Place your curser after the schema definition and press ENTER

3. In the new line, trigger code completion by pressing CTRL/CMD + SPACE, which displays 'Annotations' as the available option. Choose it by pressing ENTER

4. Add the annotation target by Press CTRL/CMD + SPACE to open a list of available targets. Use Up/Down arrow to choose from the list or start typing in the entity type name - "Z_SEPMRA_SO_SALESORDERANALYSISType" and select from the filtered list

5. Save the annotation file by clicking the ‘Save’ icon or pressing CTRL+S. It should look like below
```xml
<Annotations Target="TECHED_ALP_SOA_SRV.Z_SEPMRA_SO_SALESORDERANALYSISType">    

</Annotations>
```

### Configure Table
In this step, you will configure the table & columns displayed in the table of the Analytical List Page. UI annotation ‘LineItem’ is used to represent the table, with DataField Records representing the columns. Below steps will guide you through this activity

1. Place the curser between the Annotations tags and press CTRL/CMD + SPACE. From the options, choose UI.LineItem by pressing ENTER

2. Place your curser between Collection tags and press CTRL/CMD + SPACE. From the options, choose "DataField" Record and press ENTER

3. Press CTRL/CMD + SPACE to open the list of available value type and choose Path. Press CTRL/CMD + SPACE to open the list of available properties and choose "DeliveryCalendarYear"

4. Come to new line after the first DataField Record is closed and repeat steps (2) - (4) to add columns for properties : "DeliveryCalendarMonth", "SalesOrder", "SalesOrderItem", "Product", "MainProductCategory", "SoldToParty", "Quantity", "NetAmount"

5. Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below
```xml
<Annotation Term="UI.LineItem" >
    <Collection>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="DeliveryCalendarYear"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="DeliveryCalendarMonth"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="SalesOrder"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="SalesOrderItem"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="Product"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="MainProductCategory"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="SoldToParty"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="Quantity"/>
        </Record>
        <Record Type="UI.DataField">
            <PropertyValue Property="Value" Path="NetAmount"/>
        </Record>
    </Collection>
</Annotation>
```

### Configure Chart
In this step, you will configure the chart to be displayed in the analytical list page. UI Annotation "Chart" is used to represent the Chart control. You can configure different measures & dimensions of the Chart & as well as the chart type

1. Come to new line after the UI.LineItem annotation is closed and press CTRL/CMD + SPACE. From the options, choose UI.Chart annotation

2. Press CTRL/CMD + SPACE to choose value type as EnumMember for ChartType property. From the list, choose "UI.ChartType/Column"

3. In the new line, open the list of options by pressing CTRL/CMD + SPACE and press enter on Title property. Add string value as "Revenue by Customer"

4. Repeat  step 3 for adding Description property. Add string value for description as "Net Revenue by Customer"

5.  In the new line, add Measure property from the list of options opened by pressing CTRL/CMD + SPACE. Add the property path as "NetAmount"

6. In the new line, add Dimension property from the list of options opened by pressing CTRL/CMD + SPACE

7. Add the 2 property paths. One should be "SoldToParty" and the other should be "DeliveryCalendarYear"

8. Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below
```xml
<Annotation Term="UI.Chart" >
    <Record Type="UI.ChartDefinitionType">
        <PropertyValue Property="ChartType" EnumMember="UI.ChartType/Column"/>
        <PropertyValue Property="Title" String="Revenue by Customer"/>
        <PropertyValue Property="Description" String="Net Revenue by Customer"/>
        <PropertyValue Property="Measures">
            <Collection>
                <PropertyPath>NetAmount</PropertyPath>
            </Collection>
        </PropertyValue>
        <PropertyValue Property="Dimensions">
            <Collection>
                <PropertyPath>SoldToParty</PropertyPath>
                <PropertyPath>DeliveryCalendarYear</PropertyPath>
            </Collection>
        </PropertyValue>
    </Record>
</Annotation>
```

### Configure Presentation Variant
In this step, you will configure a UI.PresentationVariant annotation. UI.PresentationVariant allows you to configure the visualization artifacts, Sortorder, Initial expansion level in case of a grouped table,...etc. You can create multiple such presentation variants and select one of the variant to be loaded

1. In the same level as UI.Chart/UI.LineItem annotation add UI.PresentationVariant (You can press CTRL/CMD + SPACE to get the available options autocomplete)

2. As a child of the Record annotation, select Text property and add string value as "Default"

3. Add SortOrder property and set property path as "NetAmount"

4. As child to SortOrder property, add Descending property and set Bool value as "true"

5. Add IncludeGrandTotal property and set the Bool value as "false"

6. Add InitialExpansionLevel property and set Int value as "1"

7. Add Visualizations property & add the 2 annotation paths, @UI.LineItem for table and @UI.Chart for Chart

8. Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below
```xml
<Annotation Term="UI.PresentationVariant">
    <Record Type="UI.PresentationVariantType">
        <PropertyValue Property="Text" String="Default"/>
        <PropertyValue Property="SortOrder">
            <Collection>
                <Record Type="Common.SortOrderType">
                    <PropertyValue Property="Property" PropertyPath="NetAmount"/>
                    <PropertyValue Property="Descending" Bool="true"/>
                </Record>
            </Collection>
        </PropertyValue>
        <PropertyValue Property="IncludeGrandTotal" Bool="false"/>
        <PropertyValue Property="InitialExpansionLevel" Int="1"/>
        <PropertyValue Property="Visualizations">
            <Collection>
                <AnnotationPath>@UI.LineItem</AnnotationPath>
                <AnnotationPath>@UI.Chart</AnnotationPath>
            </Collection>
        </PropertyValue>
    </Record>
</Annotation>
```
*A presentation variant is used to define which table and chart will be displayed in the main content of the page.*

## RUN THE APP
Right click on webapp folder in the project explorer and choose Preview Application from the menu

## Summary
You have successfuly annotated Chart & Table required for Analytical List Page. To continue the exercise please go to [Configuration of the Filters in Analytical List Page](../ex3/README.md)

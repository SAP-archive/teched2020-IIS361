# CONFIGURATION OF CONTENT FOR FIRST PAGE (ANALYTICAL LIST PAGE)
<br>In this exercise, we will create the main page for the application based on Analytical List Page floorplan.</br>
<br>1. To start, double click on the 'annotation.xml' file in the 'annotations' folder under 'webapp' to open.</br>
<br>2. Place your curser after the schema definition and press ENTER</br>
<br>3. In the new line, trigger code completion by pressing CTRL/CMD + SPACE, which displays 'Annotations' as the available option. Choose it by pressing ENTER.</br>
<br>4. Add the annotation target by Press CTRL/CMD + SPACE to open a list of available targets. Use Up/Down arrow to choose from the list or start typing in the entity type name - "Z_SEPMRA_SO_SALESORDERANALYSISType" and select from the filtered list.</br>
<br>Save the annotation file by clicking the ‘Save’ icon or pressing CTRL+S. It should look like below</br>
```xml
<Annotations Target="TECHED_ALP_SOA_SRV.Z_SEPMRA_SO_SALESORDERANALYSISType">    

</Annotations>
```

## CONFIGURE CONTENT FOR TABLE
<br>In this step, you will configure the columns displayed in the table of the Analytical List Page. The declaration of columns is done with a ‘LineItem’ annotation, with each column corresponding to a DataField.</br>
<br>1. Place the curser between the Annotations tags and press CTRL/CMD + SPACE. From the options, choose UI.LineItem by pressing ENTER.</br>
<br>2. Place your curser between Collection tags and press CTRL/CMD + SPACE. From the options, choose "DataField" Record and press ENTER.</br>
<br>3. Press CTRL/CMD + SPACE to open the list of available value type and choose Path. Press CTRL/CMD + SPACE to open the list of available properties and choose "DeliveryCalendarYear". </br>
<br>4. Come to new line after the first DataField Record is closed and repeat steps (2) - (4) to add columns for properties : "DeliveryCalendarMonth", "SalesOrder", "SalesOrderItem", "Product", "MainProductCategory", "SoldToParty", "Quantity", "NetAmount"</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below.</br>
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

## CONFIGURE CONTENT FOR CHART
<br>In this step, you will configure the chart to be displayed in the analytical list page, using a UI.Chart annotation, where you specify which measures and dimensions should be used as default, as well as the chart type.</br>
<br>1. Come to new line after the UI.LineItem annotation is closed and press CTRL/CMD + SPACE. From the options, choose UI.Chart annotation.</br>
<br>2. Press CTRL/CMD + SPACE to choose value type as EnumMember for ChartType property. From the list, choose "UI.ChartType/Column"</br>
<br>3. In the new line, open the list of options by pressing CTRL/CMD + SPACE and press enter on Title property. Add string value as "Revenue by Customer"</br>
<br>4. Repeat  step 3 for adding Description property. Add string value for description as "Net Revenue by Customer"</br>
<br>5.  In the new line, add Measure property from the list of options opened by pressing CTRL/CMD + SPACE. Add the property path as "NetAmount".</br>
<br> In the new line, add Dimension property from the list of options opened by pressing CTRL/CMD + SPACE. Add the 2 property paths. One should be "SoldToParty" and the other should be "DeliveryCalendarYear".</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>
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

## CONFIGURE PRESENTATION VARIANT
<br>In this step, you will configure a UI.PresentationVariant annotation to specify a view on data. There you can define for example a sort order, group by, etc. and also visualizations (chart and table) which should be used.</br>
<br>1. In the next line after the UI.Chart annotation is closed and press CTRL/CMD + SPACE. From the options, choose UI.PresentationVariant.</br>
<br>2. Place the cursor between the Record tags and press CTRL/CMD + SPACE. From the options choose Text property. Add string value as "Default".</br>
<br>3. In the new line, open the list of options by pressing CTRL/CMD + SPACE and press enter on SortOrder property. Add property path as "NetAmount".</br>
<br>4. In the nect line, open the list of options by pressing CTRL/CMD + SPACE and press enter on Property "Descending". Add Bool value as "true"</br>
<br>5. In the new line after SortOrder property is closed, add IncludeGrandTotal property from the list of options opened by pressing CTRL/CMD + SPACE. Add Bool value as "false".</br>
<br>6. Repeat step 5 for adding InitialExpansionLevel property. Add Int value as "1".</br>
<br>7. In the new line, add Visualizations property from the list of options opened by pressing CTRL/CMD + SPACE. Add the 2 annotation paths, @UI.LineItem for table and @UI.Chart for Chart</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>
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
<br>*A presentation variant is used to define which table and chart will be displayed in the main content of the page.*</br>

## RUN THE APP
<br>In this step, you will preview the application. Right click on webapp and choose Preview Application from the menu</br>


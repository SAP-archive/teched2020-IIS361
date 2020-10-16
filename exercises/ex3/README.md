# CONFIGURATION OF FILTERS FOR FIRST PAGE (ANALYTICAL LIST PAGE)
In this part, you will create the annotations to display compact and visual filters in the filter bar of the analytical list page.

## CONFIGURE COMPACT FILTERS
<br>1. In the next line after the UI.PresentationVariant annotation is closed and press CTRL/CMD + SPACE. From the options, choose UI.SelectionField.</br>
<br>2. Add Property paths for "DeliveryCalendarDate", "SoldToParty", "Product", "MainProductCategory", "DeliveryCalendarQuarter"</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below.</br>
```xml
 <Annotation Term="UI.SelectionFields">
    <Collection>
        <PropertyPath>DeliveryCalendarDate</PropertyPath>
        <PropertyPath>SoldToParty</PropertyPath>
        <PropertyPath>Product</PropertyPath>
        <PropertyPath>MainProductCategory</PropertyPath>
        <PropertyPath>DeliveryCalendarQuarter</PropertyPath>
    </Collection>
</Annotation>
```

## CONFIGURE VISUAL FILTER - Quantity By Date
<br>A nice improvement are the visual filters in the Analytical List Page. They can be used besides the more conventional compact filters. The visual filters show the top outliers with respect to measures and thus provide hints to users what are the interesting filter selections. In this step and in the next one you will create two visual filters for your Analytical List Page.</br>
<br>1. In the new line after closing Annotations tag, add a new Annotations Target. Trigger code completion by pressing CTRL/CMD + SPACE, which displays 'Annotations' as the available option. Choose it by pressing ENTER.</br>
<br>2. Add the annotation target by Press CTRL/CMD + SPACE to open a list of available targets. Select "SEPMRA_SO_ALP_SLDORDERITEMType".</br>
<br>Save the annotation file by clicking the ‘Save’ icon or pressing CTRL+S. It should look like below.</br>

```xml
<Annotations Target="TECHED_ALP_SOA_SRV.SEPMRA_SO_ALP_SLDORDERITEMType">    

</Annotations>
```
<br>Let’s define the chart to be displayed.</br>
<br>3. Put the curser between the Annotations tags and press CTRL/CMD + SPACE. From the options, choose UI.Chart by pressing ENTER.</br>
<br>4. Press CTRL/CMD + SPACE to add the Qualifier for your UI.Chart annotation and add its value as "FilterQuantityByDate"</br>
<br>5. Press CTRL/CMD + SPACE to choose value type as EnumMember for ChartType property. From the list, choose "UI.ChartType/Line"</br>
<br>6. In the new line, open the list of options by pressing CTRL/CMD + SPACE and press enter on Title property.</br>
<br>7. Add type as String and value as "Quantity by Delivery Date".</br>
<br>8. In the new line, add Measure property from the list of options opened by pressing CTRL/CMD + SPACE. Add the property path as "Quantity".</br>
<br>9. In the new line, add Dimension property from the list of options opened by pressing CTRL/CMD + SPACE. Add the property path as "DeliveryDate".</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>

```xml
<Annotation Term="UI.Chart" Qualifier="FilterQuantityByDate">
    <Record Type="UI.ChartDefinitionType">
        <PropertyValue Property="ChartType" EnumMember="UI.ChartType/Line"/>
        <PropertyValue Property="Title" String="Quantity by Delivery Date"/>
        <PropertyValue Property="Measures">
            <Collection>
                <PropertyPath>Quantity</PropertyPath>
            </Collection>
        </PropertyValue>
        <PropertyValue Property="Dimensions">
            <Collection>
                <PropertyPath>DeliveryDate</PropertyPath>
            </Collection>
        </PropertyValue>
    </Record>
</Annotation>
```

<br>Now, you need to reference the chart in a presentation variant to display it in the filter bar.</br>
<br>10. Come to new line after the UI.Chart#FilterQuantityByDate annotation is closed and press CTRL/CMD + SPACE. From the options, choose UI.PresentationVariant by pressing ENTER.</br>
<br>11. Press CTRL/CMD + SPACE to add the Qualifier for your UI.PresentationVariant annotation and add its value as "FilterQuantityByDate"</br>
<br>12. Place the cursor between the Record tags and press CTRL/CMD + SPACE. From the options, add Visualizations property from the list of options.</br>
<br>13. Add the annotations path, @UI.Chart#FilterQuantityByDate.</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>

```xml
<Annotation Term="UI.PresentationVariant" Qualifier="FilterQuantityByDate">
    <Record Type="UI.PresentationVariantType">
        <PropertyValue Property="Visualizations">
            <Collection>
                <AnnotationPath>@UI.Chart#FilterQuantityByDate</AnnotationPath>
            </Collection>
        </PropertyValue>
    </Record>
</Annotation>
```

<br>Now, let’s map the 2 date properties in the 2 objects we used. This is done by annotating the. This is done by annotating the ‘DeliveryCalendarDate’ property in ‘Z_SEPMRA_SO_SALESORDERANALYSIS’.</br>
<br>14. In the new line after closing Annotations target for SEPMRA_SO_ALP_SLDORDERITEMType, add a new Annotations Target.</br>
<br>15. Trigger code completion by pressing CTRL/CMD + SPACE, which displays 'Annotations' as the available option. Choose it by pressing ENTER.</br>
<br>16. Add the annotation target by Press CTRL/CMD + SPACE to open a list of available targets. Select "Z_SEPMRA_SO_SALESORDERANALYSISType". Type a "/" after the entity type name and choose "DeliveryCalendarDate" from the suggestion.</br>
<br>17. Put the curser between the Annotations tags and press CTRL/CMD + SPACE. From the options, choose Common.ValueList by pressing ENTER.</br>
<br>18. For CollectionPath property, add the property string value as "SEPMRA_SO_ALP_SLDORDERITEM"</br>
<br>19. In the new line, add PresentationVariantQualifier property from the list of options opened by pressing CTRL/CMD + SPACE. Add the property string as "FilterQuantityByDate".</br>
<br>20. In the new line, add Parameters property from the list of options opened by pressing CTRL/CMD + SPACE. Put the cursor betweem the Collection tags and press CTRL/CMD + SPACE. From the options, choose Record "ValueListParameterInOut" and press ENTER.</br>
<br>21. For LocalDataProperty, add property path as "DeliveryCalendarDate" and for ValueListProperty and string value as "DeliveryDate".</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>
```xml
<Annotations Target="TECHED_ALP_SOA_SRV.Z_SEPMRA_SO_SALESORDERANALYSISType/DeliveryCalendarDate">
    <Annotation Term="Common.ValueList">
        <Record Type="Common.ValueListType">
            <PropertyValue Property="CollectionPath" String="SEPMRA_SO_ALP_SLDORDERITEM"/>
            <PropertyValue Property="PresentationVariantQualifier" String="FilterQuantityByDate"/>
            <PropertyValue Property="Parameters">
                <Collection>
                    <Record Type="Common.ValueListParameterInOut">
                        <PropertyValue Property="LocalDataProperty" PropertyPath="DeliveryCalendarDate"/>
                        <PropertyValue Property="ValueListProperty" String="DeliveryDate"/>
                    </Record>
                </Collection>
            </PropertyValue>
        </Record>
    </Annotation>
</Annotations>
```
<br>*Two things are needed to configure a visual filter:*</br>
<br>*You need to define a chart to be displayed in the filter bar, using a ‘UI.Chart’ annotation. The data displayed in the chart is more aggregated than what is shown in the main content of the page. In our case we display the sum of all sales order amounts by day. Therefore, you use an object which is different from the object used in the main content of the page (‘SEPMRA_SO_ALP_SLDORDERITEMType’ vs. ‘Z_SEPMRA_SO_SALESORDERANALYSIS’)*</br>
<br>*You need to define the mapping between dimensions in the visual filter and properties in the objects displayed in the main content, so that clicking on a dimension value the visual filter will filter the main content accordingly. In our case, we had to map the date property in ‘SEPMRA_SO_ALP_SLDORDERITEMType’ to the date in ‘Z_SEPMRA_SO_SALESORDERANALYSIS’, for the visual filter to work properly. This is what the ‘ValueList’ annotation is used for.*</br>

## CONFIGURE VISUAL FILTER - Quantity By Product
<br>In this step, you will add a second visual filter. The configuration is similar to what you’ve already done for the first visual filter in the previous step (definition of the chart + property mapping).<br>

<br>1. Within the Annotations target SEPMRA_SO_ALP_SLDORDERITEMType', in the next line after closing UI.PresenationVariant tag for the first visual filter, press CTRL/CMD + SPACE. From the options, choose UI.Chart by pressing ENTER.</br>
<br>2. Press CTRL/CMD + SPACE to add the Qualifier for your UI.Chart annotation and add its value as "FilterQuantityByProduct"</br>
<br>3. Press CTRL/CMD + SPACE to choose value type as EnumMember for ChartType property. From the list, choose "UI.ChartType/Bar".</br>
<br>4. In the new line, open the list of options by pressing CTRL/CMD + SPACE and press enter on Title property.</br>
<br>5. Add type as String and value as "Quantity by Product".</br>
<br>6. In the new line, add Measure property from the list of options opened by pressing CTRL/CMD + SPACE. Add the property path as "Quantity".</br>
<br>7. In the new line, add Dimension property from the list of options opened by pressing CTRL/CMD + SPACE. Add the property path as "Product".</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>

```xml
<Annotation Term="UI.Chart" Qualifier="FilterQuantityByProduct">
    <Record Type="UI.ChartDefinitionType">
        <PropertyValue Property="ChartType" EnumMember="UI.ChartType/Bar"/>
        <PropertyValue Property="Title" String="Quantity by Product"/>
        <PropertyValue Property="Measures">
            <Collection>
                <PropertyPath>Quantity</PropertyPath>
            </Collection>
        </PropertyValue>
        <PropertyValue Property="Dimensions">
            <Collection>
                <PropertyPath>Product</PropertyPath>
            </Collection>
        </PropertyValue>
    </Record>
</Annotation>
```

<br>Now, you need to reference the chart in a presentation variant to display it in the filter bar.</br>
<br>10. Come to new line after the UI.Chart#FilterQuantityByProduct annotation is closed and press CTRL/CMD + SPACE. From the options, choose UI.PresentationVariant by pressing ENTER.</br>
<br>11. Press CTRL/CMD + SPACE to add the Qualifier for your UI.PresentationVariant annotation and add its value as "FilterQuantityByProduct"</br>
<br>12. Place the cursor between the Record tags and press CTRL/CMD + SPACE. From the options, add Visualizations property from the list of options.</br>
<br>13. Add the annotations path, @UI.Chart#FilterQuantityByProduct.</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>
```xml
<Annotation Term="UI.PresentationVariant" Qualifier="FilterQuantityByProduct">
    <Record Type="UI.PresentationVariantType">
        <PropertyValue Property="Visualizations">
            <Collection>
                <AnnotationPath>@UI.Chart#FilterQuantityByProduct</AnnotationPath>
            </Collection>
        </PropertyValue>
    </Record>
</Annotation>
```

<br>Now, let’s map the 2 product properties in the 2 objects we used. </br>
<br>14. In the new line after closing Annotations target for Z_SEPMRA_SO_SALESORDERANALYSISType/DeliveryCalendarDate, add a new Annotations Target.</br>
<br>15. Trigger code completion by pressing CTRL/CMD + SPACE, which displays 'Annotations' as the available option. Choose it by pressing ENTER.</br>
<br>16. Add the annotation target by Press CTRL/CMD + SPACE to open a list of available targets. Select "Z_SEPMRA_SO_SALESORDERANALYSISType". Type a "/" after the entity type name and choose "Product" from the suggestion.</br>
<br>17. Put the curser between the Annotations tags and press CTRL/CMD + SPACE. From the options, choose Common.ValueList by pressing ENTER.</br>
<br>18. For CollectionPath property, add the property string value as "SEPMRA_SO_ALP_SLDORDERITEM"</br>
<br>19. In the new line, add PresentationVariantQualifier property from the list of options opened by pressing CTRL/CMD + SPACE. Add the property string as "FilterQuantityByProduct".</br>
<br>20. In the new line, add Parameters property from the list of options opened by pressing CTRL/CMD + SPACE. Put the cursor betweem the Collection tags and press CTRL/CMD + SPACE. From the options, choose Record "ValueListParameterInOut" and press ENTER.</br>
<br>21. For LocalDataProperty, add property path as "Product" and for ValueListProperty and string value as "Product".</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S.Your final annotation will look like below</br>

```xml
<Annotations Target="TECHED_ALP_SOA_SRV.Z_SEPMRA_SO_SALESORDERANALYSISType/Product">
    <Annotation Term="Common.ValueList" >
        <Record Type="Common.ValueListType">
            <PropertyValue Property="CollectionPath" String="SEPMRA_SO_ALP_SLDORDERITEM"/>
            <PropertyValue Property="PresentationVariantQualifier" String="FilterQuantityByProduct"/>
            <PropertyValue Property="Parameters">
                <Collection>
                    <Record Type="Common.ValueListParameterInOut">
                        <PropertyValue Property="LocalDataProperty" PropertyPath="Product"/>
                        <PropertyValue Property="ValueListProperty" String="Product"/>
                    </Record>
                </Collection>
            </PropertyValue>
        </Record>
    </Annotation>
</Annotations>
```

## SEMANTIC COLORING
In this step, you will define the criticality coloring to the visual filter bar based on the sales order items</br>
<br>1. Within the Annotations target SEPMRA_SO_ALP_SLDORDERITEMType, in the next line after closing UI.PresenationVariant tag for the second visual filter, press CTRL/CMD + SPACE. From the options, choose UI.DataPoint by pressing ENTER.</br>
<br>2. Press CTRL/CMD + SPACE to add the Qualifier for your UI.DataPoint annotation and add its value as "Quantity"</br>
<br>3. Press CTRL/CMD + SPACE to choose Value property's path "Quantity"</br>
<br>4. In the new line, open the list of options by pressing CTRL/CMD + SPACE and press enter on CriticalityCalculatioin property.</br>
<br>5. Add ImprovementDirection as EnumMember value "UI.ImprovementDirectionType/Maximize".</br>
<br>6. In the new line, add ToleranceRangeLowValue property from the list of options opened by pressing CTRL/CMD + SPACE. Add int value as "5".</br>
<br>7. In the new line, add DeviationRangeLowValue property from the list of options opened by pressing CTRL/CMD + SPACE. Add int value as "4"</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>
```xml
<Annotation Term="UI.DataPoint" Qualifier="Quantity">
    <Record Type="UI.DataPointType">
        <PropertyValue Property="Value" Path="Quantity"/>
        <PropertyValue Property="CriticalityCalculation">
            <Record Type="UI.CriticalityCalculationType">
                <PropertyValue Property="ImprovementDirection" EnumMember="UI.ImprovementDirectionType/Maximize"/>
                <PropertyValue Property="ToleranceRangeLowValue" Int="5"/>
                <PropertyValue Property="DeviationRangeLowValue" Int="4"/>
            </Record>
        </PropertyValue>
    </Record>
</Annotation>
```
<br>8. Within the UI.Chart#FilterQualityByDate, in the new line after Dimension property, press CTRL/CMD + SPACE. From the options, choose MeasureAttributes property by pressing ENTER. </br>
<br>9. Place the cursor between the Record tags and press CTRL/CMD + SPACE to add DataPoint property.</br>
<br>10. Add Annotation path as @UI.DataPoint#Quantity.</br>
<br> In the next line, add Measure property from the list of options opened by pressing CTRL/CMD + SPACE. Add the property path as "Quantity"</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final UI.Chart annotation will look like below</br>
```xml
<Annotation Term="UI.Chart" Qualifier="FilterQuantityByDate">
    <Record Type="UI.ChartDefinitionType">
        <PropertyValue Property="ChartType" EnumMember="UI.ChartType/Line"/>
        <PropertyValue Property="Title" String="Quantity by Delivery Date"/>
        <PropertyValue Property="Measures">
            <Collection>
                <PropertyPath>Quantity</PropertyPath>
            </Collection>
        </PropertyValue>
        <PropertyValue Property="Dimensions">
            <Collection>
                <PropertyPath>DeliveryDate</PropertyPath>
            </Collection>
        </PropertyValue>
        <PropertyValue Property="MeasureAttributes">
            <Collection>
                <Record Type="UI.ChartMeasureAttributeType">
                    <PropertyValue Property="Measure" PropertyPath="Quantity"/>
                    <PropertyValue Property="DataPoint" AnnotationPath="@UI.DataPoint#Quantity"/>
                </Record>
            </Collection>
        </PropertyValue>
    </Record>
</Annotation>
```

## RUN THE APP
<br>In this step, you will preview the application. Right click on webapp and choose Preview Application from the menu.</br>


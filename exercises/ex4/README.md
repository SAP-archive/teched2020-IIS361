# CONFIGURATION OF SECOND PAGE (OBJECT PAGE)
In this part, you will create the annotations to display the header and content for the Object page

## CONFIGURE HEADER
<br>In this step, you will define the information that will be displayed in the header of the object page: the ID of the sales order item and an icon.</br>
<br>1. Within the Annotations target Z_SEPMRA_SO_SALESORDERANALYSISType, in the new line after closing UI.SelectionField Annotations, press CTRL/CMD + SPACE. From the options, choose UI.HeaderInfo annotation by pressing ENTER.</br>
<br>2. For TypeName property, add type of value as String and value as "Sales Order Item"</br>
<br>For TypeNamePlural property, add type of value as String and value as "Sales Order Items"</br>
<br>3. In the next line add TypeImageUrl property choosing from the suggestion list opened up by pressing CTRL/CMD + SPACE.</br> 
<br>4. The type is added as String and value as "sap-icon://sales-order-item".</br>
<br>5. In the next line add Title property by choosing from the suggestion list opened up by pressing CTRL/CMD + SPACE.<br>
<br>6. Place your curser between PropertyValue tags and press CTRL/CMD + SPACE. From the options, choose Record "DataField" and press ENTER.</br>
<br>7. Press CTRL/CMD + SPACE to open the list of available value type and choose Path. Press CTRL/CMD + SPACE to open the list of available properties and choose "SalesOrderItem".</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S.<br>
<br>Your final annotation will look like below.<br>

```xml
<Annotation Term="UI.HeaderInfo" >
    <Record Type="UI.HeaderInfoType">
        <PropertyValue Property="TypeName" String="Sales Order Item"/>
        <PropertyValue Property="TypeNamePlural" String="Sales Order Items"/>
        <PropertyValue Property="Title">
            <Record Type="UI.DataField">
                <PropertyValue Property="Value" Path="SalesOrderItem"/>
            </Record>
        </PropertyValue>
        <PropertyValue Property="TypeImageUrl" String="sap-icon://sales-order-item"/>
    </Record>
</Annotation>
```
## DISPLAY NET AMOUNT AND STATUS RATING IN THE HEADER
<br>In this step, you will add 2 additional pieces of information in the header: the net amount corresponding to the sales order item, and the status.</br>
<br>1. In the new line after closing UI.HeaderInfo annotations, press CTRL/CMD + SPACE. From the options, choose UI.DataPoint by pressing ENTER.</br> 
<br>2. Press CTRL/CMD + SPACE to add the Qualifier for your UI.DataPoint annotation and add its value as "NetAmount"</br>
<br>3. Press CTRL/CMD + SPACE to choose type for Value property as Path and value as "NetAmount".</br>
<br>4. Repeat steps 1 - 3 for creating another DataPoint annotation.</br>
<br>5. Keep the new DataPoint's qualifier as Status and Value as "SalesOrderStatus".</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>

```xml
<Annotation Term="UI.DataPoint" Qualifier="NetAmount">  
    <Record Type="UI.DataPointType">
        <PropertyValue Property="Value" Path="NetAmount"/>
    </Record>
</Annotation>
<Annotation Term="UI.DataPoint" Qualifier="Status">
    <Record Type="UI.DataPointType">
        <PropertyValue Property="Value" Path="SalesOrderOverallStatus"/>
    </Record>
</Annotation>
```
<br>Now, you need to reference the 2 DataPoints in HeaderFacets to display them in the header.</br>
<br>1. In the new line after closing UI.Datapoint#Status annotations, press CTRL/CMD + SPACE. From the options, choose UI.HeaderFacets annotation by pressing ENTER.</br> 
<br>2. Place the cursor between the Collection tags and press CTRL/CMD + SPACE to add a record for ReferenceFacet</br>
<br>3. Press CTRL/CMD + SPACE to choose annotation path as @UI.DataPoint#NetAmount.</br>
<br>4. Repeat steps 2 - 3 for creating another record for ReferenceFacet annotation and set its annotation path as @UI.DataPoint#NetAmount.</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>
```xml
<Annotation Term="UI.HeaderFacets" >
    <Collection>
        <Record Type="UI.ReferenceFacet">
            <PropertyValue Property="Target" AnnotationPath="@UI.DataPoint#NetAmount"/>
        </Record>
        <Record Type="UI.ReferenceFacet">
            <PropertyValue Property="Target" AnnotationPath="@UI.DataPoint#Status"/>
        </Record>
    </Collection>
</Annotation>
```
<br>*A ReferenceFacet node is used to reference another node in the annotation file, that defines the information you want to display (a DataPoint in our case).*</br>
<br>*The HeaderFacets node is the parent for all the ReferenceFacet nodes that you want to display in the header of the ObjectPage.*</br>
<br>*You can also notice that the revenue figure automatically comes with a currency.*</br>
<br>*This is due to annotations already configured for you in the metadata.xml file: the NetAmount and Currency properties are tied together using the sap:unit and sap:semantics annotations.*</br>

## CONFIGURE FORMS IN THE BODY
<br>In this step, you will define 2 sections in the ObjectPage that displays information about the sales order item and its related product in a form.</br>
<br>First, you need to define the first form that contains information about a sales order item.</br>
<br>1. In the new line after closing UI.HeaderFacets annotations, press CTRL/CMD + SPACE. From the options, choose UI.FieldGroup by pressing ENTER.</br> 
<br>2. Press CTRL/CMD + SPACE to add the Qualifier for your UI.FieldGroup annotation and add its value as "General"</br>
<br>3. Place your cursor between the Record tags and Press CTRL/CMD + SPACE to add Data property.</br>
<br>4. Place your cursor between the Collection tags and Press CTRL/CMD + SPACE to add DataField record.</br>
<br>5. Add path for Value property as "SalesOrder"</br>
<br>6. Repeat steps 4 - 5 for creating DataField records for properties "DeliveryCalendarDate", "GrossAmount" and "NetAmount</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>

```xml
<Annotation Term="UI.FieldGroup" Qualifier="General">
    <Record Type="UI.FieldGroupType">
        <PropertyValue Property="Data">
            <Collection>
                <Record Type="UI.DataField">
                    <PropertyValue Property="Value" Path="SalesOrder"/>
                </Record>
                <Record Type="UI.DataField">
                    <PropertyValue Property="Value" Path="DeliveryCalendarDate"/>
                </Record>
                <Record Type="UI.DataField">
                    <PropertyValue Property="Value" Path="GrossAmount"/>
                </Record>
                <Record Type="UI.DataField">
                    <PropertyValue Property="Value" Path="NetAmount"/>
                </Record>
            </Collection>
        </PropertyValue>
    </Record>
</Annotation>
```
<br>Now, you’re going to create the second form to display product information.</br>
<br>1. In the new line after closing UI.FieldGroup#General annotations, press CTRL/CMD + SPACE. From the options, choose UI.FieldGroup by pressing ENTER.</br> 
<br>2. Press CTRL/CMD + SPACE to add the Qualifier for your UI.FieldGroup annotation and add its value as "Product"</br>
<br>3. Place your cursor between the Record tags and Press CTRL/CMD + SPACE to add Data property.</br>
<br>4. Place your cursor between the Collection tags and Press CTRL/CMD + SPACE to add DataField record.</br>
<br>5. Add path for Value property as "ProductName’"</br>
<br>6. Repeat steps 4 - 5 for creating DataField records for properties "MainProductCategory’", "SupplierCompanyName", "NetProductPrice" and "Quantity"</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>
```xml
<Annotation Term="UI.FieldGroup" Qualifier="Product">
    <Record Type="UI.FieldGroupType">
        <PropertyValue Property="Data">
            <Collection>
                <Record Type="UI.DataField">
                    <PropertyValue Property="Value" Path="ProductName"/>
                </Record>
                <Record Type="UI.DataField">
                    <PropertyValue Property="Value" Path="MainProductCategory"/>
                </Record>
                <Record Type="UI.DataField">
                    <PropertyValue Property="Value" Path="SupplierCompanyName"/>
                </Record>
                <Record Type="UI.DataField">
                    <PropertyValue Property="Value" Path="NetProductPrice"/>
                </Record>
                <Record Type="UI.DataField">
                    <PropertyValue Property="Value" Path="Quantity"/>
                </Record>
            </Collection>
        </PropertyValue>
    </Record>
</Annotation>
```
<br>Finally, you are going to create the 2 sections that references the 2 forms you’ve just created.</br>
<br>1. In the new line after closing UI.FieldGroup#Product annotations, press CTRL/CMD + SPACE. From the options, choose UI.Facets by pressing ENTER.</br> 
<br>2. Place the cursor between the Collection tags and press CTRL/CMD + SPACE to add a record for ReferenceFacet</br>
<br>3. Press CTRL/CMD + SPACE to choose annotation path as @UI.FieldGroup#General.</br>
<br>4. In the next line, press CTRL/CMD + SPACE to add property Label and its string value as "General Information".</br>
<br>5. Repeat steps 2 - 3 for creating another record for ReferenceFacet annotation and set its annotation path as @UI.FieldGroup#Product.</br>
<br>6. Set its Label as string "Product Information"</br>
<br>Save the annotation file by clicking the ‘Save’ from File Menu or pressing CTRL/CMD + S. Your final annotation will look like below</br>
```xml
            <Annotation Term="UI.Facets" >
                <Collection>
                    <Record Type="UI.ReferenceFacet">
                        <PropertyValue Property="Target" AnnotationPath="@UI.FieldGroup#General"/>
                        <PropertyValue Property="Label" String="General Information"/>
                    </Record>
                    <Record Type="UI.ReferenceFacet">
                        <PropertyValue Property="Target" AnnotationPath="@UI.FieldGroup#Product"/>
                        <PropertyValue Property="Label" String="Product Information"/>
                    </Record>
                </Collection>
            </Annotation>
```

## RUN THE APP

In this step, you will preview the application. Right click on webapp and choose Preview Application from the menu. 


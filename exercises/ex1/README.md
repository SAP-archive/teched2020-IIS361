Exercise 1 - Generating a Fiori elements app
============================================

In this exercise, you will create a new SAP Fiori elements project In SAP Business Application Studio. For this exercise, you will not connect to a real backend system. Instead, you will use local metadata and mockdata files to simulate a backend server (mock server).

Exercise 1.1 Using the UI Generator
-----------------------------------

![](media/image1.png)

(1) In SAP Business Application Studio, open **File** menu.

![](media/image2.png)

(2) Click **New Project from Template**.

![](media/image3.png)

(3) Click on the tile **SAP Fiori elements application**.

![](media/image4.png)

(4) Click **Next**.** **

![](media/image5.png)

(5) In the template selection, click on the tile **Analytical List Page**.

![](media/image6.png)

(6) Click **Next**.

![](media/image7.png)

(7) In the step **Datasource and Service Selection**, select **Upload a Metadata Document**.

![](media/image8.png)

(8) Click **Browse for Files** icon to select the metadata file from the teched sample scenario folder.

![](media/image9.png)

(9) Open the folder hierarchy path **home-\>user-\>projects-\>teched2020-IIS361-\>exercises-\>ex1-\>resources**
and select **metadata.xml**. Click **Open**.

![](media/image10.png)

(10) Click **Next**.

![](media/image11.png)

(11) In the **Entity Selection** drop down, select **Z_SEPMRA_SO_SALESORDERANALYSIS** as main entity. The properties of this entity will be used to display data on Analytical
List Report page.

![](media/image12.png)

(12) Leave value for drop down **Navigation Entity** to **None** since you want to show data of a single instance of the main entity on the object page, too. Select **None** as a table type to accept the default one.

![](media/image13.png)

(13) Click **Next**.

![](media/image14.png)

(14) Choose an App Title, for example **Sales Order Analysis**

(15) Enter **soa** as namespace

(16) Enter **salesorderanalysis** as module name

![](media/image15.png)

(17) Click **Finish**. The project gets generated.

Exercise 1.2 Importing Mock Data Files
--------------------------------------

As you are working with the mock server in this exercise, you now need to import the sample data files used by this mock server to your project to simulate a real backend server data during the application preview. For this, copy the mockdata folder from the sample project.

When you choose to connect to an OData service or SAP system in step (7), this step is not needed.

![](media/image16.png)

(18) Expand the folder
**teched2020-IIS361-\>exercises-\>ex1-\>resources** 

(19)  Expand the newly created project folder **salesorderanalysis-\>webapp-\>localService**. Drag the **mockdata **folder to the localService folder in your generated project.

Summary
-------

You have successfuly generated a Fiori elements application based on the Analytical List Page and Object Page floorplans. In the next exercise, you will configure the content in the Alalytical List Page. 

Continue to [Exercise 2 - Configuring Content Area in Analytical List Page](../ex2/README.md)

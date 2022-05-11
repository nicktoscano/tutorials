## Exploring Oracle Spatial Studio

### Introduction:
Spatial Studio is a web application for visualizing and exploring geographic data in Oracle Database or Oracle Autonomous Database. Spatial Studio provides a visual complement to Oracle Spatial Database, but it also has built-in functions for rapid data exploration. Spatial Studio is a tool for business analysts to develop an awareness of their data. With that said, Spatial Studio is not a replacement for a Geographic Information System (GIS).

I have used GIS systems in various roles, including a military intelligence officer, a national intelligence analyst, and academia. There are several features I like about Spatial Studio. First, it provides a quick workflow for exploring spatial data in Oracle’s enterprise database system. Many times, analysts need to quickly answer basic questions, such as “is one feature in proximity to another feature?”. Spatial Studio can enable this quickly on static or real-time data. A second feature I like about Spatial Studio is that I can work with enterprise data without having to pull the data out of a performant and secure system, like a database. This means I can query and explore the whole body of data without being responsible for storing, securing, and managing it elsewhere. A third feature involves the ability to write more complex queries on my data at the database level using Oracle Spatial. This enables me to push complex queries or analyses to the database rather than the application level. A fourth feature that I like is the openness of the Oracle Database. GIS systems like ArcGIS can leverage Oracle database connections.  If I find data that requires more robust analysis, I can engage with a GIS system.

### About the data:  
I have loaded the <a href="https://www.kaggle.com/datasets/START-UMD/gtd">Global Terrorism Database (GTD)</a> into an autonomous database.  The dataset provided on Kaggle provides over 180,000 events from 1970 to 2017.

The workflow on Spatial Studio is fast. It involves the following steps:  Connect to a data source, create a dataset, and create a project. The rest of the work is all done within the project workspace. Here is a quick graphical walkthrough. 

### Step 1: Establish connection to database
You can either establish a connection to Oracle Database or Oracle Autonomous Database. You can have many database connections, but I find it best to work with one or two databases at a time. Because Oracle Databases are converged databases, you don’t have to create single purpose databases any longer and can minimize the number of data base you are managing. This means you can manage all your data in one place. This is a big win for analysts!

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image1.png" width="400" height="300">

***Image: Connect to a data source***

### Step 2: Pick your data 
You can select as many datasets as you need.  There are 3 choices for selecting data: 1. Load data from a file, 2. Choose a table or view from the database, 3. Choose a 3D tile (which includes batched or point cloud).  Many times, I find myself using a combination of data from a database and file.  This enables me to use enterprise data, but also add unique data that I have created.  You can load the following file formats: spreadsheet, shapefile, kml, csv, GeoJSON.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image2.png" width="400" height="300">

***Image: Create a dataset***

### Step 3: Create a workspace 
Projects contain workspaces. To open a project, click on the representative tile. You can also create new projects. To create a new project, select the blue ‘Create Project’ button. You can also view shared projects on this page.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image3.png" width="400" height="300">

***Image: Create a project***

### Let’s Talk Maps and Map Operations:
Below is an image of a dataset added to a map. You can work with point, line, or polygon on data. GTD is point data, so I have visualized them as red dots on the map. I can add as many layers as needed. Since my base map shows administrative boundaries, there is no need for me to clutter the map with additional data. I can turn off the boundary layer or remove it altogether.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image4.png" width="400" height="300">

***Image: Global Terrorism Data on a map***

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image5.png" width="400" height="300">

***Image: Global Terrorism Data with Administrative Boundaries***

### Adding Data to the Map:
Adding data to the map for visualization is easy in Spatial Studio. Select the plus sign on the right side of Data Elements and choose to add a dataset. An added dataset will appear under the list of datasets. You can then interact with the data by doing additional spatial analysis, removing the data, viewing properties, and expanding the data to view the attributes.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image6.png" width="400" height="300">

***Image: Adding data elements to the workspace***

Once the dataset is available, you can drag the data onto the map for visualization. This will automatically create a layer under the layers list and add a legend to the map. You can adjust the way the data looks through the layer settings. Click the hamburger menu next to the layer menu to find the settings option. I am using red circles here.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image7.png" width="400" height="300">

***Image: Working with layer settings***

You can zoom the map to different views and the data will scale automatically.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image8.png" width="400" height="300">

***Image: Zooming map***

### Symbolizing Data:

There are several options to symbolize data on the fly with Spatial Studio: circle, symbol, heatmap, cluster. You can see these in the first image below. Spatial Studio includes a library of map symbols that you can use for your data

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image9.png" width="400" height="300">

***Image: Symbolizing data***

For this map I am choosing circle and setting the size of the circle 2.  

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image10.png" width="400" height="300">

***Image: Setting the color of data points***

### Filtering Data:
Filtering is also very accessible. You can filter data in a couple of places in Spatial Studio. One is to choose a filtering tool from the spatial analysis operations menu. Another way is to filter directly on the layer using the layer settings.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image11.png" width="400" height="300">

***Image: Filtering data on the layer***

### Spatial Analysis:
Spatial Studio version 21.3.0 has 28 spatial analysis tools and 25 advanced analysis tools. Oracle calls these spatial analysis operations. You might think this is not very significant, given the amount of deep spatial analysis tools a geographic information system might have. Remember, Spatial Studio is not a GIS replacement. One benefit of having a smaller set of tools is that it requires less training and decision-making on the analyst’s part. Most people do not use all the analytic tools a GIS provides. Here the analyst only needs to familiarize themself with 53 options. 
Let’s face it, analysts are time-constrained people and don’t always have time to dig through multitudes of deep analytic tools. In some situations, having less can be more beneficial. Because Spatial Studio is an extension of the database, the analyst or data engineer can define additional analytics at the database level and pull those into Spatial Studio.  You can get to the spatial tools in 3 ways: from the data layer, from the dataset, or choosing to create a new analysis from the data elements menu. When you open spatial analysis, you will see the following menu that you can click on a specific tool or operation.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image12.png" width="400" height="300">

***Image: Spatial analysis tools***

I am not going to take up screen space by scrolling through them in this article.  You can find out more about the tools in the Oracle documentation for <a href="https://docs.oracle.com/en/database/oracle/spatial-studio/21.3/index.html">Spatial Studio</a>.

Here are two quick but powerful spatial tools for analysis.

### Return Shapes That are Within Inside Another
There are many any times that analysts need to reduce large dataset down to more localized areas.  In this example, we will reduce the GTD data down to just USA.  I am using a country layer that I pulled from <a href="https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html">Tigerline</a>.  The first thing I need to do is isolate the USA administrative boundary.  I do this using the tool called ‘Return elements filtered by non-spatial rules’.  I set my rule to equal USA only and add the resulting dataset to the map as a layer.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image13.png" width="400" height="300">

***Image: Creating non-spatial rules***

<image17.png> [USA boundary]

Next is we use the ‘Return Shapes That are Within Inside Another’ tool. We are going to return GTD datasets that fall within the US boundary. Easy enough. Below is a screen shot of the tool.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image18.png" width="400" height="300">

***Image: Clipping data by boundary lines***

Here is a screen shot of the final layer.  This takes seconds to run.  An analyst can continue to clip or reduce this data down by states and even counties.

<image19.png> [GTD in the US]

### Add a Buffer of a Specified Distance
A commonly used spatial tool if buffering. Buffering is used to determine the area covered within a specific location. For example, you may buffer school locations to visualize the areas within 1000′ feet of a school. I am adding an Airports layer pulled from <a href="https://hifld-geoplatform.opendata.arcgis.com/ ">HIFLD Open Data</a>, that we will buffer to see if any GTD data is within proximity. We can do the buffer directly from the dataset menu and add the result to the map to save time.

Select the buffering tool from the spatial analysis operations menu. Add a 20-mile buffer around all airports. This airports layer has individual 940 features to buffer.  

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image14.png" width="400" height="300">

***Image: Prepare a buffer operation***

Here is a zoomed in shot of buffers applied to the airport features provided in California.  This is just to show you the 
buffer result.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image15.png" width="400" height="300">

***Image: View the buffered data***

This is not too helpful. Let’s remove the layer from the map. Next, we will run the ‘Return Shapes That are Within Inside Another’ tool to see if any terrorist attacks fall within the buffer. This process will return any GTD features within the buffered Airports layer. My result came back with 2650 GTD incidents within 20 miles of an airport. Now analysts can work with this data to conduct any further analysis required. Below is an image of the results. I am not showing airports because it is too cluttered at this scale. As a next step, the analyst might add the airport data back onto the map and begin to work at a more local scale.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Exploring%20Spatial%20Studio/image16.png" width="400" height="300">

***Image: GTD data within 20 miles of airports***

###Conclusion:
Spatial Studio is a  tool for exploring geographic data in Oracle Database. It gives analysts a fast and simple workflow to explore spatial attributes. Many other spatial tools require pulling the data out of the secure and performant environment of the database to visualize and perform spatial queries and analysis. Spatial Studio works with data without removing it from the database. Keeping it in the database makes the analyst's job easier.



## Determine Proximity using Spatial Studio

### Introduction:
Determining proximity of people, places, and things is an important analytic step.  Determining whether threats are near critical infrastructure is an important information to understand for decision making.  There are many examples of things that can be considered threats to critical infrastructure.  Threats could include weather, overhead surveillance, natural disasters, protests, foreign military aggression, gangs or terrorism, cyber-attacks, and many more examples.  Analysts should be able to determine proximity quickly for decisions makers.  Oracle Spatial Studio provides a rapid method for determining proximity quickly.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/determine_proximity_using_spatial_studio/image1.png" width="400" height="300">

***Image: Proximity Map***

Data used in this tutorial:
I retrieved state administrative boundaries from <a href="https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html">census.gov</a>. Military installations are available on <a href="https://catalog.data.gov/dataset/tiger-line-shapefile-2019-nation-u-s-military-installation-national-shapefile">data.gov</a>. The traveler 1 and 2 data are fake data I created using QGIS.  

### Step 1: Create a New Project
The first step in Spatial Studio is to launch a new project.  A project is where you perform analytic inquiries and spatial visualizations.  Select the respective icon from the menu on the left side of the window.  It should be the second icon down. Once one the Project page, click the blue button to create a new project. 

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/determine_proximity_using_spatial_studio/image2a.png" width="400" height="300">

***Image: Create a New Project***

Projects include the tools and analytics to work with spatial data.  
From left to right:
1.  On this panel, you can add data elements and perform spatial analytics.
2.  This is the layer list.  The layers list contains the data added to the map.  You can use built-in symbology tools to customize map visualizations.
3.  This is the map panel to visualize data.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/determine_proximity_using_spatial_studio/image2.png" width="400" height="300">

***Image: Project screen***

### Step 2: Add Data Elements 
Data elements enable you to add new datasets to the project and conduct analysis. You will perform your spatial work here. The results can then be dropped onto the map and visualized. Click on the plus sign next to data elements. Select Add Dataset. A window will open with the available datasets for your project. 

For this project, I add the following data:
•	State boundaries
•	Military installations
•	Traveler 1 and traveler 2 data

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/determine_proximity_using_spatial_studio/image3.png" width="400" height="300">

***Image: Add Data Elements***

### Step 3: Filter Data
To build the map visualization for Florida, perform a SELECT and a CLIP function.  First, select the state boundaries layer and choose Spatial Analysis.  Select the tool ‘Return elements filtered by non-spatial rules’ to select the Florida state boundary.  Fill out the tool parameters and select Run.  I named the analysis results dataset Florida State Land Boundary.  Drag the result to the map.  The parameters should be as follows:

•	Column: Name 
•	Operator: Equals 
•	Value: Florida. 

Next, select the Military Installations dataset and select Spatial Analysis.  Use the tool ‘Return shapes that are INSIDE another’ to return ALL military installations inside the state boundary of Florida.  Instead of using INSIDE, a SELECT operation can be used on the military installation dataset.  Because the layer already contains an attribute column for the state name.  Either option will output the desired result.  Add the resulting layer to the map.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/determine_proximity_using_spatial_studio/image3b.png" width="400" height="300">

***Image: Select Spatial Tools***

The image below shows the ‘Return shapes that are INSIDE another’ tool.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/determine_proximity_using_spatial_studio/image3c.png" width="400" height="300">

***Image: Inside Tool***

The image below shows the ‘Return elements filtered by non-spatial rules’ tool.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/determine_proximity_using_spatial_studio/image3a.png" width="400" height="300">

***Image: Filter Data on Non-Spatial Rules***

### Step 4: Apply Proximity Analysis 
In this step, we are going to perform a proximity analysis.  You can perform a proximity analysis on Either the Travel 1 or Travel 2 data.  You could also join the datasets to perform a proximity analysis on the combined data.  For the example, I am performing proximity analysis on the Travel 1 dataset.  Select the Travel 1 dataset and choose Spatial Analysis.  Select 'Return Shapes Within a Specified Distance of Another' tool.  Set the parameters of this tool to be filtered by the Florida military installations layer you created earlier.  Set the distance to 1 and the unit to Mile.   Run the tool and add the result to the map as a layer.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/determine_proximity_using_spatial_studio/image4a.png" width="400" height="300">

***Image: Select Within Distance Tool***

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/determine_proximity_using_spatial_studio/image4.png" width="400" height="300">

***Image: Within Distance Tool***

### Step 5: Visualize the Data Spatially
To build the final visualization, add the results of the proximity analysis.  Use the layer symbology options to customize the features in a meaningful way.  Travel 1 and Travel 2 data layers provide context on the behavior of the larger population of data but don't need to be on the final visualization.  Less is sometimes more.  The two red dots are the proximity layer that shows which features were within the 1-mile buffer zone around military installations.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/determine_proximity_using_spatial_studio/image5.png" width="400" height="300">

***Image5: Evaluate Results***

### Step 6: Share Insights
Once you have finished your analysis and visualization, you can publish your project and provide a URL.  First, save your project.  Next, click the icon in the upper-right part of the screen called Publishing Project.  This option will create a shared project.  To view a shared project, return to the main Projects page.  Scroll to the bottom.  You will find your project in a section called Published Projects.  You can retrieve the URL to share the project from here.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/determine_proximity_using_spatial_studio/image6.png" width="400" height="300">

***Image: Share the Project***

### Conclusion:
Spatial Studio provides a fast and simple method for understanding the proximity between features in data.  An analyst may use the resulting proximity layer as a filter to identify possible relationships with other datasets.  Sharing a project is an easy way to communicate a proximity relationship to a decision-maker.  I hope this is a helpful demonstration of how to use Spatial Studio to explore data in the Oracle database.

You can find the presentation for this here: <a href="https://github.com/nicktoscano/presentations/blob/main/proximity_using_spatial_studio_ci.pdf">Github</a>



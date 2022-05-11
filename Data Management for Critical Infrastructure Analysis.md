## Data Management for Critical Infrastructure Analysis

### Introduction:

Protecting critical infrastructure is significant for national security. There are 16 critical infrastructure sectors. Information about the sectors is on the <a href="https://www.cisa.gov/critical-infrastructure-sectors">Cybersecurity & Infrastructure Security Agency</a> webpage. This data contains spatial attributes, which National security analysts need to visualize quickly.  This article provides a brief workflow to show analysts how to use Oracle Autonomous Database and Spatial Studio to visualize critical infrastructure data.

### Quick Introduction to Oracle Autonomous Database
Here is a quick introduction to Oracle’s Autonomous Database. Oracle Autonomous Database (ADB) is a converged database that provides a data management platform that can handle all types of data and includes in-database analytics. It is a good database for professionals that are not database engineers by trade. The autonomous database manages itself. Analysts do not have to learn how to perform complex database operations like migration, security patching, upgrades, etc. The analyst needs to understand how to get data into the database and access it, which Oracle makes easy with intuitive workflows and tools. Another highlight that I find attractive with Oracle ADB is that it has machine learning algorithms, graph algorithms, and spatial functions built into the database.   I can perform data exploration and run my analytics all in-database. In this article, I am demonstrating the use of data in an Oracle ADB with Oracle Spatial Studio.

### Database Structure for Critical Infrastructure Analysis
I recommend storing data in a single converged database using separate schemas for each data category. For example, there may be separate schemas for infrastructure and operational data. Schemas will keep the data categories separate but in one database. With 16 different infrastructure sectors, it may make sense to have a schema for each sector. 

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image1.png" width="400" height="300">

***Image: Using converged database for analysis***

For this project, I stored all my data in one schema.  This is because I am only using two datasets and there is no need for me to manage separate schemas on a small research scale like this.  The two dataset I am using are the <a href="https://www.start.umd.edu/gtd/">Global Terrorism Database</a> and a US Airports data set from <a href="https://hifld-geoplatform.opendata.arcgis.com/">Homeland Infrastructure Foundation-Level Data (HIFLD)</a>.

### Step1: Create or Access an Autonomous Database
The first thing to do is create a new ADB. You can do this by selecting the ‘Oracle Database’ tab in the console menu. Then select autonomous data warehouse (ADW). Once the page opens, you can click the blue button to create a new ADB. You need to check that you are in the correct compartment before creating a database.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image2.png" width="400" height="300">

***Image: Create an ADB***

Creating a new database is fast. Once this is complete, select the newly created database. Selecting the database should open the database details page, where you want to click the option to Service Console. In the future, you can choose Database Actions. Note: Your initial user is Admin. You will need to create a new database user for working purposes. You can do this under the Administration tab. Once you create your new user, log back into the database using that profile.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image3.png" width="400" height="300">

***Image: Database details***

You should now see the database launchpad. The launchpad is where we can begin doing work. I am using Data Load and SQL Developer Web, which I highlighted with red squares in the image below. I put an arrow on the image below to highlight where to create and manage database users if you need to add a new user.  

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image4.png" width="400" height="300">

***Image: Database launchpad***

### Step 2: Load Data into the ADW
To load data into the database, select the ‘Data Load’ tool on the menu. You will be brought to a To load data into the database, select the tool called Data Load from the menu. The Data Load Tool will open a new page that will walk through a two-step workflow for loading data. You can choose to load data from a local file, another database, or cloud storage.   In my example, I selected to load data from a local file. Selecting the next button will be able to drag and drop your dataset onto the webpage. 

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image5.png" width="400" height="300">

***Image: Setting the location of the data you want to load***

I am loading the Global Terrorism Database to my ADW. Once I drag the CSV onto the webpage, I can push the green run button to execute loading the data. The amount of time it takes to load the data will depend on the size of the file and your network bandwidth. Once this is complete, you will receive a notice that the process has finished. You can then retrieve the data from your ADW.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image6.png" width="400" height="300">

***Image: Loading data***

If you download the Airport data as a CSV, repeat this process.  If you download the data as a shapefile, load it into the database using Spatial Studio.

### Step3: Launch SQL Developer Web 
Now that we have loaded data into the ADW, launch SQL Developer Web. Once in SQL Developer, all the data tables granted to your user will be available. The image below shows the GTD dataset available in my database. I can run a quick SELECT query by dragging the table onto a blank worksheet in SQL Developer. The output of the SELECT query will print in the Result window. SELECT is a helpful way of quickly reviewing your data.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image7.png" width="400" height="300">

***Image: SQL Developer Web interface***

### Step 4: Explore and Analyze Data 
SQL is a powerful language for analytics.   Analysts can quickly answer questions about their data by executing repeatable SQL queries. For example, I can quickly perform a filter on the GTD table using a SELECT query. I demonstrate how to select all GTD events labeled successful terrorist attacks in the image below.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image8.png" width="400" height="300">

***Image: Filter on non-spatial attributes***

In practice, it’s unlikely that an analyst would need to return this many columns from the table. I can shorten the SQL statement by excluding all unnecessary columns.  In the image below, I use only the SUCCESS column and only values that equal 1.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image9.png" width="400" height="300">

***Image: Customizing SELECT query***

Finally, here is an example of running a buffer operation on a dataset in the database. Below I show an example of running a 20-mile buffer around the United States airports table in the database. I can also add this table to the map for visualization or use it to create a new data table with any GTD events that fall within the 20-mile buffer of the airports. 

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image10.png" width="400" height="300">

***Image: Performing a buffer using SQL***

### Step 5: Visualize Data in Spatial Studio
The last part of my example is to take the data we have loaded in the database and visualize it in Spatial Studio. There are a few steps to perform in Spatial Studio. First, establish a connection from Spatial Studio to the autonomous data warehouse using the database wallet (download the wallet from the database details page). Once there is a database connection, create a dataset and add it to a project for visualization. The image below shows the created GTD dataset in Spatial Studio. 

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image11.png" width="400" height="300">

***Image: Creating dataset in Spatial Studio***

Finally, you can add the data to a project for visualization.  When working within a project analysts can layer their data on a map for visualization.  They can also perform analytics right in the project.   Below is an example of adding the GTD data to a project for visualization.  

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image12.png" width="400" height="300">

***Image: Visualizing GTD data***

Here is a final example that shows the GTD events that fall within a 20-mile around airports in the United States.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/database_for_ci_analysis/image13.png" width="400" height="300">

***Image: GTD events near airports***

### Conclusion:
I hope this brief example is helpful. I have skipped over many things to make this a short article. I want to wrap back to the beginning and stress that good data management is critical for large data projects. In this example, I showed how infrastructure data could be stored in an autonomous database and then visualized for spatial analysis.  

You can find the presentation for this here: <a href="https://github.com/nicktoscano/presentations/blob/main/proximity_using_spatial_studio_ci.pdf">Github</a> 

Article for this here: <a href="https://medium.com/@ntoscano01/data-management-for-critical-infrastructure-analysis-f830cab313f7">Medium</a>

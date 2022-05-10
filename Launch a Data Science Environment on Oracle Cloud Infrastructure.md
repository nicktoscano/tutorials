## Launching a Data Science Environment on Oracle Cloud Infrastructure


### Introduction
Oracle provides several solutions for machine learning.  These solutions include in-database machine learning, AI services, automated machine learning, data labeling services, and data science service.

Oracle Cloud Infrastructure Data Science is an enterprise-grade tool for launching managed data science environments. Oracle’s data science service uses JupyterLab notebooks and launches with Python 3x. I recommend checking the current product documentation if you are concerned about the exact version of Python 3. Oracle data science has many unique features vital for enterprise machine learning operations, such as model management, a software development kit, and the ability to configure compute shape and storage specifications based on what you need and when you need it.

One of my top favorite features of Oracle’s data science service is the Environment Explore, which acts as a storefront for pre-configured Conda environments.  Pre-configured environments support many data science requirements, such as natural language processing, computer vision, graph analysis, data exploration, neurophysiology, and general machine learning.  If there is an environment you need that is not currently available, you can create it yourself.  A good example maybe is a specialized environment for spatial analysis.  You can also configure the pre-configured Conda packs for your needs.  

There are 42 pre-configured Conda environments available in Oracle Data Science Service currently.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image2.png" width="400" height="300">

***Image: Environment Explorer***

One of the immediate benefits of a managed data science service for any organization performing data science is the ability to launch new environments quickly.  Oracle Cloud Infrastructure provides a quick interface to launch a new service in minutes.  This article demonstrates a fast workflow to launch a data science service on Oracle's cloud.

The general steps to launching a data science environment are:
1.	Open the Resource Manager
2.	Create a Data Science Stack
3.	Create a Data Science Project
4.	Create a Notebook Session
5.	Start a Notebook Session
6.	Install Conda Packs
7.	Review Pre-installed Libraries
8.	Launch an Example Notebook
9.	
I recommend creating a new sub-compartment before creating a data science stack.  If anything goes wrong, you can destroy the stack or sub-compartment without endangering the remainder of your services.

### Step 1: Open the Resource Manager
Once you sign into Oracle Cloud, scroll down the page to the section titled Launch Resources and select Create a Stack. This option will bring you to the Resource Manager.  If you do not see this option in the Launch Resources section, you can search for Resource Manager from the search bar.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image3a.png" width="400" height="300">

***Image: Launch Resource Manager*** 

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image3.png" width="400" height="300">

***Image: Resource Manager*** 

### Step 2: Create a Data Science Stack
You should see Create a Stack page. A stack is a Terraform configuration. Terraform allows you to quickly provision resources with minimal effort. Ensure the radial for 'Template' is checked. Under stack configuration, select Change Template. A side panel will open where you can browse available templates. Select the Service tab and then choose Data Science. The data science template is the best way to initialize a data science environment. Templates save you time and money. The data science template will help lay down the resources needed to use a data science environment in the cloud, such as IAM groups and policies, the API Gateway, Functions, and Networking services. You can choose to build all of this infrastructure yourself. Oracle provides step-by-step instructions in the documentation, but why would anyone do that?

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image4.png" width="400" height="300">

***Image: Data Science Template***

### ***Fill out the Stack Specifications:***

1. Select the Data Science template.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image4a.png" width="400" height="300">

***Image: Step 1 - Select Template***

2. Input a Name and select the correct compartment to deploy the stack in.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image4b.png" width="400" height="300">

***Image: Step 2 - Input Name***

3. Accept the IAM group names and policy configurations without change. If IAM group names and policy configurations already exist, the template names need to be changed. 

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image4c.png" width="400" height="300">

Image: Step 3 - IAM Group and Policy Configuration***

4. Accept the VCN and subnets provided.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image4d.png" width="400" height="300">

***Image: Step 4 - Network Configuration***

5. You can choose the option to create a project and notebook session while creating the stack. I recommend leaving this option unchecked and creating these later.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image4e.png" width="400" height="300">

***Image: Step 5 - Project and Notebook Configuration***

6. Review the information for the stack.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image4f.png" width="400" height="300">

***Image: Step 6 - Review Information***

7. Check the Run Apply button and then hit create. Monitor progress on the job page.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image4g.png" width="400" height="300">

***Image: Step 7 - Run Apply***

### Step 3: Create a Data Science Project    
If there are no problems with the Stack configuration, it should build the environment within a couple of minutes. Once the Stack job completes successfully, you can return to the main OCI console page. Either search for Data Science in the search bar or select it from the hamburger menu. From the hamburger menu, find Analytics & AI and then choose Data Science. Since we did not create a Project when we created the initial stack, we will need to create a new Project now. Select the blue button called Create Project. This button will open a side panel. On the side panel, you need to make sure you have the correct compartment selected. Input a name for the Project. Finally, fill out a description and hit Create. I recommend creating projects for each type of job and filling out the description field with as much detail as possible.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image5.png" width="400" height="300">

***Image: Data Science Project***

This image shows that I have two active projects. I can manage my projects from this page. Management actions include viewing details, moving resources, editing, and deleting.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image5a.png" width="400" height="300">

***Image: Active Projects***

### Step 4: Create a Notebook Session
Next, we need to create a notebook. Select the active project that you created. On the Project Details, select the blue button Create a Notebook Session. One aspect I appreciate is that Oracle logically names the resources. Logical naming conventions make it easy to locate resources. Other infrastructure providers tend to make up silly names that have no meaning to resources. After selecting Create a Notebook Session, a side panel will open.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image5b.png" width="400" height="300">

***Image: Create a Notebook Session***

### ***Filling out the notebook side panel***
Creating a notebook session is straightforward. The important things here include assigning the correct compartment, choosing the compute shape, and amount of storage. You need to bring general information about your project requirements to select the storage needs and the compute shape.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image5c.png" width="400" height="300">

***Image: Creating a Notebook Session***

You can change compute and storage later. Below are screenshots showing options for computing shape. Minimum block storage is 50 GB. Maximum block storage is 10 TB. I recommend using the smallest amount of block storage possible for your project. Database and object storage are better choices for storing and managing data. Block storage is not the place for persisting data or code. It is most useful for short development or demonstration needs. 

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image5d.png" width="400" height="300">

***Image: Notebook compute options (GPU)***

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image5e.png" width="400" height="300">

***Image: Notebook compute options (VM Standard)***

To complete notebook creation, accept the default network requirements.  Click Create.

### Step 5: Start a Notebook Session
Select the active notebook session to launch your notebook. You should receive a request to sign in the notebook. Once you sign in, the notebook will launch. You should see the JupyterLab icon flash on the screen if the session launches correctly. You can bookmark the notebook address. In the future, select the notebook bookmark to launch the notebook without the OCI console. The notebook has many features to explore. You should see the Launcher tab, Environment Explorer, and the File Browser. The Launcher tab is where you will access the Environment Explorer, existing notebooks or kernels, terminal, and sample notebooks. It would be better suited to commit an entire article to a Notebook Session overview. I will not cover this here.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image6.png" width="400" height="300">

***Image: Launcher***

### Step 6: Install a Pre-Configured Conda Pack
I have noticed that sometimes it takes a few minutes for the pre-configured Conda packs to populate in the Environment Explorer. Once the environments populate, scroll through the available Conda packs and select one to install. More information about the Conda pack is available by clicking on the drop-down arrow to expand. Copy the install CDM, which should look similar to the following: odsc conda install -s <environment name>. Paste the install cmd in a new terminal and press enter to run. This cmd will launch an install activity.
  
The image below shows 42 Conda packs available when I wrote this.
  
<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image7.png" width="400" height="300">
 
***Image: Environment Explorer***

Check Environment and Review Installed Libraries:
Once the installation process is complete, you can inspect the environment. Activate the Conda environment using 'conda activate <environment name>'. Once activated, run 'conda env list' to print out a list of installed libraries.
  
<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image8.png" width="400" height="300">
  
***Image: Install Conda Environment***

### Step 7: Launch an Example Notebook
Oracle includes sample notebooks to help users get started with the pre-configured environments. The notebook also provides instructions for working with the software development kit and other resources in OCI, such as autonomous database and block storage.
  
<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image9.png" width="400" height="300">
  
***Image: Open Sample Notebook***
  
There are tabs along the top for quick access to documentation on environment explorer, sample notebooks, and first-time instructions. You can access sample notebooks from the Extensions tab on the Launcher menu. Available notebooks will depend on installed environments. Sample Notebooks are also in the Conda directory in the browser.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Launch_a_Data_Science%20_Environment_on_Oracle_Cloud_Infrastructure/image9a.png" width="400" height="300">
  
***Image: Sample Notebooks***
  
This concludes the demonstration on setting up a data science environment in Oracle Cloud Infrastructure.

### Concluding Tips
  
Update the Data Science Service. You should update the service when Oracle pushes out updates that include new conda packs and service features. Oracle will announce updates on their blog page and in the service documentation. You need to start and stop the notebook session to receive the update. You update the notebook session on the Project Details page. Select the three vertical dots next to the notebook session name. Select DEACTIVATE. Once the service deactivates, you can reactivate the service and receive the updates. Deactivating the service does not destroy code, data, or anything else on the block storage.
  
Don’t Terminate unless you mean to do it. Terminating kills the notebook session and blows away the block storage. Anything stored on block storage will go away permanently. I recommend using object storage or an autonomous database for managing data. Use Github to control your code.
  
You can find the presentation for this here: <a href="https://github.com/nicktoscano/presentations/blob/main/launch_a_data_science_environment_in_oracle_cloud.pdf">Github</a>
  
Article for this here: <a href="https://medium.com/@ntoscano01/launch-a-data-science-environment-on-oracle-cloud-infrastructure-5d232e080507">Medium</a>

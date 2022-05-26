## Using Conda with Oracle Data Science Service

Managing conda environments is easy with Oracle Cloud Infrastructure Data Science Service. Let me give you an overview.

Below is a screenshot showing a JupyterLab notebook session running on Oracle Cloud Infrastructure. This image is a managed notebook that I launched using the data science template provided in Oracle Resource Manager. The Environment Explorer contains a list of 42 pre-configured conda packs. Conda packs provide machine learning environments for many jobs, including computer vision, natural language processing, and general machine learning.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Using%20Conda%20in%20Oracle%20Data%20Science/image1.png" width="400" height="300">

***Image: JupyterLab notebook session***

To install the conda pack, copy and paste the install script into a terminal window. The installation process will create a directory called conda for the conda environment on block storage. Example notebooks are copied into the block storage directory called conda.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/Using%20Conda%20in%20Oracle%20Data%20Science/image2.png" width="400" height="300">

***Image: Conda environment description***

The image above shows the information provided about the conda environment. A complete description is in the documentation.

Pre-configured machine learning environments are a great way to get coding quickly. However, there are times when they may not be a good solution. For example, a data scientist may need a customer environment with libraries, not in the Conda pack or may need libraries of different versions. There are options for these scenarios:
1.	Modify the Conda pack to include the environment or library version that you need
2.	Create your Conda environment, which you can share as a Conda pack on the Environment Explorer

Oracle provides blogs and YouTube videos that show how to create Conda environments and Conda packs. I provide a simple 5 step process here with a presentation. Please refer to Oracle’s blogs, documentation, and YouTube videos for any potential updates to the process.

Steps to create your own conda environment:
1. Open or launch a notebook
2. Write a conda-compatible environment.yaml File
3. Create the Conda environment with odsc conda create Command 
4. Validate the new conda environment 
5. Publish the new environment 

You can find the presentation for this here: <a href="https://github.com/nicktoscano/presentations/blob/main/Using%20Conda%20in%20Oracle%20Data%20Science.pdf">Github</a>

Article for this here: <a href="https://medium.com/@ntoscano01/48e7d10a09bc">Medium</a>



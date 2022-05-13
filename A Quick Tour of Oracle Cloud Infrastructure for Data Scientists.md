## A Quick Tour of Oracle Cloud Infrastructure for Data Scientists

### Introduction
We are living in a multi-cloud world.  This means data scientists, analysts and machine learning engineers need to be versed in working across clouds.  Each cloud provider has their own tools, language, and workflows.  If we don’t have enough demands on our plate already, now the market expects us to be educated on cloud and understand how to perform complex workflows across multiple environments.  Yay! 

If you are like me, I bet you don’t have easy access to these clouds. 

To help the community, I want to provide a brief introduction of Oracle Cloud Infrastructure.  This will help you with understanding what some of the capabilities Oracle Cloud provides.  Additionally, Oracle provides a limited <a href="https://www.oracle.com/cloud/free/">free tier</a> account where you can explore the capabilities on your own.  If you do this, I recommend that you use <a href="https://apexapps.oracle.com/pls/apex/dbpm/r/livelabs/home">Oracle LiveLabs</a>, which provides guided exercises for machine learning and data science.

### Console Introduction
Getting to the resources you need quickly is necessary for any data scientist or machine learning engineer. Oracle does a great job of providing an intuitive dashboard to locate resources. You will find that resource names and locations are all very logical. There are no funny names for resources. Oracle calls things what they are. A data science service is called a data science service. Imagine that!

I recommend using Service Links to customize your console. This is like pinning apps to your desktop toolbar.

<image1.png> [Customize your console]

The console page contains a wealth of information and resources. Quickstarts provides ready-to-go learning resources and tools. For example, you can deploy a data science service with Oracle Red Bull examples, a Kibana dashboard, an autonomous database, and even R Studio from Quickstarts.

<image2.png> [Quickstarts]

Launch Resources provides more ready-to-go services. For example, you can launch a stack or start object storage from here. This section is handy for creating a data science service or moving data to the cloud.

<image3.png> [Launch Resources]

Finally, the Start Exploring section offers help documentation, free training, and other boring stuff like managing bills.

<image4.png> [Start Exploring]

### Hamburger Menu
I want to show you where to access machine learning resources in the cloud console. Right now, don’t worry about the infrastructure to make all this run. That stuff deploys quickly and easily through OCI. You can use a stack to automate that process anyways.

Clicking on the hamburger menu in the upper left-hand corner will produce a more detailed collection of resources. Here you can pin your commonly used resources to a quick access menu.

<image5.png> [Hamburger Menu]

### Analytics & AI
Scroll down and select the Analytics & AI menu.  This menu contains the core data science resources.  This includes data labeling, data science services, big data services, and AI services.  This also includes the data catalog, which I recommend everyone utilize.

<image6.png> [Analytics & AI]

### Oracle Database
The Oracle Database menu includes autonomous database options for a data warehouse or transaction processing. Oracle provides a data lake, as well. These are found under Analytics & AI and Big Data Services.

<image7.png> [Oracle Database]

### Storage
With object storage, you can organize and manage all your data. Once in storage, the data is read into a data catalog for discovery. In addition, Oracle Data Science, Oracle Machine Learning, AI Services, and Data Labeling all work with Object storage. This resource is very central to your workflow.

<image8.png> [Storage]

### Conclusion:
I hope this provides you with an introduction to the cloud console, what resources exist for data science and machine learning, and where to locate them.



## Train a Custom Computer Vision Model Using OCI Vision Service

### Introduction:
On Feb 7,2022 Oracle announced a new service for computer vision models: href="https://blogs.oracle.com/ai-and-datascience/post/announcing-oci-vision-service">Oracle Cloud Infrastructure (OCI) Vision</a>.  This service provides pretrained image analysis models and the ability to create custom computer vision models.  The OCI vision service enables analysts to quickly conduct image classification, image detection, and optical character recognition on image datasets.  Currently, the service supports JPEG and PNG.   

Here is a 5-step process for training a custom object detection model.  The data used for this example was retrieved from href="https://www.kaggle.com/datasets/rhammell/planesnet">Kaggle.com</a>.  Here are some samples of this dataset to show an example of what this data looks like:

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image1b.png" width="600" height="200">

***Image: Samples of planesnet dataset provided through Kaggle***

To complete this project on your own, you will need access to OCI Vision through Oracle Cloud Infrastructure. You can find the vision service listed underneath Analytics and AI and then AI Services.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image1.png" width="400" height="300">

***Image: Launch OCI Vision service from cloud console***

There are three methods for finding services on Oracle Cloud. You can type in the name of the service you are looking for in the search bar at the top of the console page; you can manually select the service under the hamburger menu on the left side of the page; or you can use the search bar provided in the hamburger menu.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image1a.png" width="400" height="300">

***Image: Locating services on cloud console***

### Step 1: Store data in object storage
The first step is to upload data to a bucket in object storage.  To do this, you will need to create a bucket in your object storage.  Select Storage under the cloud console hamburger menu.  Next, select buckets.  You can now create ai bucket.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image2a.png" width="400" height="300">

***Image: Create bucket***

Once created, select the bucket and upload data.  Because I work on my home network and my bandwidth is limited, I find that uploading batches of 100 – 200 images at a time works best.  You may experience better performance.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image2b.png" width="400" height="300">

***Image: Upload data***

Here is a screen shot of what your bucket may look like after loading data. The first item is an object created by the data labeling service.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image2.png" width="400" height="300">

***Image: Objects created in bucket***

### Step 2: Create a labeling dataset 
Oracle provides a data labeling service that can read images from object storage.  The labeled data from the service can then be used by other services, such as OCI Vision.  In this step, launch the data labeling service from the OCI cloud console (this service is also listed under Analytics and AI).  Select Datasets on the right side of the page.  On the service page, click Create dataset for labeling using Oracle’s built-in labeling service.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image3.png" width="400" height="300">

***Image: Create dataset for labeling***

When creating the dataset, you need to select what kind of data you are using in the form.  I am choosing images, since that is what we are working with.  I also selected Object Detection under Annotation Class.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image3b.png" width="400" height="300">

***Image: Setting up the labeling dataset***

On the next tab you will add files and labels.  For this, I chose Select from Object Storage and then entered in the required object storage information.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image3c.png" width="400" height="300">

***Image3c: Setting up the labeling dataset***

At the bottom of the form, you can assign labels to the service.  I started with a simple label – Plane.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image3d.png" width="400" height="300">

***Image: Assign labels***

### Step 2a: Label data for training
The data labeling service provides a built-in labeling tool to quickly label a sample set of data for training. This service helps to standardize labels used for machine learning projects. When finished export the labels to the object storage. The service currently covers the ability to create bounding boxes around objects of interest. You can then assign a label to that bounding box. More labels can be created on this screen, by selecting the +Label button.

Note: In this scenario, let’s pretend that you uploaded 1,000 images to a bucket. You label 100 of those images for model training. The remaining 900 images will not be used for training the model. However, you can go back to this labeling service and either label more of the remaining unlabeled images or add more images to the existing service.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image3a.png" width="400" height="300">

***Image: Adding Labels***

### Step 3: Create a project
Vision projects can be created and managed in the vision service.  In this step, select Project under Custom Models on the right side of the webpage.  Then select the blue button called Create project.  This will launch a form that will allow you to name your project.  I called mine Planes.  Once created, you can select your project and begin to create a model.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image4.png" width="400" height="300">

***Image: Create a vision project***

### Step 4: Train the model
On the Projects page, select the big blue button called Create Model.  This will open a form called Create and train model.  This form will walk you through the 3 steps required for creating a model.

Key items for this tutorial:
1.	Select Object Detection, under Choose model type to Train.
2.	Under Train data, select Choose existing dataset.
3.	Select a Data Source.  You can choose Data Labeling Service or Object Storage. I used Data Labeling Service, but you can assign it directly to a bucket.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image5.png" width="400" height="300">

***Image: Selecting training data for model training***

There are several training durations that can be selected.  You will need to choose based on your unique requirements.  For a simple demo, I recommend selecting either Custom Duration and setting it to 0.5 or choosing the Quick Training option.  Note: You must name the model to move on. I just called this model Planes Identification

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image5a.png" width="400" height="300">

***Image: Setting training duration***

The trained model will be managed under the respective project. On this page you can retrain or delete models.  You can have many active models at a given time in one project.

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image5b.png" width="400" height="300">

***Image: Managing models***

### Step 5: Test the model
Once the model is complete, it can be tested to see how well if identifies objects in the image.  Here I have used a similar image from a synthetic dataset.  This dataset has random images of planes over different type of terrain.  On this image the model needs to determine where planes are in the image with heavy vegetation.

You can visually see that the model did a good job of identifying objects that look like planes, given a short training window and only a few labels.  However, the overall performance is low and even the confidence scores themselves are low on the planes that it did detect.  I would expect this performance to improve, given more labeled data and a longer training duration.  This could be done quickly using the OCI services. In addition, you could add in new labels into the training dataset.

Actual Performance:
•	Identified 5 planes in the picture
•	Did not identify 7 planes in the picture (most of these were obscured)

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image6.png" width="400" height="300">

***Image: Testing a single image for accuracy***

Let’s test one more image, before creating more labels and retraining the model.  This time I selected an image to test in the model that does not contain any obscurity or trickery.  The model provides a better response against this image.  I would still like the confidence scores to be between 90 and 100%.  
<image6b.png> [Testing a single image for accuracy]

Here is an example of the JSON response showing the x and y coordinates for the bounding box around the object.  The service will produce and store this JSON response for every object in the image.  

<img src="https://github.com/nicktoscano/tutorials/blob/main/assets/train_custom_vision_model/image1.png" width="400" height="300">

***Image: JSON response***

### Conclusion:
In this tutorial you rapidly create an object detection model.  Setting up the services from scratch and completing this from start to finish should take about 1.5 to 2 hours.  This is based on selecting the lowest duration for model training.  This includes using the following services: Object Storage, Data Labeling, and Vision.  

You can find the presentation for this here: <a href="https://github.com/nicktoscano/presentations/blob/main/building_custom_vision_model.pdf">Github</a>



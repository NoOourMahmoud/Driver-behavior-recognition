# Driver behavior recognition
we chosed this project because approximately 1.35 million people die each year as a result of road traffic crashes some of the reasons that lead to these accidents are the lack of driver focus or distraction with anything else, such as answering on the phone, eating lunch, or lack of sleep, causing the driver to overlook while driving, so he has to take different types of drugs as one of the drivers said I am required to sit 24 hours and may reach 30 drivers on the road, so I have to take drugs to get over.

We implemented a machine learning model which takes its input videos from camera attached to the vehicle of the driver after cutting it into frames we enhance the images with image processing filters, then we determine the driver state as distracted, drunk,sleepy or none of them.

# Datasets used
We used three datasets one for each behavior

1- For distracted :  StateFarm dataset from Kaggle

It consists of 4 Giga images of drivers engaging in distracted behaviours divided to 10 Classes : 
Save driving
Texting (left or right hand)
Talking on the phone (left or right hand)
Operating the radio
Drinking
Reaching behind
Hair and makeup
Talking to passenger

dataset is divided into train-test In a ratio of 1 to 3 with about 22k images in train part.

Sample :

![Farmers Market Finder Demo](Distracted.gif)

Dataset link : [Distracted dataset](https://www.kaggle.com/c/state-farm-distracted-driver-detection/data) 

2- For sleepy :  from study made by Stanford university Consists of videos made by 27 volunteers we cut these videos into frames of images (one frame per second) Then we classiﬁed these frames to (sleepy or sober) manually.

Sample :

![Farmers Market Finder Demo](Sleepy.gif)

3- For drunk : DIF dataset

Dataset of Intoxicated Faces for Drunk Person Identiﬁcation By IBM which was collected from three web sites Youtube, Periscope, and Twitch.
The DIF dataset is divided into  1000 videos for drunk, and 400 videos for sober and we cut it into frames.

Sample :

![Farmers Market Finder Demo](Drunk.gif)

Dataset link : [Drunk dataset](https://github.com/vivekverma080698/vivekverma080698-Intoxication-Detection-using-PHOG-LPQ-Facial-Action-Units) 


# Preprocessing
Face Detection :

We choosed MTCNN pre-trained model for face detection.

Face Alignment :

preprocessing algorithm implemented in Python to adjust face position and angles.

Filters :

filter2D, bilateralFilter, medianBlur and fastNlMeansDenoising.


# Model
A composed model classifies the driver behavior into three main categories (Distracted, sleepy, drunk)

it consists of CNN models for the Distraction and drunkenness categories and landmark predictor for the sleeping category. 

-	we tried lots of CNN models like MobileNet, NasNetMobile, ResNet50
and finally found that final and best results were by:
•	VGG16 for the Drunkenness category with test accuracy of: 93.7%
•	VGG19 for the Distracted category with test accuracy of: 92.7%

-	We also tried [dlip face detector + face landmark predictor], [MTCNN
face detector + face landmark predictor] for the sleeping category and
finally found that final and best results was by:
• [MTCNN face detector + Face Alignment Algorithm + Face landmark
predictor] with test accuracy of: 82%



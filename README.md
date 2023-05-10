# xrayid


## Overview:
Neural Networks allow for a whole new world of classification solutions. Neural networks can pick up on patterns sometimes beyond the human eye. The challenge today is bringing a neural network to bear on identifying pnenomia in a human lung. 

## Business Problem:

For 60% of the world radiology is not an available medicine. While donated equipment is becoming increasingly available and technicians are being trained to operate them, radiologist able to correctly identify a radiological scan are not available in these countries.

Many have worked around the problem through telemedicine. Sending scans and X-rays to other radiologist who will read them and send back the results.  
Reading each scan takes on average 10 minutes. 

Resources are still limited and a neural network cannot and should not take the place of a trained doctor however if we could help the doctor identify the scans more efficiently.  
And thus we could help the doctor diagnose more patients in the same amount of time.  


## Data:

The data is collection of about 6000 X-rays of Children’s lungs taken by the university of California San Diego. University of California San Diego, Guangzhou Women and Children’s Medical Center Back in 2018.

  
In order to make our model more robust we used what is called a data generator. In essence it takes know pictures and makes slight alterations to them to improve the models performance.  


It takes an image, alters it, rotates its removes edges, alters the orientation of the image, changes the brightness all to create more examples for the model to train. 

When done right it allows for various perspectives of the same image, think of it like taking multiple pictures of an object but from a different angle to get a better 

Not every lung is positioned the same way when it is scanned. By giving more orientations the model could become more robust effectively making our limited data set a much large one but use of altering the information.


## Methods:

As mentioned we used a data generator to augment our data. Simply put it takes an image and then creates variations of that image to make the model have more information to train on. Things like rotating the image slightly a few degrees in a few directions, or shifting the center of the image and filling in empty space on either side all work.

There are a number of other considerations in our model.

We want to minimize false negatives, which means maximizing sensitivity. A validation metric that reflects this objective is recall, also known as sensitivity or true positive rate. Recall measures the proportion of true positive cases (i.e., correctly predicted positives) out of all actual positive cases. So, by optimizing for recall, we are prioritizing the identification of all positive cases, even if this means that some true negatives may be misclassified as false positives.





## Results:

*picture of results Versus training plots*




In the end we were able to identify a case of pneumonia using only an Xray 97% of the time. That is a pretty good model.  
For our untrained eyes its impossible for us to distinguish between these two images. This is a powerful tool.  

However, the model was unable to differentiate between viral and bacterial cases of pneumonia. Meaning for multi class identification problems the current approach was unable to function at these levels.  This would also suggest that the model would be unable to differentiate between pneumonia, and other respiratory disease, like lymphoma, COPD or others. Due to the laws protecting personal medical information data is not abundant for testing or training.

Further it is our belief that this model is operating based on a “brightness” approach, meaning what the model is detecting is just the presence of particles in the lungs, indicating an immuno-response, or foriegn bodies. 

Brighter being more “stuff” in the lungs for the x-ray to illuminate the stuff being virus/ bacteria and the bodies immuno-response to them.

Suggesting that this model is not especially qualified to identify pneumonia, but rather the presence of an immuno-response or more accurately the presence of particulate in the lungs.

To test this we tried reducing the image size as small 25x25 pixels. This resulted in a loss of accuracy for on testing data indicating that this theory was did not hold. However what patterns the model is detecting at high resolutions we don’t know.   The neural network being a blackbox model makes this difficult to determine. 



## Conclusions:

After some refinement our model was able to detect the presence of a pneumonia in 98% of the images it was trained on.
What we dont know is how long after being infected the patient was x-rayed, we are unsure when this model should be implemented.  

We would like the model to be able to differentiate between other respiratory diseases so as to not return false positives and further the ability to differentiate between bacterial and viral cases would go a long way allowing correct treatment without needing more invasive testing. However for the time being the model is able to identify when pneumonia is present.

We believe that what the model is really doing is identifying when a pair of lungs are healthy, as the model was unable to differentiate between two types of pneumonia it may also be unable to differentiate between pneumonia and say another disease.  


## Next Steps:

We’d recommend increasing the training images, and targets to include all respiratory illnesses and if possible to include patient charts as a factor in the networks decisions making.

# Learning to identify illegal landfills through scene classificationin aerial images

The classifier exploits ResNet50 as the network backbone and augments it with a Feature Pyramid Network (FPN) architecture. FPN improves performances in object detection when  different scales must be taken into account and thus can benefit also classification tasks in which objects of the same class appear with variable sizes.
This repository contains a ResNet50+FPN architecture.
![fpn (2)](https://user-images.githubusercontent.com/62382874/135090779-132cbc65-4ea1-4b2b-bad2-f8bc19bd00b8.png)

The architecture was trainned with a private dataset of remote sensing scene classifition for illegal landfills detection.

**Dataset:** The dataset consisted of 990 images containing illegal landfills locations and the double of images without them. Each image had a spatial resolution of 20cm per pixel and for each image a random size among 600, 800 and 1000 was chosen to provide context variation. From this dataset 75% was used for training and the 25% for validation and testing.
- Data augmentation: Flip and rotation.

**Training details:** The model was trained using two GPUs Nvidia GeForce RTX 2080Ti and the following parameters:
- Learning rate: 0.005
- Batch size of 12 (given the capacity of our server)
- Loss function: Binary Cross Entropy 
- Early stopping patience: 10  
- Early stopping min delta: 0.0005
- Pretrained model:  ImageNet pre-trained weights for ResNet50 backbone. Freezing the first two layers -the code of the backbone and the pre-trained weigths can also be found in this repository-. 

A sigmoid function is applied over the last FC layer of the CNN to obtain the actual prediction of the model, that for the binary case of illegal landfills is a value between 0 and 1. 

**Execution:** The notebook "execute_model.ipynb" provides an example of how to load the trainned model and execute it on an image to obtain the classification score as well as the CAMs.
We provided only two example images using Google Maps instead aof the source used for training, given that the dataset contains sensitive data provided to us under a non-disclousure agreement.

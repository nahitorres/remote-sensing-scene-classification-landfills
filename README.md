# Learning to identify illegal landfills through scene classificationin aerial images

This repository contains a ResNet50+FPN architecture.

The architecture was trainned with a private dataset of remote sensing scene classifition for illegal landfills detection.

Dataset: The dataset consisted of 3000 images, Each image had a spatial resolution of 20cm per pixel. A 30% of the images corresponded to illegal landfills and the rest to non-supicius areas. From this dataset 75% was used for training and the 25% for validation and testing.

Training details: The model was trained with a learning rate of 0.005, a batch size of 12 (given the capacity of our server), a Binary Cross Entropy loss function. Early stopping was used with a patience of 10 and a min delta of 0.0005. The model was pretrained with ImageNet freezing the first two layers -the code of the backbone and the pre-trained weigths can also be found in this repository-. A sigmoid function is applied over the last FC layer of the CNN to obtain the actual prediction of the model, that for the binary case of illegal landfills is a value between 0 and 1. 

The notebook "execute_model.ipynb" provides an example of how to load the trainned model and execute it on an image to obtain the classification score as well as the CAMs.

Since our dataset contains sensitive data provided to us under a non-disclousure agreement, we provided only two example images and not using the same source of images than that for the training but Google Maps instead.

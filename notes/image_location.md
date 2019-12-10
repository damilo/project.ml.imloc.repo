# Notes on image location problems
## Problem description
* Object localization means detecting *where* the image should and *what* it depicts, so given an image the problem becomes two smaller problems
    * Image classification
    * the localization itself, a regression onto image coordinates

### Image classification
* Using "classical" approach: fully connected layers on top of convolution layers with pooling layers
* categorical crossentropy as loss

### Image localization
* A regression onto four values:
    * x-coordinate of one corner of the object boundary
    * y-coordinate, same
    * The width of the box
    * The height of the box
    * *Note, why not coordintaes of opposite corners?*

### Common implementaion of image localization problems
* Both parts, classification and localization are on top of the same convolutional layers
* Only the fully connected layers leading to the respective output nodes are different
* The regression part might be attached to the last convolutional layer or the last fully connected layer of the regression part
* Loss function (was unclear)
    * Euclidian distance of corner points
    * IoU, intersect over union of the boxes (intesected area of boxes / (sum of areas minus intesection (otherwise counted two times)))


## Possible benchmarks to beat
* classification: as usual, choose class by random
* localization: none found, here are a few ideas:
    * Predicted box takes up 100 percent of the image

## RCNN implementation
* Take big pretrained image loclization network
* Retrain last fully connected layers, freezing convolutional layers on desired classes *and a "no object" class*
* Let neural network make proposals of possible boxes around object
* Save those parts of the image to disk
* Train one support vector machine for each class and let them classify the proposed image parts


## Sources
1. https://leonardoaraujosantos.gitbooks.io/artificial-inteligence/content/object_localization_and_detection.html
2. 
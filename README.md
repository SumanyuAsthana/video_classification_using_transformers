# video_classification_using_transformers
Made a model that relies on CNNs and transformers to classify videos
This was a freelance job and the method can be explained as follows:

DATA PREPROCESSING:
We are getting videos that may or may not show suspicious activity of 13 classes such as abuse,vandalism,robbery etc.

We start by preprocessing the data.

And the input of our model is as follows:
We break each video into a number of frames (nFrames)
We then choose an image size (frameSize) and reshape each image to that size
Therefore if we have 60 videos and we set nFrames=25 and frameSize=(100,100), our input for the model becomes of the shape (60 ,25,100,100,3) 
We may choose to standardize or normalize the dataset as well.
For each video we also have labels attached whether suspicious activity is there or not.

Once our preprocessing is complete we feed the data into the model.
There are two different types of models that I applied to deal with the problem.

MODEL 1:
Our model is made up of two parallel submodels.
Submodel1 :
We have a deep CNN network consisting of various Conv2Ds and maxpoolings.
This is followed by an attention based block. We simply pass the output of the CNN layer to a transformer encoder.
Submodel2:
We have a pretrained inception V3 
This is followed by an attention based block. We simply pass the output of the inception model to a transformer encoder.
We get the extracted features from both the submodels and we concatenate them.
This concatenation can be done through various methods: simple mathematical operations like summing or using convolutions or using attention.

After concatenation we pass the resultant data into a fully connected network that classifies the data into the classes.

MODEL 2:
This model is made up of a simple pretrained DenseNet (which is a CNN based model) followed by a transformer encoder.

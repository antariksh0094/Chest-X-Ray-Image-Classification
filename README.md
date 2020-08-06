# Chest-X-Ray-Image-Classification
In this time of COVID crisis, tools of medical diagnosis are critical for our well being. 
Chest-X-Ray images are used to conduct preliminary diagnosis of lung abnormalities.
I am trying to build an image classification model that can detect the presence of COVID-19 and other diseases by 
"looking" at CXRs, with more than 90% accuracy.

I have compiled the dataset from various Kaggle datasets as well as academic datasets. As medical data is protected information,
its a little difficult to find good quality CXR images with proper labelling. The same images are repeated across many datasets. 
I have seived through multiple datasets and created a set of total 11276 images, with:

2530 CXR images Bacterial Pneumonia, 
288 CXR images COVID-19, 
1122 CXR images which are Normal (no disease), 
5597 CXR images of Other Findings, 
394 CXR images of TB, 
1345 CXR images of Viral Pneumonia

As labelled CXR image data was not easily available, I am trying to use all images for training. As you can see, there 
is class imabalance in the dataset. I have also created a random subset of the above dataset for quick testing
(containing 3142 images), which has a more balanced distribution across classes.

I have used the following datasets to compile mine:

For Normal and Pneumonia CXRs (A very popular dataset on Kaggle by Paul Mooney) - 
https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia - 

For COVID-19 CXRs - 
https://github.com/agchung/Figure1-COVID-chestxray-dataset
https://www.kaggle.com/tawsifurrahman/covid19-radiography-database
https://www.kaggle.com/nabeelsajid917/covid-19-x-ray-10000-images

For TB CXRs - 
https://www.kaggle.com/kmader/pulmonary-chest-xray-abnormalities

For CXRs of numerous other lung diseases - 
https://www.kaggle.com/nih-chest-xrays/sample
(It is a randomly selected subset of the full NIH Chest X-Ray dataset (42 GB))

Tools -
Convolutional Neural Networks are the de-facto tools for state of the art image classification. We do not need to 
build CNNs from scratch, as many very powerful pre-trained models such as resent34, vgg16, resnet50, etc. are available 
for use. The weights of these models, after training on the IMAGENET dataset, are also available, and are a good
starting pont for training. 
KERAS is a powerful library for image processing. It has support for data augmentation and image data generation.
Another great library is the fastai library by Jeremy Howard. It is extremely easy to use, and non-verbose. I will begin 
training wihh fastai, and later move to keras.

Methodolgy - 
I will organise the data into separate folders based on the label (present in metadata files), and train the model 
on this data, without doing any preprocessing. Keras and fastai can directly infer the class name from the folder names.

Depending on the accuracy that we get, we can try various things - 
- data augmentation for less represented classes (we have very few images of COVID-19 compared to other classes)
- undersampling the over-represented classes
- cropping the images before training
- using a different model
- unfreezing and training inner layers of the pre-trained model

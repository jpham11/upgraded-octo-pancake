# upgraded-octo-pancake
Transfer Learning model to distinguish between sickle cell and normal blood cells.

# Introduction
This project attempts to utilize a transfer learning model using VGG16 to distinguish between whether an image contains regular blood cells or sickle cells within. A DCGAN model was also used to attempt adding more images to the dataset.

# Methodology DCGAN
First, the dataset was downloaded so as to be used by the DCGAN model. Though this script was written in Google Colab, it was executed in a local python environment and ran on a CPU due to the GPU not showing up despite being part of the aquired hardware.

The images in the dataset were converted from a .tiff to .png then labeled and placed into subfolders. There were about 900 images.

After importing necessary libraries, defining paths to the data directories, and defining training parameters, such as epochs, batch size, image size, latent dimension, and gradient penalty weight, a function to load images from the directory was defined.

The generator and discriminator were then defined using the Keras Sequential API. They both contained convolutional layers followed by a batch normalization and ReLU (generator)/LeakyReLU (discriminator) activation.

Loss functions were then defined for the generator and discriminator, with the generator loss being the binary cross-entropy between the discriminator's predictions on the generated images, while the discriminator being the average of the binary cross-entropy for both real and fake images.
A function was also used for calculating the gradient penalty for better stabilizing the GAN.

A training loop was then defined using a function for the training step of one batch of images, which included generating fake images, calculating the loss for both the generator and discriminator, calculating the graidents, and applying the gradients to update the model's parameters.
A function was then used to save the generated images at each 5 epochs.

The DCGAN was then trained by initializing the generator and discriminator models as well as the optimizers, utilizing the dataset from earlier.

At the end of the script a function was used to generate and save images. Despite adding many things, such as a gradient penalty and extra convolutional layers, the images that came out of the DCGAN did not amount to what was expected of it. So using only the dataset from earlier was attempted to train the transfer learning model.

# Methodology Learning Transfer Model
The dataset was uploaded to Google Drive to run the script on Google Colab, as for some unexpected reason the results, i.e. the confusion matrix and loss accuracy graph, were having issues with use of multiple versions of CUDA, cuDNN, and Python. Multiple instalations were attempted but did not succeed so Google Colab had to be used instead to run the process.

With that said, libraries and directories were established in the beginning.

An image data generator was used for training data as well as another one for testing data. Both rescales the images while the image data generator for the training data applies data augmentation as well, which include shear, zoom, rotation, width shift, height shift, and horizontal flips. They were then displayed to visually represent the augments as well as the labels.

The model was the constructed with multiple Conv2D and MaxPooling2D layers for feature extraction, followed by Flatten and Dense layers for classification. A dropout layer was used to prevent overfitting as well. The model was compiled with an Adam optimizer, binary cross-entropy loss, and accuracy as the metric.

Early stopping and model checkpoints were used for efficient training. The model was fitted on training data for a specified number of epochs, using validation data, and the callbacks.

The training and validation losses were then plotted and visualized. A confusion matrix was also displayed. These can be found in the results folder in the main GitHub repository.

The confusion matrix coincides with the Model_Loss_12.png, while Model_Loss.png does not have one due to Google Colab limiting the amount of time to use a GPU. The Model_Loss_12.png being 12 epochs, a batch size of 32, and a dataset of about 300, while the Model_Loss.png had 10 epochs, a batch size of 16, and a dataset of about 900. Wanting to get at least 10 epochs, Google Colab would always disconnect the runtime before being able to visualize the confusion matrix. An example can be seen in the bottom of the TransferLearning_Model.ipynb file.

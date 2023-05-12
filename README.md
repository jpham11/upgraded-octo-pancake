# upgraded-octo-pancake
Transfer Learning model to distinguish between sickle cell and normal blood cells.

# Introduction
This project attempts to utilize a transfer learning model using VGG16 to distinguish between whether an image contains regular blood cells or sickle cells within. A DCGAN model was also used to attempt adding more images to the dataset.

# Methodology DCGAN
First, the dataset was downloaded so as to be used by the DCGAN model. After uploading that folder of .tiff images to Google Drive, Google Colab was used to write the script for the DCGAN.

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

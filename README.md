# upgraded-octo-pancake
Transfer Learning model to distinguish between sickle cell and normal blood cells.

# Introduction
This project attempts to utilize a transfer learning model using VGG16 to distinguish between whether an image contains regular blood cells or sickle cells within. A DCGAN model was also used to attempt adding more images to the dataset.

# Methodology DCGAN
First, the dataset was downloaded so as to be used by the DCGAN model. After uploading that folder of .tiff images to Google Drive, Google Colab was used to write the script for the DCGAN.

The images in the dataset were converted from a .tiff to .png then labeled and placed into subfolders. There were about 900 images.

After importing necessary libraries, defining paths to the data directories, and defining training parameters, such as epochs, batch size, image size, latent dimension, and gradient penalty weight, a function to load images from the directory was defined.


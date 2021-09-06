# Semantic-Segmentation-with-U-Nets
The purpose of this project is to implement the U-Net Convolutional Network architecture, first proposed by Olaf Ronneberger, Philip Fischer and Thomas Brox in 2015. Although the U-Net model was originally developed for biomedical image segmentation, it has found great success in diverse multi-class segmentation tasks.

# Dataset
The dataset used to train and test the model, is a collection of images of water bodies captured by the Sentinel-2 Satellite. Each image is  associated with a mask image, in which the water body is highlighted. The dataset contains 2841 images and 2841 masks. Each of the images and masks were resized to 128 x 128 pixel images and normalized.
# Model Architecture
The U-Net model was implemented using the Keras Functional API from TensorFlow v2. The exact same architecture structure from the paper was used, only changing the the number of filters. The downsampling ('encoder') blocks used two Conv2D layers followed by a MaxPooling2D layer. Similarly, the upsampling blocks used two Conv2D layers, followed by a Conv2DTranspose layer. Skip connections were implemented by concatenation the correct encoder output with the decoder input. The final model contained ~ 8 million trainable parameters. Here's a summary of the model: <br/>
# Training
The model was trained on 2291 pairs of images and masks, with 250 images used for validation. The remaining 300 images were used for testing. Since there were 2 output classes (water-body and non water-body), the Binary Cross Entropy Loss function was used for gradient descent, which was optimized using the Adam algorithm. Training took place over 18 epochs, with a batch size of 32.
# Test Set Performance
# Improvements/Variations
# Application

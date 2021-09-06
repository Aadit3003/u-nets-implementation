# Semantic-Segmentation-with-U-Nets
The purpose of this project is to implement the U-Net Convolutional Network architecture, first proposed by Olaf Ronneberger, Philip Fischer and Thomas Brox in 2015. Although the U-Net model was originally developed for biomedical image segmentation, it has found great success in diverse multi-class segmentation tasks.

# Dataset
The dataset used to train and test the model, is a collection of images of water bodies captured by the Sentinel-2 Satellite. Each image is  associated with a mask image, in which the water body is highlighted. The dataset contains 2841 images and 2841 masks.
# Model Architecture
# Training
The model was trained on 2291 pairs of images and masks, with 250 images used for validation. The remaining 300 images were used for testing. Since there were only 2 output classes (water-body and non water-body), the Binary Cross Entropy Loss function was used for gradient descent, which was optimized using the Adam algorithm.
# Test Set Performance
# Improvements/Variations
# Application

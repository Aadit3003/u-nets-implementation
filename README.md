# Semantic-Segmentation-with-U-Nets
The purpose of this project is to implement the classic U-Net Convolutional Network architecture, first proposed by Olaf Ronneberger, Philip Fischer and Thomas Brox (2015). Although the U-Net model was originally developed for biomedical image segmentation, it has found great success in various multi-class segmentation tasks.

# Dataset
The dataset used to train and test the model, is a collection of images of water bodies captured by the Sentinel-2 Satellite. Each image is  associated with a mask image, in which the water body is highlighted. The dataset contains 2841 images and 2841 masks. Each of the images and masks were resized to 128 x 128 pixel images and normalized.
<img src="https://github.com/Aadit3003/Semantic-Segmentation-with-U-Nets/blob/8d7f91c55c06c7d08a50b0fd74fcff1d6c8f8556/Write%20Up/Train%20Dataset.png" width="600"><br/>
Credit:
- Dataset: [Satellite Images of Water Bodies](https://www.kaggle.com/franciscoescobar/satellite-images-of-water-bodies)
- The following Kaggle Notebook was immensely helpful in the data preprocessing steps: [Water bodies segmentation with UNet and Tensorflow](https://www.kaggle.com/baranowskibrt/water-bodies-segmentation-with-unet-and-tensorflow)
# Model Architecture
The U-Net model was implemented using the Keras Functional API from TensorFlow v2. The exact same architecture structure from the paper was used, only changing the the number of filters and the size of the input. The downsampling blocks used Conv2D and MaxPooling2D layers, whereas the upsampling blocks used Conv2DTranspose layers instead of pooling. Skip connections were implemented by concatenation of the encoder outputs with the  correct decoder inputs. The final model contained ~ 8 million trainable parameters. Here's a summary of the model: <br/>
<img src="https://github.com/Aadit3003/Semantic-Segmentation-with-U-Nets/blob/8d7f91c55c06c7d08a50b0fd74fcff1d6c8f8556/Write%20Up/Model.png" width="500"><br/>

# Training
The model was trained on 2291 pairs of images and masks, with 250 images used for validation. The remaining 300 images were used for testing. Since there were 2 output classes (water-body and non water-body), the Binary Cross Entropy Loss function was used for gradient descent, which was optimized using the Adam algorithm. Training took place over 18 epochs, with a batch size of 32.

# Test Set Performance
The model performed quite well on the test set images. It obtained a solid Mean IoU (Intersection over Union) score of 0.748, despite a modest number of training epochs. Here are some test set results which show the comparison between the true and predicted masks. <br/>
 ![Test Set](https://github.com/Aadit3003/Semantic-Segmentation-with-U-Nets/blob/e9307f4bd23caade7e51a57257ef1e32abff4e02/Write%20Up/Test%20Set%20Results%20%202.png)
# Possible Improvements
These are some suggestions to improve the performance of the classic U-Net architecture:
- **Data Augmentation**: Increasing the number of training samples and fixing some of the padding issues in the dataset would greatly help.
- **Different Architecture**: TernausNet uses the U-Net model with VGG11 Encoder, and has shown impressive results with the ImageNet dataset.
- **Increasing the number of training epochs**: Hardware accelerators like GPUs could significantly bring down training time, allowing for more passes through the dataset.

# Applications
U-Net and its variants find many applications in biomedical image segmentation tasks, such as:
- *BraTS*: Multimodal Brain Tumour Segmentation
- *Silver07*: Liver Image Segmentation
- *2D EM Segmentation*: Segmentation of neuronal strucrures in EM stacks

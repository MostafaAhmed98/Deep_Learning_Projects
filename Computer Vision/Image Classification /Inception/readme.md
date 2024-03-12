 ** Image Classification with Transfer Learning using InceptionV3**

![inceptionv3](https://github.com/MostafaAhmed98/Deep_Learning_Projects/assets/90983988/10394e92-3b82-4b20-aa2f-13fbae1ac72c)

**This project demonstrates how to apply transfer learning using a pre-trained InceptionV3 model to classify images.**

**Key steps involved:**

1. **Loading a Pretrained Model:** Load the InceptionV3 model, excluding the top classification layers.
2. **Freezing Pretrained Layers:** Freeze the weights of the pre-trained layers to preserve their learned features.
3. **Adding New Layers:** Add a new "head" to the model, consisting of a flatten layer, a dense layer, and a final sigmoid layer for classification.
4. **Data Preparation:**
    - Organize images into training and validation directories.
    - Apply data augmentation to the training data (rotations, shifts, flips) for better generalization.
    - Use ImageDataGenerator to generate image batches efficiently.
5. **Training the Model:**
    - Compile the model with an optimizer, loss function, and metrics.
    - Train the model using the fit method, monitoring validation accuracy.
    - Implement early stopping to prevent overfitting.
6. **Evaluation:**
    - Visualize training and validation accuracy over epochs.

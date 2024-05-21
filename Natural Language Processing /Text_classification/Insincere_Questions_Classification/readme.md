
## Sincere or Insincere Classification Using TensorFlow

### Introduction

This project focuses on building a deep learning model to classify text as sincere or insincere. It leverages pretrained word embeddings from TensorFlow Hub to embed text data and then uses a neural network for binary classification. The dataset used in this project is a subset of the Quora Insincere Questions Classification dataset.

### Key Components

1. **Data Loading and Preparation**: 
    - The dataset is loaded from a CSV file, which is zipped and hosted online.
    - The dataset is split into training and validation sets using stratified sampling to ensure the class distribution is maintained.

2. **Model Architecture**:
    - A pre-trained embedding layer from TensorFlow Hub is used to convert text into high-dimensional vectors.
    - The embedding layer is followed by two fully connected (dense) layers with ReLU activation functions.
    - The final layer is a single neuron with a sigmoid activation function for binary classification.

3. **Training**:
    - The model is compiled with the Adam optimizer and binary cross-entropy loss function.
    - Early stopping and TensorBoard callbacks are used to monitor training and prevent overfitting.

4. **Evaluation**:
    - The model's performance is plotted in terms of accuracy and loss over epochs.

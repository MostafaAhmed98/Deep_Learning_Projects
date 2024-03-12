![resnet](https://github.com/MostafaAhmed98/Deep_Learning_Projects/assets/90983988/f1737666-0a11-4ec5-8558-b3ce6a05af72)

This code implements a deep learning pipeline for training a ResNet50 model on a food image classification task:

**Data Preprocessing:**

1. **Loading and Organizing Images:**
   - Reads image paths and class information from a text file.
   - Creates a dictionary mapping class names to lists of image filenames.
   - Organizes images by copying them into corresponding class folders within a designated directory structure.
2. **Grabbing a Random Image:**
   - Defines a function to retrieve a random image path from the dataset.
   - Selects a random image path and opens the corresponding image.
3. **Creating a Mini Dataset:**
   - Defines a function to create a smaller dataset by copying a specific list of food categories from the main dataset.

**Data Transformations:**

- Defines separate transformations for training (with random augmentation) and testing (simpler for fair evaluation).
- Training transformations (using `RandomOrder`):
   - Applies random color, spatial, and other distortions for data augmentation.
- Testing transformations:
   - Resizes and normalizes images for consistency.

**Creating Datasets:**

- Prepares datasets for training and testing using `ImageFolder`:
   - Training dataset combines two datasets (augmented and non-augmented) to provide diversity.
   - Testing dataset uses non-augmented data for a realistic evaluation.

**Visualizing Transformed Images:**

- Defines a function to display original and transformed versions of randomly selected images.

**Dataloaders:**

- Sets up `Dataloaders` for training and testing using PyTorch:
   - Groups images into batches for efficiency.
   - Utilizes multiple CPU cores for parallel data loading.
   - Shuffles training data for better generalization.
   - Stores class names and their corresponding indices for later reference.

**Model Initialization:**

- Builds a ResNet50 model using the `Bottleneck` block as the residual building block.
- Instantiates a `ResNet50` model with the number of classes from the dataset and transfers it to the specified device (e.g., GPU).

**Loss Function, Optimizer & Scheduler:**

- Defines the `nn.CrossEntropyLoss` function for multi-class classification.
- Creates an Adam optimizer for updating model parameters based on the loss.

**Training and Testing Functions:**

- `train_step`: Trains the model on a data batch, calculating loss, backpropagating, and updating parameters. Tracks and returns average loss and accuracy.
- `test_step`: Evaluates the model on a data batch, calculating loss and accuracy. No backpropagation is performed here.

**Custom Callback: Save Best Model:**

- Defines a `SaveBestModel` callback that tracks the best validation loss and a waiting period.
- Saves the model, optimizer state, and epoch/test accuracy when a better validation loss is found (after waiting period).

**Early Stopping for Overfitting Prevention:**

- Implements `ValidationLossEarlyStopping` to prevent overfitting:
   - Monitors validation loss and stops training if it doesn't improve for a specified patience window.

**Training the Model:**

- Defines a `train` function that trains the model for a specified number of epochs.
- Performs training and testing steps in each epoch.
- Tracks and stores training and testing loss/accuracy.
- Calls `SaveBestModel` to potentially save the best performing model based on validation loss.
- Implements early stopping based on `ValidationLossEarlyStopping`.

**Plotting Loss Curves:**

- Defines a function to plot training and testing loss/accuracy curves from the training results dictionary.

Overall, this code provides a well-structured and documented deep learning pipeline for training a ResNet50 model on a food image classification task. It incorporates essential elements like data preprocessing, transformations, dataloaders, model definition, training, evaluation, and visualization.

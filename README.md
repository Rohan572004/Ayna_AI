# Ayna AI - U-Net Polygon Colorization

## Overview

This project implements an improved U-Net deep learning model for polygon colorization tasks using PyTorch. The model is designed to take grayscale polygon input images and predict their colored versions based on learned color embeddings. The training process leverages data augmentation, attention mechanisms, and combined loss functions to improve accuracy and generalization.

## Features

- **Improved U-Net Architecture:** Incorporates attention blocks and dropout layers for better feature learning and regularization.
- **Color Embeddings:** Uses learned embeddings to condition the model on polygon colors.
- **Data Augmentation:** Includes rotations, affine transformations, flips, and color jittering to enhance dataset diversity.
- **Combined Loss Function:** Utilizes a combination of Mean Squared Error (MSE) and L1 loss for better reconstruction quality.
- **Early Stopping & Learning Rate Scheduling:** Implements early stopping to prevent overfitting and adaptive learning rate reduction.
- **Weights & Biases Integration:** Tracks experiments, logs metrics, and visualizes predictions using wandb.
- **GPU Support:** Automatically uses GPU if available for faster training.

## Dataset Structure

The dataset is organized as follows:

```
dataset/
├── training/
│   ├── inputs/          # Grayscale polygon images for training
│   ├── outputs/         # Colored polygon images for training
│   └── data.json        # Metadata with polygon and color info
├── validation/
│   ├── inputs/          # Grayscale polygon images for validation
│   ├── outputs/         # Colored polygon images for validation
│   └── data.json        # Metadata for validation set
```

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/Rohan572004/Ayna_AI.git
   cd Ayna_AI
   ```

2. Create and activate a Python virtual environment (optional but recommended):
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install required packages:
   ```
   pip install -r requirements.txt
   ```

4. Create a `.env` file in the project root and add your Weights & Biases API key:
   ```
   WANDB_API_KEY=your_api_key_here
   ```

## Usage

Run the training script with default settings:

```
python improved_train_unet.py
```

You can customize training parameters by modifying the `Config` class in the script or by passing command-line arguments.

## Logging and Visualization

- Training progress, losses, and learning rates are logged to Weights & Biases.
- Periodic visualizations of input, target, and predicted images are available in the wandb dashboard.

## Checkpoints

- Model checkpoints are saved periodically in the `checkpoints/` directory.
- The best model based on validation loss is saved as `best_model.pth`.
- Final model is saved as `final_model.pth`.

## Contributing

Contributions are welcome! Please open issues or pull requests for bug fixes, improvements, or new features.

## License

This project is licensed under the MIT License.




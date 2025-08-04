# U-Net Polygon Colorization Report

## Hyperparameters

- **Learning Rate:** 5e-4  
  *Rationale:* A moderate learning rate to balance convergence speed and stability.  
- **Epochs:** 100  
  *Rationale:* Sufficient epochs to allow convergence on a relatively small dataset.  
- **Batch Size:** 8  
  *Rationale:* Small batch size to fit GPU memory and improve generalization.  
- **Optimizer:** Adam with weight decay 1e-5  
- **Scheduler:** ReduceLROnPlateau with patience 8, factor 0.7, min_lr 1e-8  
- **Early Stopping:** Patience 15 epochs to prevent overfitting.

## Architecture

- **Base Model:** Improved U-Net with encoder-decoder structure.  
- **Conditioning:** Color embeddings concatenated with input to condition the model on polygon color.  
- **Attention Blocks:** Added in bottleneck to improve feature focus.  
- **Dropout:** Applied in convolutional blocks for regularization.  
- **Output Activation:** Sigmoid to constrain output pixel values between 0 and 1.

## Training Dynamics

- **Loss Functions:** Combined MSE and L1 loss to balance pixel-wise accuracy and smoothness.  
- **Loss Curves:** Training and validation losses steadily decreased with occasional plateaus.  
- **Learning Rate:** Adaptively reduced on plateau, improving convergence.  
- **Qualitative Outputs:** Model successfully learned to color polygons with correct hues and shapes.  
- **Failure Modes:** Occasional color bleeding and shape boundary inaccuracies, mitigated by data augmentation and attention.  
- **Fixes Attempted:** Increased data augmentation, added attention blocks, and combined loss functions.

## Key Learnings

- Conditioning on color embeddings significantly improved color accuracy.  
- Attention mechanisms helped focus on relevant spatial features.  
- Data augmentation was critical for generalization on small datasets.  
- Early stopping and learning rate scheduling prevented overfitting and improved training efficiency.  
- Integration with Weights & Biases provided valuable insights through visualizations and metrics tracking.

---

This report summarizes the key aspects of the U-Net polygon colorization project, highlighting the design choices, training process, and lessons learned.

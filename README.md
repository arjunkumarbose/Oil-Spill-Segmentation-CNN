# Oil Spill Segmentation in Satellite Imagery using CNN with Explainable AI

**Authors**: Arjun Kumar Bose Arnob, M. F. Mridha, Meshal Alfarhood, Mejdl Safran, Dunren Che.

**Affiliations**: American International University-Bangladesh (AIUB), King Saud University, Texas A&M University–Kingsville.

**Corresponding Author**: [firoz.mridha@aiub.edu](mailto:firoz.mridha@aiub.edu)

---

## Key Features

- Custom CNN with spatial attention and residual connections
- Weighted loss function to handle class imbalance
- Grad-CAM integration for explainability
- Advanced on-the-fly data augmentation
- State-of-the-art segmentation accuracy and recall

---

## Results Summary

<img width="395" alt="Screenshot 2025-07-02 at 12 25 00 PM" src="https://github.com/user-attachments/assets/04b1ca2b-de59-4663-80e8-03034ae3ae24" />
<img width="395" alt="Screenshot 2025-07-02 at 12 25 00 PM" src="https://github.com/user-attachments/assets/04710dc3-efab-40bc-ad91-8ab5227213b9" />


---

## Dataset

We use the [Oil Spill Detection Dataset](https://m4d.iti.gr/oil-spill-detection-dataset/) provided by the M4D group. It includes:

- 1002 training samples, 110 test samples
- 5 classes: Sea Surface, Oil Spill, Lookalike, Ship, Land
- RGB-encoded masks for semantic segmentation
- Sentinel-1 SAR imagery validated by EMSA

> Access requires a request via M4D's dataset portal.

---

## Model Architecture

The architecture is a modified U-Net with spatial attention, dropout regularization, and skip connections.

<img width="1379" alt="Screenshot 2025-07-02 at 12 00 38 PM" src="https://github.com/user-attachments/assets/6a09200c-0dfb-4dd5-b141-d624d931ae47" />

_Figure: Proposed CNN model architecture with attention and residual connections._

---

## Training the Model

### Directory Structure

Organize your dataset in the following format:

```bash
data/
├── train/
│   ├── images/
│   └── masks/
└── test/
    ├── images/
    └── masks/
```

Each image should have a corresponding RGB mask. Images must be resized to **256×256** pixels before training.

### Key Training Details

- **Input Image Size**: 256×256
- **Batch Size**: 16
- **Epochs**: 50
- **Optimizer**: Adam
- **Learning Rate**: 1e-4 (adaptive)
- **Loss Function**: Weighted categorical cross-entropy
- **Augmentation**: On-the-fly (rotation, flip, blur, color jitter, etc.)
- **Early Stopping**: Based on validation loss
- **Dropout**: 10%–50% (varies by layer depth)

Approx. 49,600 augmented images were seen during training.

---

## Evaluation

Computes:

- Accuracy, Precision, Recall, F1-Score
- Intersection over Union (IoU)
- Class-wise classification report
- Grad-CAM visualization outputs
- Overlay plots for predictions vs ground truth

Sample outputs include:

- Overlay comparisons of segmentation masks
- Heatmaps of class activations
- Class-specific IoU bar plots


![figure7](https://github.com/user-attachments/assets/d32350d7-4942-4fe7-8441-e16f761f9db7)

_Figure: Comparison of original images, true masks, and predicted masks for oil spill segmentation._

---

## Explainable AI

We use Grad-CAM to provide class-specific attention heatmaps for interpretability. This will produce visual overlays showing which regions the model focused on during prediction.

![figure12](https://github.com/user-attachments/assets/38865e5b-9beb-432c-bb71-7ced28489db2)

_Figure: Grad-CAM visualization of model attention for oil spill and maritime feature detection._

---

## SOTA Comparison

<img width="1030" alt="Screenshot 2025-07-02 at 12 13 02 PM" src="https://github.com/user-attachments/assets/de129a6d-948c-4969-a732-624dcd771024" />

> Our model outperforms UNet, FMNet, and other baselines by up to **32.09%** in average recall.

---

## Contact

For academic or technical inquiries: [arjunkumarbosu@gmail.com](mailto:arjunkumarbosu@gmail.com)

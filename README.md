# Skin lesion classification with Pretrained CNN
This project implements a skin lesion image classifier using a pretrained ResNet-18 model, fine-tuned on the [Skin Lesions Classification Dataset](https://www.kaggle.com/datasets/ahmedxc4/skin-ds).

## Project Structure
```
skin-lesion-classification/
├── skin_lesion_resnet18.pth
├── skin_lesion_classification.ipynb
└── README.md
```

## Dataset  
The dataset used is the [Skin Lesions Classification Dataset](https://www.kaggle.com/datasets/ahmedxc4/skin-ds), which contains dermoscopic images organized into **15 different classes**.  

- **Structure:** The data is split into three folders — `train`, `val`, and `test` — each containing images for all 14 classes.  
- **Preprocessing:** Standard transformations (resize, converted to tensor, normalization) were applied to improve generalization.  
- **Batching:** Training was performed using mini-batches of 32 images.  

## Training

Run all cells in the notebook.
Saves best model (`skin_lesion_model.pth`) based on validation accuracy

## Results
The model was trained for **5 epochs**, with the **best model achieved at the last epoch**.  

- **Test Accuracy:** 83.45%  
- **Validation Accuracy:** 84.95%  

### Confusion Matrix

The matrix compares the predictions made by the model (columns) against the actual diagnoses (rows).  
The model is most effective at identifying:  

- **Melanocytic nevi:** 1,153 correct predictions  
- **Monkeypox:** 421 correct predictions  
- **HFMD:** 240 correct predictions  

The model shows poor performance on certain classes such as **Vascular lesions**, correctly identifying only 22 cases, indicating unreliability for this category.

<img width="840" height="729" alt="Confusion Matrix" src="https://github.com/user-attachments/assets/221a99e0-11b5-4137-af66-8ea1309c12c5" />

### Loss Curves

Both training and validation losses decrease over epochs and remain relatively close together, demonstrating that the model is improving its performance on both seen and unseen data.

<img width="691" height="470" alt="Loss Curves" src="https://github.com/user-attachments/assets/897dd5d0-d336-44ea-8f82-6f072be4e316" />

## Future Work  
1. **Bounding Box Lesion Localization** – Extend the model to detect and localize lesions within images, not just classify them.
2. Test improvement on the accuracy using more epochs (stronger GPU required) and also using more augmentation techniques.
3. **Multimodal Learning (Image + Text)** – Incorporate clinical metadata or textual notes alongside image features for improved diagnostic performance.  

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1-PtTMX8M3eF5wi0SSNwtZulHuAAKyH2g?usp=sharing)

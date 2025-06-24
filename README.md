# Nanoparticle Classification with SAM vs YOLO

## Project Goal

This project compares the performance of **Segment Anything Model (SAM)** and **YOLOv11** for classifying different nanoparticle shapes (triangles, dots, and cubes).  
We show that **SAM-based pipelines** significantly outperform YOLO—even with small datasets.

All data used in this project can be accessed here: [Google Drive Link](_____link_____)

---
## Performance Summary
results could be found in `Summary_Table.pdf` file.
---

## 📁 Repository Structure Description

- **triangles/**  
  Contains all scripts related to triangle-shaped nanoparticles.  
  Includes:
  - SAM segmentation and mask extraction
  - DINOv2-based feature extraction and classification (validation and test)
  - YOLOv11 training notebook for triangle data

- **cubes/**  
  Contains all scripts related to cube-shaped nanoparticles.  
  Includes:
  - SAM segmentation and mask extraction
  - DINOv2-based feature extraction and classification (validation and test)
  - YOLOv11 training notebook for cube data

- **dots/**  
  Contains all scripts related to dot-like nanoparticle classification.  
  Includes:
  - SAM segmentation and mask extraction
  - DINOv2-based feature extraction and classification (validation and test)
  - YOLOv11 training notebook for dot data

- **results/**  
  Contains output tables, performance metrics, and summary comparisons (e.g., Recall, Precision, F1-scores of SAM vs YOLO).

---
## File Descriptions

### 🔺 Triangles

- `cut_triangles_sam.ipynb`  
   Generates segmentation masks using the **SAM** model and saves cropped triangle regions.

- `triangles_silhouette_validation_dinov2.ipynb`  
   Extracts embeddings with DINOv2 for training and evaluating classifiers (SVM, RF, LR, NB) using silhouette & separation scores.

- `triangles_silhouette_test_dinov2.ipynb`  
   Evaluates model generalization on unseen triangle data. Includes PCA, confusion matrix, classification report.

- `yolo_training_triangles.ipynb`  
   Trains a **YOLO** model for detecting triangle subtypes. Includes data prep and model evaluation.

### 🧊 Cubes

- Same structure as the `triangles/` folder, using cube images instead.
  - `cut_cubes_sam.ipynb`  
  - `cubes_silhouette_validation_dinov2.ipynb`  
  - `cubes_silhouette_test_dinov2.ipynb`  
  - `yolo_training_cubes.ipynb`

### ⚪ Dots

- Same structure as the `triangles/` folder, using dot images instead.
  - `cut_dots_sam.ipynb`  
  - `dots_silhouette_validation_dinov2.ipynb`  
  - `dots_silhouette_test_dinov2.ipynb`  
  - `yolo_training_dots.ipynb`
 
---
## Data Availability:
 Data could be downloaded from: [nanoparticle-classificaation-data](https://drive.google.com/drive/folders/1GdorkrrcLbj-b55gbeYYuipEBSp8yCJm).
 data is divided into folders: Triangles, Dots and Cubes. 
 each folder includes a folder with full images with description in theyre name: train/valid/test and another folder with masked segmentations particles
 classified by the folder they're in (e.g for triangle data: "triangle" or "circle" or "truncated") and bbox description of where and in which image the parcticle
was originally found:

dataset_originalImage_x1_y1_x2_y2

where: (x1,y1) is the bottom left point and (x2,y2) is the top right point of bounding box.

for example:

> `triangles/truncated/triangle_train2_234_105_554_667.jpg`

means that object was segmented and masked from triangles data image "triangles_train2.jpg", classified as a truncated triangle and its bbox coordinates in original image are (x1,y1)=(234,105) (x2,y2)=(554,667).

for yolo training these annotations were transformed to yolo format annotations as shown in the yolo training notebooks functions to the following format:
for each original image_name.jpg we made a yolo_labels_image_name.txt file which looks like:

class_id, x_center_norm, y_center_norm, norm_width, norm_height

normalaized by original image size (w,h).
each image has as many lines as obejcts detected in it.

yolo labels could be found at: [yolo labels full images](link).

---


# DeepFake Detection: Classical Computer Vision vs Deep Learning

This project investigates DeepFake image detection by comparing classical computer vision techniques with modern deep learning approaches. The main objective is to understand whether performance is driven primarily by handcrafted features or by learned representations.

Developed as part of a Data Science workshop at the Open University of Israel.

## Project Goals

The project focuses on two main research questions:

1. Does representation learning outperform classical feature engineering for DeepFake detection?
2. Do learned representations generalize beyond a single generator family?

## Approach

The work was carried out as a full end-to-end pipeline, including data validation, exploratory analysis, model development, interpretability, and cross-dataset evaluation.

### 1. Data Cleaning and Bias Validation
- Verified dataset integrity
- Performed sanity checks
- Examined possible dataset biases before training

### 2. Exploratory Data Analysis
- Visual inspection of real and fake faces
- PCA analysis
- t-SNE visualization
- K-Means clustering

### 3. Classical Computer Vision Pipeline
- Dense SIFT feature extraction
- Bag-of-Visual-Words representation
- Linear SVM classification

### 4. Deep Learning Pipeline
- Transfer learning with ResNet-18
- Fine-tuning on the DeepFake classification task
- Evaluation on a held-out test set

### 5. Representation Analysis
- Extracted CNN embeddings
- Trained a Linear SVM on frozen ResNet embeddings
- Compared learned representations to handcrafted features

### 6. Interpretability
- Grad-CAM visualization to inspect which facial regions influenced the CNN predictions

### 7. Cross-Dataset Generalization
- Evaluated generalization under distribution shift
- Trained on StyleGAN-based data and tested on Diffusion-generated images

## Main Results

The project produced a clear empirical comparison between classical and deep approaches:

- **Classical SIFT + BoW + Linear SVM:** 76.8% accuracy
- **Frozen ResNet-18 embeddings + Linear SVM:** 93.2% accuracy
- **Fine-tuned ResNet-18:** 98.6% accuracy

In cross-dataset evaluation:
- **In-domain (StyleGAN):** 98.6% accuracy, AUC = 0.998
- **Cross-domain (Diffusion):** 84.5% accuracy, AUC = 0.964

These results show that learned representations are the main driver of performance, while also demonstrating meaningful cross-generator generalization under distribution shift.

## Key Takeaway

The findings of this project strongly suggest that DeepFake detection performance is fundamentally driven by representation learning. While classical handcrafted pipelines can detect some synthetic artifacts, deep learned features provide substantially stronger separation and better transferability.

## Repository Contents

- `deepfake_detection.ipynb` — full notebook containing preprocessing, analysis, experiments, visualizations, and results

## Authors

**Hadi Hleihil**  
Computer Science – Data Science Track  
Open University of Israel  

**Naomi Eisenstark**  
Computer Science  
Open University of Israel

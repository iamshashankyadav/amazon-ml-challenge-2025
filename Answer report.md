# ML Challenge 2025: Smart Product Pricing Solution

---

**Team Name:** Woo hoo!! We are Techie
**Team Members:** 1.Shashank Yadav
                  2.Farhan Alam
                  3.Amay Dixit
                  4.Sidhesh Kumar Patra  
**Submission Date:** 13-10-2025

---

## 1. Executive Summary

Our solution introduces a architecture that accurately predicts product prices by deeply analyzing textual descriptions . We integrate a pre-trained **BERT** model to understand text , feeding its insights into a final prediction layer. This approach allows our model to capture a comprehensive set of features, leading to significantly improved pricing accuracy.

---

## 2. Methodology Overview

### 2.1 Problem Analysis

During the Exploratory Data Analysis (EDA), we identified that a product's price is influenced by a combination of its textual description and its visual representation. The `catalog_content` contained rich textual information, while the product images provided visual cues that are highly correlated with the price. This led us to the insight that a multimodal approach, leveraging both text and image data, would be the most effective way to tackle this pricing challenge. Our analysis also revealed the need for robust preprocessing pipelines for both data modalities to handle missing values and normalize the features.

### 2.2 Solution Strategy

Our high-level approach is a  learning solution that combines the power of large language models for text understanding .

* **Approach Type:** Single 
* **Core Innovation:** Our core technical contribution is the development of a hybrid architecture that integrates a pre-trained **BERT** model for text processing . The embeddings from both models are concatenated and then passed through a regression layer to predict the final price. This allows the model to learn from both the textual features of the products, leading to more accurate price predictions

---

## 3. Model Architecture

### 3.1 Architecture Overview

Our model architecture is a two-stream deep learning network designed to process and fuse information from text and image data simultaneously.

1.  **Text Stream:** Product text data is fed into a pre-trained BERT model (`bert-base-uncased`) to generate contextualized embeddings.
2.  **Prediction:** This fused vector is passed through a regressiom-Layer  with dropout layers for regularization, which then outputs the final price prediction.



### 3.2 Model Components

#### Text Processing Pipeline

* **Preprocessing steps:**
    * **Parsing and Structuring:** The semi-structured `catalog_content` column was parsed by splitting the text by newline characters. A script was used to merge broken lines, and then key-value pairs were extracted to create new columns like `Item Name`, `Product Description`, `Bullet Points`, `Value`, and `Unit`.
    * **Feature Engineering:** A unified text feature, named `text`, was created by concatenating the content from `Item Name`, all `Bullet Point` columns, and `Product Description`. Missing values in these source columns were filled with an empty string before concatenation.
    * **Numerical & Categorical Imputation:** Missing values in the newly created `Value` column were imputed with the column's median. Missing values in the `Unit` column were filled with the string 'unknown' and the entire column was converted to lowercase.
    * **Text Cleaning and Normalization:** The `text` data was converted to lowercase, tokenized, and common English stopwords were removed using the NLTK library.
* **Model type:** BERT (`bert-base-uncased`)
* **Key parameters:** Max length = 128, Batch size = 32, Learning Rate = 2e-5


---

## 4. Model Performance

### 4.1 Validation Results

Our model was evaluated using the Symmetric Mean Absolute Percentage Error (SMAPE), achieving a highly competitive score on the validation set.

* **SMAPE Score:** **50.94**


---

## 5. Conclusion

Our multimodal solution, which uniquely combines BERT and a Vision Transformer, proved highly effective for the smart pricing challenge. By leveraging features from both text and images, we achieved a strong SMAPE score of 50.94, demonstrating the value of a holistic data approach. The key lesson learned was the importance of robust preprocessing and the synergistic power of fusing different data modalities to solve complex prediction tasks.

---

## Appendix

### A. Code artefacts

https://drive.google.com/drive/folders/1NiRKcGZ1lJOOo2WddTwh9qhFVD8clJ1f?usp=sharing


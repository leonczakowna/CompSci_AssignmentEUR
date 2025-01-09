# **Product Feature Cleaning, Clustering, and Duplicate Detection**  
### *Computer Science Individual Assignment*  
##### Author: **Oliwia Monika Leończak**  
##### Student ID: 595644  

---

## **Overview**  
This project performs data cleaning, feature extraction, clustering, and duplicate detection for product information. It utilizes advanced techniques such as MinHashing and Locality Sensitive Hashing (LSH) to identify potential duplicates and evaluates its effectiveness using a bootstrap-based evaluation.  

The dataset used in this project is stored in JSON format (`TVs-all-merged.json`) and represents a collection of product entries from various sources.

---

## **Key Features**  

### **1. Aquiring potential duplicates out of the titles**
- Exstracts potential duplicates candidates out of the title for further enhancements of the matrics.

### **2. Data Cleaning and Normalization**  
- **Title Cleaning**: Removes punctuation, unifies units, and eliminates redundant information from product titles.  
- **Feature Standardization**: Normalizes units and merges synonymous features into unified attributes. Leaves only features with count above 300 occurences. 

### **3. Model Words Creation**
- Creates a model words list from cleaned product titles and feature sets.

### **4. Feature Vectorization**  
- Transforming product individual model word lists into binary vectors for similarity analysis.

### **5 . MinHashing and Locality Sensitive Hashing (LSH)**  
- Implements **MinHashing** to create compact representations of product features.  
- Applies **Locality Sensitive Hashing** (LSH) to identify candidate pairs of duplicates efficiently.  

### **5. Similarity Computation and Deduplication**  
- Employs Jaccard Similarity for refined duplicate detection using the Multi-component Similarity Method with Pre-selection (MSMP).  

### **6. Bootstrap-Based Evaluation**  
- Evaluates model effectiveness using bootstrapping (10 bootstrapps with 63% of original data used as train data) to compute metrics such as precision, recall, pair quality, pair completeness, F1* and F1-scores for four scenarios: LSH, LSH with potential duplicates extension, MSMP and MSMP with potential duplicates extension.  

---

## **Installation**  
**Required Libraries**:  
   - `numpy`  
   - `pandas`  
   - `tqdm`  
   - `nltk`  
   - `scikit-learn`  
   - `matplotlib`  
   - `scipy`  

## **Evaluation Metrics Explained**
- True positive (TP) = pairs of products that are predicted to be duplicates and are real duplicates
- False positive (FP) = pairs of products that are predicted to be duplicates but are real non-duplicates
- True negative (TN) = pairs of products that are predicted to be non-duplicates and are real non-duplicates
- False negative (FN) = pairs of products that are predicted to be non-duplicates but are real duplicates

- Precision = TP / (TP + FP)
- Recall = TP / (TP + FN) 

To evaluate the performance of the algorithm the average F1-measure (harmonic mean between precision and recall) is used. 

- Pair Quality = (number of duplicates found) / (number of comparisons made)
- Pair  Completeness = (number  of  duplicates  found) / (total  number  of  duplicates)

To evaluate the performance of scalability solution F1*- measure (harmonic mean between pair quality and pair completeness) is used.  

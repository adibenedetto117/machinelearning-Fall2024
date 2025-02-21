# Income Classification and Regression Models Using Illinois ACS Housing Data

## Authors  
Anthony DiBenedetto  
Claire Griffin  
Nathaniel D. Padal  
Brad Baldys  
**Engineering, Computing, and Mathematical Sciences**  
**Lewis University, Romeoville, IL, United States**  

## Contact  
- Anthony DiBenedetto: [anthonypdibenedett@lewisu.edu](mailto:anthonypdibenedett@lewisu.edu)  
- Claire Griffin: [clairekgriffin@lewisu.edu](mailto:clairekgriffin@lewisu.edu)  
- Nathaniel D. Padal: [nathanieldpadal@lewisu.edu](mailto:nathanieldpadal@lewisu.edu)  
- Brad Baldys: [bradhbaldys@lewisu.edu](mailto:bradhbaldys@lewisu.edu)  

---

## Overview  
This project applies machine learning techniques to predict household incomes using Illinois-specific data from the **2013 American Community Survey (ACS)**. We developed and tested two separate models:  
1. **A convolutional neural network (CNN) for income regression**  
2. **A CNN-based logistic regression model for income classification**  

The primary objective is to explore how deep learning methods can be leveraged to fill data gaps in socio-economic research, providing more accurate income predictions where household data is missing.

---

## Key Features  
- **Data Source:** 2013 ACS Housing Data (Illinois-specific)  
- **Models Used:**
  - CNN for regression
  - CNN for classification (binary income classification)  
- **Preprocessing Steps:**  
  - Feature selection  
  - Handling missing values using imputation techniques  
  - Exclusion of extreme incomes (>$200,000 for regression)  
  - Income classification threshold set at $50,000  
- **Performance Metrics:**  
  - **Regression Model:**  
    - Mean Absolute Error (MAE): **27,832**  
    - R-Squared Score: **0.373**  
  - **Classification Model:**  
    - F1-Score: **0.77**  
    - Area Under Curve (AUC): **0.85**  

---

## Dataset and Preprocessing  
The dataset was sourced from the **2013 U.S. Census ACS Public Use Microdata Sample (PUMS)**. The following attributes were selected for modeling based on relevance and prior research:  
- Number of bedrooms  
- Household size  
- Number of children  
- Property value  
- Land size  
- House tenure  
- Number of vehicles  
- Household type  
- Household language  
- Internet access  

### Data Cleaning:  
- **Missing values**: Addressed using a proximity-based imputation technique  
- **Extreme values**: Capped at $200,000 for regression  
- **Income classification threshold**: $50,000 based on Illinois low-income standards  

---

## Model Architecture  

### CNN Regression Model  
- Input layer reshaped to match dataset features  
- 4 convolutional blocks, each containing:  
  - Two **1D convolutional layers** (kernel size = 3, ReLU activation)  
  - Max-pooling (pool size = 2)  
  - Batch normalization  
- Fully connected layers: 512, 256, 128, and 64 neurons with dropout (50%)  
- Final output: Single neuron (linear activation)  

### CNN Classification Model  
- Similar to the regression model, but the final layer uses **softmax activation** for binary classification  

### Training Process  
- **Optimizer:** Adam  
- **Loss function:**  
  - Mean Squared Error (MSE) for regression  
  - Binary Cross-Entropy for classification  
- **Batch size:** 64  
- **Early stopping:** Stops training after 10 consecutive epochs without improvement  

---

## Results  

### Regression Model Performance  
| Metric  | Value |  
|---------|--------|  
| **Mean Target Income** | 71,470 |  
| **Mean Prediction** | 71,050 |  
| **Median Target** | 63,000 |  
| **Median Prediction** | 70,445 |  
| **R-Squared** | 0.373 |  
| **Mean Squared Error (MSE)** | 1.28885e+09 |  
| **Mean Absolute Error (MAE)** | 27,832 |  
| **Baseline MAE** | 37,041.5 |  

---

### Classification Model Performance  
| Class | Precision | Recall | F1-Score | Support |  
|-------|-----------|--------|----------|---------|  
| 0 (Low Income) | 0.72 | 0.75 | 0.73 | 3,709 |  
| 1 (High Income) | 0.83 | 0.80 | 0.81 | 5,583 |  
| **Overall Accuracy** | **0.78** | | | 9,292 |  
| **AUC (ROC Curve)** | **0.85** | | | |  

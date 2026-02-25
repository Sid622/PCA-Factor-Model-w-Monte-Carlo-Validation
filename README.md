PCA Factor Model with Monte Carlo Validation

Project Overview: 
This project identifies risk factors that drive portfolio returns by applying dimensionality reduction to historical stock data. PCA shows that portfolio variance can be explained by about 3-4 systematic factors. This stability is later validated through a Monte Carlo simulation. 

Goal: 

1. Compress a 15-dimenstional return matrix into 3-4 principal components

2. Perform factor interpretation on the mathematical components

3. Prove factor stability using bootstrapping to ensure validity

Mathematical Framework - PCA aims to reduce dimensionality of a 15-stock return matrix while trying to retain the maximum amount of variance. The process follows these steps. 

1. Covariance Matrix: We compute the 15 x 15 matrix of standardized stock returns to identify how assets move in relation to each other

2. Eigenvalue Decomposition

lambda = diagonal matrix of eigenvalues (how much variance each PC explains)

V = matrix of eigenvectors (the direction of each PC in the 15x15 matrix)

3. Principal Components

PC1(Main Eigenvector): The unit vector captures the direction of the highest variance in the data. This is typically beta in finance. Next, subsequent components are created to be orthogonal to the previous ones. This ensures each factor represents a uncorrelated source of risk. 

4. Dimensionality Reduction: By selecting only the components with eigenvalues > 1 (Kaiser Criterion), we filter out noise and retain only the statistcally significant drivers.

Main Steps

1. Data Collection

Dataset: Four years of daily returns from 01-01-2022 to 01-01-2026 with 15 stocks across technology, finance, 
energy and consumer sectors. Standardized returns to ensure equal weighting

2. Principal Component Analysis

Computed correlation matrix across assets and then performed eigenvalue decomposition
to extract PC's. Calculated factor loadings to interpret the economic meaning of 
each PC and then applied the Kaiser criterion for factor selection to ensure each 
factor was stable and not noise. 

3. Monte Carlo Validation

Bootstrap sampled with replacement (1,000) iterations and re-ran PCA on each sample to
test the factor stability. Calculated 95% confidence intervals for eigenvalues to
distinguish factors from sample noise. 

Key Results

Factor: 
PC1 Interpretation: Market Factor (Beta)
Eigenvalue = 6.03 (5.58-6.50)
Explained Variance = 46.63%

PC2 Interpretion: Value vs Growth rotation
Eigenvalue = 2.36 (2.18-2.54)
Explained Variance = 15.70%

PC3 Interpretation: Quality or Size
Eigenvalue = 1.49 (1.36-1.62)
Explained Variance = 7.83%

PC4 Interpreation: Momentum Reversal
Eigenvalue = 1.19 (1.11-1.29)
Explained Variance - 6.85%

Correlation Matrix

<img width="763" height="605" alt="image" src="https://github.com/user-attachments/assets/e3b89147-6898-40b9-99d4-30043604cd0f" />


Factor Loadings

<img width="766" height="590" alt="image" src="https://github.com/user-attachments/assets/59f95f66-9b35-477c-ba64-4fabd63810a9" />

Red (Positive) = Stock moves with the factor
Blue (Negative) = Stock moves against the factor
White (Zero) = Stock is barely moved by the factor

PC1: All stocks are red (0.43-0.85). When the market goes up, everything
else goes up together.

PC2: MSFT, CVX, BAC are positive (value stocks). AMZN, NVDA, JPM are negative
(growth stocks). This shows the rotation between growth and value regimes. 

PC3: TGT, WMT, WFC, are strongly positive (0.44-0.61) while the rest are near
zero. While consumers are spending, stocks move together. 

PC4: Mixed colors, no pattern. Confirms this is noise and not a real factor.

This matters because instead of tracking multiple stocks, we can track 
3 key factors and understand 77% of what is happening. 

Factor Stability
<img width="757" height="611" alt="image" src="https://github.com/user-attachments/assets/c0d5533c-a39b-47c3-9025-7e6d45d8f8db" />

<img width="750" height="568" alt="image" src="https://github.com/user-attachments/assets/19fdb43d-ffeb-4b9c-a223-97b049300732" />

<img width="749" height="567" alt="image" src="https://github.com/user-attachments/assets/13d32d73-3454-4f52-9cea-b0dfa5a61ab4" />


As seen by the eigenvalue stability of all factors, PC1 and PC2 are very stable as their eigenvalue always stays well above the Kaiser criterion(>1) and never dips below 2. PC3 on the other hand is ranging from about 1.1-1.3
which means that the consumer factor can change frequently but is always above the Kaiser Criterion. Therefore, it is a real factor but weaker and more sensitive when time periods are changed. PC4 significantly falls below 1
and in 10-15% of samples, the eigenvalue drops below 1 meaning it would not qualify as a factor meaning it is sample dependent. 





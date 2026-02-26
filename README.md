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
All stocks are red (0.22-0.81). When the market goes up, everything else goes up together. 

PC2 Interpretion: Value vs Growth rotation
Eigenvalue = 2.36 (2.18-2.54)
Explained Variance = 15.70%
NVDA, JPM, and AMZN all have high loadings while MSFT, CVX, and COP all have low loadings as seen from the factor correlations graph. This shows a sector rotation in the sense that when investors prefer highly volatile growth stocks (NVDA, JPM, AMZN), they rotate out of the traditional value stocks in the energy/defensive sectors. 

PC3 Interpretation: Quality
Eigenvalue = 1.49 (1.36-1.62)
Explained Variance = 7.83%
Strong positive correlations in JNJ and XOM which are seen as stable companies. Surprisingly, GOOG is also present here instead of PC2 which indicates it could have traded like a mature tech company instead of a speculative company. 

PC4 Interpreation: Momentum Reversal
Eigenvalue = 1.19 (1.11-1.29)
Explained Variance - 6.85%
TGT and WMT are key retail companies present here along with WFC which is related to domestic banking. Although this PC passes the Kaiser Criterion, it is still highly sensitive to noise than the other PC's. 

Correlation Matrix

<img width="763" height="605" alt="image" src="https://github.com/user-attachments/assets/e3b89147-6898-40b9-99d4-30043604cd0f" />


Factor Loadings

<img width="766" height="590" alt="image" src="https://github.com/user-attachments/assets/59f95f66-9b35-477c-ba64-4fabd63810a9" />

Red (Positive) = Stock moves with the factor
Blue (Negative) = Stock moves against the factor
White (Zero) = Stock is barely moved by the factor

Factor Stability

<img width="757" height="611" alt="image" src="https://github.com/user-attachments/assets/c0d5533c-a39b-47c3-9025-7e6d45d8f8db" />

<img width="750" height="568" alt="image" src="https://github.com/user-attachments/assets/19fdb43d-ffeb-4b9c-a223-97b049300732" />

<img width="749" height="567" alt="image" src="https://github.com/user-attachments/assets/13d32d73-3454-4f52-9cea-b0dfa5a61ab4" />

<img width="756" height="562" alt="image" src="https://github.com/user-attachments/assets/6dd27fb4-5603-4faf-998e-479bbfe1a226" />

PC1-PC3 as shown by the box and whisker plot had eigenvalues significantly higher than 1 so they can be used as factors. PC4 also barely has an eigenvalue over one which means it also counts as a PC. PC5 on the other hand never goes above 1 even in the 95th percentile proving that it cannot be a PC. This matters because instead of tracking multiple stocks, we can track 4 key factors and understand 74% of movement in the portfolio.




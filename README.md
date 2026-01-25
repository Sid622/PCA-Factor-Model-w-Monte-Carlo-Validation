PCA Factor Model with Monte Carlo Validation

Overview: 
This project identifies risk factors that drive portfolio returns by applying
dimensionality reduction to historical stock data. PCA shows that portfolio 
variance can be explained by about 3-4 systematic factors. This stability is later 
validated through a Monte Carlo simulation. 

1. Data Collection

Dataset: 5 years of daily returns from 15 stocks across technology, finance, 
energy and consumer sectors. Standardized returns to ensure equal weighting

2. Principal Component Analysis

Computed correlation matrix across assets and then performed eigenvalue decomposition
to extract PC's. Calculated factor loadings to interpret the economic meaning of 
each PC and then applied the Kaiser criterion for factor selection to ensure each 
factor was stable and not noise. 

3. Monte Carlo Validation

Bootstrap sampled with replace (1,000) iterations and re-ran PCA on each sample to
test the factor stability. Calculated 95% confidence intervals for eigenvalues to
distinguish factors from sample noise. 

Key Results

Factor: 
PC1 Interpretation: Market Facotr (Beta)
Eigenvalue = 7 (6.5-7.5)
Explained Variance = 46.63%

PC2 Interpretion: Value vs Growth rotation
Eigenvalue = 2.36 (2.2-2.6)
Explained Variance = 15.70%

PC3 Interpretation: Consumer/Sector factor
Eigenvalue = 1.17 (1.1-1.3)
Explained Variance = 7.83%

PC4 Interpreation: Unstable 
Eigenvalue = 1.03
Explained Variance - 6.85%

<img width="754" height="593" alt="image" src="https://github.com/user-attachments/assets/0d1e5d8f-0cf9-4a5c-8e16-daf872b5304f" />

Factor Loadings
<img width="763" height="588" alt="image" src="https://github.com/user-attachments/assets/53207331-4f2d-4b7a-876e-1a4e84b959b7" />

Red (Positive) = Stock moves with the factor
Blue (Negative) = Stock moves against the factor
White (Zero) = Stock is barely moved by the factor

PC1: All stocks are red (0.43-0.85). When the market goes up, everything
else goes up together.

PC2: MSFT, CVX, BAC are positive (value stocks). AMZN, NVDA, JPM are negative
(growth stocks). When investors prefer value stocks, they go up and growth 
stocks go down and vice versa. 

PC3: TGT, WMT, WFC, are strongly positive (0.44-0.61) while the rest are near
zero. While consumers are spending, stocks move together. 

PC4: Mixed colors, no pattern. Confirms this is noise and not a real factor.

This matters because instead of tracking multiple stocks, we can track 
3 key factors and understand 77% of what is happening. 

<img width="754" height="618" alt="image" src="https://github.com/user-attachments/assets/8d4efd03-7627-4d4d-ac9e-e52b2a4087f2" />

<img width="751" height="567" alt="image" src="https://github.com/user-attachments/assets/5fd171fd-967c-4792-8e7a-79ffd409d9da" />

<img width="749" height="567" alt="image" src="https://github.com/user-attachments/assets/5bd1a219-4f3b-4d02-8778-3546e9dff67b" />








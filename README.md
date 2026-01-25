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

Components  Eigenvalues  Explained Variance %  Cumulative Variance %
0         PC1         7.00                 46.63                  46.63
1         PC2         2.36                 15.70                  62.33
2         PC3         1.17                  7.83                  70.16
3         PC4         1.03                  6.85                  77.01
4         PC5         0.75                  5.01                  82.02
5         PC6         0.55                  3.68                  85.70
6         PC7         0.44                  2.92                  88.61
7         PC8         0.36                  2.39                  91.00
8         PC9         0.34                  2.29                  93.30
9        PC10         0.24                  1.60                  94.90
10       PC11         0.22                  1.48                  96.37
11       PC12         0.17                  1.12                  97.49
12       PC13         0.15                  0.97                  98.46
13       PC14         0.13                  0.84                  99.31
14       PC15         0.10                  0.69                 100.00

<img width="754" height="593" alt="image" src="https://github.com/user-attachments/assets/0d1e5d8f-0cf9-4a5c-8e16-daf872b5304f" />

<img width="763" height="588" alt="image" src="https://github.com/user-attachments/assets/53207331-4f2d-4b7a-876e-1a4e84b959b7" />

<img width="754" height="618" alt="image" src="https://github.com/user-attachments/assets/8d4efd03-7627-4d4d-ac9e-e52b2a4087f2" />

<img width="751" height="567" alt="image" src="https://github.com/user-attachments/assets/5fd171fd-967c-4792-8e7a-79ffd409d9da" />

<img width="749" height="567" alt="image" src="https://github.com/user-attachments/assets/5bd1a219-4f3b-4d02-8778-3546e9dff67b" />








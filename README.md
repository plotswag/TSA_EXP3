# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date:02/09/25

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Load CSV file
df = pd.read_csv("/content/cardekho.csv")

# 👇 Replace this with the numeric column you want
data = df["selling_price"].values  

N = len(data)
lags = range(35)
autocorr_values = []

mean_data = np.mean(data)
variance_data = np.var(data)

# Compute autocorrelation
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)  # ACF at lag 0 is always 1
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

# Plot
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)  
plt.title("Autocorrelation of CarDekho Data")
plt.xlabel("Lag")
plt.ylabel("Autocorrelation")
plt.grid(True)
plt.show()
```
### OUTPUT:
<img width="1465" height="707" alt="image" src="https://github.com/user-attachments/assets/c5ed0347-3397-46c0-8568-9835d22d7a0b" />

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.

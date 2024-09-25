# DEVELOPED BY : SHALINI K
# REGISTER NUMBER : 212222240095
# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 

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
```py
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
file_path = 'coin_Bitcoin.csv'
data = pd.read_csv(file_path)

# Extract the 'Close' column
close_prices = data['Close'].dropna()

# Mean
data_mean = np.mean(close_prices)

# Variance
data_var = np.var(close_prices)

# Normalized data
normalized_data = (close_prices - data_mean) / np.sqrt(data_var)

# Compute the autocorrelation function (ACF)
acf_result = np.correlate(normalized_data, normalized_data, mode='full')

# Take only the positive lags
acf_result = acf_result[len(acf_result)//2:]

# Plot the ACF
plt.figure(figsize=(10, 5))
plt.stem(acf_result[:36])  # Removed use_line_collection
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.title('Autocorrelation Function (ACF) for Bitcoin Close Prices')
plt.show()

```
### OUTPUT:
![image](https://github.com/user-attachments/assets/c3986cdb-9fff-4b76-8ef0-a85feb38f7ea)

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.

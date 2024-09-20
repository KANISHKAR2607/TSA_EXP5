### Developed By : KANISHKAR M
### Reg. NO . 212222240044
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average of pH on the Water Quality data.

### ALGORITHM:

1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:


```py


# Importing the required libraries
import pandas as pd
from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.pyplot as plt

# Load the dataset
  # Replace with the correct path to your file
df = pd.read_csv('/content/waterquality.csv')

# Display the first 5 rows of the dataset
print("First 5 Rows of the dataset:")
print(df.head())

# Converting the 'date' column to datetime and setting it as the index
df['Date'] = pd.to_datetime(df['Date'], format='%Y-%m-%d')
df.set_index('Date', inplace=True)

# Filling missing values for the "pH" column (if any) using forward fill
df['pH'] = df['pH'].fillna(method='ffill')

# Performing seasonal decomposition on the "pH" feature (additive model)
decomposition = seasonal_decompose(df['pH'], model='additive', period=7)

# Plot and save each component separately with different colors

# Plot and save the observed (original) data
plt.figure(figsize=(10, 4))
decomposition.observed.plot(color='blue')
plt.title('Observed')
plt.ylabel('Observed')
plt.savefig('observed_plot.png')
plt.show()

# Plot and save the trend component
plt.figure(figsize=(10, 4))
decomposition.trend.plot(color='green')
plt.title('Trend')
plt.ylabel('Trend')
plt.savefig('trend_plot.png')
plt.show()

# Plot and save the seasonal component
plt.figure(figsize=(10, 4))
decomposition.seasonal.plot(color='red')
plt.title('Seasonal')
plt.ylabel('Seasonal')
plt.savefig('seasonal_plot.png')
plt.show()

# Plot and save the residual component
plt.figure(figsize=(10, 4))
decomposition.resid.plot(color='purple')
plt.title('Residual')
plt.ylabel('Residual')
plt.savefig('residual_plot.png')
plt.show()

```


### OUTPUT:

#### FIRST FIVE ROWS:

![image](https://github.com/user-attachments/assets/47ab8be9-67c4-48a1-b7b7-f3f56e85fd87)


#### SEASONAL PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/174f5dea-807f-43c0-bddd-4182cd483185)



#### TREND PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/8ba61398-8eac-4691-ae1b-bfc966171511)

#### PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/f11b0681-253b-4f97-9447-fe7dbd3141c9)

#### OVERAL REPRESENTATION:

![image](https://github.com/user-attachments/assets/3c4fbbf7-e9c8-4d0a-a3c2-238071ee405f)


### RESULT:
Thus we have created the python code for the time series analysis and decomposition of the Water Quality data.

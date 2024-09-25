## Name: M.Harini
## Reg No: 212222240035
## Date:

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION

### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load data
data = pd.read_csv('Microsoft_Stock.csv')  # Assuming you have at least two years of data
data['date'] = pd.to_datetime(data['Date'])

# Check the date range
print(data['Date'].min(), data['Date'].max())

# Resample monthly data
monthly_data = data.resample('M', on='Date')['open'].sum().reset_index()

# Check the size of monthly_data
print(monthly_data)

# Ensure 'date' is set as the index
monthly_data.set_index('Date', inplace=True)

# Check if we have enough data for decomposition
if len(monthly_data) < 24:
    print("Not enough data for seasonal decomposition. Need at least 24 observations.")
else:
    # Perform seasonal decomposition
    decomposition = seasonal_decompose(monthly_data['open'], model='additive')

    # Plotting
    plt.figure(figsize=(8, 12))

    # Original Data
    plt.subplot(411)
    plt.plot(monthly_data['open'], label='Monthly Open Prices')
    plt.legend(loc='upper left')
    plt.title('Monthly Open Prices')

    # Trend Plot
    plt.subplot(412)
    plt.plot(decomposition.trend, label='Trend', color='orange')
    plt.legend(loc='upper left')
    plt.title('Trend Plot')

    # Seasonal Plot
    plt.subplot(413)
    plt.plot(decomposition.seasonal, label='Seasonal', color='green')
    plt.legend(loc='upper left')
    plt.title('Seasonal Plot')

    # Residual Plot
    plt.subplot(414)
    plt.plot(decomposition.resid, label='Residual', color='red')
    plt.legend(loc='upper left')
    plt.title('Residual Plot')

    plt.tight_layout()
    plt.show()
```

### OUTPUT:


#### FIRST FIVE ROWS:
![Screenshot 2024-09-24 121924](https://github.com/user-attachments/assets/418cf8d2-bcf7-41a2-b950-536dfd7dfbd3)

#### PLOTTING THE DATA:
![Screenshot 2024-09-24 121939](https://github.com/user-attachments/assets/bc9fec78-f52a-42c6-990f-acbb1c6b7fa6)

#### SEASONAL PLOT REPRESENTATION :

![Screenshot 2024-09-24 121955](https://github.com/user-attachments/assets/51817a20-1f47-492b-b1ed-cf9f85a96ca6)


#### TREND PLOT REPRESENTATION :
![Screenshot 2024-09-24 122011](https://github.com/user-attachments/assets/ff3b6c35-d476-46c2-b72b-bc4b0d6f6d5e)

#### RESIDUAL PLOT REPRESENTATION:
![Screenshot 2024-09-24 122029](https://github.com/user-attachments/assets/32a55fab-7431-4a89-a784-52b2a665cb60)




### RESULT:
Thus, the python code for the time series analysis and decomposition is successfully implemented.





















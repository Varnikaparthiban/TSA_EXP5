# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose


data = pd.read_csv(
    '/content/weather_2013_to_2024.csv',
    parse_dates=['DATE'],      
    index_col='DATE'
)

print("Available columns in the CSV:")
print(data.columns)
print("\nFirst 5 rows of the dataset (without date parsing/indexing yet):")
print(data.head())


decomposition = seasonal_decompose(
    data['temp'],
    model='additive',
    period=365 
)

plt.figure(figsize=(10, 12))

# Original Data
plt.subplot(411)
plt.plot(data['temp'], label='Original Data')
plt.legend(loc='upper left')
plt.title('Original Data - Temperature')

# Trend Plot
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

# Seasonal Plot
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

# Residual Plot
plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()
```

### OUTPUT:
FIRST FIVE ROWS:

<img width="687" height="742" alt="image" src="https://github.com/user-attachments/assets/603abd5a-bc63-4bc0-a38f-fd818d37cb9e" />


PLOTTING THE DATA:
<img width="1050" height="292" alt="image" src="https://github.com/user-attachments/assets/5ccda3d0-a4af-42a0-a674-c98f7396b53d" />

SEASONAL PLOT REPRESENTATION :
<img width="1016" height="313" alt="image" src="https://github.com/user-attachments/assets/231179cc-8f5f-4897-9035-198626ffbe3d" />


TREND PLOT REPRESENTATION :
<img width="1055" height="286" alt="image" src="https://github.com/user-attachments/assets/9638337b-fb5a-4763-8d38-e6be1ea761aa" />

OVERAL REPRESENTATION:
<img width="1083" height="316" alt="image" src="https://github.com/user-attachments/assets/427647be-f520-4862-af76-4d008ddcc933" />



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.

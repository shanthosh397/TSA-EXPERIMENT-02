# Experiment 02 – Time Series Analysis and Decomposition

### Name: SHANTHOSH G
### Register No: 2305003008

## Aim
To perform time series analysis and decomposition on the monthly average temperature of a city
using Python.

## Algorithm
1. Start the program.
2. Import Pandas, Matplotlib, and seasonal_decompose from statsmodels.
3. Create monthly temperature data for two complete yearly cycles.
4. Generate a monthly date index using Pandas.
5. Create a time-series object using the temperature values and date index.
6. Display the monthly temperature data.
7. Plot the original monthly average temperature time series.
8. Apply additive seasonal decomposition with period = 12.
9. Display the Observed, Trend, Seasonal, and Residual components.
10. Interpret the plotted components.
11. Stop the program.


## Program
File: `experiment_02.py`

```python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
temperature = [
    25, 27, 29, 32, 34, 33,
    32, 31, 30, 29, 27, 25,
    25, 27, 29, 32, 34, 33,
    32, 31, 30, 29, 27, 25
]
dates = pd.date_range(
    start="2025-01-01",
    periods=24,
    freq="ME"
)
data = pd.Series(
    temperature,
    index=dates
)
print("Monthly Temperature:")
print(data)
plt.figure(figsize=(10, 5))
plt.plot(data.index, data.values, marker="o")
plt.title("Monthly Average Temperature")
plt.xlabel("Month")
plt.ylabel("Temperature (°C)")
plt.grid()
plt.show()
result = seasonal_decompose(
    data,
    model="additive",
    period=12
)
result.plot()
plt.show()
```

## Output

### Original Time Series

<img width="1460" height="860" alt="image" src="https://github.com/user-attachments/assets/5240dbfb-3a4d-4e05-a794-e3284ccb3ec3" />

### TIME SERIES DECOMPOSITION

<img width="1505" height="245" alt="image" src="https://github.com/user-attachments/assets/5ea7bdd5-910a-4097-a085-1733b6c554d3" />

<img width="1505" height="245" alt="image" src="https://github.com/user-attachments/assets/ea2715e4-289b-4e4e-ad09-d7a2cbedfeb6" />

<img width="1505" height="250" alt="image" src="https://github.com/user-attachments/assets/221f63b9-19ef-4266-91a7-a49386513f46" />

<img width="1505" height="260" alt="image" src="https://github.com/user-attachments/assets/bf2890d5-88f0-4ae3-b121-25dcfb26a5ac" />


## Observation
The monthly temperature shows a repeating seasonal pattern. The decomposition separates the
original series into observed, trend, seasonal, and residual components. The residual values are very
close to zero because the two yearly cycles follow the same repeated temperature pattern.

## Result
Thus, the monthly temperature time series was successfully plotted and decomposed into observed,
trend, seasonal, and residual components using Python.

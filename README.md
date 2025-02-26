# Air Quality Prediction Using Interpolation and Polynomial Approximation

## Overview
This project explores the application of various interpolation techniques to predict air quality metrics based on historical data. Using the Air Quality UCI dataset, we implemented and compared three interpolation methods:
- Lagrange Interpolation
- Newton's Divided Differences
- Cubic Splines

The study aims to understand the effectiveness of mathematical models in capturing real-world environmental dynamics, with a focus on predicting pollutant levels such as carbon monoxide (CO), nitrogen dioxide (NO2), and ozone (O3).

## Dataset
The Air Quality UCI dataset comprises 9,358 instances of hourly averaged responses from an array of five metal oxide chemical sensors. The data was collected from March 2004 to February 2005 in an Italian city.

### Key Features
- Timestamps (Date and Time)
- True hourly averaged concentration measurements for various pollutants:
  - Carbon monoxide (CO)
  - Non-methane hydrocarbons (NMHC)
  - Benzene (C6H6)
  - Nitrogen oxides (NOx)
  - Nitrogen dioxide (NO2)
  - Ozone (O3)
- Sensor responses targeted at specific pollutants
- Environmental parameters (Temperature, Relative Humidity, Absolute Humidity)

## Methodology
### Interpolation Techniques
1. **Lagrange Interpolation**
   - Classical method constructing a polynomial through a given set of data points
   - Mathematically expressed as: P(x) = Σ[i=0 to n] yi∏[j=0 to n, j≠i] (x-xj)/(xi-xj)

2. **Newton's Divided Differences**
   - More efficient approach using divided differences
   - Generates a polynomial in Newton's form to reduce computational overhead

3. **Cubic Splines**
   - Piecewise interpolation method fitting cubic polynomials between consecutive data points
   - Minimizes oscillations while maintaining continuity in derivatives

### Implementation
- The project is implemented in Python
- Visualization techniques include subplots for comparing predicted values with original data
- Error metrics are used to evaluate the accuracy of different interpolation methods

## Results

### Carbon Monoxide (CO)
- Lagrange interpolation showed good performance for smaller data subsets but suffered from oscillations with larger datasets
- Newton's method provided more stable interpolation with lower errors
- Cubic splines delivered the most accurate predictions, effectively capturing temporal variations

### Nitrogen Dioxide (NO2)
- Lagrange interpolation had limitations with high-variance data
- Newton's method offered smoother predictions and better handling of temporal trends
- Cubic splines excelled in modeling both gradual and abrupt changes in pollutant levels

### Ozone (O3)
- Lagrange interpolation performed moderately for small datasets but struggled with complex patterns
- Newton's method improved predictions with fewer oscillations
- Cubic splines provided the most reliable approximations for both baseline levels and peak events

## Conclusions
- Cubic splines emerged as the most effective technique for air quality prediction
- Lagrange interpolation is suitable for smaller datasets but has limitations with complex data
- Newton's Divided Differences offer a balanced approach between computational efficiency and accuracy
- The choice of interpolation technique significantly impacts prediction accuracy in environmental data modeling

## Future Work
- Explore hybrid approaches combining interpolation with machine learning techniques
- Incorporate spatial dimensions for comprehensive air quality modeling
- Investigate techniques to handle sensor drift and cross-sensitivity in environmental data

## Requirements
- Python 3.x
- NumPy
- SciPy
- Matplotlib
- Pandas

## How to Use
```python
# Example code for using cubic splines interpolation
from scipy.interpolate import CubicSpline
import numpy as np
import matplotlib.pyplot as plt

# Load your data
x = np.array([...])  # Time points
y = np.array([...])  # Pollutant concentration

# Create cubic spline
cs = CubicSpline(x, y)

# Predict at new points
x_new = np.linspace(min(x), max(x), 100)
y_new = cs(x_new)

# Visualize results
plt.figure(figsize=(10, 6))
plt.plot(x, y, 'o', label='Data')
plt.plot(x_new, y_new, '-', label='Cubic Spline')
plt.legend()
plt.title('Air Quality Prediction using Cubic Spline')
plt.xlabel('Time')
plt.ylabel('Concentration')
plt.show()
```

## Author
Muhammad Tahir Zia - Bachelors Computer Engineering, Lahore, Pakistan

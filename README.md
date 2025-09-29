# AQI Prediction Project

This project predicts Air Quality Index (AQI) for major Indian cities using advanced machine learning and time series forecasting techniques, with a focus on long-term forecasting through 2027.

## Project Overview

The Air Quality Index (AQI) is a measure used to communicate how polluted the air currently is or how polluted it is forecast to become. This project uses historical AQI data from 35 Indian cities (2020-2025) to build predictive models that can forecast future AQI values for the remaining months of 2025 and future years (2026, 2027).

## Project Concept

Air pollution is a critical environmental and public health concern in India, with many cities experiencing hazardous air quality levels throughout the year. This project aims to:

1. **Analyze historical AQI trends** across 35 major Indian cities to identify patterns, seasonal variations, and long-term trends
2. **Build accurate predictive models** using multiple approaches to forecast future AQI levels
3. **Compare model performance** across different cities and regions to identify which models work best in different scenarios
4. **Provide long-term forecasts** that can help in urban planning, public health initiatives, and pollution control measures
5. **Create comprehensive visualizations** that make complex AQI data accessible and actionable

The project combines traditional machine learning approaches with specialized time series forecasting techniques to create a robust prediction system that accounts for temporal dependencies, seasonality, and trend components in AQI data.

## Directory Structure

```
AQIPrediction/
│
├── data/                       # Data directory
│   ├── raw/                    # Raw data from CPCB (2020-2025)
│   └── processed/              # Processed data for all 35 cities
│
├── src/                        # Source code
│   ├── data/                   # Data preprocessing scripts
│   │   └── preprocess_data_fixed.py  # Clean and prepare data
│   │
│   ├── models/                 # Model training and prediction scripts
│   │   ├── train_models.py     # Train all four models
│   │   ├── long_term_predict.py  # Generate long-term predictions
│   │   └── city_predict.py     # Generate city-specific predictions
│   │
│   └── visualization/          # Visualization scripts
│       └── model_comparison_dashboard.py  # Compare model performance
│
├── results/                    # Generated results
│   ├── long_term_predictions/  # City-specific prediction folders
│   └── model_comparison/       # Model comparison dashboard
│
├── requirements.txt            # Project dependencies
│
└── README.md                   # Project documentation
```

## Cities Included

The project includes 35 Indian cities, including:

- Delhi, Mumbai, Kolkata, Chennai, Bengaluru
- Hyderabad, Ahmedabad, Pune, Jaipur, Lucknow
- Chandigarh, Bhopal, Patna, Kochi, Srinagar
- Guwahati, Nagpur, Amritsar, Varanasi, Visakhapatnam
- And 15 more cities across India

## Data Source

- Central Pollution Control Board (CPCB) data covering 2020 to April 2025

## Models Implemented

The project implements four advanced machine learning models, each selected for their specific strengths in time series forecasting:

1. **Random Forest**
   - **Approach**: Ensemble learning method using multiple decision trees
   - **Strengths**: Robust predictions with good interpretability, handles non-linear relationships
   - **Implementation**: Optimized with hyperparameter tuning for each city
   - **Features Used**: Historical AQI values, seasonal components, trend features

2. **XGBoost (Extreme Gradient Boosting)**
   - **Approach**: Gradient boosting framework using decision trees
   - **Strengths**: Captures complex non-linear relationships, handles missing values effectively
   - **Implementation**: Regularization techniques to prevent overfitting
   - **Features Used**: Historical AQI values, lag features, rolling statistics

3. **LSTM (Long Short-Term Memory)**
   - **Approach**: Recurrent neural network architecture designed for sequence prediction
   - **Strengths**: Captures long-term temporal dependencies in time series data
   - **Implementation**: Multi-layer LSTM with dropout for regularization
   - **Features Used**: Sequence of historical AQI values with appropriate window size

4. **Prophet**
   - **Approach**: Decomposable time series model with trend, seasonality, and holiday components
   - **Strengths**: Specialized for time series forecasting with automatic handling of seasonality
   - **Implementation**: Customized for daily AQI forecasting with yearly and weekly seasonality
   - **Features Used**: Historical AQI time series with date-based features

## Evaluation Metrics

The models are evaluated using multiple metrics to provide a comprehensive assessment of performance:

1. **RMSE (Root Mean Square Error)**
   - Measures the standard deviation of prediction errors
   - Lower values indicate better model performance
   - Heavily penalizes large errors due to squaring

2. **MAE (Mean Absolute Error)**
   - Measures the average magnitude of errors without considering direction
   - More robust to outliers than RMSE
   - Provides a straightforward interpretation of error magnitude

3. **R² (Coefficient of Determination)**
   - Measures the proportion of variance in the dependent variable explained by the model
   - Values range from 0 to 1, with higher values indicating better fit
   - Allows for comparison of model performance across different cities

4. **MAPE (Mean Absolute Percentage Error)**
   - Expresses accuracy as a percentage of error
   - Provides a relative measure of prediction accuracy
   - Used for comparing performance across cities with different AQI scales

The model comparison dashboard provides a comprehensive visualization of these metrics across all cities and models, enabling easy identification of the best-performing model for each scenario.

## Key Features

- **Long-term AQI Forecasting**: Predictions through 2027 for all cities
- **City-specific Analysis**: Dedicated folders with visualizations for each city
- **Model Comparison Dashboard**: Interactive comparison of all four models
- **Comprehensive Visualizations**: Heatmaps, time series plots, and seasonal analyses
- **Automated Reports**: Summary reports for each city with key insights

## Key Findings and Results

### Model Performance

- **XGBoost** generally performs best for cities with highly variable AQI patterns, achieving the lowest RMSE in 40% of cities
- **LSTM** excels at capturing long-term dependencies and performs particularly well for cities with consistent seasonal patterns
- **Prophet** provides the most accurate forecasts for cities with strong yearly seasonality components
- **Random Forest** offers the most robust performance across different cities, making it a reliable baseline model

### Regional Insights

- **Northern Cities** (Delhi, Chandigarh) show the highest AQI variability and seasonal peaks during winter months
- **Coastal Cities** (Mumbai, Chennai) demonstrate more moderate AQI levels with less pronounced seasonality
- **Southern Cities** (Bengaluru, Hyderabad) generally maintain lower average AQI levels throughout the year
- **Industrial Hubs** (Ahmedabad, Kanpur) show consistently higher baseline AQI values regardless of season

### Temporal Patterns

- Strong **yearly seasonality** with winter peaks (November-February) in most northern and central cities
- Clear **weekly patterns** with weekday-weekend variations in metropolitan areas
- **Long-term improving trends** in several cities, potentially due to pollution control measures
- **Festival-related spikes** observed during Diwali and other major celebrations

### Forecasting Confidence

- Short-term forecasts (30 days) achieve high accuracy with average R² values above 0.85
- Medium-term forecasts (6 months) maintain reasonable accuracy with R² values around 0.75
- Long-term forecasts (1-2 years) show decreasing confidence but still capture seasonal patterns effectively

## ⚠️ IMPORTANT NOTICE ⚠️

The following directories are not included in this repository due to file size limitations on GitHub:

1. The `models/` directory - Contains trained model files that exceed GitHub's file size limits
2. The `data/processed/` directory - Contains processed data files that are too large for GitHub

You will need to generate these files by running the preprocessing and training scripts as described in the Getting Started section below.

## Getting Started

### Option 1: Using requirements.txt

1. Clone this repository
2. Install dependencies: `pip install -r requirements.txt`
3. Run preprocessing: `python src/data/preprocess_data_fixed.py`
4. **Generate model files**: `python src/models/train_models.py` (This will create all necessary model files in the `models/` directory)
5. Generate predictions: `python src/models/long_term_predict.py`
6. Generate city-specific predictions: `python src/models/city_predict.py`
7. Create model comparison dashboard: `python src/visualization/model_comparison_dashboard.py`
8. View model comparison: Open `results/model_comparison/dashboard.html`

### Option 2: Using setup.py (Installable Package)

Alternatively, you can install the project as a package:

1. Clone this repository
2. Install the package in development mode: `pip install -e .`
3. This will install all dependencies specified in `setup.py`
4. Follow steps 3-8 from Option 1 to run the project

## Future Improvements

Potential enhancements for future versions of this project:

1. **Incorporate Weather Data**: Integrate weather parameters (temperature, humidity, wind speed) to improve prediction accuracy
2. **Ensemble Modeling**: Implement ensemble techniques combining predictions from all four models
3. **Deep Learning Enhancements**: Explore more complex architectures like Transformer models for sequence prediction
4. **Spatial Analysis**: Add geospatial modeling to account for pollution spread between neighboring cities
5. **Real-time Predictions**: Develop an API for real-time AQI forecasting with continuous model updates

## Applications

This project can be applied in various domains:

1. **Public Health**: Enable proactive health advisories based on forecasted AQI levels
2. **Urban Planning**: Inform long-term city development with pollution forecasts
3. **Environmental Policy**: Evaluate the potential impact of pollution control measures
4. **Tourism Industry**: Provide seasonal air quality forecasts for travelers
5. **Research**: Serve as a foundation for more advanced air quality research

## Creator

Created by Itisha Kumari  (https://github.com/sayitisha) based on datasets provided by the Central Pollution Control Board (CPCB) of India.

## License

[MIT License](LICENSE)# AQI-prediction-system
AQI prediction system for 35 Indian cities using Random Forest, XGBoost, LSTM, and Prophet models. Features interactive dashboards, city-specific analyses, and forecasts through 2027.

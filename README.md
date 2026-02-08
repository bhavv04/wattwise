# wattwise Ontario

Machine learning-based electricity demand forecasting system for Ontario's power grid.

## Overview

wattwise Ontario predicts electricity demand for Ontario's power grid hours to days in advance, enabling grid operators to optimize generation scheduling, reduce reliance on expensive peaker plants, and better integrate renewable energy sources.

Accurate demand forecasting is critical for grid stability and cost efficiency. This project demonstrates end-to-end machine learning pipeline development, from data acquisition to model deployment, with a focus on business impact and model interpretability.

## Business Problem

Ontario's Independent Electricity System Operator (IESO) must continuously balance electricity supply and demand across the province. Poor forecasting leads to:

- **High costs**: Emergency activation of expensive natural gas peaker plants ($150/MWh vs $60/MWh for baseload)
- **Grid instability**: Risk of brownouts or blackouts when demand exceeds supply
- **Inefficiency**: Wasted capacity when supply significantly exceeds demand
- **Integration challenges**: Difficulty managing variable renewable sources (wind, solar)

Even a 5% improvement in forecast accuracy during peak demand periods can save millions of dollars annually by enabling better generation scheduling and capacity planning.

## Project Goals

1. Build accurate short-term (24-48 hour) demand forecasts using machine learning
2. Identify key drivers of electricity demand (weather, time, seasonality)
3. Provide interpretable predictions that grid operators can trust and act on
4. Quantify business impact in terms of potential cost savings
5. Deploy an interactive dashboard for real-time forecasting

## Data Sources

- **IESO Public Reports**: Historical and real-time Ontario electricity demand data
- **Environment Canada**: Weather data for Toronto and surrounding regions
- **OpenWeather API**: Real-time weather conditions and forecasts
- **Additional features**: Holidays, day of week, time of day, seasonal patterns

## Methodology

### 1. Data Collection & Preprocessing
- Aggregate hourly demand data from IESO
- Merge with weather data (temperature, humidity, cloud cover)
- Handle missing values and outliers
- Feature engineering for time-based patterns

### 2. Exploratory Data Analysis
- Identify daily, weekly, and seasonal demand patterns
- Analyze correlations between weather and demand
- Detect anomalies and special events

### 3. Feature Engineering
- Temporal features: hour, day of week, month, holiday indicators
- Lag features: demand from previous hours, days, weeks
- Rolling statistics: moving averages, standard deviations
- Weather features: temperature, "feels like" temperature, degree days
- Cyclical encoding for time-based features

### 4. Model Development
Comparing multiple approaches:
- Baseline: Naive forecast (previous day same hour)
- Statistical: ARIMA, Prophet
- Machine Learning: Random Forest, XGBoost, LightGBM
- Deep Learning: LSTM neural networks

### 5. Evaluation Metrics
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Mean Absolute Percentage Error (MAPE)
- Peak hour accuracy (critical for cost savings)

### 6. Model Interpretation
- SHAP values for feature importance
- Partial dependence plots
- Individual prediction explanations

### 7. Business Impact Analysis
- Calculate cost savings from improved peak demand forecasting
- Analyze scenarios: reduced peaker plant usage, better renewable integration
- ROI quantification

## Project Structure

```
wattwise-ontario/
├── data/
│   ├── raw/              # Raw data from IESO and weather APIs
│   ├── processed/        # Cleaned and feature-engineered data
│   └── predictions/      # Model outputs and forecasts
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_model_development.ipynb
│   └── 04_business_analysis.ipynb
├── src/
│   ├── data/            # Data collection and preprocessing
│   ├── features/        # Feature engineering
│   ├── models/          # Model training and evaluation
│   └── visualization/   # Plotting and dashboard code
├── dashboard/           # Streamlit dashboard application
├── requirements.txt
└── README.md
```

## Installation

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/wattwise.git
cd wattwise

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## Usage

### Data Collection
```bash
python src/data/fetch_ieso_data.py
python src/data/fetch_weather_data.py
```

### Model Training
```bash
python src/models/train.py --model xgboost --lookback 168
```

### Generate Predictions
```bash
python src/models/predict.py --horizon 24
```

### Launch Dashboard
```bash
streamlit run dashboard/app.py
```

## Key Findings

*This section will be updated as the project progresses with insights such as:*
- Most important features driving demand predictions
- Model performance comparison
- Quantified cost savings potential
- Seasonal and weather-based patterns discovered

## Technologies Used

- **Python 3.9+**
- **Data Processing**: pandas, numpy
- **Machine Learning**: scikit-learn, XGBoost, LightGBM
- **Time Series**: Prophet, statsmodels
- **Deep Learning**: TensorFlow/Keras (optional)
- **Visualization**: matplotlib, seaborn, plotly
- **Dashboard**: Streamlit
- **Model Interpretation**: SHAP

## Future Enhancements

- Incorporate real-time renewable generation data (solar, wind)
- Add forecasting for individual zones within Ontario
- Implement ensemble methods combining multiple models
- Deploy as cloud-based service with automated daily updates
- Include economic indicators (manufacturing activity, events)
- Multi-step ahead forecasting (7-day horizon)

## Business Impact

*To be quantified upon project completion*

Expected impacts:
- X% reduction in forecast error during peak demand periods
- Estimated $Y annual savings from optimized generation scheduling
- Improved renewable energy integration capacity
- Enhanced grid reliability metrics

## Author

**Your Name**  
Computer Science Student | Data Science & ML Enthusiast  
[LinkedIn](your-linkedin) | [Portfolio](your-website) | [Email](your-email)

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- IESO for providing public access to grid data
- Environment Canada for weather data
- Ontario energy grid operators for inspiring this work

---

*This project was developed as part of a portfolio to demonstrate end-to-end machine learning capabilities with real-world business applications.*

# Taxi Trip Duration Prediction Analysis

A comprehensive machine learning project to predict taxi trip durations using geographic, temporal, and fare-based features. This analysis includes data exploration, clustering, feature engineering, and predictive modeling.

## 🚖 Project Overview

This project analyzes taxi trip data to predict trip duration using various machine learning techniques. The analysis is divided into four main parts:

1. **Data Exploration** - Understanding patterns in taxi trips
2. **Geographic Clustering** - Identifying neighborhood patterns using K-Means
3. **Data Cleaning & Feature Engineering** - Creating meaningful features for prediction
4. **Predictive Modeling** - Comparing Random Forest and XGBoost models

## 📊 Dataset Schema

The project expects a CSV file with the following columns:

| Column Name | Description |
|-------------|-------------|
| `GratuityAmount` | Tip amount in dollars |
| `SurchargeAmount` | Additional surcharge fees |
| `ExtraFareAmount` | Extra fare charges |
| `TollAmount` | Toll charges |
| `TotalAmount` | Total fare amount |
| `PaymentType` | Payment method used |
| `StartDateTime` | Trip start timestamp |
| `EndDateTime` | Trip end timestamp |
| `OriginStreetNumber` | Pickup street number |
| `OriginStreetName` | Pickup street name |
| `OriginCity` | Pickup city |
| `OriginState` | Pickup state |
| `OriginZip` | Pickup ZIP code |
| `OriginLatitude` | Pickup latitude |
| `OriginLongitude` | Pickup longitude |
| `DestinationStreetNumber` | Dropoff street number |
| `DestinationStreetName` | Dropoff street name |
| `DestinationCity` | Dropoff city |
| `DestinationState` | Dropoff state |
| `DestinationZip` | Dropoff ZIP code |
| `DestinationLatitude` | Dropoff latitude |
| `DestinationLongitude` | Dropoff longitude |
| `Milage` | Trip distance |
| `Duration` | Trip duration |

## 🛠️ Installation & Setup

### Prerequisites

- Python 3.7+
- Jupyter Notebook (for .ipynb version)

### Required Libraries

```bash
pip install numpy pandas seaborn matplotlib scikit-learn xgboost tqdm
```

Or install all at once:

```bash
pip install -r requirements.txt
```

### File Structure

```
taxi-analysis/
│
├── taxi_analysis.ipynb          # Jupyter notebook version
├── train.csv                    # Your taxi data 
├── README.md                    # This file
└── requirements.txt             # Python dependencies
```

## 🚀 Usage

### Option 1: Jupyter Notebook (Recommended)

1. **Place your dataset** in the same folder as the notebook
2. **Update the dataset filename** in the notebook:
   ```python
   df_all = pd.read_csv('your_dataset_name.csv')  # Line 29
   ```
3. **Adjust city center coordinates** if not analyzing NYC data:
   ```python
   city_center = (40.7589, -73.9851)  # Line 239 - Change to your city
   ```
4. **Run the notebook** cell by cell or all at once

### Option 2: Python Script

1. **Update the dataset path** in the script
2. **Run the script**:
   ```bash
   python taxi_analysis.py
   ```

## 📈 Analysis Components

### Part 1: Data Exploration
- **Trip duration, distance, and fare distributions**
- **Rush hour analysis** with hourly and daily patterns
- **Payment type analysis**
- **Speed and geographic pattern analysis**

### Part 2: Geographic Clustering
- **K-Means clustering** (100 clusters) on pickup/dropoff locations
- **Cluster visualization** overlaid on geographic coordinates
- **Cluster statistics** including average duration and fare per cluster
- **Neighborhood pattern identification**

### Part 3: Data Cleaning & Feature Engineering
- **Outlier detection and removal**:
  - Trips < 1 minute or > 4 hours
  - Unrealistic speeds (< 0.5 m/s or > 30 m/s)
  - Extreme distances (> 100 km) or fares (> $200)
- **Advanced feature creation**:
  - Cyclical time features (sin/cos transformations)
  - Haversine and Manhattan distances
  - Bearing calculations
  - Distance from city center
  - PCA components for coordinate rotation
  - Cluster-based statistical features

### Part 4: Predictive Modeling
- **Model comparison**: Random Forest vs XGBoost
- **Evaluation metric**: Root Mean Squared Logarithmic Error (RMSLE)
- **Feature importance analysis**
- **Prediction vs actual visualizations**
- **Residual analysis**

## 📊 Key Features Created

| Feature Category | Features |
|------------------|----------|
| **Temporal** | Hour, day of week, month, cyclical transformations |
| **Geographic** | Haversine distance, Manhattan distance, bearing |
| **Location-based** | Distance to city center, PCA components, clusters |
| **Statistical** | Cluster means, standard deviations |
| **Categorical** | Encoded payment types |

## 🎯 Expected Results

- **Comprehensive visualizations** showing data patterns and model performance
- **RMSLE scores** typically in the range of 0.35-0.45 for well-tuned models
- **Feature importance rankings** highlighting distance and time features
- **Geographic insights** about trip patterns and congestion areas

## 📋 Model Performance Metrics

The project evaluates models using:
- **RMSLE (Root Mean Squared Logarithmic Error)** - Primary metric
- **Feature importance analysis** - Understanding key predictors
- **Residual analysis** - Model error patterns
- **Prediction vs actual scatter plots** - Visual performance assessment

## 🔧 Customization Options

### Adjusting Parameters

1. **Number of clusters**: Change `n_clusters=100` in the clustering section
2. **City center coordinates**: Update `city_center` variable for your location
3. **Outlier thresholds**: Modify filtering conditions in Part 3
4. **Model parameters**: Adjust Random Forest and XGBoost hyperparameters

### Adding Features

The modular design allows easy addition of new features:
```python
# Add new feature
df_clean['new_feature'] = your_calculation

# Add to feature list
feature_cols.append('new_feature')
```
## 📝 Output Files

The analysis generates:
- **Multiple visualization plots** showing data patterns
- **Model performance metrics** and comparisons
- **Feature importance rankings**
- **Cleaned dataset** with engineered features (in memory)

## 🤝 Contributing

To contribute to this project:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📞 Support

For questions or issues-
- Review the code comments for detailed explanations
- Ensure all dependencies are properly installed

## 🏆 Acknowledgments

- Inspired by Kaggle taxi trip duration competitions
- Uses standard data science libraries and best practices
- Geographic analysis techniques adapted from urban mobility research

---

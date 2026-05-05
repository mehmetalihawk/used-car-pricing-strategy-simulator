# Used Car Pricing Strategy & Market Positioning Simulator

## Project Overview
This project focuses on building a machine learning-based pricing decision support system for used car listings.

Instead of stopping at classical price prediction, the project extends the output into a **pricing strategy simulator** that helps position a vehicle in the market and generate scenario-based pricing recommendations.

The system is designed to answer questions such as:

- What is the estimated fair market value of this vehicle?
- What could be a lower price for faster selling potential?
- What could be a balanced market-level price?
- What could be a higher price for revenue-focused sellers?
- Is the vehicle positioned below market, at market, or above market compared to similar listings?

---

## Business Problem
In used car marketplaces, sellers often struggle to determine the right listing price.

- If the price is too high, the vehicle may stay on the platform for too long.
- If the price is too low, the seller may lose potential revenue.

This project aims to support pricing decisions through machine learning and similarity-based market comparison.

---

## Dataset
The project uses structured used car listing data including:

- brand
- series
- model
- year
- mileage
- transmission type
- fuel type
- body type
- color
- engine size
- engine power
- changed parts count
- painted parts count
- seller type
- price

---

## Project Workflow

### 1. Data Understanding
The dataset was explored to understand:
- data types
- number of observations
- unique category counts
- statistical summaries
- price distribution

### 2. Data Cleaning
The following cleaning steps were applied:
- duplicate row detection
- duplicate removal
- basic consistency checks

### 3. Feature Engineering
The following new features were created:

- **vehicle_age**: derived from listing year
- **yearly_mileage**: mileage divided by vehicle age
- **total_damage**: changed parts + painted parts
- **log_price**: log-transformed target variable

These features were created to better capture real-world pricing behavior and improve model performance.

### 4. Exploratory Data Analysis
EDA was performed to analyze relationships between price and:

- vehicle age
- mileage
- damage level
- brand
- price distribution
- log-transformed price distribution

Key observations:
- price distribution was highly right-skewed
- log transformation produced a more balanced target distribution
- vehicle age and mileage showed negative relationships with price
- total damage showed a negative relationship with median price
- premium brands and performance-oriented models had higher price levels

### 5. Modeling
Three models were evaluated:

- **Baseline Mean Model**
- **Ridge Regression**
- **Random Forest Regressor**

The target variable used in modeling was **log-transformed price**.

### 6. Model Comparison
The final model comparison showed:

| Model | MAE (TL) | RMSE (TL) | R² (log target) |
|------|---------:|----------:|----------------:|
| Baseline Mean Model | 435,077.87 | 774,219.13 | ~0.00 |
| Ridge Regression | 68,004.63 | 157,950.55 | 0.957 |
| Random Forest | 73,983.54 | 169,775.74 | 0.953 |

**Ridge Regression** was selected as the final model because it provided the best overall performance in the current setup.

---

## Pricing Strategy Simulator
The project was extended beyond price prediction into a **pricing strategy simulator**.

For a selected vehicle, the system generates:

- **Fast Sale Price**
- **Balanced Price**
- **Max Revenue Price**

Current strategy logic:
- Fast Sale Price = Predicted Price × 0.95
- Balanced Price = Predicted Price
- Max Revenue Price = Predicted Price × 1.05

These scenario-based outputs are designed to simulate different seller priorities.

---

## Market Positioning Logic
The project also compares the selected vehicle with similar listings in the dataset.

Similarity is currently based on:
- same brand
- same series
- same transmission type
- same fuel type

The system then compares the predicted price against the median price of similar vehicles and classifies the listing as:

- **Below Market**
- **At Market**
- **Above Market**

---

## Sample Use Case Output
For a sample Honda Jazz listing, the system generated:

- **Predicted Fair Market Price:** 506,156 TL
- **Fast Sale Price:** 480,849 TL
- **Balanced Price:** 506,156 TL
- **Max Revenue Price:** 531,464 TL
- **Similar Vehicles Median Price:** 607,500 TL
- **Market Position:** Below Market

This demonstrates how the project can move from pure prediction into decision-support output.

---

## Technologies Used
- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn

Main methods and techniques:
- Data Cleaning
- Exploratory Data Analysis
- Feature Engineering
- One-Hot Encoding
- Standard Scaling
- Ridge Regression
- Random Forest Regression
- Model Evaluation (MAE, RMSE, R²)

---

## Why This Project Matters
This project is not only a regression task.

It demonstrates how a machine learning model can be transformed into a **business-oriented pricing intelligence tool** that supports:

- seller pricing decisions
- market positioning analysis
- listing quality assessment
- pricing strategy generation

---

## Future Improvements
This project can be extended in several directions:

### 1. Time-to-Sell Modeling
The current dataset does not contain actual selling duration information.  
A future version could model **days on market** and connect price recommendations with expected selling speed.

### 2. Dynamic Pricing Bands
Instead of fixed ±5% strategy rules, future versions could generate adaptive price bands based on:
- vehicle segment
- demand intensity
- market sensitivity
- historical sales behavior

### 3. Better Similarity Modeling
Current similarity logic is rule-based.  
Future work could use:
- nearest neighbors
- similarity scoring
- embedding-based matching

### 4. Additional Data Sources
Potential future features:
- regional demand indicators
- fuel price trends
- macroeconomic variables
- listing freshness
- user engagement metrics
- view/favorite counts

### 5. NLP and Computer Vision
Future versions could use:
- vehicle descriptions with NLP
- listing photos with computer vision

This could improve the understanding of:
- cosmetic condition
- premium equipment
- listing quality

### 6. Model Optimization
Performance could be further improved through:
- hyperparameter tuning
- cross-validation
- CatBoost / LightGBM / XGBoost
- ensemble methods

### 7. Productization
This project can evolve into an end-to-end pricing intelligence system with:
- automated data ingestion
- feature processing pipelines
- model prediction API
- seller dashboard
- real-time recommendation engine

---

## Portfolio Value
This project was designed not only as a technical machine learning notebook, but as a **product-oriented pricing analytics use case**.

It shows the ability to:
- frame a business problem
- clean and interpret real marketplace data
- build predictive models
- compare models objectively
- generate strategy-oriented outputs
- think beyond prediction into decision support and productization

---

## Author
Mehmet Ali Şahin

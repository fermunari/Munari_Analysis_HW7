# Munari_Analysis_HW7
## Streamflow Forecasting Workflow (5-Day Prediction Model)

### Overview

This repository contains a complete workflow for generating 5-day streamflow forecasts using historical USGS gauge data. The project implements simple statistical forecasting approaches and evaluates their performance using training and validation datasets.

The workflow is designed to:

Retrieve hydrologic data
Train forecasting models
Validate model performance
Generate short-term (5-day) forecasts

### Features
Data retrieval via hf_hydrodata
Model training (long-term average and day-of-year approaches)
Forecast generation (5-day horizon)
Model evaluation metrics and visualization
Reproducible workflow using shell script

### Repository Structure

forecast_functions.py     # Core functions (data processing, modeling, plotting)
train_model.py            # Train and validate forecasting model
generate_forecast.py      # Generate 5-day forecasts
run_workflow.sh           # End-to-end workflow automation
README.md                 # Project information
activities.md             # Assignment instructions / notes

### Getting Started
1. Clone the Repository
git clone https://github.com/fermunari/Munari_Analysis_HW7.git
cd Munari_Analysis_HW7

2. Create Environment

If using conda:

conda create -n hw7_forecast python=3.11
conda activate hw7_forecast
conda config --add channels conda-forge

Install dependencies:

pip install pandas matplotlib hf_hydrodata

3. Run Workflow

You can run everything at once:

bash run_workflow.sh

Or run scripts individually:

Train Model
python train_model.py \
  --email YOUR_EMAIL \
  --pin YOUR_PIN \
  --gauge-id 09506000

Generate Forecast
python generate_forecast.py \
  --email YOUR_EMAIL \
  --pin YOUR_PIN \
  --forecast-date 2024-04-30

### Models Implemented
1. Long-Term Average Model
Uses historical average streamflow
Simple baseline model
Useful for comparison

2. Day-of-Year Model
Uses seasonal patterns based on day-of-year (January 24th)
Captures recurring hydrologic trends

### Outputs
Forecast plots (observed vs predicted)
Validation metrics (e.g., RMSE, MAE)
Saved trained model objects
Key Functions (forecast_functions.py)

get_training_test_data() – splits dataset
fit_longterm_avg_model() – trains baseline model
make_5day_forecast_longterm() – generates forecasts
compute_metrics() – evaluates model performance
plot_validation() – visualization of results

### Dependencies
Python 3.11
pandas
matplotlib
hf_hydrodata

### Notes
Requires valid hf_hydrodata credentials (email + PIN)
Gauge ID defaults to 09506000 (can be changed)
Model choice controlled via --model argument


### Author

Fernanda Munari
M.S. Hydrogeology – University of Arizona

### License

This project is for academic use. Add a license (e.g., MIT) if distributing publicly.

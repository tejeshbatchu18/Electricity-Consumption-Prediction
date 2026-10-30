# Electricity Consumption Prediction Using Machine Learning

## Overview
This project develops an end-to-end machine learning workflow to predict next-hour household electricity consumption using historical power measurements. It follows the CRISP-DM (Cross-Industry Standard Process for Data Mining) methodology.

The notebook cleans minute-level readings, aggregates them into hourly averages, creates lag and calendar features, trains regression models, evaluates their performance, and saves the selected model.

## Objectives
- Load and clean household electricity-consumption data.
- Handle invalid or missing readings.
- Aggregate minute-level measurements into hourly averages.
- Explore electricity-consumption patterns.
- Create lag-based and calendar features for next-hour prediction.
- Compare Linear Regression and Decision Tree Regression.
- Evaluate models using MAE, RMSE, and R².
- Save the selected model and demonstrate a prediction.

## Dataset
Expected dataset file: `household_power_consumption.csv`

The dataset should contain these columns:
- `Date`
- `Time`
- `Global_active_power`
- `Global_reactive_power`
- `Voltage`
- `Global_intensity`
- `Sub_metering_1`
- `Sub_metering_2`
- `Sub_metering_3`

The notebook reads the dataset from `/content/household_power_consumption.csv` in Google Colab. Upload or place the file at that location before running the notebook.

> Note: The report says the file structure is consistent with the Individual Household Electric Power Consumption dataset from the UCI Machine Learning Repository, but the exact source of the supplied file should be confirmed before submission.

## Models
The notebook compares:
1. Linear Regression
2. Decision Tree Regression

These are used for a regression task because the target is a numerical electricity-consumption value.

## Workflow (CRISP-DM)
1. **Business Understanding** — define next-hour household electricity consumption prediction.
2. **Data Understanding** — inspect the dataset and visualize consumption over time and by hour of day.
3. **Data Preparation** — clean fields, parse timestamps, convert measurements to numeric values, aggregate readings hourly, handle short missing-data gaps, and create features.
4. **Modelling** — train Linear Regression and Decision Tree Regression.
5. **Evaluation** — compare MAE, RMSE, and R² on a chronological hold-out test set.
6. **Deployment** — save the selected model and demonstrate a prediction function.

## Features
The notebook uses seven features:
- `Consumption_lag_1`
- `Consumption_lag_2`
- `Consumption_lag_3`
- `Consumption_lag_24`
- `Hour`
- `DayOfWeek`
- `Month`

The target is the next-hour average `Global_active_power` value.

**Important validation note:** The hourly series contains gaps. Because a simple `shift(-1)` targets the next available row, check that consecutive timestamps are exactly one hour apart before interpreting every target as exactly one hour ahead. This should be verified or corrected before final submission.

## Evaluation Metrics
- **MAE (Mean Absolute Error):** average absolute prediction error; lower is better.
- **RMSE (Root Mean Squared Error):** penalizes larger errors more strongly; lower is better.
- **R²:** measures fit relative to a baseline; higher is generally better.

Recorded notebook results (verify after your final run):

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 0.394730 | 0.545633 | 0.461798 |
| Decision Tree Regression | 0.371975 | 0.550005 | 0.453139 |

The notebook selects the model with the lower RMSE, which is Linear Regression in the recorded results. The Decision Tree has lower MAE, so the best model depends on the chosen metric.

## Requirements
The notebook uses common Python data-science libraries, including:
- pandas
- NumPy
- Matplotlib
- scikit-learn
- joblib

The notebook may import additional libraries. Refer to its import cells for the exact environment.

## How to Run in Google Colab
1. Download `Electricity_Consumption_Prediction_Syllabus_Aligned.ipynb`.
2. Open Google Colab: https://colab.research.google.com/
3. Select **File → Upload notebook** and upload the `.ipynb` file.
4. Upload or place `household_power_consumption.csv` at `/content/household_power_consumption.csv`.
5. Run the notebook cells from top to bottom.
6. Review the generated charts, evaluation table, and example prediction.
7. Confirm that the saved model file is generated successfully.

## Limitations
- The project uses a single household's historical measurements.
- The evaluation uses a chronological hold-out split; the notebook does not perform hyperparameter search or cross-validation.
- External factors such as weather, occupancy, holidays, and electricity prices are not included.
- The notebook saves a model and demonstrates prediction; it is not a deployed website, API, or production application.
- Validate the timestamp gaps and next-hour target logic before final submission.

## Project Files
- `Electricity_Consumption_Prediction_Syllabus_Aligned.ipynb` — notebook containing preprocessing, analysis, training, evaluation, and prediction.
- `household_power_consumption.csv` — required input dataset.
- A trained model file — generated by the notebook when its save cell is run.

## Author
- Name: B. Tejesh
- Roll Number: 24501A4407
- Branch: CSD

Update the author details if this README is being used by another student.

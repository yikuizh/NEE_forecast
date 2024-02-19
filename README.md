# Net Ecosystem Exchange (NEE) forecast
How to map NEE in regions that lack state-of-the-art observations? This repository proposes an XGBoost model for global NEE extrapolation and mapping by fusing multiple sources of data, including `Fluxnet` project observation (https://www.fluxcom.org/), Remote sensing data (MODIS) (https://modis.gsfc.nasa.gov/), GLDAS, and ERA5 reanalysis data (https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=overview) at monthly time scale. The model is trained in all locations of Fluxnet station in Europe and applied in US at grid scale as an out-of-sample prediction to test the model generalization ability in the observation-missing regions. The jupyter notebooks include data collection, data preprocessing, feature engineering, feature selection, modeling and visualization. The project is in cooperation with Dr. Alon Nissan, ETH Zurich.

# Model Input and output
`data` folder contains two samples `csv` files `data2_ML.csv` and `data2_ML_new.csv` showing the preprocessed data format that can be used for the XGBoost model from multiple data sources; `result` folder contains sample outputs `csv` files that shows the `NSE` scores at each of the prediction sites.

# UPDATE 05/07/2023
`xgboost_0507.ipynb` is the newest and cleanest version with:
- Updated atmospheric variables from ERA5 data

# UPDATE 04/22/2023
`xgboost_04022023.ipynb` is the updated and cleaned version with updates in:
- Data loading
- Model performance Visualization
- Feature importance evaluation 

# Scripts for modeling:
(1).`xgboost_0121.ipynb` is the oldest version including functions for:
- Loading dataset
- Preparing dataset for training 
- Feature selection/engineering as well as the visualization
- Leave-one-out XGBoost training and prediction strategy
- single location prediction visualization 
- Full model training processes on all sites
(2). `XGBoost_workflow.ipynb`: a simplified demo for the `XGBoost` model input feature preparation, poointing out the required features for the following prediction;
(3). `LSTM_NEE_exp2.ipynb`/`LSTM_NEE_exp2.ipynb`: LSTM model was applied based on the same 'loaded dataset' and training strategy as the `XGBoost` model, but as the performance is worse than `XGBoost` model, the `LSTM` NEE mapping model is discarded and only shown here as a demo. 

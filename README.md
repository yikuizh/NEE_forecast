# Net Ecosystem Exchange (NEE) forecast
How to map NEE in regions that lack state-of-the-art observations? This repository proposes an XGBoost model for global NEE extrapolation and mapping by fusing multiple sources of data, including `Fluxnet` project observation (https://www.fluxcom.org/), Remote sensing data (MODIS) (https://modis.gsfc.nasa.gov/), and ERA5 reanalysis data (https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=overview) at monthly time scale. The model is trained in all locations of Fluxnet station in Europe and applied in US at grid scale as an out-of-sample prediction to test the model generalization ability in the observation-missing regions. The jupyter notebooks include data collection, data preprocessing, feature engineering, feature selection, modeling and visualization. The project is in cooperation with Dr. Alon Nissan, ETH Zurich.

# Model Input and output
`data` folder contains two samples `csv` files `data2_ML.csv` and `data2_ML_new.csv` for the preprocessed data format that can be used for the XGBoost model from multiple data sources; `result` folder contains sample outputs `csv` files that shows the `NSE` scores at each of the prediction sites.

# UPDATE 05/07/2023
xgboost_0507.ipynb is the newest and clean version for:
- Updated atmospheric variables from ERA5 data

# UPDATE 04/22/2023
xgboost_04022023.ipynb is the newest and clean version with updates in:
- Data loading
- Model performance Visualization
- Feature importance evaluation 

- Reading data
- Preparing dataset for training 
- Feature selection/engineering 
- leave-one-out XGBoost training and prediction on sub-dataset 
- single event visualization 
- Full model training on all sites

# Machine learning for sub-seasonal pattern-based precipitation prediction
The repository includes codes for a benchmarking sub-seasonal pattern-based precipitation prediction model as well as feature selection using Random Forest model, including two folders:
1) `DataProcess`: create the target data and all possible features used for prediction
- `ClusterSelect.ipynb`/`Cluster_CESM.ipynb`: Derive monthly and seasonal precipitation regional patterns as the prediction target based on K-means clustering analysis, using precipitation data from observation `EOBS` and the ensemble earth system model `CESM` respectively;
- `EOF_slp.ipynb`/'EOF_sst.ipynb'/'eof_u200.ipynb'/'eof_z500.ipynb': pre-process `sea level pressure`, `sea surface temperature`, `U200`, `Z500` from CESM ensemble and conduct EOF analysis to create features;
- `NAO.ipynb`: calculate seas surface temperature anomalies in a North Atlantic and the annual NAO index
2) `FeatureEngineering`:
- `FeatureEngineering.ipynb`: The script collects all types of pre-processed features  and outputs a feature set with all 235 features and corresponding values;
- `feature_selection.ipynb`: The script uses the selected features to run feature selection models -- 1) hyperpatameter selection for the random forest model; 2) feature selection for Recursive feature elimination-Random Forest (REF-RF) and Monte Carlo-Random Forest (MC-RF); 3) model performance evaluation for RFE-RF and MC-RF model; And visualization of the evaluation scores.
# Dataset preparation: Both observation dataset and earth system model data were used for model feature engineering and prediction
- Precipitation: collected from both `EOBS` as observation and `CESM` earth system model simulation;
- Other climate variables: collected from `CESM` earth system model simulation.
- `CESM` dataset refers to https://www.cesm.ucar.edu/;
- `EBOS` dataset refers to https://www.ecad.eu/download/ensembles/download.php


# Nonlinear-Drivers-of-Land-Carbon-Sources-and-Sinks-with-Spatial-Effects-by-ExplainableGeoML
This repository contains computed raster and tabular LCS data, LCE data, driver data, and code for interpretable machine learning
# Abstract
Revealing the impact of socio-ecological factors on land carbon sources/sinks is the key to balancing ecological protection and economic development under the carbon neutrality goal. However, existing studies are limited by the separation of source-sink perspectives, insufficient dynamic interaction analysis, and the difficulty in simultaneously depicting spatial effects and nonlinear relationships, which restricts the in-depth understanding of the driving mechanism. Based on estimated land carbon emissions (LCE) and land carbon sinks (LCS) in Yunnan central urban agglomeration (YNUA), this study incorporated geographic coordinates (GEO) as spatial features and applied an explainable geospatial machine learning (XGeoML) model that integrates LightGBM and GeoShapley. This model was used to systematically examine the nonlinear driving mechanisms from four perspectives: importance and directionality, threshold effects, interaction effects, and spatial effects. The results revealed that (1) LCE continued to rise but at a decelerating rate, while LCS showed an overall declining trend with fluctuation. Both exhibited significant spatial clustering. (2) Human activities, climate, and vegetation factors jointly explained over 65% of the spatiotemporal variation in LCE and LCS, with the independent influence of GEO surpassing that of most driving factors. (3) The influence of socioeconomic factors varied with the stage of urban development. Natural ecological factors exhibited multi-threshold nonlinear responses, and landscape pattern optimization supported emission reduction and sink enhancement. Significant dynamic interactions were observed among the factors. (4) From the local scale, GEO not only directly shaped the spatial pattern of LCE and LCS but also modulated the intensity and direction of other factors, demonstrating a clear spatial regulatory effect. This study emphasizes the necessity of incorporating nonlinearity and spatial effects into carbon management and provides a scientific basis for precise regional emission reduction and sink enhancement.
# Code for Spatial Machine Learning and Interpretability Analysis

This repository contains code for multi-model evaluation based on spatial clustering cross-validation, GeoShapley partial dependency graphs, SHAP interaction analysis, and more.

## Dependencies

- Python 3.8+
- Install dependencies: `pip install -r requirements.txt`
- Note: `geoshapley` must be installed separately (see https://github.com/geoshapley/geoshapley)

## Data Preparation

Place the CSV files for each year in the `data/` directory, using the naming convention `2002GWRF.csv`, `2009GWRF.csv`, etc.  
The CSV files must contain the following columns (specific column names can be adjusted in `config.py`):
- Feature columns: `RD, PD, LPI, contag, pre, pop, NDVI, HAI, GDP, DEM, srad`
- Target column: `LCE` or `LCS`
- Coordinate columns: `longitude, latitude`

## Running Instructions

1. **Main Model Evaluation**  
   `python main_model_evaluation.py`  
   Outputs the spatial cross-validation results and test set performance for each model, and performs statistical tests.

2. **GeoShapley Partial Dependence Plot**  
   `python geoshapley_pdp.py`  
   Calculates and plots the GeoShapley partial dependence plot (using GAM smoothing).

3. **Confidence Intervals for Threshold Points**  
   `python geoshapley_threshold_ci.py`  
   Mark threshold points on the partial dependence plot and calculate bootstrap confidence intervals.

4. **SHAP Interaction**  
   `python shap_interaction.py`  
   Analyse SHAP interaction values for two specified variables, fit GAM curves grouped by a third variable, and calculate intersection points.

## Configuration Modifications

All adjustable parameters (year, features, model parameters, etc.) are defined in `config.py` or in the constants section at the top of each script. Modify them as required.

## Output Results

- Evaluation metrics and p-values for statistical tests are printed to the console.
- Images are saved as PNG files in the current directory.
                                                                                                                                                                                      

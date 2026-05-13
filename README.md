# Estimation of Traffic Noise Using Sentinel-2 Imagery and Elevation Model Based on Deep Learning

## Introduction

Traffic noise is an important environmental issue that affects human health and urban quality of life. Traditional physical noise models can provide reliable estimates, but they often require detailed input data, high computational effort, and extensive modelling parameters.

This repository contains the code and selected outputs from my master's thesis, which explores a deep learning-based approach for estimating road traffic noise using geospatial raster data. The study applies a U-Net-based convolutional neural network to predict continuous road traffic noise patterns from Sentinel-2 imagery and Digital Elevation Model (DEM) data.

The project focuses not only on prediction accuracy, but also on whether the model can learn terrain-related noise propagation behaviour, such as attenuation caused by elevation differences, simulated barrier walls, and shadow-effect patterns.

## Project Overview

The research compares two main modelling approaches:

1. A baseline model using Sentinel-2 image-based input features.
2. A DEM-integrated model using Sentinel-2 imagery and elevation information.

Additional experiments were conducted to analyse:

- DEM normalization strategies,
- data augmentation and masking strategies,
- model behaviour under simulated barrier-wall conditions,
- shadow-effect-like patterns,
- model generalization in a different geographical region.

## Objectives

The main objectives of this project are:

- Estimate spatial road traffic noise levels using deep learning and geospatial raster data.
- Compare a Sentinel-2-based baseline model with a DEM-enhanced model.
- Evaluate model performance using RMSE, MAE, and R².
- Analyse the role of topography in predicted noise propagation.
- Test whether the trained model shows physically meaningful behaviour under controlled elevation simulations.
- Assess model generalization using selected patches from Baden-Württemberg.

## Repository Structure

```text
Traffic-Noise-Estimation/
│
├── README.md
├── .gitignore
│
├── Data Processing/
│   ├── DEM_Cropping.ipynb
│   ├── DEM_Tiling.ipynb
│   ├── Patch Extraction.ipynb
│   ├── Patch Extraction_nodem.ipynb
│   └── Patch Formation.ipynb
│
├── Traffic Noise Estimation Sentinel-2 image/
│   └── Traffic Noise Estimation Sentinel-2 image.ipynb
│
├── Traffic Noise Estimation with DEM/
│   └── Traffic Noise Estimation with DEM.ipynb
│
├── Best Performing Model.ipynb
│
├── Barrier Wall Simulation/
│   └── Barrier_wall-Simulation.ipynb
│
├── Shadow Effect/
│   └── Shadow Effect.ipynb
│
├── Model Generalization/
│   └── Model Generalization.ipynb
│
└── Results/
    ├── Barrier Wall Simulation/
    ├── DEM and no DEM comparison/
    ├── Model Generalization/
    ├── Model Without DEM/
    ├── Model with DEM/
    └── Shadow Effect/

```
## Notebook Descriptions

### Data Processing

The notebooks in this folder contain the preprocessing workflow used to prepare the geospatial raster inputs. This includes DEM cropping, DEM tiling, patch extraction, and patch formation. The processed patches combine Sentinel-2 image bands, DEM information, and road traffic noise data into aligned raster inputs for model training and evaluation.

### Traffic Noise Estimation Sentinel-2 image

This notebook contains the baseline model workflow using Sentinel-2 image-based input features. The model uses RGB and NIR bands to estimate road traffic noise without adding elevation information. It includes experiments related to masking strategy, augmentation, training, and evaluation.

### Traffic Noise Estimation with DEM

This notebook contains the DEM-integrated traffic noise estimation workflow. The model uses Sentinel-2 imagery together with DEM information to evaluate whether topography improves noise prediction and spatial consistency. Different DEM normalization strategies are tested, including Z-score normalization, percentile-based scaling, and fixed-denominator scaling.

### Best Performing Model

This notebook contains the final selected model configuration. The best-performing setup is based on the DEM-integrated model with fixed-denominator DEM scaling. It includes hyperparameter tuning using different learning rates, batch sizes, and loss functions, followed by evaluation across different random seeds.

### Barrier Wall Simulation

This notebook contains the controlled barrier-wall simulation experiment. Artificial elevation modifications are introduced near selected road corridors to analyse whether the trained model responds to barrier-like topographic changes. The experiment compares different barrier heights, widths, and spatial configurations.

### Shadow Effect

This notebook contains the rectangular-object simulation experiment used to analyse shadow-effect behaviour. Synthetic rectangular elevation objects are inserted into the DEM, and the change in predicted noise is analysed in front and shadow regions.

### Model Generalization

This notebook evaluates the trained model on selected patches from Baden-Württemberg. The purpose is to test whether the model trained on the Swiss dataset can transfer learned spatial noise patterns to a different geographical region.

## Dataset Used

Sentinel 2(R,G,B,NIR), Swiss Alti3D DEM as input , Noise Map by FOEN as ground truth The full datasets are not included in this repository because of large file size and data storage limitations

## Conclusion

This project shows that a U-Net-based deep learning model can approximate large-scale road traffic noise patterns using Sentinel-2 imagery and DEM data. Sentinel-2 imagery alone provides useful spatial information for detecting road-related noise structures, while the integration of elevation data improves spatial consistency and supports the representation of terrain-related effects.


## Keywords

Traffic Noise Estimation, Road Traffic Noise, Environmental Noise, Deep Learning, U-Net, CNN, Sentinel-2, DEM, Remote Sensing, GIS, Geospatial Analysis, Raster Processing, Noise Mapping, Terrain Influence, Barrier Simulation, Shadow Effect, Python, PyTorch

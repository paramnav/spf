# Spatial Prediction Framework (SPF)

A generalized framework for spatial predictions using machine learning models, designed to work with any spatial dataset that follows the specified format.

## Overview

The Spatial Prediction Framework (SPF) is a comprehensive toolkit for creating spatial predictions from point measurements and gridded features. It provides a standardized approach to spatial prediction problems, supporting both tree-based and deep learning models.

## Features

- **Generalized Framework**: Works with any spatial dataset following the specified format
- **Multiple Model Types**: Support for Random Forest, XGBoost, CatBoost, Neural Networks, and TabPFN
- **Input Formats**: Support for .npy, .nc (NetCDF), and .grd files

## Repository Structure

```
spf/
├── config/
│   └── spf_config.yaml          # Main configuration file
├── data/
│   ├── features/                 # Gridded feature data (.npy, .nc, .grd)
│   └── measurements/             # Point measurements (.csv)
├── notebooks/
│   ├── 01_data_preprocessing.ipynb      # Data preprocessing workflow
│   ├── 02_tree_based_models.ipynb       # Tree-based model training
│   ├── 03_deep_learning_models.ipynb    # Deep learning model training
│   └── 04_visualization.ipynb           # Results visualization
├── src/
│   ├── preprocessing/            # Data preprocessing modules
│   ├── models/                   # Model implementations
│   └── postprocessing/           # Post-processing and evaluation
├── output/                       # Model outputs and predictions
└── docs/                         # Documentation
```

## Data Format Requirements

### Features (Gridded Data)
- **Format**: .npy, .nc (NetCDF), or .grd files
- **Structure**: 2D or 3D arrays with spatial coordinates
- **Grid**: Regular grid (e.g., 2160x4320 for global datasets)
- **Coordinate System**: WGS84 or configurable

### Measurements (Point Data)
- **Format**: CSV file
- **Required Columns**: 
  - `x` or `longitude`: X-coordinate
  - `y` or `latitude`: Y-coordinate  
  - `label` or `target`: Target variable to predict
- **Optional Columns**: Additional metadata

## Quick Start

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Prepare Your Data

Place your data in the appropriate folders:
- Gridded features → `data/features/`
- Point measurements → `data/measurements/`

### 3. Configure the Framework

Edit `config/spf_config.yaml` to match your dataset and requirements.

### 4. Run the Workflow

Execute the notebooks in order:
1. **Data Preprocessing**: Extract features for measurement locations
2. **Tree-based Models**: Train Random Forest, XGBoost, CatBoost
3. **Deep Learning**: Train Neural Networks and TabPFN
4. **Visualization**: Generate maps and analysis plots

## Configuration

The `spf_config.yaml` file is the central control point for the entire framework. Key sections include:

- **Data Configuration**: File paths, formats, and grid specifications
- **Model Configuration**: Hyperparameter ranges for all supported models
- **Training Configuration**: Data splitting, validation, and ensemble methods
- **Evaluation Configuration**: Metrics and spatial validation settings

## Supported Models

### Tree-based Models
- **Random Forest**: Configurable ensemble size, depth, and feature selection
- **XGBoost**: Gradient boosting with extensive hyperparameter options
- **CatBoost**: Categorical boosting with built-in categorical handling

### Deep Learning Models
- **Neural Networks**: Configurable architectures with dropout and regularization
- **TabPFN**: Transformer-based model for tabular data

## Hyperparameter Optimization

The framework automatically optimizes hyperparameters using:
- **Optuna**: Advanced optimization with pruning and early stopping
- **Hyperopt**: Bayesian optimization
- **scikit-learn**: Grid and random search

## Spatial Validation

Proper spatial validation is crucial for spatial prediction tasks:
- **Spatial Cross-Validation**: Ensures training and validation sets are spatially separated
- **Leave-One-Out**: For small datasets
- **Custom Spatial Folds**: User-defined spatial partitioning

## Output and Visualization

The framework generates:
- **Predictions**: Gridded predictions in multiple formats
- **Model Artifacts**: Trained models and feature importance
- **Visualizations**: Maps, performance plots, and analysis reports
- **Evaluation Reports**: Comprehensive model comparison

## Example Use Cases

- **Marine Sediment TOC**: Total Organic Carbon prediction from sediment samples
- **Environmental Variables**: Temperature, salinity, or other oceanographic parameters
- **Geological Properties**: Soil composition, rock properties, or mineral content
- **Climate Data**: Precipitation, temperature, or other meteorological variables

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Citation

If you use this framework in your research, please cite:

```bibtex
@software{spatial_prediction_framework,
  title={Spatial Prediction Framework (SPF)},
  author={Your Name},
  year={2024},
  url={https://github.com/yourusername/spf}
}
```

## Support

For questions and support:
- Open an issue on GitHub
- Check the documentation in the `docs/` folder
- Review the example notebooks

## Acknowledgments

This framework was inspired by the nn-toc-update project for marine sediment TOC prediction and generalized for broader spatial prediction applications. 

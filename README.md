# Geospatial Fine-grained Population Density Estimation Using Machine Learning

**Portfolio Case Study | Data Science & Machine Learning Internship at Ooredoo Algeria**

> This repository presents a high-level overview of a geospatial machine learning project and my technical contributions. It does not contain company-owned source code, confidential datasets, trained models, or prediction results.

## 📌 Project Overview

The objective of this project was to develop a geospatial machine learning pipeline to estimate population density across Algeria.

The solution combined population-related reference data with multiple geographic and satellite-derived data sources to build predictive models. The workflow was designed to extend population density estimation from a labelled sample of geographic cells to a nationwide spatial grid.

The project covered the complete pipeline, from geospatial data collection and preprocessing to machine learning, geographic segmentation, nationwide inference, calibration, database integration, and interactive visualization.

The final solution included a web-based platform allowing users to explore spatial estimates through an interactive map and statistical dashboards.

## 🎯 My Contributions

My contributions covered several stages of the project:

- Collected and prepared geospatial and satellite-derived data from multiple sources.
- Cleaned, transformed, and integrated heterogeneous datasets.
- Combined geographic features with reference population data to prepare the modelling dataset.
- Compared candidate machine learning models.
- Performed feature engineering and feature selection.
- Investigated spatial prediction errors and limitations of a single-model approach.
- Applied K-means clustering to segment geographic areas according to their characteristics.
- Developed a specialized modelling strategy using multiple CatBoost models.
- Prepared nationwide geospatial data for large-scale inference.
- Generated population density estimates across the national grid.
- Applied a calibration stage using official statistical data.
- Stored processed results in PostgreSQL.
- Contributed to the development of an interactive web platform for geospatial exploration and data visualization.

## ⚙️ Technical Workflow

### 1. Geospatial Data Collection & Preparation

The project started with a reference dataset containing labelled geographic cells distributed across Algeria.

I collected additional geographic information for these locations from several sources:

- **OpenStreetMap (OSM):** Geographic and infrastructure-related information.
- **Building data:** Building-related geographic features.
- **Global Human Settlement Layer (GHSL):** Built-environment and settlement-related information.
- **Harmonized satellite data:** Remote-sensing indicators, including NDVI and NDBI.

The collected datasets were cleaned, transformed, and merged with the reference data to create a unified dataset for machine learning.

### 2. Exploratory Modelling & Feature Engineering

To identify suitable algorithms for the prediction task, I initially used **LazyPredict** to compare several candidate regression models.

Following this comparison, I performed:

- Feature engineering to improve the input variables.
- Feature selection to retain relevant predictive features.
- Model evaluation to identify a suitable approach.

**CatBoost** was selected for the subsequent modelling stage based on the evaluation results.

### 3. Spatial Error Analysis

Although the initial model achieved good overall evaluation metrics, further investigation revealed significant prediction errors in certain geographic environments.

This highlighted a limitation of using a single general-purpose model across geographically diverse areas.

Rather than relying exclusively on aggregate evaluation metrics, we investigated problematic areas and reconsidered the modelling strategy to account for geographic heterogeneity.

### 4. Geographic Segmentation & Specialized Modelling

To address the limitations of the initial approach, I applied **K-means clustering** to segment geographic areas according to their characteristics.

The resulting segmentation was used to introduce a specialized modelling strategy.

Instead of relying on one model for the entire territory, the solution incorporated multiple **CatBoost sub-models**, with certain geographic categories handled together through a weighted approach.

This allowed the prediction workflow to better account for differences between geographic environments.

### 5. Nationwide Inference

Once the modelling strategy had been established, the workflow was extended to a nationwide H3 grid covering Algeria.

I generated the geographic cells required for inference and collected their corresponding geospatial features using the same general data preparation methodology developed during the training stage.

The prepared data was then passed through the specialized prediction workflow to generate population density estimates across the country.

### 6. Calibration Using Official Statistics

Following nationwide inference, a calibration stage was performed using official statistical data from Algeria's National Statistics Office (ONS).

This step was introduced to address limitations and potential biases in the reference population data used during training.

Calibration helped adjust the nationwide estimates using an external statistical reference.

### 7. Database Integration

After prediction and calibration, the resulting data was exported and stored in a **PostgreSQL** database.

The database served as the data source for the visualization platform, making the processed geospatial information available for interactive exploration.

### 8. Interactive Geospatial Platform

In addition to the machine learning pipeline, I contributed to the development of a web-based platform designed to make the results accessible and interpretable.

The platform consisted of two main sections:

#### 🗺️ Interactive Geospatial Map

The map allowed users to:

- Search and navigate across geographic locations.
- Explore Algeria through a grid of H3 hexagonal cells.
- Zoom in and out while maintaining appropriate spatial resolution.
- Visualize geographic cells using colours representing estimated population density or geographic cluster categories.

The working grid used **H3 resolution 8**, with lower-resolution levels available to support visualization at different zoom levels.

#### 📊 Statistical Dashboard

The second section provided an overview of the results through dashboards presenting:

- Population-related summaries at wilaya level.
- A nationwide overview.
- Aggregated information to facilitate geographic comparison and exploration.

The platform connected the processed data stored in PostgreSQL with an interactive interface for exploring the results.

## 🛠️ Technologies & Methods

| Category | Technologies / Methods |
|---|---|
| Programming | Python |
| Geospatial data | H3, OpenStreetMap, GHSL |
| Remote sensing | NDVI, NDBI |
| Machine learning | CatBoost, LazyPredict |
| Unsupervised learning | K-means clustering |
| Feature preparation | Feature engineering, feature selection |
| Database | PostgreSQL |
| Statistical reference | ONS data |
| Visualization | Interactive maps and dashboards |

## 💡 Key Challenges & Learnings

This project provided practical experience in addressing several challenges encountered in real-world geospatial machine learning.

**Integrating heterogeneous data sources**

Combining geographic, building-related, and satellite-derived information required careful preprocessing and integration to create consistent model inputs.

**Looking beyond aggregate model metrics**

Good overall evaluation metrics did not guarantee reliable predictions everywhere. Investigating spatial errors revealed the importance of considering geographic heterogeneity.

**Adapting the modelling strategy**

The initial single-model approach was improved by introducing geographic segmentation and specialized models.

**Scaling to nationwide inference**

The project required extending the data preparation and prediction pipeline from a labelled sample to a much larger nationwide geographic grid.

**Addressing limitations in reference data**

The calibration stage highlighted the importance of evaluating training-data quality and potential biases, especially when predictions are intended to represent large geographic areas.

**Connecting machine learning to an end-user application**

The project extended beyond model development to include database storage and an interactive platform for exploring the results.

## 📚 What I Learned

Through this project, I gained hands-on experience with:

- End-to-end machine learning workflows.
- Geospatial data collection and preprocessing.
- Integration of multiple geographic and satellite-derived datasets.
- Feature engineering and feature selection.
- Regression model comparison and evaluation.
- Unsupervised geographic segmentation.
- Specialized machine learning models.
- Large-scale geospatial inference.
- Calibration using external statistical references.
- PostgreSQL database integration.
- Interactive data visualization applications.

Most importantly, I learned that building a useful machine learning solution involves more than selecting an algorithm and optimizing its metrics. Data quality, geographic context, error investigation, calibration, scalability, and the final application all play important roles.

## 🔒 Confidentiality Notice

This repository is intended solely as a high-level portfolio description of my technical contributions.

It does not include:

- The original reference dataset or population and density labels.
- Geographic coordinates, cell geometries, or confidential location-level records.
- Collected and merged project datasets.
- Nationwide grid data or prediction outputs.
- Trained model files, serialized objects, or model configurations.
- Internal source code or database exports.
- Confidential evaluation metrics or calibration parameters.
- Internal documentation, screenshots, production URLs, or credentials.

All company-owned data, implementation assets, and restricted project information remain excluded.

This case study is not an official publication by Ooredoo Algeria. Any information included in this repository remains subject to the applicable confidentiality agreement and should only be published where disclosure is authorized.

---

*This case study describes my work and learning during an internship project. It does not represent an official publication by Ooredoo Algeria.*

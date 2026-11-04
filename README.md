# Geospatial-Population-Density-Estimation-Using-Machine-Learning
Portfolio case study — based on work carried out during my graduation internship at Ooredoo Algeria.  This repository presents a high-level overview of the project, its technical workflow, and my contributions. It does not contain company-owned source code, confidential datasets, model artifacts, or prediction results.

1. Project Overview

The objective of this project was to develop a geospatial machine learning pipeline capable of estimating population density across Algeria.

The project combined population-related reference data with multiple geospatial and remotely sensed data sources to build predictive models. The resulting workflow was designed to extend population density estimation from a labelled sample of geographic cells to a nationwide spatial grid.

Beyond model development, the project involved building an end-to-end solution covering geospatial data collection, preprocessing, feature engineering, model evaluation, territory segmentation, nationwide inference, calibration, database integration, and interactive visualization.

The final solution included a web-based platform allowing users to explore spatial estimates through an interactive map and statistical dashboards.

2. My Contributions

I contributed to several stages of the project, including:

Collecting geospatial and satellite-derived data from multiple sources.

Cleaning, transforming, and integrating heterogeneous datasets.

Preparing the machine learning dataset by combining geographic features with reference population data.

Comparing candidate machine learning models.

Performing feature engineering and feature selection.

Investigating spatial prediction errors and identifying limitations of a single-model approach.

Applying K-means clustering to segment geographic areas according to their characteristics.

Developing a specialized modelling strategy using multiple CatBoost models.

Preparing nationwide geospatial data for large-scale inference.

Generating population density estimates across the national grid.

Applying a calibration stage using official statistical data.

Storing processed results in PostgreSQL.

Developing an interactive web platform for geospatial exploration and data visualization.

3. Technical Workflow

3.1. Geospatial Data Collection and Preparation

The project started with a reference dataset containing labelled geographic cells distributed across Algeria.

My first responsibility was to collect additional geographic information for these locations from several sources.

The data sources included:

OpenStreetMap (OSM): Geographic and infrastructure-related information.

Building data: Building-related geographic features.

Global Human Settlement Layer (GHSL): Built-environment and settlement-related information.

Harmonized satellite data: Remote-sensing indicators, including NDVI and NDBI.

The collected datasets required preprocessing before they could be used for machine learning.

This stage involved cleaning, transforming, and merging the different sources with the reference dataset to construct a unified modelling dataset.

3.2. Exploratory Modelling and Feature Engineering

After preparing the dataset, I explored different machine learning approaches to identify suitable candidate models.

LazyPredict was used during the initial model comparison stage to evaluate several regression algorithms and identify promising candidates.

Following this comparison, I worked on feature engineering and feature selection to improve the quality of the input data and retain relevant predictive features.

CatBoost was selected for the subsequent modelling stage based on the evaluation results obtained during the project.

3.3. Spatial Error Analysis

Although the initial model achieved good overall evaluation metrics, further investigation revealed significant prediction errors in certain geographic environments.

This demonstrated that a single general-purpose model did not adequately capture the differences between all types of territory.

Rather than relying exclusively on aggregate evaluation metrics, we investigated problematic areas and reconsidered the modelling strategy to account for geographic heterogeneity.

3.4. Geographic Segmentation and Specialized Modelling

To address the limitations of the initial approach, I applied K-means clustering to segment geographic areas according to their characteristics.

The resulting segmentation was used to introduce a specialized modelling strategy.

Instead of using one model for the entire territory, the solution incorporated multiple CatBoost sub-models, with certain geographic categories handled together through a weighted approach.

This allowed the prediction workflow to better account for differences between geographic environments.

3.5. Nationwide Inference

Once the modelling strategy had been established, the workflow was extended to a nationwide H3 grid covering Algeria.

I generated the geographic cells required for inference and collected the corresponding geospatial features using the same general data preparation methodology developed during the training stage.

The prepared data was then passed through the specialized prediction workflow to generate population density estimates across the country.

This stage required extending the data collection and preprocessing pipeline beyond the original labelled sample.

3.6. Calibration Using Official Statistics

Following nationwide inference, a calibration stage was performed using official statistical data from Algeria's National Statistics Office (ONS).

This step was necessary because the reference population data used during training had limitations that could introduce bias into the resulting estimates.

Calibration helped adjust the predictions using an external statistical reference.

3.7. Database Integration

After prediction and calibration, the resulting data was exported and stored in a PostgreSQL database.

The database served as the data source for the visualization platform, making the processed geospatial information available for interactive exploration.

3.8. Interactive Geospatial Platform

In addition to the machine learning pipeline, I contributed to the development of a web-based platform designed to make the results accessible and interpretable.

The platform consisted of two main sections.

Interactive Geospatial Map

The map allowed users to:

Search and navigate across geographic locations.

Explore Algeria through a grid of H3 hexagonal cells.

Zoom in and out while maintaining an appropriate spatial resolution.

Visualize geographic cells using colours representing estimated population density or geographic cluster categories.

The map used H3 resolution 8 for the main working grid, with lower-resolution levels available to support visualization at different zoom levels.

Statistical Dashboard

The second section provided an overview of the results through dashboards presenting:

Population-related summaries at wilaya level.

A nationwide overview of the estimated data.

Aggregated information to facilitate geographic comparison and exploration.

The platform connected the processed data stored in PostgreSQL with an interactive interface for exploring the results.

4. Technologies and Methods

The project involved the following technologies and technical methods:

Area

Technologies / Methods

Programming

Python

Data processing

Data cleaning, transformation, integration

Geospatial data

H3, OpenStreetMap, GHSL

Remote sensing

NDVI, NDBI

Machine learning

CatBoost, LazyPredict

Unsupervised learning

K-means clustering

Feature preparation

Feature engineering, feature selection

Database

PostgreSQL

Visualization

Interactive maps and dashboards

5. Key Challenges and Technical Learnings

This project provided practical experience in addressing several challenges encountered in real-world geospatial machine learning.

Integrating heterogeneous data sources

Combining geographic, building-related, and satellite-derived information required careful preprocessing and integration to create consistent model inputs.

Looking beyond aggregate model metrics

Good overall evaluation metrics did not guarantee reliable predictions everywhere. Investigating spatial errors revealed the importance of considering geographic heterogeneity.

Adapting the modelling strategy

The initial single-model approach was improved by introducing geographic segmentation and specialized models.

Scaling from training data to nationwide inference

The project required extending the data preparation and prediction pipeline from a labelled sample to a much larger nationwide geographic grid.

Addressing limitations in reference data

The calibration stage highlighted the importance of evaluating the quality and potential biases of training labels, especially when predictions are intended to represent large geographic areas.

Connecting machine learning to an end-user application

The project extended beyond model development to include database storage and an interactive platform for exploring the results.

6. What I Learned

Through this project, I gained hands-on experience with:

End-to-end machine learning workflows.

Geospatial data collection and preprocessing.

Integrating multiple geographic and satellite-derived datasets.

Feature engineering and feature selection.

Regression model comparison and evaluation.

Unsupervised geographic segmentation.

Specialized machine learning models.

Large-scale geospatial inference.

Calibration using external statistical references.

PostgreSQL database integration.

Developing interactive data visualization applications.

Most importantly, I learned that building a useful machine learning solution involves more than selecting an algorithm and optimizing its metrics. Data quality, geographic context, error investigation, calibration, scalability, and the final application all play important roles.

7. Confidentiality Notice

This repository is intended solely as a high-level portfolio description of my technical contributions.

It does not include:

The original reference dataset or its population and density labels.

Geographic coordinates, cell geometries, or confidential location-level records.

The collected and merged project datasets.

Nationwide grid data or prediction outputs.

Trained model files, serialized objects, or model configurations.

Internal source code or database exports.

Confidential evaluation metrics or calibration parameters.

Internal documentation, screenshots, production URLs, or credentials.

All company-owned data, implementation assets, and restricted project information remain excluded.

This case study is not an official publication by Ooredoo Algeria. Any information included in this repository remains subject to the applicable confidentiality agreement and should only be published where disclosure is authorized.

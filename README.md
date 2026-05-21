# cloud-cover-classification-ai4eo
The classification of cloud 
## Project Overview
This project focuses on cloud cover classification using Sentinel-2 satellite imagery. The objective is to identify cloud-covered pixels by analysing spectral information from selected bands and applying a machine learning model.

The workflow includes data preprocessing, feature extraction, model training, and the generation of a cloud mask. The final output is a classification map distinguishing cloud and non-cloud regions.
## Motivation
Optical satellite imagery, such as data from the Sentinel-2 mission, plays a key role in Earth Observation (EO) by providing high-resolution information about the Earth's surface. These data are widely used in applications such as land cover mapping, vegetation monitoring, environmental assessment, and disaster management.

However, one of the main limitations of optical imagery is the presence of clouds. Clouds can partially or completely obscure the surface, leading to missing or unreliable information. As a result, many EO applications require an effective cloud detection step before further analysis can be performed.

Traditional approaches to cloud detection often rely on simple thresholding techniques based on spectral properties. While these methods are computationally efficient, they may struggle in complex scenarios, such as thin clouds or bright surfaces.

Recent advances in artificial intelligence, particularly machine learning and deep learning, have improved cloud detection performance. However, these methods often require large labelled datasets and significant computational resources.

This project is motivated by the need for a balanced approach: developing a method that is both effective and computationally efficient. By using spectral features and a classical machine learning model, this work aims to provide a practical solution that can be applied in real-world EO workflows with lower environmental cost.
## Study Area

The study area is located within Sentinel-2 tile T30UYC in Western Europe and was selected from a Sentinel-2B Level-2A scene acquired on 30 June 2022. The region was chosen due to its extensive cloud coverage and visible variations in cloud thickness and texture, making it suitable for cloud classification experiments using unsupervised machine learning methods.

The analysed subset contains dense cloud formations, semi-transparent cloud regions, and partially visible surface features beneath the cloud layer. These characteristics provide a useful test environment for comparing the behaviour of K-Means clustering and Gaussian Mixture Models (GMM) in multispectral satellite imagery.

To reduce computational cost and memory usage, only a cropped portion of the original Sentinel-2 scene was used during the analysis while preserving representative cloud structures for classification.

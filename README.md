# cloud-cover-classification-ai4eo
The classification of cloud 
## Project Overview
This project focuses on cloud cover classification using Sentinel-3 OLCI satellite imagery. The objective is to identify cloud-covered pixels by analysing spectral information from selected bands and applying a machine learning model.

The workflow includes data preprocessing, feature extraction, model training, and the generation of a cloud mask. The final output is a classification map distinguishing cloud and non-cloud regions.
## Motivation
Optical satellite imagery, such as data from the Sentinel-2 mission, plays a key role in Earth Observation (EO) by providing high-resolution information about the Earth's surface. These data are widely used in applications such as land cover mapping, vegetation monitoring, environmental assessment, and disaster management.

However, one of the main limitations of optical imagery is the presence of clouds. Clouds can partially or completely obscure the surface, leading to missing or unreliable information. As a result, many EO applications require an effective cloud detection step before further analysis can be performed.

Traditional approaches to cloud detection often rely on simple thresholding techniques based on spectral properties. While these methods are computationally efficient, they may struggle in complex scenarios, such as thin clouds or bright surfaces.

Recent advances in artificial intelligence, particularly machine learning and deep learning, have improved cloud detection performance. However, these methods often require large labelled datasets and significant computational resources.

This project is motivated by the need for a balanced approach: developing a method that is both effective and computationally efficient. By using spectral features and a classical machine learning model, this work aims to provide a practical solution that can be applied in real-world EO workflows with lower environmental cost.

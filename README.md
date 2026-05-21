# cloud-cover-classification-ai4eo

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

The study area is located around London, United Kingdom, and was selected using a geographic bounding box covering longitudes from **-0.35 to 0.15** and latitudes from **51.35 to 51.65**. This bounding box was used to query Sentinel-2 Level-2A imagery from the Copernicus Data Space Ecosystem.

The downloaded Sentinel-2 product corresponds to tile **T30UYC**, which intersects the selected London study area. Since Sentinel-2 products are distributed as full tiles, the downloaded image covers a larger spatial extent than the initial query region.

The selected scene contains extensive cloud coverage with varying cloud thickness and semi-transparent cloud structures. These characteristics make the scene suitable for testing unsupervised machine learning approaches for cloud classification.

The RGB image generated from Sentinel-2 bands B02 (Blue), B03 (Green), and B04 (Red) was used for visual interpretation and as input for both K-Means clustering and Gaussian Mixture Model (GMM) classification workflows.

<p align="center">
  <img src="location.jpeg" alt="Study Area Location" width="48%">
  <img src="satellite.jpeg" alt="Sentinel-2 RGB Image" width="48%">
</p>

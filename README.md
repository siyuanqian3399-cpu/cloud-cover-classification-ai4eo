# cloud-cover-classification-ai4eo

# Project Overview
This project focuses on cloud cover classification using Sentinel-2 satellite imagery. The objective is to identify cloud-covered pixels by analysing spectral information from selected bands and applying a machine learning model.

The workflow includes data preprocessing, feature extraction, model training, and the generation of a cloud mask. The final output is a classification map distinguishing cloud and non-cloud regions.

# Motivation
Optical satellite imagery, such as data from the Sentinel-2 mission, plays a key role in Earth Observation (EO) by providing high-resolution information about the Earth's surface. These data are widely used in applications such as land cover mapping, vegetation monitoring, environmental assessment, and disaster management.

However, one of the main limitations of optical imagery is the presence of clouds. Clouds can partially or completely obscure the surface, leading to missing or unreliable information. As a result, many EO applications require an effective cloud detection step before further analysis can be performed.

Traditional approaches to cloud detection often rely on simple thresholding techniques based on spectral properties. While these methods are computationally efficient, they may struggle in complex scenarios, such as thin clouds or bright surfaces.

Recent advances in artificial intelligence, particularly machine learning and deep learning, have improved cloud detection performance. However, these methods often require large labelled datasets and significant computational resources.

This project is motivated by the need for a balanced approach: developing a method that is both effective and computationally efficient. By using spectral features and a classical machine learning model, this work aims to provide a practical solution that can be applied in real-world EO workflows with lower environmental cost.

# Study Area

The study area is located around London, United Kingdom, and was selected using a geographic bounding box covering longitudes from **-0.35 to 0.15** and latitudes from **51.35 to 51.65**. This bounding box was used to query Sentinel-2 Level-2A imagery from the Copernicus Data Space Ecosystem.

The downloaded Sentinel-2 product corresponds to tile **T30UYC**, which intersects the selected London study area. Since Sentinel-2 products are distributed as full tiles, the downloaded image covers a larger spatial extent than the initial query region.

The selected scene contains extensive cloud coverage with varying cloud thickness and semi-transparent cloud structures. These characteristics make the scene suitable for testing unsupervised machine learning approaches for cloud classification.

The RGB image generated from Sentinel-2 bands B02 (Blue), B03 (Green), and B04 (Red) was used for visual interpretation and as input for both K-Means clustering and Gaussian Mixture Model (GMM) classification workflows.

<p align="center">
  <img src="location.jpeg" alt="Study Area Location" width="48%">
  <img src="satellate.jpeg" alt="Satellite" width="48%">
</p>
 
# Data

This project uses Sentinel-2 Level-2A optical satellite imagery obtained from the Copernicus Data Space Ecosystem. The selected product was acquired by Sentinel-2B on **30 June 2022** and corresponds to tile **T30UYC**.

Sentinel-2 Level-2A data were selected because they provide atmospherically corrected surface reflectance, which is suitable for image classification and spectral analysis.

The analysis uses three 10 m resolution optical bands:

| Band | Description | Resolution |
|------|-------------|------------|
| B02 | Blue | 10 m |
| B03 | Green | 10 m |
| B04 | Red | 10 m |

These bands were stacked to create a true-colour RGB image and were also used as input features for the unsupervised clustering methods.

The downloaded Sentinel-2 product was provided in `.SAFE` format. The relevant image files were located in the `IMG_DATA/R10m/` folder as `.jp2` files.

The original RGB image shows extensive cloud coverage across the scene, including dense bright cloud regions, semi-transparent cloud structures, and partially visible surface features beneath the cloud layer. These characteristics make the scene suitable for testing cloud classification methods using multispectral satellite imagery.

<p align="center">
  <img src="original.png" alt="Original Sentinel-2 RGB Image" width="70%">
</p>

# Methodology

## Method Overview

This project uses unsupervised machine learning methods to classify cloud-covered regions from Sentinel-2 RGB imagery. The overall workflow consists of reading Sentinel-2 optical bands, stacking the RGB bands into a feature matrix, applying clustering algorithms, and extracting the cloud-related cluster as a binary cloud mask.

Two unsupervised clustering methods were applied and compared:

1. **K-Means Clustering**
2. **Gaussian Mixture Model (GMM)**

Both methods used the same input features: Sentinel-2 bands **B02 (Blue)**, **B03 (Green)**, and **B04 (Red)**.

---

## K-Means Clustering

K-Means clustering is an unsupervised machine learning algorithm that groups pixels based on spectral similarity. In this project, each pixel was represented by its RGB reflectance values:

```text
Pixel = [Red, Green, Blue]
```

The algorithm divides the image pixels into a fixed number of clusters. Pixels with similar RGB values are assigned to the same cluster.

K-Means performs **hard clustering**, meaning each pixel can only belong to one cluster. This makes the method simple, fast, and easy to interpret. However, it can also produce sharp boundaries between clusters, which may be less suitable for gradual cloud transitions or thin cloud areas.

<p align="center">
  <img src="k.png" alt="K-Means Workflow" width="90%">
</p>

### K-Means Workflow Summary

| Step | Description |
|---|---|
| Data Input | Sentinel-2 Level-2A RGB bands |
| Preprocessing | Read and stack B02, B03, B04 |
| Feature Matrix | Convert image into RGB pixel vectors |
| Clustering | Apply K-Means clustering |
| Cloud Selection | Select brightest cluster |
| Output | Binary cloud mask |

---

## Gaussian Mixture Model (GMM)

Gaussian Mixture Model is also an unsupervised clustering method, but it uses a probabilistic approach. Instead of assigning pixels only by distance to a cluster centre, GMM models the pixel values as a mixture of Gaussian distributions.

Each pixel is assigned to the component with the highest probability. This allows GMM to capture more gradual transitions between different surface or cloud types.

Compared with K-Means, GMM is more flexible and can better represent semi-transparent clouds, cloud edges, and subtle spectral variations. However, it is also more computationally expensive.

<p align="center">
  <img src="gm.png" alt="GMM Workflow" width="90%">
</p>

### GMM Workflow Summary

| Step | Description |
|---|---|
| Data Input | Sentinel-2 Level-2A RGB bands |
| Preprocessing | Read and stack B02, B03, B04 |
| Feature Matrix | Convert image into RGB pixel vectors |
| Clustering | Apply Gaussian Mixture Model |
| Cloud Selection | Select highest reflectance component |
| Output | Binary cloud mask |

---

## Cloud Identification

Clouds generally appear bright in true-colour Sentinel-2 imagery because they have high reflectance in the visible bands. After clustering, the cluster corresponding to the brightest cloud-covered regions was selected as the cloud class.

The selected cloud cluster was then converted into a binary cloud mask:

```text
Cloud = 1
Non-cloud = 0
```

In the final cloud mask, white pixels represent cloud-covered regions, while black pixels represent non-cloud regions or background areas.

This cloud identification step was performed separately for both K-Means and GMM outputs, allowing the two methods to be compared visually and quantitatively.

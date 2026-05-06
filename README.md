# cloud-cover-classification-ai4eo
The classification of cloud 
## Project Overview
Clouds represent one of the most significant sources of uncertainty in optical satellite imagery. Because clouds block the view of the Earth's surface, they reduce the usability and reliability of Earth Observation (EO) data. This limitation affects a wide range of applications, including land cover classification, vegetation monitoring, climate analysis, and disaster response such as flood detection.

Accurate cloud detection is therefore a critical preprocessing step in satellite image analysis. Without effective cloud masking, downstream models may produce incorrect or misleading results. While recent advances in deep learning (e.g., convolutional neural networks) have achieved high performance in cloud detection tasks, these methods often require large labelled datasets and substantial computational resources.

In this project, we aim to develop a simple, interpretable, and computationally efficient approach for detecting cloud-covered pixels in Sentinel-2 imagery. By using spectral features derived from key bands (Blue, Green, Red, and Near Infrared) and applying a classical machine learning model such as Random Forest, we seek to provide a lightweight alternative to more complex approaches.

---
layout: page
title: UAVSAR Wildfire Monitoring
description: classification of polarmetric data to generate fire perimeters and burn severity
img: assets/img/uavsar/cover.png
importance: 2
category: research & analysis
---
### Abstract
Wildfires are an ongoing threat to communities due to climate change. They are characterized by their unpredictability and can lead to severe consequences if not handled appropriately. Remote sensing can significantly contribute to wildfire monitoring by providing image data over large areas of land. Uninhabited Aerial Vehicle Synthetic Aperture Radar (UAVSAR) is a type of active radar sensor well-suited for assessing forest structure due to its ability to penetrate the atmosphere under most conditions. We utilize the polarimetric data collected from UAVSAR’s L-band radar to detect burn scars and classify fire perimeters. The polarimetric data provides valuable insights into the land’s scattering properties, which exhibit remarkable sensitivity to forest fuel load, a key indicator for fire burn scars and vegetation burn severity. Using classification techniques, we automate the generation of fire perimeters and burn severity maps, reducing the manual efforts required. This product will enable real-time wildfire monitoring by providing timely updates to aid disaster response and serve as a protype for future research in wildfire classification using UAVSAR data.

#### To Access
__The project report can be assessed [here](https://github.com/wentama/uavsar_wildfire_classification/blob/main/JPL_sum23_report.pdf).__

__Published code can be found on JPL's GitHub [here](https://github.com/nasa-jpl/uavsar-wildfire).__

<div class="row">
    <div class="col-sm-5.5 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/uavsar/study_area.png" title="study area image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6.5 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/uavsar/fire_timeline.png" title="fire timeline image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 1. Left: General location of the three studied fire. Right. Timeline showing fire events and data collection dates.
</div>

### Sample Output
Below shows a sample output fire perimeter and burn severity of the 2020 La Tuna Fire. 

- __Radar (UAVSAR)__: The outputs under `previous` and `improved` are generated using UAVSAR's polarmetric data. Radar has the ability to penetrates clouds, smoke, and vegetation. As a result, radar is sensitive to surface structure and moisture, making it effective in detecting burn impacts, even in challenging conditions.
- __Optical (Landsat/Sentinel-2)__: The `baseline`, from [MTBS](https://www.mtbs.gov/), used Landsat and Sentinel-2 optical imagery. Optical sensors capture surface reflectance and vegetation health but are limited by clouds or smoke.
- __Differences__: The variation in burn severity between radar and optical data reflects their different methods of observation. Radar focuses on structural changes, while optical sensors highlight reflectance, leading to distinct assessments. However, their perimeter remain constant. 
  
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/uavsar/sample_output.png" title="study area image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 2. Left, output from the Summer 2023 version. Middle, output from the improved Fall 2023 version. Right, baseline comparison from MTBS.
</div>
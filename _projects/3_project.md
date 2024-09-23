---
layout: page
title: UAVSAR Wildfire Monitoring
description: classification of polarmetric data to generate fire perimeters and burn severity
img: assets/img/uavsar/cover.png
importance: 2
category: research
---
### Abstract
Wildfires are an ongoing threat to communities due to climate change. They are characterized by their unpredictability and can lead to severe consequences if not handled appropriately. Remote sensing can significantly contribute to wildfire monitoring by providing image data over large areas of land. Uninhabited Aerial Vehicle Synthetic Aperture Radar (UAVSAR) is a type of active radar sensor well-suited for assessing forest structure due to its ability to penetrate the atmosphere under most conditions. We utilize the polarimetric data collected from UAVSAR’s L-band radar to detect burn scars and classify fire perimeters. The polarimetric data provides valuable insights into the land’s scattering properties, which exhibit remarkable sensitivity to forest fuel load, a key indicator for fire burn scars and vegetation burn severity. Using classification techniques, we automate the generation of fire perimeters and burn severity maps, reducing the manual efforts required. This product will enable real-time wildfire monitoring by providing timely updates to aid disaster response and serve as a protype for future research in wildfire classification using UAVSAR data.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/uavsar/study_area.png" title="study area image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/uavsar/fire_timeline.png" title="fire timeline image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 1. Left: General location of the three studied fire. Right. Timeline showing fire events and data collection dates.
</div>
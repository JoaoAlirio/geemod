---
layout: default
title: Reference
body_class: left-align
---

# Scientific publication
<br>
(in development)  
<br>
<br>

# Resources used in geeMod
<br>

## GEE reference pages for each classification algorithm
<br>
<br>

|Classifier|reference page|
|---|---|
|Random Forest|<a href="https://developers.google.com/earth-engine/apidocs/ee-classifier-smilerandomforest" target="_blank">https://developers.google.com/earth-engine/apidocs/ee-classifier-smilerandomforest</a>|
|Gradient Tree Boost|<a href="https://developers.google.com/earth-engine/apidocs/ee-classifier-smilegradienttreeboost" target="_blank">https://developers.google.com/earth-engine/apidocs/ee-classifier-smilegradienttreeboost</a>|
|CART|<a href="https://developers.google.com/earth-engine/apidocs/ee-classifier-smilecart" target="_blank">https://developers.google.com/earth-engine/apidocs/ee-classifier-smilecart</a>|
|MaxEnt|<a href="https://developers.google.com/earth-engine/apidocs/ee-classifier-amnhmaxent" target="_blank">https://developers.google.com/earth-engine/apidocs/ee-classifier-amnhmaxent</a>|

<br>

## GEE products used in selectable predictor variables

|Group|Name|Description|Units|Scale factor|Pixel Size (m)|GEE Snippet|
|--|---|------|-|--|--|---|
|Climatic|bio01|Annual mean temperature|°C|0.1|927.67|WORLDCLIM/V1/BIO|
|Climatic|bio02|Mean diurnal range|°C|0.1|927.67|WORLDCLIM/V1/BIO|
|Climatic|bio03|Isothermality (bio02/bio07 * 100)|%| - |927.67|WORLDCLIM/V1/BIO|
|Climatic|bio04|Temperature seasonality|°C|0.01|927.67|WORLDCLIM/V1/BIO|
|Climatic|bio05|Max temperature of warmest month|°C|0.1|927.67|WORLDCLIM/V1/BIO|
|Climatic|bio06|Min temperature of coldest month|°C|0.1|927.67|WORLDCLIM/V1/BIO|
|Climatic|bio07|Temperature annual range (bio05-bio06)|°C|0.1|927.67|WORLDCLIM/V1/BIO|
|Climatic|bio08|Mean temperature of wettest quarter|°C|0.1|927.67|WORLDCLIM/V1/BIO|
|Climatic|bio09|Mean temperature of driest quarter|°C|0.1|927.67|WORLDCLIM/V1/BIO|
|Climatic|bio10|Mean temperature of warmest quarter|°C|0.1|927.67|WORLDCLIM/V1/BIO|
|Climatic|bio11|Mean temperature of coldest quarter|°C|0.1|927.67|WORLDCLIM/V1/BIO|
|Climatic|bio12|Annual precipitation|mm| - |927.67|WORLDCLIM/V1/BIO|
|Climatic|bio13|Precipitation of wettest month|mm| - |927.67|WORLDCLIM/V1/BIO|
|Climatic|bio14|Precipitation of driest month|mm| - |927.67|WORLDCLIM/V1/BIO|
|Climatic|bio15|Precipitation seasonality|coefficient| - |927.67|WORLDCLIM/V1/BIO|
|Climatic|bio16|Precipitation of wettest quarter|mm| - |927.67|WORLDCLIM/V1/BIO|
|Climatic|bio17|Precipitation of driest quarter|mm| - |927.67|WORLDCLIM/V1/BIO|
|Climatic|bio18|Precipitation of warmest quarter|mm| - |927.67|WORLDCLIM/V1/BIO|
|Climatic|bio19|Precipitation of coldest quarter|mm| - |927.67|WORLDCLIM/V1/BIO|
|Topographic|elevation|Elevation|m| - |30|USGS/SRTMGL1_003|
|Topographic|slope|Slope|m| - |30|USGS/SRTMGL1_003|
|Modis Index|NDVI|Normalized Difference Vegetation Index| - |0.0001|250|MODIS/061/MOD13Q1|
|Modis Index|EVI|Enhanced Vegetation Index| - |0.0001|250|MODIS/061/MOD13Q1|
|Modis Index|FPAR|Fraction of Photosynthetically Active Radiation|%|0.01|500|MODIS/061/MOD15A2H|
|Modis Index|LAI|Leaf Area Index|area fraction|0.1|500|MODIS/061/MOD15A2H|
|Modis Index|ET|Total evapotranspiration|kg/m^2/8day|0.1|500|MODIS/061/MOD16A2GF|



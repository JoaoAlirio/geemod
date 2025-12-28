---
layout: default
title: Methods
---

# Application general structure
geeMod is organized into modules that are combined according to the following general scheme:  
![geemod_general_structure ](https://github.com/user-attachments/assets/d2f9f508-735e-4570-8eba-f0e5277621fa)
Within each module there are some specific functions described in each of the following sections.
## general settings
parameters that are transversal to the process
### CRS - coordinate system
The coordinate system ...
### Pixel Size (m)
It must be specified in meters.
### Replications
The number of times the models will be run, with different subsets of occurrences.  
The different subsets for each replication are obtained by randomly separating presences and absences into training and test subsets, according to the defined percentage of test points.
### Test points (%)
percentage of occurrences that will be reserved for validation.
## Regions
Defining the study area involves selecting two regions, one for calibration and the other for projection.  
...  
...  
## Presences
coming soon ...
## Predictors
coming soon ...
## model settings
coming soon ...

## Run Models
coming soon ...

## Variables importance
coming soon ...
## Validation
coming soon ...
## Ensemble
coming soon ...

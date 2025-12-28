---
layout: default
title: Methods
body_class: left-align
---

# Application general structure
geeMod is organized into modules that are combined according to the following general scheme:  
![geemod_general_structure](https://github.com/user-attachments/assets/4ee934ab-a8f5-4d2e-8230-7c7f7c04ec35)
<br>

Within each module there are some specific functions described in each of the following section
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

---
layout: default
title: Methods
body_class: left-align
---

# Application general structure
geeMod is organized into modules that are combined according to the following general scheme:  

<br>
![geemod_general_structure](https://github.com/user-attachments/assets/a8f92a24-5037-48e0-b7aa-6dd1390591e7)

Within each module there are some specific functions described in each of the following section
## general settings
parameters that are transversal to the process
### CRS
The coordinate system ... dizer onde se aplica
### Pixel Size (m)
It must be specified in meters. ... dizer onde se aplica
### Replications
The number of times the models will be run, with different subsets of occurrences.  
The different subsets for each replication are obtained by randomly separating presences and absences into training and test subsets, according to the defined percentage of test points.
### Test points (%)
Percentage of occurrences that will be reserved for validation.  

## Regions
Defining the study area involves selecting two regions, one for calibration and the other for projection.  
...  
...  
## Presences
coming soon ... (explicar remover duplicados e pseudo-ausencias)  
## Predictors
coming soon ... (breve explicação, remeter para reference e script no code editor - modules)  
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

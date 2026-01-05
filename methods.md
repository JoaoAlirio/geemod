---
layout: default
title: Methods
body_class: left-align
---

# Application general structure
geeMod is organized into modules that are combined according to the following general scheme:  

![geemod_general_structure](https://github.com/user-attachments/assets/0a16d7b3-12d9-41da-82f9-25898f77f50a)

The user interface menu is also organized into modules.
The structure of the following sections follows the organization of the menu buttons and contains information about each module.
 

## general settings
parameters that are transversal to the process  

**CRS**  

The coordinate system must be written explicitly (e.g., "EPSG:4326", "EPSG:3035").
The various layers (e.g., regions, predictor variables) are reprojected onto this CRS using the reproject() function. This causes the outputs to also be generated within this CRS.  

**Pixel Size (m)**  

It must be specified in meters. It is also used in the reproject() function in conjunction with CRS. In addition, it impacts the cleanup of occurrences.
In the codeEditor version, it is necessary to retype the scale in the Tasks export panel.

**Replications**  

The number of times the models will be run, with different subsets of occurrences.  
The different subsets for each replication are obtained by randomly separating presences and absences into training and test subsets, according to the defined percentage of test points.  

**Test points (%)**  

Percentage of occurrences that will be reserved for validation.  
<br>

## Regions
Defining the **study area** involves selecting two regions, one for calibration and the other for projection. The same region can be used to define both areas if the goal is to train and project the models in the same geographic space. Occurrences will be restricted to the calibration region. Predictor variables will be limited separately to each region. There are four ways to define the two regions that are illustrated in the video tutorial (by file, by selecting countries, by selecting ecoregions, and by drawing polygons).  

## Presences
coming soon ... (, background maxent 10.000 random points ... dizer que user deve verificar se ocurrencias estão conforme esperado)  


There are two ways to prepare the occurrences.

**Load a file with presences and absences**  

- The file must have a property called "Presence", with 1 for presence and zero for absence.  

**Load a file with only presences and let geeMod generate pseudo-absences**  

- Pseudo-absences will be random points created within a subregion obtained by removing cells with presences from the calibration region.  
- The number of random points will be equal to the number of presences multiplied by the user-defined factor (decimal number between 1 and 2).  

**Notes:**  
- Presences will be filtered by the calibration region.  
- Duplicate occurrences will be removed, leaving only one presence per cell (according to the defined crs and scale).  
- The background used in MaxEnt is obtained from 10,000 random points generated in the calibration region, limited by the algorithm to the number of cells existing in that area.
- The user should verify that the presences and absences are as expected.

## Predictors
coming soon ... (There is a specific script for calculating the variables (modules/predictors.js) ... the user should verify that the predictor variables are as expected... see information about the resources used to calculate the variables in the "Reference" tab.)  

## model settings
The classifiers selected in the checkbox of each upper left panel will be executed (Random Forest, Gradient Tree Boosting, CART, and/or Maxent). If none are selected and the models are run, the results will be empty.  
There are some parameters for each classifier that the user can configure. The others parameters are kept at their default values. See the complete information on the GEE reference pages listed in the "Reference" tab.  

## Run Models
coming soon ...

## Variables importance
coming soon ...
## Validation
coming soon ...
## Ensemble
coming soon ...
## Load Project
coming soon ...
## Save Project
coming soon ...

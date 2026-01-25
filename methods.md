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
Defining the **study area** involves selecting two regions, one for **calibration** and the other for **projection**.  
- Occurrences will be restricted to the calibration region.
- The same region can be used to define both areas, in order to project the models onto the same geographical space.
- The predictor variables will be limited separately for both the calibration and projection regions.
- There are four ways to define the two regions (that are illustrated in the video tutorial):
    - by file
    - by selecting countries
    - by selecting ecoregions
    - by drawing polygons

<br>

## Presences

There are two ways to prepare the occurrences.

**Load a file with presences and absences**  

- The file must have a property called 'Presence', with 1 for presence and 0 for absence.  

**Load a file with only presences and let geeMod generate pseudo-absences**  

- Pseudo-absences will be random points created within a subregion obtained by removing cells with presences from the calibration region.  
- The number of random points will be equal to the number of presences multiplied by the user-defined factor (decimal number between 1 and 2).  

**Notes:**  
- Presences will be filtered by the calibration region.  
- Duplicate occurrences will be removed, leaving only one presence per cell (according to the defined crs and scale).  
- The background used in MaxEnt is obtained from 10,000 random points generated in the calibration region, limited by the algorithm to the number of cells existing in that area.
- There are some examples of dataset occurrences, with or without absences, that are available for selection.
- The user should verify that the presences and absences are as expected, by loading the various layers on the map and analysing the quantities in the table that appears in the results panel.

<br>

## Predictors

There are two modes to define predictor variables:
- **Select Variables mode** - The user selects from a list of 26 environmental layers (see table on "Reference" tab).  
- **Image Asset mode** - The user explicitly indicates two assets.

**Notes:**  
- Identical assets are required for calibration and projection within the same spatiotemporal domain.  
- Projections to a different domain require distinct assets with identical band names and comparable units.
- There is an option for users to calculate the Spearman correlation between variables.
- The user should verify that the predictor variables are as expected, viewing the predictors on the map.
- There is an external script for calculating the variables (geemod/modules/predictors.js), which is called by the main script.

<br>

## model settings
The classifiers selected in the checkbox of each upper left panel will be executed (Random Forest, Gradient Tree Boosting, CART, and/or Maxent). If none are selected and the models are run, the results will be empty.  
There are some parameters for each classifier that the user can configure. The others parameters are kept at their default values. See the complete information on the GEE reference pages listed in the "Reference" tab.  

<br>

## Run Models
coming soon ...

<br>

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

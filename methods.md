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
- There are some examples of occurrence datasets available for selection, with or without absences.
- The background used in MaxEnt is obtained from 10,000 random points generated in the calibration region, limited by the algorithm to the number of cells existing in that area
- The user can verify if the presences and absences are as expected by loading the different layers on the map and analyzing the numerical results presented.

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
- The classifiers selected in the checkbox of each upper left panel will be executed: (Random Forest, Gradient Tree Boosting, CART, and/or MaxEnt).
- If none are selected and the models are run, the results will be empty.
- In RF, GTB, and CART, the output mode has been set to probabilistic, and the result band has been renamed to "probability." MaxEnt already follows this format.
- There are some parameters for each classifier that the user can configure. The others parameters are kept at their default values. See the complete information on the GEE reference pages listed in the "Reference" tab.  

<br>

## Run Models
- The execution of the models is replicated the number of times defined by the user.
- For each replication, the sets of occurrences are randomly separated into training and test subsets, according to the defined percentage (seeds vary, so partitions are distinct across replications).
- The chosen models run separately, and the results appear as they are completed.
- The implementation of the code is divided into three blocks:
    - The first block contains the generic modelling functions (one function for MaxEnt and another for the other three classifiers), which apply the settings and various inputs to train (calibrate) the classifiers. After training, for the replication performed, the function returns a trained classifier object and a dictionary with the Importance of Predictors;
    - The second block prepares the inputs and calls the generic modelling function of each classifier, for each replication, passing them the respective input data;
    - The third block extracts and prepares the results for presentation in the user interface.
- geeMod provides the mean prediction and standard deviation maps for each classifier. The mean map represents the averaged suitability across replications and can be used for further evaluation and ensemble modelling.

<br>

## Variables importance

- geeMod extracts raw importance scores per replication per classifier and converts them to normalised percentages.
- We caution users about direct comparisons across different definitions of importance from each algorithm and encourage interpretation in terms of relative contributions and ecological plausibility rather than absolute values.

<br>

## Validation

- The evaluation of the selected models is performed separately, and the results of each model appear as they are completed.
- Users can set the number of steps (thresholds) they wish to use. The usual range is between 20 and 25. A lower value can be set for a faster response, but this reduces the accuracy of identifying correctly classified test occurrences between the different thresholds. A higher value increases accuracy but may take longer or fail.
- The implementation of the code is divided into two blocks. The first block has four functions, one for each classifier, which manage the validation process for the respective classifier.
    - Each of these functions begins by obtaining the trained classifier object and the set of presences and absences reserved for testing for each replication.
    - It then applies the trained classifier to the image of the calibration predictor variables and obtains the model's result maps in the calibration region.
    - With these results and test occurrences, it calls the specific functions to calculate each evaluation partial.
    - Finally, it receives the evaluation results for each replication and calculates their average to obtain the final metrics for that model.
- The second block has four specific functions:
    - The getThreshMetrics() function counts the correctly classified test occurrences for each threshold (TR - True Positives and TN - True Negatives), and then calculates some rates to complete the table with all partial results:
        - True Positive Rate (Sensitivity) -> (TPR = TP / 'Presence Test Size')
        - True Negative Rate (Specificity) -> [TNR = TN / 'Absence Test Size']
        - False Positive Rate -> FPR = 1 - TNR
        - True Skill Statistic -> (TSS = Sensitivity + Specificity - 1)
    - The getAUCROC() function uses the trapezoidal approximation to compute the Area Under the Curve (AUC) of the Receiver Operating Characteristic (ROC), that represents the true positive rate (Sensitivity) in relation to the false positive rate (1-Specificity) at all possible classification thresholds;
    - The evalReps() function only manages the process throughout the replications;
    - The tssAucReps() function obtains the final TSS and AUC from the results of the previous functions.

<br>

## Ensemble
coming soon ...
## Load Project
coming soon ...
## Save Project
coming soon ...

RainSlope
================
Model to calculate coupled rainfall-infiltration-runoff patterns on a sloped terrain. Based on 2017 and 2018 paper which can be found in the 'publications' directory. Citations are as follows:

**Johnson and Loaiciga 2017:** *Johnson, J.M., Loaiciga, H.A. (2017)	Coupled Infiltration and Kinematic-Wave Runoff Simulation in Slopes: Implications for Slope Stability. Water, 9, 327.*

**Loaiciga and Johnson 2018:** *Loaiciga, H.A., Johnson, J.M. (2018). Infiltration on sloping terrain and its role on runoff generation and slope stability. Journal of Hydrology (in press).*

## Input Requirements
The model requires user-input regarding the:
 1) **Hill shape**: Vertical and horizontal length and depth
 2) **Soil**: Roughness, conductivity, soil water tension, porosity, and volumetric content
 3) **Rainfall**: For this the user has three option:
    1. Constant: Rainfall rate derived from total depth, time and time step
    2. Triangular: Rainfall rate derived from total depth, time and time step
    3. Input file: Given as a .csv or .xlsx describing rainfall depth at a given time increment
    4. A distance step and time step for the model to run on
    
## Installation

To install the  package, you must install from GitHub using the `devtools` packages:

```r
library(devtools)
install_github("mikejohnson51/RainSlope")
```

## Model Workflow

1) Parameterize your scenario with the **param()** function. If this is your first time creating a scenario file fill out all pertainent information and click 'submit'. If errors are encountered reference the functions help file using ?param. *To facilitate sesitivity testing, or multiple scenarios, old scenarios can be modified by entering the files name in the 'Use previous run' heading, clicking 'Use Old Run', modifing as you wish, and clicking submit.*

```r
scene1 = param()
```
<p align="center">
<img src= "https://github.com/mikejohnson51/Rainfall_Infiltration_hillslope/blob/master/imgs/param_ex.png" width="300">
</p>

2) Execute the model using your scenario file as input using the **exe()** function

```r
mod_1 = exe(scene1)
```
<p align="center">
<img src= "https://github.com/mikejohnson51/Rainfall_Infiltration_hillslope/blob/master/imgs/model_run.png" width="400">
</p>

3) Process your results for defined time slices by generating graphs and/or writing excel workbooks using the **process()** function. In the following example an excel workbook and plots will be generated for hours 5, 10, 15, 20 and 24 hours. 

```
output = process(mod_1, hrs = c(5,10,15,20,24), plots= TRUE, excel = TRUE)
```

![USCB](https://upload.wikimedia.org/wikipedia/commons/archive/9/9f/20130715012958%21UCSB_logo.png)

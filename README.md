# Energy A.I. Hackathon 2022

## Hosts: [Prof. Michael Pyrcz](https://twitter.com/GeostatsGuy) and [Prof. John Foster](https://twitter.com/johntfoster)

### Architects: [Wen Pan](https://www.linkedin.com/in/wen-pan/) and [Elnara Rustamzade](https://www.linkedin.com/in/elnara-rustamzade-779396162/)

### Sponsor: [Prof. Jon Olson](https://twitter.com/ProfJEOlson), and the [Hildebrand Department of Petroleum and Geosystems Engineering](https://twitter.com/UT_PGE)

### Organization and Student Engagement: Gabby Banales, Sara Hernando and Tracey Wilson

___

### Energy A.I. Problem Description 

**Goal**: Develop a data analytics and machine learning workflow in Python to:

1. select the best **3 infill well locations and associated completion intervals (upper or lower)** that maximize the cumulative oil production over the next 2 years
2. predict the **cumulative oil production over the next 2 years for each of your proposed wells**
 
#### Background

We challenge the Energy A.I. hackathon teams of The University of Texas at Austin, engineering and science students to build a data-driven model to predict oil production. This will require:

* data analysis and evaluation of multiple data sources and a variety of features
* spatial data analytics for spatial predictions and feature imputation
* integration of domain expertise at every step
* selection, training and tuning robust machine learning prediction models  

This data-driven approach will replace the conventional engineering and geoscience approach:

* characterizing and modeling the subsurface
* physics-based fluid flow simulations

___
 
#### The Reservoir Unit

Specifications of the reservoir unit of interest: 

* **Depositional Setting**: turbidite channel system with two vertically stacked flow units (upper and lower). 
* **Structure**: both upper and lower units are disected by fault that crosses the reservoir (see location and equation on the image below). 

<img width="408" alt="image" src="https://user-images.githubusercontent.com/95392867/159757439-0edc215e-4bb3-4cc0-a2a3-4250dde3545a.png">

* **Wells**: 50 approximately vertical wells (you can assume vertical) were drilled across the reservoir and completed throughout upper or lower completion intervals. The reservoir has been produced since 2012. Due to the drilling sequence and field management issues, 50 wells produced oil for different time periods from 2012 until present. Given the increasing oil price, the company has decided to add 3 infill wells in the reservoir to explore sweet spots that have been left over during previous development stage in order to increase the production over the next 2 years.


* **Question**: What will be the best locations for the 3 infill wells that will result in the highest additional oil production in the next 2-years?  

___

### Available Data Files Inventory

You have the following data is available.

#### Well Logs

The folder named **Well_Log** contains the well log data along the wellbore for all 50 wells.

* **WPx.csv** - well logs for the previous production wells. Note, x denotes the well index from 0 - 49.

The features include:

* **MD** - measured depth, measured in feet along the vertical wells downward from the Kelly bushing elevation
* **PORO** - porosity, as a fraction measure only at core locations
* **Permeability (mD)** - permeability in mD measure only at core locations
* **RHOB** - density from well log in g/cm^3. Note, formation water has a density of 1 g/cm^3.
* **NPHI** - porosity from well log in fraction.
* **Other Petrophysical Well Logs** - DT (sonic compressional wave delay time in us/ft), DTS (sonic shear wave delay time in us/ft), PEF (Photoelectic effect in B/E), RD (Deep resistivity from lateral log in OHMM) and RS (Shallow resistivity from lateral log in OHMM)
* **Other Geomechanical Well Data** - ROP (rate of penetration during drilling), DENC (density correction log in g/cm3)
* **Zone** - upper of lower zone of the reservoir

Well head data include: 
* **Well_Head_and_Completion.csv** - contains well locations, datum elevations and associated completion intervals.

Comments: 

* all the well names are masked (replaced with simple indices from 0 to 49) and coordinates are transformed to the area of interest to conceal the actual reservoir. 
* available petrophysical and geomechanical properties are listed. 
* -999 in the file indicate missing data at those locations.

#### Map Data - 2D seismic maps

The following map data is available:

* **AI.csv** - 2D acoustic impedance maps are interpreted from the seismic survey conducted in 2012-01-01 and 2021-12-20 for both interval to help identify potential sweep spots.

Comments:

* values indicate the vertically averaged property as the vertical resolution of the seismic is the entire reservoir unit (upper or lower)
* the first two columns are the coordinates and the remainder of the columns is AI values at given coordinates for lower and upper units in 2012 and 2022.

#### Production History
The bottom hole flowing pressure is set to 250 Bar in each well during their production history.
The following production history is available:

* **Production_History_Field.csv** - contains the daily oil productions for the 50 previous production wells within 10 years (2012-2022).

___

### Required Hackathon Submissions

By March 27th at noon each team must submit:

* **Solution Table** - a .csv file with your predictions for the **locations of 3 wells, associated completion intervals, and their associated 2 year cumulative production prediction** using the template given in [Sample_Submission.csv](Sample_Submission.csv) in this directory.

    * the file must be named 'solution.csv' with final values in a commit and then pushed to Github (folder [scoring/submission](https://github.com/PGEHackathon/data/tree/master/scoring/submission)) for the automated scoring.

* **Python Workflow and Associated Files** - committed to this repository with the workflow as a Jupyter Notebook .ipynb file along with all data files required to reproduce your team's solutions. The submitted workflow Jupyter Notebook should follow the format of the provided template [Hackathon_ProjectTemplate](https://github.com/PGEHackathon/resources/blob/main/Hackathon_ProjectTemplate.ipynb) for enhanced workflow communication and code readibility.

    * the file must be named 'xxxx.ipynb' and pushed to GitHub (folder [scoring/workflow](scoring/workflow)  for review and scoring (for code readability) by the hackathon architects, , where **xxxx** is your team name.

* **Presentation** - a PowerPoint slide deck .PPTX file for your team's final presentation to our judges. The submitted presentation should follow the format of the provided example presentation [Hackathon_PresentationTemplate](https://github.com/PGEHackathon/resources/blob/master/Hackathon_PresentationTemplate.pptx).

    * the file must be named 'xxxx.pdf' and pushed to GitHub (folder [scoring/presentation](scoring/presentation) for review by the judges, where **xxxx** is your team name.

The Workflow, Presentation submission templates and the results submission template are in the [PGEHackathon/resources](https://github.com/PGEHackathon/resources).

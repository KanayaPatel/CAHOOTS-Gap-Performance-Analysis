# CAHOOTS Gap Analysis
Project completed in Rori Rolfs' DSCI410L (Data Science in Action) Course @ University of Oregon, 2026

## Overview

After CAHOOTS was defunded in April 2025, the city of Eugene lost one of its organizations 
who would assist in a majority of welfare check calls. Most, if not all welfare check calls 
are now in the hands of the EPD. Given this, prior members of CAHOOTS asked us to take a 
look into the gaps the defunding caused. Specifically for this project:

- How have welfare checks been handled (by EPD? MCSLC?)?
- Has welfare check call volume changed?
- Has there been a change in the number of arrests during these welfare check calls?

## Project Structure
```
DSiA/
└── data/
│   ├── 2015-2025 SPD Calls for Service.xlsx
│   ├── 2015-2025 SPD Responding Units.xlsx
│   ├── 2015-2025 SPD Calls with Close Codes.xlsx
│   ├── EugeneCAD2015noloc.csv
│   ├── EugeneCAD2016noloc.csv
│   ├── EugeneCAD2017noloc.csv
│   ├── EugeneCAD2018noloc.csv
│   ├── EugeneCAD2019noloc.csv
│   ├── EugeneCAD2020noloc.csv
│   ├── EugeneCAD2021noloc.csv
│   ├── EugeneCAD2022noloc.csv
│   ├── EugeneCAD2023noloc.csv
│   ├── EugeneCAD2024noloc.csv
│   ├── EugeneCAD2025noloc.csv
│   └── MCSLC.xlsx
├── clean_data.ipynb
├── volume_analysis.ipynb
├── outcome_analysis.ipynb
├── cleaned_eug.csv                         !- This file is re-generated when running files -!
├── cleaned_spd.csv                         !- This file is re-generated when running files -!
├── diff_in_diff_volume.png                 !- This file is re-generated when running files -!
├── diff_in_diff_outcome.png                !- This file is re-generated when running files -!
└── requirements.txt
```
> Note: The cleaned .csv files are intentionally located in the root directory, not in data/.

## Setup and Installation

Ensure that Python 3.13 is installed on your device. Then, open a PowerShell terminal and navigate to the DSiA directory. Run the following command to install all required packages: ```pip install -r "requirements.txt"```

As an additional requirement, make sure to have Jupyter Notebook installed on your device (all of the actual files are notebooks!). 
Here is a tutorial to install Jupyter Notebook: [INSTALL JUPYTER](https://jupyter.org/install)

## How to Run
Before running any files, ensure you have read and completed all steps in the [Setup and Installation](#setup-and-installation) section.

### 1. `clean_data.ipynb`
Cleans the raw data and produces three output files in the root directory:
- `cleaned_eug.csv` — Eugene CAD data including CAHOOTS calls
- `cleaned_spd.csv` — Springfield call data + outcome data

### 2. `volume_analysis.ipynb`
Produces `diff_in_diff_volume.png`, a difference-in-differences plot showing how the volume of welfare check calls changed after CAHOOTS was defunded. Springfield is used as a control, as they still have their version of CAHOOTS.

> Note: This file uses both of the cleaned files above. Run ```clean_data.ipynb``` first.

### 3. `outcome_analysis.ipynb`
Produces `diff_in_diff_volume.png`, showing how the number of arrests made during welfare checks changed after CAHOOTS was disbanded in both cities. Springfield is used as a control, as they still have their version of CAHOOTS.


> Note: This file uses both cleaned files above. Run ```clean_data.ipynb``` first.

---
This project is complete as of June 2nd, 2026 (6/2/26). Below are key findings. 
- After CAHOOTS was defunded, there was a statstically significant drop in the weekly volume of welfare check calls. Through difference-in-differences, the counterfactual says there should be substantially more. 
- After CAHOOTS was defunded, there was a statistically significant rise in the volume of welfare check calls that end in an arrest being made by the responding unit (in this case, EPD). Through difference-in-differences, the counterfactual says there should be less arrests coming from welfare check calls.
- Through both analyses, Springfields numbers remained relatively the same before and after. 

> Note: Each difference-in-differences passed the parallel trends test visually ONLY. Therefore, no causal inferences can be made.
---
For purposes of replication, each file that was used is included in this repository as well as a report written to show the entire process of this research. 
---
Questions? Feel free to email me at kanaya.patel97402@gmail.com

# capstone_prescribed_burn
Yale EDS: Capstone project on prescribed burns and their effect on longleaf pines
*Capstone project for the Yale Environmental Data Science Certificate
* Author: Katie Safford
Last Updated: November 19, 2026

##Project Description
Fire is a natural occurrence in southern pine forests, including the Francis Marion National Forest. However, due to roads, streams, and fire suppression, they no longer occur without human support. Over time, foresters have recognized the importance of fire in balancing a forest's understory and overstory. Under the 2016 Land Management Plan, fire-adapted longleaf pine ecosystems require a 2-to-3-year fire return interval to suppress competing hardwood/sweetgum shrubs and stimulate native grasses (like wiregrass) and longleaf seedlings. This project uses U.S. Forest Service data to compare forest growth in the Francis Marion National Forest with regular intervals of prescribed burns. 

##Research Question
"Are the Francis Marion National Forest’s prescribed burn intervals achieving desired ecological outcomes—specifically promoting longleaf pine regeneration, reducing midstory woody encroachment, and lowering hazardous fuel loads?"

##Data
- Actv_HazFuelTrt_PL: FACTS Hazardous Fuel Treatments: Polygons of completed controlled burns (Activity_Code for Broadcast Burn / Underburn), Date_Completed, and Acres filtered to Francis Marion.
- Forest Inventory and Analysis Database: Filtered for SC (SC_PLOT, SC_TREE, SC_SEEDLING). Measures tree species, diameter, height, and seedling counts across SC. Analysis will begin in the year 2005.

## Repository Structure
stream_temp_project/
├── README.md ← you are here
├── raw_data/ ← original data, never edited
│   ├── ACTV_HazFuel_Trt_PL folder ←polygons for burn areas
│   └── SC_PLOT.csv
│   └── SC_COND.csv
│   └── SC_TREE.csv
│   └── SC_SEED.csv
├── clean_data/ ← output of 1_data_cleaning_capstone.ipynb
│   └── clean_sc_longleaf.csv
├── figures/ ← plots and tables (coming in later scripts)
└── scripts/ ← notebooks, numbered in the order they run
    ├──  0_project_setup_Capstone.ipynb
    └── 1_data_cleaning_capstone.ipynb

## How to run the code
All scripts are Google Colab notebooks written in R. Run them in numerical order:
1. `scripts/0_project_setup_Capstone.ipynb` creates the project folder and subfolders in
Google Drive.
2. `scripts/1_data_cleanning_capstone.ipynb` reads SC raw files, reshapes and joins them, and
writes `clean_data/clean_sc_longleaf.csv`.
3. `scripts/2_analysis.ipynb` *(coming soon)* will compare longleaf growth to fire intervals and save figures to `figures/`.
Each notebook mounts Google Drive with one Python cell (`drive.mount()`), then
switches to the R runtime. See the notes at the top of each notebook.

##Data Cleaning Steps (1_data_cleaning_capstone.ipynb)
Filtered data: 
  -Filtered to look at Berkley and Charleston Counties where the Francis Marion is located
  -Filtered to look at longleaf pine stands and only longleaf pine trees and seedlings
  -Filtered to look at 2005 and later to account for the FACTS Dataset beginning in 2005
Joined datasets to create one clean longleaf dataset for Charleston and Berkley counties. 
  -Used inner_join to only include plots that are national forests and longleaf stands. 
  -Used left join to add tree and seedling columns from clean_sc_tree and clean_sc_seedlings

  ##Known data issues
  I don't yet know how to use the polygon FACTS data, so I'll need to complete additional cleaning and joining. 

  ##Status and Next Steps
  [x] Set up the project folder and GitHub repository
- [1/2] Clean and combine the raw data (Half finished)
      -Identify plots with regular burn intervals
- [ ] Exploratory plots: tree growth over time, avg tree diameter per plot, avg seedlings per plot.
- [ ] Compare plots with regular burn intervals to those without: vg tree diameter and regular burn intervals
  
##AI Disclosure
I used Google Gemini to identify potential datasets. I also used Gemini to troubleshoot why my initial cleaned dataset was full of NAs, which led me to use an inner_join rather than a left_join. 

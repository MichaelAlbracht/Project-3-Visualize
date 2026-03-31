
Project 3 – Visualize
CIVE 202 – Engineering Problem-Solving with Computers
README / User Guide
Author: Michael Albracht  |  Client: Federal Highway Administration (FHWA)  |

1. Project Summary
This repository contains all code, data, and documentation for Project 3 of CIVE 202. The project was completed on behalf of the Federal Highway Administration (FHWA) to organize and visualize two national transportation datasets prior to a transportation planning group meeting.

Two datasets are analyzed:
•	National Household Travel Survey (NHTS) — Vehicle-level records capturing household vehicle type and household composition across the United States. 
•	Next Generation Simulation (NGSIM) — High-frequency time-step records of leader-follower vehicle pairs on U.S. highway segments. 
2. Repository Contents

├── Project3_Visualize.ipynb         Main Jupyter Notebook (all code)
├── NHTS(in).csv                     National Household Travel Survey data
├── NGSIM(in).csv                    Next Generation Simulation data
├── Project3_Technical_Report.docx   Formal technical report
├── Project3_ACD.xlsx                Annotated Code Document
├── Project3_SOW.docx                Scope of Work
└── README.docx                      This file
3. Requirements
The following Python libraries are required to run the notebook. All are available via pip:

pip install pandas numpy matplotlib seaborn

Library	Purpose
pandas	Loading and manipulating CSV data
numpy	Array creation and simulation math
matplotlib	Base plotting library for all figures
seaborn	Statistical plot styling, boxplot, and countplot

Python version: 3.8 or higher recommended.
4. User Guide
Follow these steps in order to run the notebook and reproduce all outputs.
Step 1 — Download the Repository
Download this repository so that all files are in the same folder on your machine.

 Step 2 — Confirm Data Files Are Present
Verify that both CSV files are in the same directory as the notebook:
•	NHTS(in).csv
•	NGSIM(in).csv

Important: The notebook uses relative paths (e.g., pd.read_csv('NHTS(in).csv')), so both files must be in the same folder as the .ipynb file or the data loading cells will raise a FileNotFoundError.
Step 3 — Open the Notebook
Launch Jupyter Notebook or JupyterLab from the project directory:

jupyter notebook Project3_Visualize.ipynb
Step 4 — Run All Cells in Order
The notebook is organized into four sequential sections. Run cells from top to bottom — do not skip sections, as later sections depend on variables defined earlier.

Section	Description
Section 1 – Setup & Data Loading	Imports libraries, loads NHTS and NGSIM CSVs, prints shape and column info, and runs descriptive statistics
Section 2 – NHTS Visualizations	Produces Plot 1 (grouped bar chart), Plot 2 (histogram), and Plot 3 (seaborn boxplot)
Section 3 – NGSIM Time-Series	Selects trajectory #5, produces Plot 4 (leader position & follower speed dual-axis) and Plot 5 (acceleration vs. time)
Section 4 – IDM Simulation	Defines and tests the IDM function, runs the Euler simulation loop, produces Plot 6 (IDM acceleration comparison) and Plot 7 (position comparison bonus)


Step 5 — Review Outputs
Each plot is displayed inline in the notebook. Review the plots to understand and make conclusions about the data. These plots are what is referenced in the analysis of the report.
5. Variables Used
NHTS Dataset
Variable	Column Name	Used In
Vehicle Type	vehicle_type	Bar chart, Boxplot
Household Size	household_size	Bar chart, Histogram, Boxplot

NGSIM Dataset (Trajectory #5)
Variable	Column Name	Used In
Time	Time	All NGSIM plots
Leader Position	leader_position(m)	Time-Series 1, IDM simulation
Follower Speed	follower_speed(m/s)	Time-Series 1
Leader Acceleration	leader_acc(m/s^2)	Time-Series 2, IDM plot
Follower Acceleration	follower_acc(m/s^2)	Time-Series 2, IDM plot
Trajectory Number	trajectory_number	Filter for trajectory #5
6. IDM Parameters
The Intelligent Driver Model simulation uses the following default parameters:

Parameter	Symbol	Value
Desired velocity	v₀	30 m/s
Minimum spacing	s₀	2 m
Desired time headway	T	1.5 s
Maximum acceleration	a	1.0 m/s²
Comfortable deceleration	b	1.5 m/s²
Acceleration exponent	δ	4

To experiment with different driving behaviors, modify these values in Section 4 of the notebook before re-running the simulation cells.
7. References
Federal Highway Administration. (2022). National Household Travel Survey (NHTS). https://nhts.ornl.gov/
Treiber, M., Hennecke, A., & Helbing, D. (2000). Congested traffic states in empirical observations and microscopic simulations. Physical Review E, 62(2), 1805–1824.
Treiber, M., & Kesting, A. (2013). Traffic Flow Dynamics: Data, Models, and Simulation. Springer.

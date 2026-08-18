ST2195 Coursework – Programming for Data Science
Part 1 & Part 2 Implementation (Python + R)

Author: Jaimurugaesan Ramesh Babu
Student ID: 240635200
Course: ST2195 – Programming for Data Science

This repository contains the full reproducible code used to complete the ST2195 coursework project. The project combines Markov Chain Monte Carlo simulation and large-scale flight data analysis using both Python and R.

The goal of this repository is to allow another user to fully reproduce all analyses and results presented in the final report.

Project Overview

The coursework consists of two independent parts:

Part 1 — Metropolis-Hastings (MCMC Simulation)

We implement the Random Walk Metropolis algorithm to simulate samples from the Laplace distribution:

$$f(x) = \frac{1}{2}e^{-|x|}$$

Tasks performed:

Generate 10,000 samples using Metropolis-Hastings
Estimate distribution via:
Histogram
Kernel density estimate
Compute Monte-Carlo estimates:
Sample mean
Sample standard deviation
Evaluate convergence using R̂ diagnostic
Study convergence behaviour across multiple proposal variances
Part 2 — US Flight Data Analysis (2004–2008)

We analyse US domestic flight data from the ASA Data Expo to answer three real-world questions:

What are the best times and days to minimise delays?
Do older aircraft experience more delays?
Can flight diversions be predicted before departure?

All analyses were implemented in both Python and R to cross-validate results.

Data Source

Flight data obtained from Harvard Dataverse:

https://doi.org/10.7910/DVN/HG7NV7

Dataset includes:

Flight records (2004–2008)
Aircraft registry (plane-data.csv)
Carrier information (carriers.csv)
Airport coordinates (airports.csv)

This dataset contains millions of flight records, so preprocessing and sampling steps are included in the scripts.

Repository Structure
├── Part_1/
│   ├── part_1_ipynb.ipynb      # Python implementation of MCMC
│   ├── part_1_ipynb.html       # HTML export of the Python notebook
│   ├── part_1_rmd.Rmd          # R implementation of MCMC
│   ├── part_1_rmd.html         # HTML export of the RMarkdown file
│   └── ST2195_Part1_Report.docx # Report for Part 1
│
├── Part_2/
│   ├── part_2_ipynb.ipynb      # Python flight analysis
│   ├── part_2_ipynb.html       # HTML export of the Python notebook
│   ├── part_2_rmd.Rmd          # R flight analysis
│   ├── part_2_rmd.html         # HTML export of the RMarkdown file
│   ├── ST2195_Part2_Report.docx # Report for Part 2
│   └── data/
│       ├── 2004.csv – 2008.csv
│       ├── plane-data.csv
│       ├── carriers.csv
│       ├── airports.csv
│       └── shapefiles/         # Shapefiles for geospatial analysis
│
└── README.md                   # This file

How to Reproduce the Project

Python Setup
Install required packages:
pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter geopandas

Run notebooks:

jupyter notebook

Open and run:

part_1_ipynb.ipynb
part_2_ipynb.ipynb

R Setup
Install required libraries:

install.packages(c(
  "tidyverse", "ggplot2", "glmnet", "pROC", "lubridate",
  "data.table", "readr", "patchwork", "scales", "RColorBrewer",
  "Matrix", "sf"
))

Run RMarkdown files:

rmarkdown::render("part_1_rmd.Rmd")
rmarkdown::render("part_2_rmd.Rmd")
Key Methodology Summary
Data Cleaning
Cancelled flights removed from delay analysis
Missing aircraft manufacturing years imputed with median
Flights grouped by:
Day of week
Departure hour
Aircraft age bands
Modelling

Diversion prediction used Logistic Regression with:

Numeric features

Departure hour
Arrival hour
Distance
Month
Coordinates
Aircraft age

Categorical features

Carrier
Origin state
Destination state

Class imbalance handled using:

Downsampling
Balanced class weights
Ridge regularization

Training data: 2004–2007
Test data: 2008

Key Findings
Best Time to Fly
Lowest delays: Tuesday & Wednesday ~06:00 departures
Worst delays: Thursday & Friday evenings (18:00–21:00)
Aircraft Age vs Delays
Correlation ≈ 0.01–0.02
Aircraft age has no meaningful impact on delays.
Diversion Prediction
Logistic regression AUC ≈ 0.65
Strongest predictor: Flight distance
Weather data likely required for major improvement.

Python and R produced consistent conclusions, validating the analysis.

Reproducibility Notes
Random seeds are set where applicable.
Large dataset handled via sampling for modelling.
Running the full pipeline may require significant RAM.
Technologies Used
Python (Pandas, Scikit-learn, Matplotlib)
R (tidyverse, glmnet, pROC)
Jupyter Notebook
RMarkdown
Submission Contents

This repository includes:

Final report (PDF)
Python notebooks
RMarkdown scripts
README (replication guide)

All materials required to reproduce the coursework results are provided.


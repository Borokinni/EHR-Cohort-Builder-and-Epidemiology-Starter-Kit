# EHR-Cohort-Builder-and-Epidemiology-Starter-Kit

This repository demonstrates a reproducible workflow for EHR style analytics using a synthetic OMOP like data model. It is designed to show how I build analysis ready cohorts, derive covariates, run regression models, and produce publication ready tables and figures.

The data in this repository is fully synthetic and contains no patient information.

## What this project shows

1. Reproducible Python code for data wrangling, analysis, and visualisation
2. OMOP like table structure and cohort construction with an index date
3. Baseline covariates derived from a lookback period
4. Data quality checks and cohort flow counts
5. Statistical analysis with regression and interpretable outputs
6. Figure generation suitable for manuscripts and presentations

## Study question

Among adults with a baseline lookback period, is medication exposure associated with a clinical outcome during follow up, after adjusting for confounders?

This is a standard retrospective cohort pattern used in EHR epidemiology.

## Data model

The synthetic dataset mirrors common OMOP style tables

1. person
2. visit_occurrence
3. condition_occurrence
4. drug_exposure
5. measurement

## Cohort definition

1. Adults age 18 and above at index date
2. Index date is the first qualifying drug exposure date
3. Baseline lookback period is 180 days before index date
4. Follow up window is 180 days after index date
5. Outcome is a condition occurring after index date within follow up

## How to run

### Step 1 Create a virtual environment and install dependencies

pip install -r requirements.txt

### Step 2 Run the full pipeline

python -m src.run_pipeline

## Outputs

After running, you will get

1. Cohort flow table in outputs tables
2. Baseline table in outputs tables
3. Model results table in outputs tables
4. Figures in outputs figures
   - cohort flow bar chart
   - baseline covariate balance style plot
   - effect estimate plot

## Notes on reproducibility

The pipeline is deterministic by default because it uses a fixed random seed. All transformations are implemented in src modules and can be reviewed and rerun.

## Next extensions

1. Propensity score matching or weighting
2. Survival analysis with time to event outcomes
3. Multiple outcomes and sensitivity analyses

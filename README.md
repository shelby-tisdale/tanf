# tanf

This repository contains all code and data for my senior honors thesis project at Duke University, "The Diminishing Cash Safety Net: Predicting Fulfillment of TANF Goals from Unobligated Funds with Bayesian Hierarchical Modeling. This is a developing project.

## Data

The document `sipp_data_cleaning.qmd` contains all code to create the final dataset `sipp_tanf.csv` included in the `\data` folder. Each variable in the dataset is at one of \_\_ levels to be included in the hierarchical model. The dataset contains 511497 observations of 33 variables. Each observation is an individual in a month.

### Data Dictionary

### `sipp_tanf.csv`

| Variable                | Type        | Level          | Description | Source                                                                                                                                |
|-------------------------|-------------|----------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------|
| `household_id`          | ID; numeric | Household      |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `pnum`                  | ID; numeric | Person         |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `month`                 | numeric     | Person-month   |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `year`                  | numeric     | Household-year |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `age`                   | numeric     | Person-year    |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `state`                 | character   | Household      |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `education`             | character   | Person         |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `ethnicity`             | character   | Person         |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `race`                  | character   | Person         |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `sex`                   | character   | Person         |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `citizenship`           | numeric     | Person         |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `total_children`        | numeric     | Person-year    |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `in_goal1`              | numeric     | Household      |             | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri} |
| `in_goal2`              | numeric     | Household      |             | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri} |
| `in_goal3`              | numeric     | Person         |             | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri} |
| `in_goal4`              | numeric     | Household      |             | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri} |
| `goal1`                 | numeric     | Household      |             | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri} |
| `goal2`                 | numeric     | Household      |             | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri} |
| `goal3`                 | numeric     | Person         |             | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri} |
| `goal4`                 | numeric     | Household      |             | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri} |
| `pct_unobligated`       | numeric     | State-year     |             | derived from [TANF Financial Data](https://www.acf.hhs.gov/ofa/programs/tanf/data-reports){.uri}                                      |
| `pct_program_mgmt`      | numeric     | State-year     |             | derived from [TANF Financial Data](https://www.acf.hhs.gov/ofa/programs/tanf/data-reports){.uri}                                      |
| `pct_basic_assistance`  | numeric     | State-year     |             | derived from [TANF Financial Data](https://www.acf.hhs.gov/ofa/programs/tanf/data-reports){.uri}                                      |
| `received_job_training` | numeric     | Person-month   |             | derived from [TANF Financial Data](https://www.acf.hhs.gov/ofa/programs/tanf/data-reports){.uri}                                      |
| `hh_married_month`      | numeric     | Person         |             | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri} |
| `tanf_begin_month`      | numeric     | Person-month   |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `tanf_initial_year`     | numeric     | Person-month   |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `tanf_end_month`        | numeric     | Person-month   |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `tanf_coverage_type`    | character   | Person-month   |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `tanf_owner`            | numeric     | Person-month   |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `tanf_continue_flag`    | character   | Person-month   |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `tanf_received_month`   | numeric     | Person-month   |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `tanf_received_year`    | numeric     | Person-year    |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `tanf_amt_received`     | numeric     | Person-month   |             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html){.uri}              |
| `party`                 | character   | State-year     |             | [Wikipedia List of States' Governors](https://en.wikipedia.org/wiki/Category:Lists_of_state_governors_of_the_United_States){.uri}     |

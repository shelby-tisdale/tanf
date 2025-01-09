# tanf

This repository contains all code and data for my senior honors thesis project at Duke University, "The Diminishing Cash Safety Net: Predicting Fulfillment of TANF Goals from Unobligated Funds with Bayesian Hierarchical Modeling. This is a developing project.

## Data

The document `sipp_data_cleaning.qmd` contains all code to create the final dataset `sipp_tanf.csv` included in the `\data` folder. Each variable in the dataset is at one of \_\_ levels to be included in the hierarchical model. The dataset contains 511497 observations of 36 variables. Each observation is an individual in a month.

### Data Dictionary

### `sipp_tanf.csv`

| Variable                | Type        | Level           | Description                                                                                                                                                                                                                                                                                                                                                         | Source                                                                                                                          |
|-------------------------|-------------|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| `household_id`          | ID; numeric | Household       | Household identifier. Can be used to match households in different survey years.                                                                                                                                                                                                                                                                                    | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `pnum`                  | ID; numeric | Person          | Person number. Each individual in a household is given a distinct person number for that household.                                                                                                                                                                                                                                                                 | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `month`                 | numeric     | Person-month    | Reference month.                                                                                                                                                                                                                                                                                                                                                    | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `year`                  | numeric     | Household-year  | Survey panel year (reference year).                                                                                                                                                                                                                                                                                                                                 | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `age`                   | numeric     | Person-year     | Age as of last birthday                                                                                                                                                                                                                                                                                                                                             | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `state`                 | character   | Household       | State of residence for the interview address.                                                                                                                                                                                                                                                                                                                       | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `education`             | character   | Person          | Highest level of education received by December of reference year.                                                                                                                                                                                                                                                                                                  | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `ethnicity`             | character   | Person          | Whether person is of Hispanic, Latino or Spanish origin.                                                                                                                                                                                                                                                                                                            | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `race`                  | character   | Person          | Race (detailed categories).                                                                                                                                                                                                                                                                                                                                         | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `sex`                   | character   | Person          | Sex assigned at birth.                                                                                                                                                                                                                                                                                                                                              | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `citizenship`           | numeric     | Person          | Whether person is a U.S. citizen.                                                                                                                                                                                                                                                                                                                                   | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `total_children`        | numeric     | Household-month | Children ever born or fathered.                                                                                                                                                                                                                                                                                                                                     | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `in_goal1`              | numeric     | Household-month | Indicator for whether household fits criteria to be evaluated for TANF Goal 1: "Provide assistance to needy families so that children can be cared for in their own homes or in the homes of relatives." <br><br> `in_goal1` = 1 if at least one child lives in household during any year of the survey.                                                            | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html) |
| `in_goal2`              | numeric     | Household       | Indicator for whether household fits criteria to be evaluated for TANF Goal 2: "End the dependence of needy parents on government benefits by promoting job preparation, work, and marriage." <br><br> `in_goal2` = 1 if household is receiving any kind of government benefits in their earliest year of participation in the study (during reference time frame). | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html) |
| `in_goal3`              | numeric     | Perseon         | Indicator for whether household fits criteria to be evaluated for TANF Goal 3: "Prevent and reduce the incidence of out-of-wedlock pregnancies" <br><br> `in_goal3` = 1 if person is a woman over the age of 14 and is unmarried in reference year.                                                                                                                 | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html) |
| `in_goal4`              | numeric     | Household       | Indicator for whether household fits criteria to be evaluated for TANF Goal 4: "Encourage the formation and maintenance of two-parent families." <br><br> `in_goal4` = 1 if household includes at least one child and at least one parent.                                                                                                                          | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html) |
| `goal1`                 | numeric     | Household-month | Indicates whether TANF Goal 1 is fulfilled for the given household and month. <br><br> `goal1` = 1 if all children in the household have at least one relative in the household.                                                                                                                                                                                    | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html) |
| `goal2`                 | numeric     | Household       | Indicates whether TANF Goal 2 is fulfilled for the given household.<br><br>`goal2` = 1 if household members are no longer receiving government benefits by the end of the reference period.                                                                                                                                                                         | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html) |
| `goal3`                 | numeric     | Person          | Indicates whether TANF Goal 3 is fulfilled for the given person.<br><br>`goal3` = 1 if the number of children of an unmarried individual does not increase during the reference period.                                                                                                                                                                             | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html) |
| `goal4`                 | numeric     | Household       | Indicates whether TANF Goal 4 is fulfilled for the given household.<br><br>If the household is a one-parent family, `goal4` = 1 if the family is a two-parent family at the end of the reference period.<br><br>If the household is a two-parent family, `goal4` = 1 if the family is still a two-parent family at the end of the reference period.                 | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html) |
| `pct_unobligated`       | numeric     | State-year      | Percent of available TANF funds unobligated. Calculated by dividing unobligated balance for fiscal year by the sum of awarded yearly funds and carryover from previous year.                                                                                                                                                                                        | derived from [TANF Financial Data](https://www.acf.hhs.gov/ofa/programs/tanf/data-reports)                                      |
| `pct_program_mgmt`      | numeric     | State-year      | Percent of total expenditures allotted to program management expenses (administrative costs, assessment & service provision, systems)                                                                                                                                                                                                                               | derived from [TANF Financial Data](https://www.acf.hhs.gov/ofa/programs/tanf/data-reports)                                      |
| `pct_basic_assistance`  | numeric     | State-year      | Percent of total expenditures allotted to basic assistance (cash, payments, vouchers, and other forms of benefits designed to meet a family's ongoing basic needs).                                                                                                                                                                                                 | derived from derived from [TANF Financial Data](https://www.acf.hhs.gov/ofa/programs/tanf/data-reports)                         |
| `received_job_training` | numeric     | Person-month    | Indicator for whether person received any kind of job training in reference month.                                                                                                                                                                                                                                                                                  | derived from [TANF Financial Data](https://www.acf.hhs.gov/ofa/programs/tanf/data-reports)                                      |
| `hh_married_month`      | numeric     | Person          | Indicates whether householder is married in reference month.                                                                                                                                                                                                                                                                                                        | derived from [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html) |
| `tanf_begin_month`      | numeric     | Person-month    | Beginning month of TANF receipt.                                                                                                                                                                                                                                                                                                                                    | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `tanf_initial_year`     | numeric     | Person-month    | Initial year of TANF benefit receipt.                                                                                                                                                                                                                                                                                                                               | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `tanf_end_month`        | numeric     | Person-month    | End month of TANF benefit receipt.                                                                                                                                                                                                                                                                                                                                  | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `tanf_coverage_type`    | character   | Person-month    | Type of TANF benefit coverage.                                                                                                                                                                                                                                                                                                                                      | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `tanf_owner`            | numeric     | Person-month    | Person number for owner of TANF benefit this month.                                                                                                                                                                                                                                                                                                                 | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `tanf_continue_flag`    | character   | Person-month    | Continuation status of TANF benefit receipt in the last month of the reference period.                                                                                                                                                                                                                                                                              | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `tanf_received_month`   | numeric     | Person-month    | Whether person received TANF benefits this month.                                                                                                                                                                                                                                                                                                                   | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `tanf_received_year`    | numeric     | Person-year     | Whether person received TANF benefits this year.                                                                                                                                                                                                                                                                                                                    | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `tanf_amt_received`     | numeric     | Person-month    | Value of the TANF benefits received this month.                                                                                                                                                                                                                                                                                                                     | [Survey of Income and Program Participation Data](https://www.census.gov/programs-surveys/sipp/data/datasets.html)              |
| `party`                 | character   | State-year      | Political party affiliation of state's governor.                                                                                                                                                                                                                                                                                                                    | [Wikipedia List of States' Governors](https://en.wikipedia.org/wiki/Category:Lists_of_state_governors_of_the_United_States)     |

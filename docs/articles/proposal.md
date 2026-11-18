# BST 260 Final Project Proposal

## Project Overview

For my final project, I plan to use two CDC datasets: waterborne and
cdcmurd. I want to explore patterns in public health data across
different regions and time in the United States. I will use R to clean
the data, calculate summary statistics, and create plots. I also plan to
write some R functions to make the analysis easier to repeat.

### CDC Waterborne Illness Outbreaks

**Research Question**: How has the distribution of water exposure types
among reported waterborne outbreaks changed from 1971 to 2023 in the
United States?

**Population and Unit of Analysis**: The dataset contains reported
outbreaks in the United States from 1971 to 2023. I will focus on
records where primary_mode == “Water”, which gives 3,106 records. Each
record represents one reported outbreak.

**Exposure**: The main exposure is calendar decade, created from the
year variable. I will group outbreaks into the 1970s, 1980s, 1990s,
2000s, 2010s, and 2020s. Calendar decade will be treated as a
categorical variable.

**Outcome**: Water exposure type, which is a categorical variable. I
will classify outbreaks into six groups: drinking water, treated
recreational water, untreated recreational water, other/environmental
water, undetermined water, and multiple exposure types. If an outbreak
has more than one exposure type, I will put it in the multiple exposure
group.

**Potential confounders**: Geographic region may be related to water
exposure types, so I plan to compare the patterns across regions.
Reporting practices may also have changed over time, which could affect
the results. However, I do not have enough information to adjust for
these changes, so I will mention this as a limitation.

**Missing data**: I checked the year and water exposure type variables
in the 3,106 waterborne outbreak records and found no missing or invalid
values. Therefore, I will keep all 3,106 records for the main analysis.

**Analysis**: I will calculate the number and percentage of outbreaks
for each water exposure type in each decade. Then I will create 100%
stacked bar plots to compare the patterns over time. I will discuss how
changes in reporting practices may affect the results.

### CDC Homicide Mortality

**Research Question**: Have differences in homicide mortality rates
between U.S. states increased or decreased from 2014 to 2024?

**Study Population Selection**: I will exclude Washington, D.C. because
my research question focuses on differences between the 50 U.S. states.
Washington, D.C. is a federal district rather than a state, and it
differs from most states in geographic size, population size, and
urbanization. These differences may affect its homicide mortality rate
and make it less comparable with the states. Since my outcome is the
standard deviation of state homicide mortality rates, including D.C.
could also affect the results.

**Population and Unit of Analysis**: I will use homicide mortality data
for 50 U.S. states from 2014 to 2024. Each original record represents
one state in one year. I will calculate summary statistics across states
for each year, so the main trend analysis will use yearly summaries.

**Exposure**: Calendar year, treated as a numeric variable. I will focus
on 2014–2024 and exclude records outside this period. I will check for
missing or invalid year values before the analysis.

**Outcome**: The standard deviation (SD) of state homicide mortality
rates for each year, which is a continuous summary measure. I will also
calculate the interquartile range (IQR) as an additional measure of
differences between states.

**Potential confounders**: Differences in age, sex and firearm ownership
distributions may affect homicide mortality rates across states.
However, these variables are not available in this dataset, so I will
not be able to adjust for them. This analysis will focus on describing
changes in state-level variation over time rather than estimating a
causal effect of calendar year. I will discuss these factors as possible
limitations in the final analysis.

**Missing Data**: From 2014 to 2024, there are 550 state-year records
for the 50 U.S. states, excluding Washington, D.C. Among these records,
25 have missing homicide mortality rates, leaving 525 available records.
For the main analysis, I will calculate SD and IQR using states with
available death rates in each year, without imputing missing values. I
will report the number of available states each year. As a sensitivity
analysis, I will repeat the calculations using only states with complete
data for all 11 years to check whether missing data affect the observed
trends.

**Analysis**: I will calculate SD and IQR of state homicide mortality
rates for each year and I will create line plots to show whether
differences between states have increased or decreased over time. I also
plan to write an R function to calculate these statistics for different
years.

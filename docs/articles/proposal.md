# BST 260 Final Project Proposal

## Project Overview

For my final project, I plan to use two CDC datasets: waterborne and
cdcmurd. I want to explore patterns in public health data across
different regions and time in the United States. I will use R to clean
the data, calculate summary statistics, and create plots. I also plan to
write some R functions to make the analysis easier to repeat.

### CDC Waterborne Illness Outbreaks

**Research Question**: How do seasonal patterns in reported waterborne
illness outbreaks differ across regions in the United States?

**Population and Unit of Analysis**: The dataset contains reported
outbreaks in the United States from 1971 to 2023. I will focus on
records where primary_mode == “Water”. There are 3,106 records in this
group. Each record represents a reported outbreak. For regional
comparisons, I will use 3,079 records that can be matched to the 50 U.S.
states. I will group the records by season, region, and year to
calculate outbreak counts.

**Exposure**: The main exposures are season and geographic region. I
will use the month variable to create four seasons: winter
(December–February), spring (March–May), summer (June–August), and fall
(September–November). I will use state.region in R to group states into
four geographic regions.

**Outcome**: Number of reported waterborne illness outbreaks, which is a
count variable.

**Potential confounders**: Calendar year may affect the results because
reporting practices and surveillance may change over time. I will
account for year by comparing seasonal and regional patterns within
different time periods.

**Missing data**: I will check for missing values in state, month, and
year. Among the 3,106 waterborne outbreak records, 27 cannot be matched
to the four geographic regions because they refer to locations such as
Puerto Rico, Washington, D.C., other territories, or multistate
outbreaks. I will exclude these 27 records from regional comparisons and
report this exclusion in the final analysis. I will also exclude records
with missing month or year information when needed.

**Analysis**: I plan to first convert the original list into a tidy data
frame. Then I will calculate outbreak counts by season and region and
create grouped bar plots to compare seasonal patterns across regions. I
will also write an R function to summarize outbreak counts for different
groups.

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
could also affect the results. Therefore, I will exclude D.C. based on
my study population definition rather than its observed mortality rate.

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

# Relationship Between Power Outages and Severe Weather
This is a project for DSC 80 at UCSD
**Name(s)**: Haoyang Yu, Jessie Zhang

### Introduction
The original dataframe have 1534 rows and 57 columns. But there exist some useless and duplicate informations, we decided to only keep 13 columns that may helpful for our research of power outages.

**Possible Questions**:
  1. Whether the length of outages due to natural disasters depends on the climate zone.
  2. Which cause of outages is more common in each state?
  3. Which cause of outages caused the most demand loss in total?
  4. Whether the place have most outage times have the most natural disaster.
  5. Whether the avaerge time of outage cause by weather is longer than overall average outage time?
  6. Which kind of weather cause the most average time of outage?

  **One question we pick**:
    Did severe weather cause more power outages than all causes over years?

#### Step 1: Data Cleaning
**Step 1.1**: 
   1. Compute power outage start date and time
   2. Compute power restoration date and time
**Step 1.2**: 
   1. Change some columns name to be more readble
   2. Create a sub dataframe that only contains major power outages. (Durate more than 0 mins).
   3. Create new column 'YEAR' 

#### Step 2: Univariate Analysis
**Step 2.1**: 
The first graph we draw is a a bar chat that about count the times of major outages each year. It helps us realize which year often has major outages.
**Step 2.2**: 
The second we draw is a line graph which contains two lines. First line counts the major outages that caused by severe weather over year and the second line is counts the major outages for all causes. 

#### Step 3: Bivariate Analysis
During the process of identify possible associations: 

**Step 3.1**: We first try decide whether the outages that caused by severe weather were drawn at random from all power outage.

**Step 3.2**: Then, we want to find out the realtion between outages cause by server weather and cause by other factors.

#### Step 4: Interesting Aggregates

We choose to group CAUSE.CATEGORY column and index of each year to create the pivot table. It helps us to realize the amount of power outages different between each caused reasons. 

### Assessment of Missingness
#### Step 5: NMAR Analysis
**Step 5.1**: 

- **Null Hypothesis**: Values in the 'OUTAGE.DURATION' column for rows where the 'CUSTOMERS.AFFECTED' was missing were drawn from the same distribution as the values in rows where 'CUSTOMERS.AFFECTED' was not missing.

- **Alternative Hypothesis**: They were drawn from different distributions.

**Step 5.2**: 

- **Null Hypothesis**: Values in the 'TOTAL.PRICE' column for rows where the 'CUSTOMERS.AFFECTED' was missing were drawn from the same distribution as the values in rows where 'CUSTOMERS.AFFECTED' was not missing.

- **Alternative Hypothesis**: They were drawn from different distributions.

### Hypothesis Testing
#### Severe Weather V.S. All Causes

We already have the data of each years power outages, and we are wondering if the severe weather cause more power outages than all causes over years?

- **Null Hypothesis**: Outages that caused by severe weather **were** drawn at random from all power outage.


- **Alternative Hypothesis**: Outages that caused by severe weather **were not** drawn at random from all power outage.

- **Observation**: Outages per Year Distribution of Severe Weather.

Let's compute the TVD between Severe Weather outage distribution and All Causes's outage distribution.

#### The plan

To conduct our hypothesis test, we will:

- Repeatedly generate samples of size 1398 (number of power outages) from the outages per Year distribution of all causes.

- Each time, compute the TVD between the simulated distribution and all causes's distribution.

- **This will generate an empirical distribution of TVDs, under the null.**

- Finally, determine whether the observed TVD is consistent with the empirical distribution of TVDs.

### Conclusion

- The chance that the observed TVD came from the distribution of TVDs under the null is essentially 0.
- This matches our intuition from the start – the two distributions looked very different to begin with. But now we're quite sure the difference can't be explained solely due to chance.
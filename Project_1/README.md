# Project 1: Standardized Testing, Statistical Summaries and Inference

### Problem Statement
State legislatures mandating SAT & ACT exams on students may have caused individual state score averages to decline.

In certain states, we have seen a decline in the average SAT & ACT total & Composite scores respectively.

At first glance, low averages may be indicative of a State's education quality. However, as we will see in the analysis that follows, that this is not necessarily the case.

We should investigate, amongst other factors, if implementing rules to mandate standardized tests may bring about the misleading conclusion of a State's education quality.
___
### Overview of the Data
The data used is SAT and ACT scores by state, as well as participation rates, for the graduating class of 2017/18.

4 separate datasets have been utilized and combined to obtain a larger dataset. Normality is assumed here for all variables except for with Participation Rates.

||Type|Dataset|Description|
|---|---|---|---|
|**state**|*object*|ACT/SAT|The name of the state. The data includes the 50 states of the United States of America plus the District of Columbia| 
|**participation_sat17**|*integer*|SAT|The SAT participation rate per state in 2017|
|**evidence_based_reading_and_writing_sat17**|*integer*|SAT|The average SAT Evidence Based Reading and Writing score per state in 2017. Scores can range from 200-800.|
|**math_sat17**|*integer*|SAT|The average SAT Math score per state in 2017. Scores can range from 200-800.|
|**total_sat17**|*integer*|SAT|The SAT Total score per state in 2017. Total can range from 400-1600|
|**participation_act17**|*integer*|ACT|The ACT participation rate per state in 2017|
|**english_act17**|*float*|ACT|The average ACT English score per state in 2017. Score can range from 1-36|
|**math_act17**|*float*|ACT|The average ACT Math score per state in 2017. Score can range from 1-36|
|**reading_act17**|*float*|ACT|The average ACT Reading score per state in 2017. Score can range from 1-36|
|**science_act17**|*float*|ACT|The average ACT Science score per state in 2017. Score can range from 1-36|
|**composite_act17**|*float*|ACT|The average score between ACT English,Math,Reading and Science scores per state in 2017. Composite can range from 1-36|
|**participation_sat18**|*integer*|SAT|The SAT participation rate per state in 2018|
|**evidence_based_reading_and_writing_sat18**|*integer*|SAT|The average SAT Evidence Based Reading and Writing score per state in 2018. Scores can range from 200-800.|
|**math_sat18**|*integer*|SAT|The average SAT Math score per state in 2018. Scores can range from 200-800.|
|**total_sat18**|*integer*|SAT|The SAT Total score per state in 2018. Total can range from 400-1600|
|**participation_act18**|*integer*|ACT|The ACT participation rate per state in 2018|
|**english_act18**|*float*|ACT|The average ACT English score per state in 2018. Score can range from 1-36|
|**math_act18**|*float*|ACT|The average ACT Math score per state in 2018. Score can range from 1-36|
|**reading_act18**|*float*|ACT|The average ACT Reading score per state in 2018. Score can range from 1-36|
|**science_act18**|*float*|ACT|The average ACT Science score per state in 2018. Score can range from 1-36|
|**composite_act18**|*float*|ACT|The average score between ACT English,Math,Reading and Science scores per state in 2018. Composite can range from 1-36|




# Observations

Participation rates and average total SAT scores have a strong inverse correlation of -0.87 and -0.79 for 2017 and 2018 respectively.
Strong inverse correlations can be indicative of how strong the inverse relationships are of 2 given variables.

We observe a similar trend for ACT participation rates along with the composite scores as well.

![](https://i.ibb.co/LtNLQ6v/download.png)

![](https://i.ibb.co/7zfFdfk/participation-rate-and-total-score-ACT.png) 





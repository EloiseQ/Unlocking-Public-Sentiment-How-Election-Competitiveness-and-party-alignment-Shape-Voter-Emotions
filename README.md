## Exploring Sentiment Reaction to U.S. President Election
#### Objective: This part focuses on the public sentiment reaction during U.S. Presidential Elections (2012, 2016, 2020).
Research Questions:
1. How does electoral competition influence sentiment?
2. Does party alignment affect sentiment?
3. How do sentiments vary across different time windows (Pre-election, Election Day, Post-election)?
#### Key Variables:
1. Sentiment Score (derived from Twitter posts) 
2. Party Alignment (State vs. National Party Alignment)
3. Time WIndow ( Pre-Election, Election Day, Post-Election 
4. Fluctuation rate (year over year changes in vote share between major political parties) in specific state.

### Data and Variable Overview
#### Data Preparation Steps
1. Merged sentiment data with election data (2012, 2016, 2020).
2. Excluded Election Day to focus on pre/post-election effectsa.
3. Final dataset includes fluctuation rates, time windows, and party alignment.
4. Party Alignment: Created as a binary variable indicating whether the state-winning party matches the national-winning party.
5. fluctuation Rate: Calculated as the absolute year-over-year change in vote shares for DEMOCRAT and REPUBLICAN parties within each state.
6. Time Windows: Defined as 5 days before (Pre-election) and 5 days after (Post-election) the election day, excluding the election day itself.

### Models:
#### Model 1: Basic OLS Regression Model 
- Objective:  Understanding the direct effect of the key variable (fluctuation rate, treatment, time windows), on twitter sentiment. 
- Formula :  ‘SCORE ~ fluctuation_rate + treatment + time_window_Pre_election + time_window_Post_election'
##### Key Insight: 
- Election Competitiveness Matters:The fluctuation rate plays a critical role in shaping public sentiment. Competitive elections generate higher sentiment scores, emphasizing the importance of fair and competitive democratic processes.
Party Alignment Has No Direct Effect:The insignificance of the treatment variable indicates that party alignment alone does not significantly influence sentiment. This may suggest that public sentiment is driven more by election dynamics and timing rather than political alignment.
Timing Effects Are Strong:Both time windows are associated with significantly higher sentiment compared to the baseline period. This highlights the importance of the election timeline in shaping public emotions.

#### Model 2: Interaction Regression Model 
- Objective: Examine how the effects of fluctuation rate and time windows vary by treatment (party alignment).
- Formula = 'SCORE ~ fluctuation_rate * treatment + time_window_Election_day * treatment + time_window_Post_election * treatment'
##### Key Results:
- Fluctuation Rate * Treatment(Coefficient:0.2928, Significant): Competition intensity has a stronger positive effect in aligned states.
- Time Windows*Treatment (Not Significant for election day or post election )
- Interpretation: Party alignment amplifies the sensitivity of public sentiment to competition intensity but does not alter time dynamics.

#### Model 3: DiD Analysis 
- Objective: In this approach, a separate Difference-in-Differences (DID) model is applied to each election year (2012, 2016, and 2020) to evaluate the causal effect of party alignment (treatment) on sentiment scores (SCORE) during the Post-election period.
	1.	2012: No significant effects were observed for party alignment, post-election periods, or election competitiveness.Sentiment remained stable across treatment groups and time.
	3.	2016:	Party alignment had a negative effect, particularly in the post-election period. Competitive elections showed a marginal negative impact on sentiment.
	4.	2020: Party alignment showed a positive post-election effect, boosting sentiment in aligned states.The post-election period overall saw a decline in sentiment, except in aligned states.Election competitiveness had a strong positive effect on sentiment.



# The Analysis

## What are the most demanded skills for top 3 most popular data jobs in the US and in Vietnam?
Data jobs in the US are very common. So I want to highlight the most popular jobs and most often required skills for these jobs in this country and have a comparison with the situation in Vietnam. This helps me to focus on skills most important to my job target.

### Methodology
 1. Filter data
 2. Clean up job_skills column 
 3. Calculate skill counts, job counts based on job_title_short
 4. Calculate skill percentage
 5. Plot final findings

View my notebook with details steps here:
[2_Skill_Demand.ipynb](Project\2_Skill_Demand.ipynb)

### Data Visualization
```python
fig, ax = plt.subplots(len(job_titles_US),1)

for i, job_title in enumerate(job_titles_US):
    df_final_US = df_skill_percent_US[df_skill_percent_US['job_title_short'] == job_title].head(5)

    sns.barplot(df_final_US, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_percent', palette='dark:steelblue_r')

    ax[i].set_title(job_title)
    ax[i].legend ().set_visible(False)  
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].set_xlim(0,78)

    if i != len(job_titles_US)-1:
        ax[i].set_xticks([])

    for index, value in enumerate(df_final_US['skill_percent']):
        ax[i].text(value+1,index,f'{value:,.0f}%', va='center')

fig.suptitle('Likelihood of Skills Requested in Job Posting in the US', fontsize=15)
fig.tight_layout()
```
### Result

![Visualization of Top Demanded Skills in the US](Project\Plot_images\1_skill_demand_US.png)

![Visualization of Top Demanded Skills in Vietanm](Project\Plot_images\2_skill_demand_VN.png)

### Insights

SQL and Python are core skills in the data job markets of both the US and Vietnam. Overall, both countries have relatively similar demand for specific skills across each role:

* Data Analysts focus more on tools for data manipulation and visualization (Excel, Tableau, Power BI).
* Data Engineers require knowledge of cloud platforms.
* Data Scientists are expected to have expertise in statistical analysis (R, SAS).

Key differences between the two countries:

* SAS is highly demanded in the US, but not in Vietnam.
* In Vietnam, Power BI is slightly more popular than Tableau for Data Analysts.
* For Data Engineers, Azure is the 4th most required skill in the US, while in Vietnam, it's Java.
* For Data Scientists, SAS and Tableau are the 4th and 5th most requested skills in the US, while in Vietnam, Spark and TensorFlow are more in demand.

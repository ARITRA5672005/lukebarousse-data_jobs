# The Analysis
## This project analyzes the most in-demand skills across various job titles in the U.S. job market. Using a dataset of job postings and their listed skills, it visualizes the top 5 skills for each role (e.g., Data Analyst, Data Engineer, Data Scientist), along with the percentage of postings that mention each skill.

## view my notebook with detailed steps here:
[2_Skills_demand.ipynb](Project\2_Skills_demand.ipynb)

# Visualize Data
```python
fig, ax = plt.subplots(len(job_titles), 1)
sns.set_theme(style='ticks')
for i, job_title in enumerate(job_titles):
 df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
 sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')
 ax[i].set_title(job_title)
 ax[i].set_ylabel('')
 ax[i].set_xlabel('')
 ax[i].get_legend().remove()
 ax[i].set_xlim(0, 78)

 for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{v:.0f}%', va='center')

fig.suptitle('Likelihood of Skills Requested in US Job Postings', fontsize=15)
fig.tight_layout(h_pad=0.5) # fix the overlap

plt.show()
```

# Results
![Visualisation of Top skills for Data Nerds](Project\skill_demand.png)

This visualization shows three horizontal bar charts titled Likelihood of Skills Requested in US Job Postings. Each chart represents the top five skills for three job roles: Data Analyst, Data Engineer, and Data Scientist. The bars indicate the percentage of job postings mentioning each skill, with percentages labeled at the end of each bar. 

For Data Analysts, SQL leads with 51%, followed by Excel at 41%, Tableau at 28%, Python at 27%, and SAS at 19%. For Data Engineers, SQL is at 68%, Python at 65%, AWS at 43%, Azure at 32%, and Spark at 32%. For Data Scientists, Python dominates at 72%, followed by SQL at 51%, R at 44%, SAS at 24%, and Tableau at 24%. The charts use a clean, professional style with a dark color palette, and the overall tone is informative and analytical.

# Insights
SQL is crucial across all three roles—most demanded for Data Engineers (68%) and also highly required for Data Analysts (51%) and Data Scientists (51%).

Python dominates Data Science roles (72%) and is also important for Data Engineering (65%) and Data Analysis (27%).

Excel is notably relevant for Data Analysts (41%) but not mentioned for the other roles.

Cloud and big data tools like AWS (43%), Azure (32%), and Spark (32%) are more prominent in Data Engineer roles.

Statistical tools like R and SAS are more common for Data Scientists (R: 44%, SAS: 24%) and Analysts (SAS: 19%).

Visualization tool Tableau appears for both Analysts (28%) and Scientists (24%).
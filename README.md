# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?
To find the most demanded skills for the top 3 most popular
data roles, I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This code highlights the most popular data job titles and their top skills, showing which skills you should pay attention to depending on the role you're targeting.

View my notebook with walkthrough notes here:

[2_skills_counting.ipynb](3_Project\2_skills_counting.ipynb)


### Visualisation Code
---
```python
fig, ax = plt.subplots(len(job_titles), 1)
sns.set_theme(style='ticks')
for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x='skill_perc', y='job_skills', ax=ax[i], hue='skill_perc', palette='dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].legend().set_visible(False)
    ax[i].set_xlim(0, 75)
    
    for y, x in enumerate(df_plot['skill_perc']):
        ax[i].text(x + 1, y, f'{x:.0f}%', va='center')

    if i != len(job_titles) -1:
        ax[i].set_xticks([])

fig.suptitle('% of Top Skills in Job Postings UK', fontsize=15)
fig.tight_layout()
plt.show()
```

### Results
---
![Bar plot of top skills for data jobs](3_Project/Images/Skill_Demand_Vis.png)


### Insights
---
#### **Data Analyst**

Key Skills:
- SQL (43%) and Excel (41%) dominate, showing a strong need for database management and spreadsheet analysis in data analyst roles.

- Power BI (27%) and Tableau (16%) emphasize the importance of data visualization skills in presenting insights.

- Python (20%) is a usefull skill but is less critical compared to visualization and database tools.

Insight: Data Analysts are expected to have a mix of foundational database, spreadsheet, and visualization skills, with less emphasis on advanced programming.

### **Data Engineer**

Key Skills:
- SQL (60%) and Python (55%) are critical, reflecting the role's focus on handling large-scale data pipelines and integrations.

- Cloud skills such as Azure (41%) and AWS (33%) are also prominent, showing the industry's shift toward cloud infrastructure.

- Spark (18%) highlights the demand for big data processing in this role.

Insight: Data Engineers require expertise in database management, programming, and cloud technologies, with a focus on handling complex data architectures.


### **Data Scientist**

Key Skills:
- Python (69%) leads by a wide margin, reflecting its essential role in machine learning, data modeling, and statistical analysis.

- SQL (44%) remains important for querying and managing data. R (29%) is notable, indicating its use in statistical analysis alongside Python.

- AWS (17%) and Azure (14%) suggest some overlap with cloud-based solutions but are less emphasized compared to engineering roles.

Insight: Data Scientists prioritize advanced programming, statistical tools, and some database skills, with minimal emphasis on cloud platforms.

## 2. How are in-demand skills trending for Data Analysts?

To find out how the most in-demand skills for data analysts are trending, I filtered the data to show on data analyst jobs, found the top 5 skills and then grouped them by the month of which the jobs were posted. This code highlights the trends of how often different skills are asked for in data analyst job postings throughout 2023.

View my notebook with walkthrough notes here:

[3_skill_trends.ipynb](3_Project\3_skill_trends.ipynb)


### Visualisation code
---
```python
df_plot = df_perc.iloc[:, :5]
sns.set_theme(style='ticks')
sns.lineplot(data=df_plot, dashes=False, palette='tab10', legend=False)
for i in range(5):
    plt.text(11, df_plot.iloc[-2, i], df_plot.columns[i], color=sns.color_palette('tab10')[i])
sns.despine()
ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))
plt.title(f'Trends of the Top Skills for {job_title}s in the {job_place}')
plt.ylabel('In Job Posting %')
plt.xlabel('2023')
plt.show()
```

### Results
---
![Line plot of top skill trends for data analysts](3_Project/Images/skill_trend_vis.png)


### Indights
---
- SQL (47.3% in October, ~42% average): SQL is consistently the most demanded skill across the months. Its dominance highlights the critical importance of database querying and management for data analysts.

- Excel (45.6% in February, ~40% average): Excel remains a close second. Demonstrating its importance for spreadsheet analysis and data organization.

- Power BI (33.3% in July, ~27% average): Power BI saw notable growth in the summer months, this reflects the increasing reliance on business intelligence tools for visualization and reporting.

- Python (26.4% in October, ~21% average): Python’s demand rises steadily throughout the year, signifying its role in automation, data analysis, and programming.

- Tableau (19.7% in October, ~15% average): Tableau maintains a smaller but steady demand. It is a complementary skill for data visualization alongside Power BI.

Insight:
The trends highlight that SQL and Excel remain foundational for data analyst roles, emphasizing database management and spreadsheet expertise. Meanwhile, the increasing demand for Power BI and Python suggests a shift toward data visualization and programming skills. Tableau is valuable but plays a more niche role compared to Power BI. Data analysts aiming to remain competitive should focus on mastering SQL, Excel, and Power BI, with growing attention to Python for automation and advanced analytics.



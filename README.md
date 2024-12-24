# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?
To find the most demanded skills for the top 3 most popular
data roles, I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This code highlights the most popular data job titles and their top skills, showing which skills you should pay attention to depending on the role you're targeting.

View my notebook with walkthrough notes here:

[2_skills_counting,ipynb](3_Project\2_skills_counting.ipynb)


## Visialsation Code
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

## Results

![Bar plot of top skills for data jobs](3_Project/Images/Skill_Demand_Vis.png)


## Insights

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
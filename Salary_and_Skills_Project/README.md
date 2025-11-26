# Project 1 Analysis
## Introduction  
In this Project, I wanted to examine the relationship between skills and salary, and find out which skills are relevant for Data Science.  

### Questions to Analyze  
1. Do more skills get you better pay?  
2. Whats the salary for data jobs in different regions?  
3. What are the top skills of data professionals?
4. What's the pay for the top 10 skills?  

### Excel Skills Used  
- Pivot Tables
- Pivot Charts
- DAX (Data Analysis Expression)
- Power Query
- Power Pivot


### Data Jobs Dataset

The dataset for this project is has real world data science job information from 2023.  
It includes detailed information of:
- Job Titles
- Salaries
- Locations
- Skills

## 1️⃣ Do more skills get you better pay?

### Skill: Power Query

#### Extract

- I first used Power Query to extract the original data (`data_jobs_salary_all.xlsx`) and create two queries:
    - First one with all the data jobs information
    - The second listing the skills for each job ID

#### Transform

- Then, I transformed each query by changing column types, removing unnecessary columns, cleaning text to eliminate specific words, and trimming excess whitespace
    - data_jobs_all  
      <img width="435" height="537" alt="Transfersteps" src="https://github.com/user-attachments/assets/344ca4f6-a675-4d7b-8458-9c9fb42875a9" />

    - data_job_skills  
      <img width="437" height="551" alt="job_skills_steps" src="https://github.com/user-attachments/assets/deaa63ef-da8b-44d8-8012-288581504e1e" />

#### Load

- Finally, I loaded both transformed queries into the workbook, setting the foundation for my subsequent analysis
    - data_jobs_all

        <img width="3071" height="1799" alt="jobs_salary_load" src="https://github.com/user-attachments/assets/f00f6a76-877e-4d87-a756-2248f2a014ee" />


    - data_job_skills

        <img width="3067" height="1795" alt="jobs_skills_load" src="https://github.com/user-attachments/assets/c8ba4017-2a57-4e4e-9a45-af0171b49eb1" />


### Analysis

#### Insights

- There is a positive correlation between the number of skills requested in job postings and the median salary, particularly in roles like Senior Data Engineer and Data Scientist
- Roles that require fewer skills, like Business Analyst, tend to offer lower salaries, suggesting that more specialized skill sets command higher market value

    
 <img width="1144" height="589" alt="Screenshot 2025-11-26 211222" src="https://github.com/user-attachments/assets/f709a0db-f327-4bf1-84ee-425b874d4ea3" />

## 2️⃣ What’s the salary for data jobs in different regions?

### Skills: PivotTables & DAX

#### Pivot Table

- I created a PivotTable using the Data Model I created with Power Pivot
- I moved the `job_title_short` to the rows area and `salary_year_avg` into the values area
- Then I added new measure to calculate the median salary for United States jobs
    ```
    =CALCULATE(
        MEDIAN(data_jobs_all[salary_year_avg]),
        data_jobs_all[job_country] = "United States")
    ```

#### DAX

- To calculate the median year salary I used DAX.

    ```
    Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
    ```

### Analysis

#### Insights

- Job roles like Senior Data Engineer and Data Scientist command higher median salaries both in the US and internationally, showcasing the global demand for high-level data expertise.
- The salary disparity between US and Non-US roles is particularly notable in high-tech jobs, which might be influenced by the concentration of tech industries in the US.

    <img width="1279" height="500" alt="Salary_Comparer_Argentina" src="https://github.com/user-attachments/assets/9c9823ec-3abb-44f8-b5f8-f47b0bcd0db7" />

## 3️⃣ What are the top skills of data professionals?

### Skill: Power Pivot

#### Power Pivot

- I created a data model by integrating the `data_jobs_salary_all` and `data_jobs_skills` tables into one model.
- Since I had already cleaned the data using Power Query; Power Pivot created a relationship between these two tables.

#### Data Model

- I created a relationship between my two tables using the `job_id` column.

    <img width="1044" height="841" alt="Data_model_salary" src="https://github.com/user-attachments/assets/b948108d-f340-4de1-a5eb-c391153cf6f9" />

#### Power Pivot Menu

- The Power Pivot menu was used to refine my data model and makes it easy to create measures.

    <img width="3071" height="1177" alt="Power_Pivot" src="https://github.com/user-attachments/assets/2029485e-0b24-4e99-9f74-abf370afa4a0" />


### Analysis

#### Insights

- SQL and Python dominate as top skills in data-related jobs, reflecting their foundational role in data processing and analysis.
- Emerging technologies like AWS and Azure also show significant presence, underlining the industry's shift towards cloud services and big data technologies.

    <img width="920" height="556" alt="Skill_likelihood" src="https://github.com/user-attachments/assets/1e00817e-0c14-4ff1-b6ce-fc43443ec667" />


## 4️⃣ What’s the pay of the top 10 skills?

### Skill: Advanced Charts (Pivot Chart)

#### PivotChart

- I created a combo PivotChart to plot median salary and skill likelihood (%) from my PivotTable.
    - **Primary Axis:** Median Salary (as a Clustered Column)
    - **Secondary Axis:** Skill Likelihood (as a Line with Markers)
- To customize the chart, I added a title axis title, removed the lines (skill likelihood), and changed the markers to diamonds.

### Analysis

#### Insights

- Higher median salaries are associated with skills like Python, Oracle, and SQL, suggesting their critical role in high-paying tech jobs.
- Skills like PowerPoint and Word have the lowest median salaries and likelihood, indicating less specialization and demand in high-salary sectors.

    <img width="1100" height="680" alt="Top_10_Skills_Graph" src="https://github.com/user-attachments/assets/c1fbcbfb-1409-43a4-b6b4-765c358fac9a" />


## Conclusion

As someone who is interested in learning new data science skills, I started this Excel project to use my excel skills and discover valuable insights about the data science job market. Using a dataset I've found of real-world job postings, I analyzed job titles, salaries, locations, and essential skills. By using Excel features like Power Query, PivotTables, DAX, and charts, I discovered key correlations between multiple skills and higher salaries, particularly in Python and SQL.

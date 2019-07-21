# Data Cleaning and Analysis of Employee Resignation Survey results

In this project, we were tasked with cleaning and analyzing Employee Exit Survey responses from employees of [Department of Education, Training and Employment](https://en.wikipedia.org/wiki/Department_of_Education_and_Training_) (DETE), and the [Technical and Further Education](https://en.wikipedia.org/wiki/TAFE_Queensland) (TAFE) body of the Queensland government in Australia. The DETE exit survey data can be [found here](https://data.gov.au/dataset/ds-qld-fe96ff30-d157-4a81-851d-215f2a0fe26d/details?q=exit%20survey), and the TAFE exist survey data can be [found here](https://data.gov.au/dataset/ds-qld-89970a3b-182b-41ea-aea2-6f9f17b5907e/details?q=exit%20survey).

Specifically, we looked to gain answers to the following questions:
- Are employees who only worked for the institutes for a short period of time resigning due to some kind of dissatisfaction? What about employees who have been there longer?
- Are younger employees resigning due to some kind of dissatisfaction? What about older employees?

We decided to combine the two datasets containing results for both surveys to answer the above questions. However, although both used the same survey template, one of them customized some of the answers - something that introduced some complications into our work.

## Data Cleaning

- Unnecessary columns for our goals were dropped. 
- Column names were standardized as much as possible across both columns, to facilitate table merging. In particular:
   - Capitalization was made lowercase
   - Spaces were replaced with underscores
   - Trailing whitespace from the ends of the strings were removed
- Reduced dataframes to include only employees who resigned, and not those who left because they found jobs elsewhere, or retired because of age.
- Created a new column that calculates an employee's duration of employment, by calculating the difference between their resignation date and hire date, using the `datetime` library.
- Identified columns that corresponded to employee dissatisfaction, and more explicitly outlined employee dissatisfaction by creating a new column that indicated dissatisfaction using Boolean values of `True` or `False`, or NaN in the case of 
- Columns with very large numbers of missing values (> 500) were dropped.
- After Merging, it was noticed that `institute_service` column contained data in inconsistent formats, such as "11-20", and "More than 20 years". Regular expressions were used to standardize this column into digits, and then the digits were categorized into 4 categories of work experience:       
  - New: Less than 3 years at a company
  - Experienced: 3-6 years at a company
  - Established: 7-10 years at a company
  - Veteran: 11 or more years at a company
- Another column was created to reflect this category. 
- Missing values in the `dissatisfied` column were filled with `False`, since that was the most frequent value in that column. 

## Visualizing the results

### Employee Dissatisfaction by Career Stage:
![career stage dissatisfaction](https://i.gyazo.com/e3e44d5c102490a9aed527bcf6d1e3ba.png)

The graph above suggests that the longer an employee works, the more likely they are to resign citing dissatisfaction with something.

Employees with less than 3 years of work experience cite dissatisfaction only 30% of the time when resigning, while those who worked 4-7 years cited dissatisfaction 35% of the time.

In contrast, those with 7 years or more of work experience reported being dissatisfied about 50% of the time when they resigned.

### Employee Dissatisfaction by Age

- Age column was also cleaned and standardized into the same format using Regular expressions, and then categories were made to represent age, which were then used for the visualization.

![dissatisfaction by age](https://i.gyazo.com/cf3973c632c15c70cfa7fa683047d948.png)

The overall trend observed based on Age groups here is somewhat similar to the outcome observed with Career Stages from above.

In general, older employees seem to be more likely to resign reporting dissatisfaction. This trend is fairly consistent across all age groups, apart from the 26-30 and 31-35 age groups. This might be because older employees could have more accumulated grievances. 


### Employee Dissatisfaction by Institute

![dissatisfaction by institute](https://i.gyazo.com/7a97e12ac48852a5f94b818b046949ff.png)

At first glance, it looks like employees in DETE are significantly more likely to report dissatisfaction. However, this is probably because of the fact that there were more columns in the DETE table which indicated dissatisfaction. This is the case because survey answers were recorded in different formats, even though the survey template was the same. This unequalness in how the survey responses were handled was one limitation of this project.


# Data Cleaning and Analysis of Employee Resignation Survey results

In this project, we were tasked with cleaning and analyzing Employee Exit Survey responses from employees of [Department of Education, Training and Employment](https://en.wikipedia.org/wiki/Department_of_Education_and_Training_(Queensland) (DETE), and the [Technical and Further Education](https://en.wikipedia.org/wiki/TAFE_Queensland) (TAFE) body of the Queensland government in Australia. The DETE exit survey data can be [found here](https://data.gov.au/dataset/ds-qld-fe96ff30-d157-4a81-851d-215f2a0fe26d/details?q=exit%20survey), and the TAFE exist survey data can be [found here](https://data.gov.au/dataset/ds-qld-89970a3b-182b-41ea-aea2-6f9f17b5907e/details?q=exit%20survey).

Specifically, we looked to gain answers to the following questions:
- Are employees who only worked for the institutes for a short period of time resigning due to some kind of dissatisfaction? What about employees who have been there longer?
- Are younger employees resigning due to some kind of dissatisfaction? What about older employees?

We decided to combine the two datasets containing results for both surveys to answer the above questions. However, although both used the same survey template, one of them customized some of the answers - something that introduced some complications into our work.

## Data Cleaning

- Unnecessary columns for our goals were dropped. 
- Column names were standardized as much as possible across both columns, to facilitate table merging. In particular:
   - Capitalization will be made lowercase
   - Spaces will be replaced with underscores
   - Trailing whitespace from the end of the strings will be removed


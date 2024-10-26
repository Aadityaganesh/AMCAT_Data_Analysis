# AMCAT_Data_Analysis
The AMCAT Data Analysis Project is designed to demonstrate proficiency in data analysis skills through the practical application of various analytical techniques and tools. This project focuses on preparing for the AMCAT (Aspiring Minds Computer Adaptive Test) Data Analysis module, which assesses candidates' abilities to interpret and analyze data effectively.

# Table of Contents
- [Installation](#installation)
- [Tools](#tools)
- [Objective](#objective)
- [Features](#features)
- [Data Preprocessing](#data-preprocessing)
- [Data Analysis](#data-analysis)

# Installation
**Installing Jupyter lab**
Open your terminal and then run this command to install jupyter lab

    pip install jupyter lab
    
**Clone this Repository**
If the repository on github, Clone it to your local machine

    git clone https://github.com/Aadityaganesh/Ambition_box_Web_Scrapping_EDA

**Launch jupyter lab**

Launch juypter lab in terminal by running the following command

    jupyter lab

# Tools 
These are the Tools used in this Project

- **Python:** A versatile programming language widely used for data analysis, web development, and automation.
- **Numpy:** A Python library for numerical computing, providing support for large, multi-dimensional arrays and matrices.
- **Pandas:** A data analysis library in Python, offering data structures like DataFrames for manipulating structured data.
- **Matplotlib:** A Python library for creating static, animated, and interactive visualizations in data analysis.
- **Seaborn:** A Python visualization library based on Matplotlib, known for making attractive and informative statistical graphics.

You can install all these libraries in one command using pip.
Here’s how:
  
    pip install python regex numpy pandas matplotlib seaborn

For Jupyter Notebooks,
use:

    !pip install python numpy pandas matplotlib seaborn

Make sure you have Python and pip installed on your system. This command installs all libraries with the latest compatible versions.

# Objective

The objective of this analysis is to understand the factors that influence career outcomes for graduates, particularly focusing on salary distribution, specializations, designations, and how demographics such as gender and academic performance (10th, 12th, CGPA, etc.) affect employability and role selection. By examining these factors, we aim to derive insights into how different branches and skills correlate with salary levels and job roles in various sectors, such as IT, engineering, and others.

# Features

- **ID**: A unique identifier for each individual in the dataset.
- **Salary**: The current salary of the individual, typically expressed in monetary units.
- **DOJ**: Date of Joining, indicating when the individual started their current position.
- **DOL**: Date of Leaving, indicating when the individual left their position (if applicable).
- **Designation**: The job title or position held by the individual within the organization.
- **JobCity**: The city where the individual is currently employed.
- **Gender**: The gender of the individual (e.g., Male, Female, Other).
- **DOB**: Date of Birth, indicating the individual's birth date.
- **10percentage**: The percentage score obtained in the 10th-grade examinations.
- **10board**: The educational board under which the individual completed their 10th grade (e.g., CBSE, ICSE).
- **12graduation**: The type of qualification obtained in the 12th grade (e.g., Science, Commerce).
- **12percentage**: The percentage score obtained in the 12th-grade examinations.
- **12board**: The educational board under which the individual completed their 12th grade (e.g., CBSE, ICSE).
- **CollegeID**: A unique identifier for the college or university attended by the individual.
- **CollegeTier**: The tier classification of the college (e.g., Tier 1, Tier 2) based on its reputation and academic standing.
- **Degree**: The degree obtained by the individual (e.g., Bachelor’s, Master’s).
- **Specialization**: The specific field of study or major during the individual's degree (e.g., Computer Science, Mechanical Engineering).
- **collegeGPA**: The Grade Point Average achieved by the individual during their college education.
- **CollegeCityID**: A unique identifier for the city where the college is located.
- **CollegeCityTier**: The tier classification of the college city (e.g., Tier 1, Tier 2).
- **CollegeState**: The state where the college is located.
- **GraduationYear**: The year in which the individual graduated from college.
- **English**: The score obtained in the English subject (possibly in an assessment or examination).
- **Logical**: The score obtained in logical reasoning assessments.
- **Quant**: The score obtained in quantitative aptitude assessments.
- **Domain**: The specific domain or area of expertise of the individual.
- **ComputerProgramming**: The score or competency level in computer programming.
- **ElectronicsAndSemicon**: The score or competency level in electronics and semiconductor knowledge.
- **ComputerScience**: The score or competency level in computer science-related subjects.
- **MechanicalEngg**: The score or competency level in mechanical engineering.
- **ElectricalEngg**: The score or competency level in electrical engineering.
- **TelecomEngg**: The score or competency level in telecommunications engineering.
- **CivilEngg**: The score or competency level in civil engineering.
- **conscientiousness**: A personality trait score indicating the individual's level of conscientiousness.
- **agreeableness**: A personality trait score indicating the individual's level of agreeableness.
- **extraversion**: A personality trait score indicating the individual's level of extraversion.
- **nueroticism**: A personality trait score indicating the individual's level of neuroticism.
- **openness_to_experience**: A personality trait score indicating the individual's openness to new experiences.

# Data Preprocessing

   ### Data Cleaning
    Data cleaning refers to the process of identifying and correcting errors or inconsistencies in a dataset to improve its quality and ensure its suitability for analysis. This process is crucial in the data preparation phase 
    
    ```python
    df.isna().sum()

    Firstly, we check the data has nnull values are not, but here in this data it has no null values so no need of data cleaning
    
   ### Data Exploration
    
   ## Unique Values and Value Counts Analysis
    
    The following code snippet analyzes categorical columns in the dataset. It retrieves the number of unique values for each categorical column and displays the value counts for each category. This analysis helps in understanding the distribution of categorical data, which is crucial for feature engineering and identifying potential areas for further investigation.
    
    ```python
    for column in df.select_dtypes(include="object").columns:
        print("*" * 37)
        print(f"Unique values for {column}: {df[column].nunique()}")
        print(f"Value counts for {column} is:")
        print(df[column].value_counts())
        print("*" * 37, "\n")


    While exploring each and every column i found that there are some words which are miss-spelled so i done data cleaning here for the columns which are spelled incorrectly
    ```python
    # Dictionary to update incorrect city names
    city_dict_update = {'bangalore': 'banglore',
                        'banaglore': 'banglore',
                        'nouda': 'noida', 
                        'bhubaneshwar': 'bhuvaneswar', 
                        'bhubneshwar': 'bhuvaneswar',
                        'gajiabaad': 'ghaziabad', 
                        'gurga': 'gurgaon', 
                        'vizag': 'visakhapatnam',
                        'gandhi nagar': 'gandhinagar',
                        'kochi/cochin': 'kochi',
                        'calicut': 'kozhikode', 
                        'sonepat': 'sonipat',
                        'nasikcity': 'nashik',
                        'tirupathi': 'tirupati','raipur': 'raipur', 
                        'dhanbad': 'dhanbad',                    
                        'miryalaguda': 'hyderabad',
                        'trichy': 'tiruchirappalli',
                        'secunderabad': 'hyderabad',
                        'rayagada, odisha': 'rayagada',
                        'keral': 'kerala',
                        'latur (maharashtra)': 'latur',
                        'rayagada, odisha':'rayagad',
                        'a-64,sec-64,noida':'noida',
                        'miryalaguda':'hyderabad',    
    }
    
    df['JobCity'] = df['JobCity'].str.lower().replace(city_dict_update)
    df['JobCity'].value_counts()


# Data Analysis

### Group by
Groupby is a method that splits the data into groups based on some criteria, applies a function (such as sum, mean, count, etc.) to each group, and then combines the results back into a DataFrame or Series. It is an essential tool for data aggregation and transformation.
  
    df.groupby(["Degree", "Branch"])['Specialization'].value_counts()


### Analysis based on their percentage
    print(f"Minimum percentage scored by 10th passed student percentage is :{df['10percentage'].min()}")
    print(f"Maximum percentage scored by 10th passed student percentage is :{df['10percentage'].max()}")
    print(f"Mean of 10th passed students percentage is :{df['10percentage'].mean():.2f}")
    print(f"Median of 10th passed students percentage is :{df['10percentage'].median():.2f}")
    print(f"Mode of 10th passed students percentage is :{df['10percentage'].mode()}")
    
    plt.title("Percenatge of 10th class students")
    sns.boxplot(df['10percentage'])
    
    # 12th percentage
    
    print(f"Minimum percentage scored by 12th passed student percentage is :{df['12percentage'].min()}")
    print(f"Maximum percentage scored by 12th passed student percentage is :{df['12percentage'].max()}")
    
    print(f"Mean of 12th passed students percentage is :{df['12percentage'].mean():.2f}")
    print(f"Median of 12th passed students percentage is :{df['12percentage'].median():.2f}")
    print(f"Mode of 12th passed students percentage is :{df['12percentage'].mode()}")
    
    plt.title("Percenatge of 12th class students")
    sns.boxplot(df['12percentage'])

    # College CGPA

    print(f"Minimum CGPA scored by degree student percentage is :{df['collegeGPA'].min()}")
    print(f"Maximum percentage scored by 12th passed student percentage is :{df['collegeGPA'].max()}")
    
    print(f"Mean CGPA of college students percentage is :{df['collegeGPA'].mean():.2f}")
    print(f"Median CGPA of college students percentage is :{df['collegeGPA'].median():.2f}")
    print(f"Mode CGPA of college students percentage is :{df['collegeGPA'].mode()}")
    
    plt.title("GPA of College class students")
    sns.boxplot(df['collegeGPA'])

### Higest Count based on designation

    top_20_designations = df['Designation'].value_counts().head(20).index
    print(f"There are {df['Designation'].nunique()} unique designations in total, out of which these are the top 20 most common roles.")
    sns.countplot(y='Designation', data=df, order=top_20_designations)
    
    plt.title('Top 20 Most Common Designations')
    plt.xlabel('Count')
    plt.ylabel('Designation')
    plt.show()
  ![image](https://github.com/user-attachments/assets/80bba78d-eb60-46f0-99f1-cd61360aa497)

### Count of individaul based on gender
    plt.title("Pie Chart of Gender Distribution")
    df['Gender'].value_counts().plot(kind = 'pie', autopct = "%0.2f")
   
   ![image](https://github.com/user-attachments/assets/07db6001-dad7-4d23-98ab-b0b5fab49c8e)

### Created a new column
Here i created a new column called as branch. The main intntion of this is to reduce cardinality and make good use of the dataset

    branch_dict_updated = {'electronics and communication engineering': 'ECE',
                            'electronics & telecommunications': 'ECE',
                            'electronics and instrumentation engineering': 'ECE',
                            'electronics engineering': 'ECE',
                            'applied electronics and instrumentation': 'ECE',
                            'electronics and computer engineering': 'ECE',
                            'telecommunication engineering': 'ECE',
                            'electronics & instrumentation eng': 'ECE',
                            'electronics': 'ECE',
                            
                            'computer science & engineering': 'CSE',
                            'computer engineering': 'CSE',
                            'information technology': 'CSE',
                            'computer application': 'General',
                            'information science engineering': 'CSE',
                            'computer science and technology': 'CSE',
                            'computer and communication engineering': 'CSE',
                            'computer science': 'CSE',
                            'computer networking': 'CSE',
                            'embedded systems technology': 'CSE',
                            
                            'mechanical engineering': 'Mechanical',
                            'mechanical and automation': 'Mechanical',
                            'mechanical & production engineering': 'Mechanical',
                            'automobile/automotive engineering': 'Mechanical',
                            'mechatronics': 'Mechanical',
                            'aeronautical engineering': 'Mechanical',
                            'ceramic engineering': 'Mechanical',
                            'metallurgical engineering': 'Mechanical',
                            'internal combustion engine': 'Mechanical',
                            'power systems and automation': 'Mechanical',
                        
                            'information technology': 'IT',
                            'information science engineering': 'IT',
                            'information & communication technology': 'IT',
                        
                            'electrical engineering': 'EEE',
                            'electronics and electrical engineering': 'EEE',
                            'electrical and power engineering': 'EEE',
                        
                            'instrumentation and control engineering': 'Instrumentation',
                            'instrumentation engineering': 'Instrumentation',
                            'control and instrumentation engineering': 'Instrumentation',
                        
                            'civil engineering': 'Civil',
                        
                            'biotechnology': 'Biotechnology',
                            'biomedical engineering': 'Biotechnology',
                        
                            'industrial & production engineering': 'Industrial & Production',
                            'industrial engineering': 'Industrial & Production',
                            'industrial & management engineering': 'Industrial & Production',
                        
                            'chemical engineering': 'Chemical',
                            'polymer technology': 'Chemical',
                        
                            'other': 'Other',
    }
    
    df['Specialization'] = df['Specialization'].str.lower()
    df['Branch'] = df['Specialization'].replace(branch_dict_updated)
    df['Branch'].value_counts()

### Salary Distribution per Branch of Study

Here we analyze what kind of branch has more salaries

    plt.figure(figsize=(15, 5))
    sns.boxplot(x='Salary', y='Branch', data=df, palette='Set2')
    plt.title('Distribution of Salaries by Specialization', fontsize=16)
    plt.xlabel('Salary (in currency)', fontsize=12)
    plt.ylabel('Branch', fontsize=12)
    plt.legend()
    plt.show()

   ![image](https://github.com/user-attachments/assets/da958427-fcb6-48a2-9a47-ebafbaf52088)

### Is there a relationship between gender and Branch (specialization)? Does the preference of Branch (specialization) depend on gender?

To determine if there is a relationship between gender and Branch (specialization), we can conduct a Chi-square test of independence. This test evaluates whether the observed frequencies of different categories (in this case, gender and specialization) differ significantly from what would be expected if the two variables were independent.

    from scipy.stats import chi2_contingency

    contingency_table = pd.crosstab(df['Gender'], df['Branch'], margins=True)
    print("Contingency Table:")
    print(contingency_table)
    
    chi2, p, dof, expected = chi2_contingency(contingency_table.iloc[:-1, :-1])  # Exclude 'All' row and column
    print(f"Chi-square statistic: {chi2}, p-value: {p}")
    
    plt.figure(figsize=(12, 6))
    sns.countplot(data=df, y='Branch', hue='Gender', order=df['Branch'].value_counts().index)
    plt.title('Distribution of Specialization by Gender', fontsize=16)
    plt.xlabel('Specialization', fontsize=12)
    plt.ylabel('Count', fontsize=12)
    plt.legend(title='Gender')
    plt.show()

![image](https://github.com/user-attachments/assets/fc3c7356-8fc7-46a8-b83e-b54634c1412b)

Fields like CSE, IT, EEE, ECE, and Mechanical Engineering males significantly outnumber females, showing that these fields are more male-dominated. While certain fields like Biotechnology may attract more females, the overall trend across engineering disciplines reveals a significant gender imbalance, particularly in technical fields.

### Times of India article dated Jan 18, 2019 states that “After doing your Computer Science Engineering if you take up jobs as a Programming Analyst, Software Engineer, Hardware Engineer and Associate Engineer you can earn up to 2.5-3 lakhs as a fresh graduate.” Test this claim with the data given to you.


To test the claim made by the Times of India article regarding the earning potential of fresh graduates in specific roles within Computer Science Engineering, we can analyze the salary data for the relevant roles: Program Analyst, Software Engineer, Hardware Engineer, and Associate Engineer. Here’s a structured approach to assess the claim:

Analysis Steps
- **Filter Data**: Extract the salary data for the specified job roles from the dataset.

    relevant_roles = ['program analyst', 'software engineer', 'hardware engineer', 'associate engineer']
    filtered_df = df[df['Designation'].isin(relevant_roles)]
  
- **Descriptive Statistics:** Compute basic descriptive statistics for the salaries of the filtered roles, such as count, mean, median, minimum, maximum, and standard deviation.

    salary_stats = filtered_df['Salary'].describe()
    print("Descriptive Statistics for Salary:")
    print(salary_stats)

- **Average and Median Salary:** Calculate and print the average and median salary for these roles.

    average_salary = filtered_df['Salary'].mean()
    median_salary = filtered_df['Salary'].median()
    print(f"The average salary for the relevant roles is: {average_salary:.2f} Lakhs")
    print(f"The median salary for the relevant roles is: {median_salary:.2f} Lakhs")

- **Salary Distribution Visualization:** Create a box plot to visually represent the distribution of salaries for the relevant roles. This will help identify the spread, any outliers, and how many salaries fall within the specified range of 2.5 to 3 lakhs.


    plt.figure(figsize=(10, 5))
    sns.boxplot(x='Salary', data=filtered_df)
    plt.title('Salary Distribution for Selected Roles')
    plt.xlabel('Salary (in Lakhs)')
    plt.axvline(2.5, color='red', linestyle='--', label='2.5 Lakhs')
    plt.axvline(3.0, color='green', linestyle='--', label='3.0 Lakhs')
    plt.legend()
    plt.show()

Interpretation of Results
- **Descriptive Statistics:** The describe() function will provide insights into the distribution of salaries, including:

**Count:** The number of entries for the selected roles.

**Mean and Median:** These values indicate the average and midpoint salary, respectively.

**Min and Max:** Show the lowest and highest salaries, helping to understand the range.

**Average and Median Salary:** If the average and median salaries for these roles fall within or above the specified range of 2.5 to 3 lakhs, this supports the article's claim. Conversely, if both values are below this range, the claim may not hold true.

- **Box Plot Analysis:** The box plot visually represents the salary distribution:

The box indicates the interquartile range (IQR), showing where the middle 50% of salaries lie.

The red and green dashed lines represent the 2.5 and 3.0 lakh salary thresholds, allowing for a clear visual comparison.

If the majority of the salaries are below these lines, it suggests that the claim may be exaggerated.

![image](https://github.com/user-attachments/assets/e3175db0-0579-48d3-b2be-3db40c19cf27)

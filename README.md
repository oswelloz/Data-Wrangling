
This project involves cleaning and processing a dataset of personality scores, calculating personality subscale totals, merging the personality data with department data, and assessing the risk status of individuals based on their personality traits. The final result summarizes the risk status by department.

# Project Overview
This Python notebook performs the following key tasks:

1. Load and Explore the Data:

    - Load personality score data from a CSV file.
    - Inspect the data structure and display basic information.

2. Clean the Data:

    - Remove empty columns and rows with missing values.
    - Clean column names by removing unwanted characters and special symbols.

3. Calculate Personality Subscale Totals:

    - Define personality subscales (e.g., Extraversion, Agreeableness, Conscientiousness).
    - Calculate the total score for each subscale for each individual, accounting for reverse scoring where necessary.

4. Merge with Department Data:

Load department data from another CSV file.
Merge the personality data with department data on the common "ID" column.

5. Create Risk Status Labels:

    - Create a "RiskStatus" column based on specific personality traits, defining individuals as either "High risk" or "Low risk" based on their subscale totals.

6. Summarize the Risk Status by Department:

    - Group data by department and calculate the count of individuals with "High risk" and "Low risk" status within each department.

# File Structure
- data/personality_scores.csv: The CSV file containing personality scores for individuals across various traits.
- data/departments.csv: The CSV file containing department information (e.g., department names corresponding to individual IDs).

# Data Processing Steps

1. Load and Explore the Data
    - The notebook first loads the personality scores dataset and inspects its structure, displaying basic information about the columns and data types.

2. Clean the Data
    - It removes columns that are entirely empty and drops rows with any missing values.
    - It standardizes column names by stripping whitespace and removing special characters.

3. Define Personality Subscales and Calculate Total Scores
    - The personality traits are divided into subscales, such as Extraversion, Agreeableness, and others.
    - For each subscale, the scores are summed, with reverse scoring applied to some items (e.g., reversing the Likert scale for negative statements).

4. Merge Personality and Department Data
    - Department data is loaded and merged with the personality score data on the "ID" column, which is generated from the index of both DataFrames.

5. Create Risk Status Labels
    - A "RiskStatus" column is generated based on the total scores of specific subscales.
        - Individuals with low scores on Emotional Stability, Conscientiousness, and Agreeableness are classified as "High risk".
        - All other individuals are classified as "Low risk".

6. Summarize the Risk Status by Department
    - The risk status for each department is summarized by counting how many individuals fall into the "High risk" and "Low risk" categories.

# Risk Status Criteria
The following criteria are used to classify risk status:

- High risk:
    - Emotional StabilityTotal < 30
    - ConscientiousnessTotal < 30
    - AgreeablenessTotal < 30

- Low risk:
    - Any individual who does not meet the criteria for "High risk".

# Dependencies
To run this notebook, you need to have the following Python packages installed:

- `pandas` - For data manipulation and analysis.

Install the necessary libraries using pip if you haven't already:

```bash
pip install pandas
```
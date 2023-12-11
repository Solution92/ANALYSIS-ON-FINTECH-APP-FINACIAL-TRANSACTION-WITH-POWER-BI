# ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI
This Project was done for a fintech company I did contract with.

![Fintech image](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/ee71ff4e-67b4-4c98-bc90-00db51d7b339)


## Table of Content
- [Introduction](#introduction)
- [Problem Statement](#problem-statement)
- [Data Sourcing](#data-sourcing)
- [Data Transformation/Cleaning](#data-transformation-cleaning)
- [Data Analysis and Visuals](#data-analysis-and-visuals)
- [The Dashboard](#the-dashboard)
- [Result and Observations](#result-and-observations)
- [Conclusions & Recommendations](#conclusions-recommendations)
- [Reference](#reference)


### Introduction

A prominent fintech company operating in the Andaman & Nicobar Islands, this organization offers a diverse array of financial services, including recharge and bill payments, peer-to-peer transactions, merchant payments, and more. Throughout the years 2018 to 2022, the company showcased significant growth in transaction volumes and amounts across various districts, such as North and Middle Andaman, South Andaman, and Nicobars. Notably, the company collaborated with well-known smartphone brands like Xiaomi, Samsung, Vivo, and others, reflecting a strategic alignment with leading players in the technology sector. This synergy between financial services and technology giants positions them as a key player in the evolving landscape of fintech in the region.

### Problem Statement

Analyze the given dataset and provide us with some insights about the behavior and health of the business for the past 5 years of operation. Also, provide us with your recommendation concerning your analysis to guide business decisions.
In this project, you will be able to use any tool you want such as Python, PowerBI, Excel or many more, depending on your needs. It is your responsibility to formulate an analysis on the business level, such as what actions should be taken by the business as a result of your analysis.

My Exploratory Data Analysis will focus on the following

- Brand Distribution
- Quarterly Transaction Trends
- Top Performing States
- Transaction Amount by Service Type
- Brand Percentage Distribution
- Registered Users by State
  

### Data Sourcing

The Data was given by the Company in Excel format. I downloaded the CSV file and extracted it into Power BI for cleaning, analysis, and visualization.
The dataset has 6 different tables that are related to some fintech company including details about the location, details about the app, the amount, and so on. Each of the tables has about 1,000 rows and 7 columns.

### Data Transformation/Cleaning:

After loading the different datasets to the Power Query editor, I merged them into 1 table using “State” as the primary key. 

![merged 0](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/9b4fecb7-08e7-4f09-bf70-ce7f32ffc11d)

Meanwhile, I discovered that one of the columns (name) in the table contains both text and numeric values which makes it impossible to analyze.

![fintech 1](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/52d193fc-eafd-4834-94fa-1536b851684d)

So, how did I handle this? 
- I created a column called “index column” as a backup to the column (name) that has the discrepancies.
- I duplicated the column (name) that has the issues
- Then in one of the columns I filtered the “Text” values out and in the other table filtered the “Numeric” values out as well.
- Next, I merged the two tables and deleted all other unnecessary columns.
- Finally, I have two different columns (“Name_Text” and “Name_Numeric”)

![Screenshot_166](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/4135ce3e-2a37-4b80-b752-dcdbcac27180)


**Unpivot Columns**

In this transformation process, I also discovered several columns with the same values but different column headers. For instance, “count”, “amount”, and “value”. In this case, how was I able to combine these columns without losing data?

Unpivoting refers to the process of transforming columns into rows. Specifically, it involves converting columns with similar characteristics or data types into attribute-value pairs. This transformation is useful when you have data in a wide format, and you want to reshape it into a long format for better analysis or visualization.

The unpivoting process is beneficial when you want to work with data in a more structured or normalized format, especially for downstream analysis or visualization tools that prefer data in a long or narrow format.
In Power Query Editor, you typically use the "Unpivot Columns" transformation to achieve this. The specific steps may vary based on your version of Power Query and the interface you're using, but it's generally found in the "Transform" or "Transformations" tab.

Now, after the tables are done Unpivoting, you will have two (2) columns- “Attribute” and “Value”. 
The "Attribute" column holds the names of the columns that were unpivoted, and the "Value" column holds the corresponding values.
If you don't need these additional columns and prefer to work with a more compact representation, you can delete the "Attribute" column. Deleting this column won't affect the "Value" column, which contains the actual data.

I like to delete it to reduce the number of columns and make my table simple and easy for analysis.

![Unpivot](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/de9d7ebe-24b4-47dd-877b-b726622e55a1)

### Data Analysis and Visuals

I loaded the dataset to the Power BI Desktop and added some measures as follows:

- Number of Registered Users

   - Registered_Users = SUM('fintech1'[registered_user])
 
- Total Amount of transactions in five(5) years
  
   - Total_Amount = SUM('fintech1'[amount])

- Total number of Brands

  - Brands = DISTINCTCOUNT('fintech1'[brand])
 
- Average number of times the App was opened within the specified duration

  - Average_App_Opens = AVERAGE('fintech1'[appOpens])
 
- Duration of Business operation in Years

  - No. of Years = DISTINCTCOUNT('fintech1'[year])
 

### The Dashboard

Here is the summary of the stories

![Screenshot_163](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/06b4b949-69be-4587-97ac-6f9499f48f58)


### Result and Observations

**Brand Distribution**

The percentage count of service type shows that "Oppo, Realme, Samsung, etc has 9.10% while HMD Global has 0.20% to come out as the last in the brand.

![Screenshot_166](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/eec450c1-e152-48a1-90e2-be2d646f48ea)


**Quarterly Transaction Trends**

At 397,015,035,985,044.40, first quarter had the highest Total Amount and was 72.38% higher than 2nd quarter, which had the lowest Total Amount at 230,309,622,796,837.90. First quarter had the highest Total Amount at 397,015,035,985,044.40, followed by 4th, 3rd, and 2nd quarters respectively. First quarter accounted for 32.29% of the Total Amount.  Across all 4 quarters, the Total Amount ranged from 230,309,622,796,837.90 to 397,015,035,985,044.40.  

![Screenshot_167](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/2bdd21d1-e3ac-4377-acb9-bad09415e4cc)


**Brand Percentage Distribution**

All Service Types had a Count of brands of 28,800, which makes it equal distribution in percentage (20%) of all brands.

![Screenshot_169](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/89313690-2f39-460b-82a2-0942a7a1ad8d)


**Top Performing States**

At 393,185,325,268,771.70, Andhra Pradesh had the highest Sum of the amount and was 14,391.04% higher than dadra-&-nagar-haveli-&-daman-&-diu, which had the lowest Sum of the amount at 2,713,298,641,558.80.  Andhra Pradesh accounted for 31.98% of Sum of amount.  Across all 12 states, the Sum of the amount ranged from 2,713,298,641,558.80 to 393,185,325,268,771.70.  

![Screenshot_168](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/0bee6240-d2df-4bf7-83a7-55651d0fd341)


**Transaction Amount by Service Type**

At 804,202,220,398,651.80, Peer-to-peer payments had the highest Total Amount and was 1,016.90% higher than Others, which had the lowest Total Amount at 72,003,002,051,007.22. Peer-to-peer payments accounted for 65.41% of Total Amount.  Across all 5 Service Types, Total Amount ranged from 72,003,002,051,007.22 to 804,202,220,398,651.80.  

![Screenshot_170](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/5c361dba-ba04-4925-9216-57aba3600e8c)


**Registered Users by State**

At 8,699,463,576, Arunachal Pradesh had the highest number of Registered Users and was 38,872.95% higher than Bihar, which had the lowest number of Registered Users at 22,321,800. Arunachal Pradesh accounted for 50.05% of Registered Users.  Across all 12 states, Registered Users ranged from 22,321,800 to 8,699,463,576.  

![Screenshot_171](https://github.com/Solution92/ANALYSIS-ON-FINTECH-APP-FINACIAL-TRANSACTION-WITH-POWER-BI/assets/144762124/80806902-ebf9-4bab-b71f-e6b46008e9f7)

### Conclusions & Recommendations

- Based on the analyzed dataset, it is recommended to focus on optimizing services related to Oppo, Realme, Samsung, etc., which collectively contribute to 9.10% of the market share. 
- Additionally, considering the quarterly transaction trends, efforts should be directed towards enhancing performance in Quarter 1, as it has the highest total amount and accounts for 32.29% of the total transactions. 
- Furthermore, prioritizing marketing and user engagement initiatives in Andhra Pradesh, the top-performing state with 31.98% of the total amount, can potentially lead to significant growth.

### Reference

Part of my research during the analysis can be accessed from [Here](https://www.kaggle.com/datasets/utkarshsen/fintech-company-dataset)



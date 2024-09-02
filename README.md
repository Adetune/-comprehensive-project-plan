# Refine Production Planning: Utilize Customer Segmentation & Data Insights for Supply Chain
# Table of contents 


- [Objective](#objective)
- [Data Source](#data-source)
- [Stages](#stages)
- [Design](#design)
  - [Mockup](#mockup)
  - [Tools](#tools)
- [Development](#development)
  - [Pseudocode](#pseudocode)
  - [Data Exploration](#data-exploration)
  - [Data Cleaning](#data-cleaning)
  - [Transform the Data](#transform-the-data)
  - [Create the SQL View](#create-the-sql-view)
- [Testing](#testing)
  - [Data Quality Tests](#data-quality-tests)
- [Visualization](#visualization)
  - [Results](#results)
  - [DAX Measures](#dax-measures)
- [Analysis](#analysis)
  - [Findings](#findings)
  - [Validation](#validation)
  - [Discovery](#discovery)
- [Recommendations](#recommendations)
  - [Potential ROI](#potential-roi)
  - [Potential Courses of Actions](#potential-courses-of-actions)


# Objective 
Understanding the Datasets
First, let's understand the datasets you have provided:
Customer Data (customer_data.csv): Likely contains customer demographics, purchase history, and other relevant details.
Inventory Data (inventory_data.csv): Probably includes information about current inventory levels, product categories, and warehouse locations.
Production Data (production_data.csv): May contain details about production volumes, product types, and manufacturing timelines.
Sales Data (sales_data.csv): Should have records of sales transactions, including product details, quantities sold, and customer information.

 Step-by-Step Approach
1. Data Cleaning and Preparation
Consolidate Data: Import and consolidate these datasets into Excel.
Clean Data: Check for and handle missing values, duplicates, and inconsistencies.
Data Transformation: Format and transform data as needed for analysis (e.g., date formatting, categorical data encoding).

 STEPS
a. Checking for Missing Values
Open your Excel dataset.
Select the range of data or the entire sheet.
Go to the 'Home' tab, click on 'Find & Select', and choose 'Go To Special'.
Select 'Blanks' and click 'OK'. This will highlight all cells that are empty.

 b.Find and Remove Duplicates
Select the range of data or the entire sheet.
Go to the 'Data' tab and click on 'Remove Duplicates'.
Choose the columns to check for duplicates, then click 'OK'.

 c. Data Transformation
Converting Text to Dates:
Using the =text(), to split the timestamp columns to date and time.
Then using the datevalue() to ensure that they are in the date data type.

 d. Checking Data Types
Excel doesn't explicitly show data types like a programming language, but you can infer:
Numbers are right-aligned by default.
Texts are left-aligned.


 RESULTS
Customer Data
Missing Values: None detected.
Data Types: Mostly integers and objects (for categorical data like Gender and Geographic Location).

 Inventory Data
Missing Values: None detected.
Data Types: Integers for numerical data and objects for categorical data (Storage Location).

 Production Data
Missing Values: None detected.
Data Types: Integers for numerical data and objects for categorical data (Resource Allocation).

 Sales Data
Missing Values: None detected.
Data Types: Integers for numerical data; the Timestamp column is an object and needs to be converted to a datetime format.

 UP NEXT
Customer Segmentation:
Segment customers based on demographics (age, gender, income) and geographic location.
Identify patterns or trends within each segment.

 Inventory and Production Overview:
Assess inventory levels, stockouts, and production capacities.
Identify any mismatches between production and inventory levels.

 Sales Analysis:
Analyse sales data to understand product preferences and customer buying behaviors.
Identify top-selling products and customer preferences within each segment.

 Integrating Findings:
Combine insights from customer segmentation, inventory, production, and sales data.
Propose strategies for supply chain optimization and customer-centric production planning.

 2. Customer Data Analysis and Segmentation
Segment customers based on demographics (age, gender and income) and geographic location.
Identify patterns or trends within each segment.

 STEPS
Explore Customer Data: Examine the distribution of age,gender,  income, and geographic location. In Excel, you can use pivot tables and charts (like histograms and bar charts) for this.

 Segment Customers:
Age Groups: Create age groups (e.g. Adults, Middle-aged, Seniors). Use Excel formulas to categorise each customer based on their age.
Formula used- =IF(B2>=60,"Seniors",IF(B2>=41,"Middle-aged","Adult")).

 Distribution
Adult 18-40
Middle-aged 41-60
Senior 61-69

 Income Brackets: Divide income into brackets (e.g., Low and High). You can use Excel's median function to divide their income into high and low. Low incomes are based on incomes that are below or 80% of the most likely salary of the customers in the data(median)
Formula used-=IF(D2<=0.8*$K$2,"Low","High")

 Demographic segmentation: based on age group and income bracket. 
adult + low Type 1
adult + high Type 2
middle-aged + low Type 3
middle-aged + high Type 4
senior + low Type 5
senior + high Type 6

 Geographic Location: Already present in the data.
Visualise Distribution: Use Excel charts to visualise the distribution of each segment.

 RESULTS
Based on exploration of columns
The visualisation provides an overview of the distribution of age, gender, income, and geographic location among SmartHome Solutions Inc.'s customers:

 Age Distribution: The age of customers appears to be fairly evenly distributed, with a slight skew towards younger ages. This suggests a diverse range of age groups among the customer base.

 Gender Distribution: There is representation from different gender groups but males are slightly more than females. It's important to see if certain products or services are preferred by specific gender groups.

 Income Distribution: The income distribution shows some variability, which can be crucial for understanding purchasing power and preferences.

 Geographic Location Distribution: Customers are distributed across different geographic locations but we have more people in “City C”. This can impact logistics, inventory management, and product preferences.

 Based on segments
The distribution of customers across different segments reveals valuable insights:

 Age Group Distribution:
We have more Adults than Middle aged and senior individuals.

 Income Bracket Distribution:
Majority of the customers fall under the High Income Category.

 Demographic segmentation distribution:
The breakdown of these category based on both income and age group
From the distribution it seems that majority fall under the segment Type 2 and the least being Type 5
The distribution by region, here are the insights;
For City A, Type 1  takes the led while Type 5 is the least in that City
For City B, it seems that Type 1 the best performing segment is the Type 6  the least being Type
For City C, Type 1 is the best while Type 6 is the worst

 With these segmentations in place, we can now analyze the sales data to identify product preferences and buying behaviors within each segment. This will help in aligning production with customer demands and managing inventory more efficiently.


 3. Merging Datasets
Datasets can be merged using the Power Pivot Function on Excel.

 4. Analysing Product Preferences by Customer Segment
Which products are popular among customer segments and location.
Any notable trends or patterns in purchasing behaviour across these segments.
We will analyse the dataset to understand that.

 STEPS
Calculate Top Products for Each Segment:
Create pivot tables in Excel to aggregate sales by product SKU within each customer segment.
Use the 'Sum' function in the pivot table to total sales quantities.
Sort the results to identify the top-selling products in each segment.

 RESULTS
The analysis reveals the top-selling products in each segment based on the quantity sold:
Top Products for Each Customer Segment:
Type 1: Products with SKUs 21, 56,20,69 and 79 being the top SKUs
Type 2:Products with SKUs 36,83, 41, 93, 81 being the top SKUs
Type 3:Products with SKUs 83,78,99,67,58 being the top SKUs
Type 4:Products with SKUs 89,9,90,77,87 being the top SKUs
Type 5:Products with SKUs 90,35,61,19,94 being the top SKUs
Type 6:Products with SKUs 87,80, 78, 8, 85 being the top SKUs

 Top Products for Each Geographic Location:
City A: Products with SKUs 34, 69, 98, 68, 14 are leading.
City B: Products with SKUs 95, 85, 91, 1, 53 are most popular.
City C: Products with SKUs 79, 67, 83, 77, 10 are in high demand.

 5. Sales Trend by month of the High Value based on the Customer segment
To understand the sales trends over time for the High Valued SKUs, we can do a bar chart to understand the total sales per month in the year 2026 as represented in the data. This will allow us to observe how sales volumes for these top products have varied across different time periods. We'll focus on the following:

 STEPS
Adding the Value column from the inventory data to the Merged Customer-Sales data.
Selecting Time Periods: Depending on the granularity of the data (daily, weekly, monthly), we can choose appropriate time intervals for analysis.
Trend Analysis by Segment:
Plotting sales trends for the top SKUs in each demographic and geographic location.
Observing seasonal patterns, growth or decline trends, and any significant fluctuations.

 RESULTS
In General, it seems that there were more sales in the month of January than in other months and least being March.

 By Customer Types,  there seems to be variations in sales by Type, in general there are more sales in January for all except for Type 4 customers where most sales came in, in February than other months.

 By Customer Type for each city, for city A there seems to be more sales in January except for type 3 and type 6 customers that have more sales in february. City B shows a trend for more sales in January except for Type 5 and Type 6 Customers that have more sales in February. City C, There seems to be a general flow of more sales happening in February except for Type 1 and Type 2 customers where most sales occurred in January,

 6.Dashboard Design, Drawing Conclusions and Strategic Recommendations
Based on the analysis of product preferences by customer segment, Inventory segmentation and Trend Analysis we can derive insights for production planning and inventory management.
Dashboard design to put all our findings in one place.
 It will contain visualisations for;
Customer types by Location- How popular are our customers in each city?(Popularity of the customers in each city)
Customer types by Quantity sold- How well are the customers buying from us? (Customer Monthly Sales Trend)
Sales Quantity of each Customer type by month- what is the monthly sales by each customer type?(Customer Monthly Sales Trend)
What is the Current Inventory Levels of each SKU-( vizualize the top SKUs by each customers)
What is out of stock and by how many dayscan it be replenished?
What is the current production capacity fro SKU in hours?
Then Cards showing; number of SKUs, Number of Customer, Quantity of SKU sold, Customers Segment.






Insights and Recommendations
Based on the detailed observations you provided, here are the insights and recommendations for SmartHome Solutions Inc.:

 General Insights:

1. Diverse Customer Base: The even distribution across different ages and the presence of various gender groups indicate a wide-ranging customer base.

2. Income and Age Group Correlation: The majority of customers being adults with High income suggests priority to SKUs for this customer sect.

3. Geographic Variability: Different preferences in different cities indicate the need for region-specific strategies.

4. Product Preferences by Segment: Each customer segment (Type 1 to Type 6) shows distinct preferences for certain SKUs, highlighting the importance of tailored product offerings.

5. High Value SKUs: The identification of top SKU bought by cutomers suggests a focused demand for specific products.

6. Sales Variability and Seasonality: Sales varies for different month when in different locations by different Customer Types.

Recommendations:

1. Product Strategy:
   - Diversification: Develop products catering to the diverse needs of different age and income groups.
   - Tailoring for High-Value SKUs: Focus production on top SKU from the customer segment, ensuring they are well-stocked and readily available.

2. Inventory Management:
   - Dynamic Stocking: Adjust inventory levels based on sales trends of high-value SKUs for each customer type.
   - Regional Focus: Tailor inventory to regional preferences, ensuring that popular products in each city are adequately stocked based what each customer prefers.

3. Marketing and Sales:
   - Segment-Specific Campaigns: Develop targeted marketing campaigns for each customer segment (Type 1 to Type 6), focusing on their preferred SKUs.
   - Promotional Timing: Align marketing campaigns with peak sales periods to capitalise on increased demand.

4. Production Planning:
   - Demand-Driven Production: Adjust production schedules based on the sales trends of the top SKUs which are the specific demands of each customer segment.
   - Efficiency in Low-Demand Products: For the lower-value SKUs, which are the least sort after SKUs, adopt a lean production approach to minimise excess inventory.

5. Regional Strategies:
   - Localized Offerings: Customize product offerings and stock levels based on the preferences in Cities A, B, and C.
   - Distribution Optimization: Optimize distribution and logistics to cater to the unique demands of each geographic location.

6. Data-Driven Approach:
   - Continuous Monitoring: Regularly analyze sales data to adapt strategies in real-time.
   - Feedback Loops: Use customer feedback to refine product offerings and marketing strategies.

7. Customer Engagement:
   - Community Building: Engage with different customer groups to build brand loyalty and gain deeper insights into their preferences.
   - Responsive Customer Service: Provide excellent customer service, especially to the dominant adult low-income segment, to foster long-term relationships.

 Implementation Pathway:

- Short-Term: Focus on inventory adjustments and marketing campaigns targeting key segments and high-value SKUs.
- Medium-Term: Develop and refine products based on customer segment feedback and sales data analysis.
- Long-Term: Invest in technology and processes that enhance understanding of customer preferences and market dynamics, enabling agile and responsive supply chain management.

By adopting these recommendations, SmartHome Solutions Inc. can better align its products and services with the diverse needs of its customer base, optimising both customer satisfaction and operational efficiency.




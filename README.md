📊 Customer Churn Analysis Dashboard (Power BI)

This Power BI project analyses customer churn patterns using over 10,000 records from a European banking dataset. The dashboard uncovers churn drivers, demographic trends, credit score behaviour, and simulates potential retention improvements using What-If analysis.

The solution demonstrates key Power BI capabilities, including data modelling, DAX calculations, interactive visuals, drill-through navigation, bookmarks, and dynamic parameter-driven simulations.

📂 Dataset

Raw data files sourced from:
🔗 GitHub Repository (External) – (add original dataset link)

Data includes multiple files:

Bank_Churn – Fact table containing age, tenure, balance, credit score, salary, and churn status

CustomerInfo – Customer surnames

Gender – Gender categories

Geography – Country mapping

Credit Card – Credit card holder status

Active Customers – Active/inactive member status

Exit Customer – Exit vs retained status

🧹 Data Preparation

Cleaning and transformation performed in Power Query Editor, including:

Promoting headers

Changing data types

Removing unnecessary columns (e.g., RowNumber)

Ensuring CustomerId uniqueness

Checking for null or inconsistent values

Merging and modelling dimension tables

Creating a calculated DateMaster table using:

DateMaster = CALENDAR(FIRSTDATE(Bank_Churn[Bank DOJ]), LASTDATE(Bank_Churn[Bank DOJ]))


Added:

Year

Month

Month Name

Custom date hierarchy

🧩 Data Model

This project uses a star schema design, with:

Bank_Churn as the central fact table

Linked dimension tables:

Gender

Geography

CustomerInfo

Credit Card

Exit Customer

Active Customers

DateMaster

✅ One-to-many relationships
✅ Single directional filtering
✅ Dimension-driven slicing
✅ Sorting columns for consistency

🧠 DAX Measures

Key KPIs created:

Total Customers = DISTINCTCOUNT(Bank_Churn[CustomerId])
Exit Customers = CALCULATE(COUNT(Bank_Churn[CustomerId]), 'Exit Customer'[ExitCategory] = "Exit")
Retain Customers = CALCULATE(COUNT(Bank_Churn[CustomerId]), 'Exit Customer'[ExitCategory] = "Retain")
Churn Rate = DIVIDE([Exit Customers], [Total Customers], 0)
Average Age = AVERAGE(Bank_Churn[Age])
Average Balance = AVERAGE(Bank_Churn[Balance])
Average Credit Score = AVERAGE(Bank_Churn[CreditScore])
Average Salary = AVERAGE(Bank_Churn[EstimatedSalary])


Calculated columns include:

Credit score category (Excellent → Poor)

Salary band + sort column

Age group + sort column

⚙️ What-If Parameters

Created using GENERATESERIES():

Tenure Increase

Salary Increase

Credit Score Improvement

These drive simulated metrics:

Simulated Churn Rate

Churn Reduction %

Retention Improvement (%)

Simulated Average Salary / Tenure / Credit Score

Example:

Simulated Churn Rate =
VAR tenureEffect = (1 - ('Tenure Increase'[Tenure Increase Value] * 0.03))
VAR salaryEffect = (1 - ('Salary Increase'[Salary Increase Value] * 0.01))
VAR creditEffect = (1 - ('Credit Score Improvement'[Credit Score Improvement Value] * 0.015))
VAR adjusted = [Churn Rate] * tenureEffect * salaryEffect * creditEffect
RETURN IF(adjusted < 0, 0, adjusted)

📄 Dashboard Pages
✅ Overview Page

KPIs: Churn rate, active/inactive, exits, credit card holders

Customer distribution charts

Time-series line chart with drill down

Slicers for segmentation

✅ Customer Demographics

Age, salary, credit score averages

Gender breakdown

Geography distribution

Salary band and age group insights

✅ Churn Analysis (Bookmarks)

Toggle buttons for: Exit Metrics ↔ Churn Rate

Churn analysis across key segments

✅ Drill-Through Details

Row-level data view

Customer-level attributes

Activated from any segment

✅ What-If Analysis

Parameter slicers

Simulated KPIs

Side-by-side actual vs simulated charts

Interactive scenario modelling

📊 Insights

Key findings include:

Low credit score customers show highest churn

Customers aged 46–60 have largest exit rate

Customers with only 1 product churn the most

Salary impacts churn slightly; credit score and tenure influence it more strongly

Simulated improvements show potential to reduce churn significantly

🚀 Skills Demonstrated

Power BI Dashboard Design

Power Query Data Cleaning

Data Modelling (Star Schema)

DAX Measures and Calculated Columns

What-If Analysis and Forecasting

Drill-Through Pages

Bookmarks and Interactive Buttons

Time Intelligence

Business Insight Communication

📁 Repository Structure
/Dataset
    Bank_Churn.csv
    Geography.csv
    Gender.csv
    CustomerInfo.csv
    ActiveCustomers.csv
    ExitCustomer.csv
    CreditCard.csv

/PowerBI
    Customer_Churn_Dashboard.pbix

README.md

🔗 Project Page

See full project explanation and dashboard screenshots here:
👉 add your website link

✅ How to Use

Download the .pbix file.

Open in Power BI Desktop.

Use slicers and bookmarks to explore insights.

Adjust What-If parameters to simulate retention strategies.

📬 Contact

If you’d like to collaborate or discuss BI/Analytics opportunities:
📧 Email: (your email)
🌐 Portfolio: https://www.manujasprojects.co.uk

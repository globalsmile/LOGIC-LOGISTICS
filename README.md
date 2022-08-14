# Logic Logistics Analysis

<img align="right" alt="Snoring Partner" width="1000" height = "400" src="https://i0.wp.com/leonine.com.ng/new/wp-content/uploads/2020/03/Leonine-Advisory-Page-Routine-Advisory-Services.jpg?resize=1024%2C729&ssl=1">

---


# Table of Contents

- [Introduction](https://github.com/globalsmile/Logic-Logistics-Report#introduction)
- [Problem Statement](https://github.com/globalsmile/Logic-Logistics-Report#Problem-Statement)
- [Data Sourcing](https://github.com/globalsmile/Logic-Logistics-Report#Data-Sourcing)
- [Data Transformation](https://github.com/globalsmile/Logic-Logistics-Report#Data-Transformation)
- [Data Modeling](https://github.com/globalsmile/Logic-Logistics-Report#Data-Modeling)
- [Data Visualization](https://github.com/globalsmile/Logic-Logistics-Report#Data-Visualization)
- [Data Analysis](https://github.com/globalsmile/Logic-Logistics-Report#Data-Analysis)
- [Insights](https://github.com/globalsmile/Logic-Logistics-Report#Insights)
- [Recommendation](https://github.com/globalsmile/Logic-Logistics-Report#Recommendation)
- [Shareable link](https://github.com/globalsmile/Logic-Logistics-Report#Shareable-Link)


---

# Introduction

The goal of this analysis is to perform an exploratory data analysis of the dataset and uncover interesting insights. 


---

# Problem Statement

Build a Power BI Report for Logic Logistics Company and have this report published to Power BI Service, create a Dashboard from the Report and share the Dashboard with your stakeholders.

---

# Data Sourcing

This Datasets is available at https://aka.ms/30DLDATGitHubRepo. 
Locate the "KaggleCarData" csv file.

---

# Data Transformation

Data transformation was done in Power Query and the datasets were loaded into Microsoft Power BI Desktop for modeling.

The logistics data consists of  `9 rows and 1000colums` of observations contained in a table `Car`


The tabulation below shows the `Transactions` table with its column names and their description:
| Column Name | Description |
| ----------- | ----------- |
| Car Name | Describes the name of the car |
| Year | Describes the model year of the car |
| Present Price | Represents the present price of the car |
| Kms Driven | Represents the number of kilometers driven by the car |
| Fuel Type | Describes the fuel type of the car |
| Seller Type | Describes the seller type of the car |
| Transmisson | Describes the transmission type of the car |
| Owner | Describes the owner of the car |
| Selling Price | Represents the sellingpresent price of the car |


Data Cleaning for the dataset was done in power query as follows:

- Changed type of the  `Year` and `owner` from whole number to text only
- Added a custom column with the Power Query M-formula `Table.AddColumn(#"Changed Type1", "Car_ID", each [Car_Name]& "_" &[Year])`
- Duplicated the `Car` table
- Named the duplicated data table `Cars`
- Removed unneccessary columns and turned the `Cars` table into a dimesion table
- Changed the type of the `Car_ID` column from alphanumeric to text only
- Removed duplicates from the `Cars` table
- Removed unneccessary columns and turned the `Car` table into a fact table
- Renamed the `Car` table to `Car Sales` table
- Added a custom column with the Power Query M-formula `Table.AddColumn(#"Reordered Columns", "Profit", each [Present_Price] - [Selling_Price])`  to `Car Sales` table
- Changed the type of the `Profit` column from alphanumeric to text only


---

# Data Modeling

After the dataset was cleaned and transformed, it was ready to be modeled.

- A `many-to-many (*:*) relationship` was created between the `Cars` and the `Car Sales` tables using the `Car_ID` column in each of the tables

---

# Data Visualization

Data visualization for the datasets was done using Microsft Power BI Desktop:

- The `Dashboard`: Shows the Average number of kilometers driven by the cars, Total present price cars, Total profit made from the cars, etc.

Figure 1 shows visualizations from  the `Dashboard`

| Figure 1 |
| ----------- |
| ![image](https://user-images.githubusercontent.com/106287208/183564662-5a1714c7-610e-45f7-be17-6ae94c6a4628.png) |

---

# Data Analysis

Measures used in visualization are:

- Avg Kms = `AVERAGEX('Car Sales', 'Car Sales'[Kms_Driven])`
- Total Present Price = `SUMX('Car Sales','Car Sales'[Present_Price])`
- Total Profit = `SUMX('Car Sales','Car Sales'[Profit])`


As shown from [Data Visualization](https://github.com/globalsmile/Logic-Logistics-Report#Data-Visualization), It can be deducted that:

- The average number of kilometers driven by the cars is `36k`
- The total present price of the cars is `$1.05bn`
- The total profit made from the cars is  `$70.27m`

---

# Insights

As shown by [Data Visualization](https://github.com/globalsmile/Logic-Logistics-Report#Data-Visualization), It can be deducted that:

- The car with the highest profit is `city` at `$6.3m` 
- The car with the most driven kilometer is a `2008 Activa 3g`

---

# Recommendation

The `city` car sells more than the other cars, perhaps more `city` cars should be mad available.

---

# Shareable Link

You can interact with the report here: 

https://badmus67-my.sharepoint.com/:x:/g/personal/mohammed_badmus67_onmicrosoft_com/EfKDjq3DT4RJhenoDiMh8PMBDZlr7QphTXE5LavoYkjkRw?e=Ak5sqZ

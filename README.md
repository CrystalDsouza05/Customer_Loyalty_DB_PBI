
# Customer Satisfaction & Loyalty Dashboard

### 📊 Dashboard Link Coming Soon...

---

## 📌 Problem Statement

I built this Power BI dashboard for the **Customer Satisfaction and Loyalty Analytics Challenge.**

As a data analyst at OmniRetail, I analyzed 2024 customer feedback to understand what drives satisfaction, support engagement, and repeat purchases.
The dashboard uncovers key patterns across regions, income levels, age groups, and loyalty tiers to support better retention strategies.

Snap of Dashboad Pages (3) ,

![image](https://github.com/user-attachments/assets/48ce50eb-6ef0-47ec-aab7-d9e9912ee40d)

![image](https://github.com/user-attachments/assets/dd78a8eb-62ca-4312-a9a6-936d751f2f61)

![image](https://github.com/user-attachments/assets/02accf50-c462-4c20-a050-7ad5fcc4701d)


More Information ToolTip Sample

![image](https://github.com/user-attachments/assets/8c6fbe84-f54a-46fc-acfe-d08ea9be8a30)

Dashboard Theme 

![image](https://github.com/user-attachments/assets/7898e991-0cd1-4747-b5a5-4eb0ab6a23c6)

Dashboard Background

![PAGE 1 (9)](https://github.com/user-attachments/assets/b089231a-3abe-42b5-8ccf-feca323c64b2)

---

## 🧾 Pages Included

| Page No. | Page Title             |
|----------|------------------------|
| 1        | Customer Overview      |
| 2        | Behavior Insights      |
| 3        | Risk Analysis          |

---

## 🧩 Key Visuals and Features

### ✅ **Customer Overview**
- **KPI Cards** showing total customers, average satisfaction score, repeat rate, support % and at-risk %
- **Donut Charts** for satisfaction by age and loyalty tier
- **Bar Chart** highlighting top satisfaction factors (Packaging, Brand Reputation, Ease of Use)
- **Risk % by Age Group** visual to spot vulnerable age segments

### ✅ **Behavior Insights**
- **Demographic Distribution** by gender and age group
- **Support Interaction** split (Yes vs No)
- **Geo Map** of customer distribution across the U.S.
- **City-wise Satisfaction Chart** comparing average scores by city

### ✅ **Risk Analysis**
- **Customer Segmentation Treemap** by Age + Loyalty level
- **Pie Chart** showing customers with and without purchase history
- **Watchlist Table**: Lists high-risk or silent loyal customers with satisfaction below 5 but high loyalty

---

## 📐 DAX Measures & Calculated Columns

### 🔹 **Key Measures**

```dax
Total Customers = DISTINCTCOUNT(Data[Customer_ID])

Avg Score = AVERAGE(Data[Satisfaction_Score])

Female % =
DIVIDE(CALCULATE(COUNT(Data[Customer_ID]), Data[Gender] = "Female"), [Total Customers])

Male % =
DIVIDE(CALCULATE(COUNT(Data[Customer_ID]), Data[Gender] = "Male"), [Total Customers])

Repeat_Customer_Percent =
DIVIDE(CALCULATE([Total Customers], Data[Purchase_History] = "Yes"), [Total Customers])

Support_Contacted_Percent =
DIVIDE(CALCULATE([Total Customers], Data[Support_Contacted] = "Yes"), [Total Customers])

At_Risk_Count =
CALCULATE(COUNTROWS(Data), Data[Is_At_Risk] = "Yes")

At_Risk_Percent =
DIVIDE(CALCULATE([Total Customers], Data[Is_At_Risk] = "Yes"), [Total Customers])

Silent_Loyal =
CALCULATE(COUNTROWS(Data), FILTER(Data, Data[Loyalty_Level] = "High" && Data[Satisfaction_Score] < 5))

High_Loyalty_Percent =
DIVIDE(CALCULATE(SUM(Data[Satisfaction_Score]), Data[Loyalty_Level] = "High"), CALCULATE(SUM(Data[Satisfaction_Score])))

Medium_Loyalty_Percent =
DIVIDE(CALCULATE(SUM(Data[Satisfaction_Score]), Data[Loyalty_Level] = "Medium"), CALCULATE(SUM(Data[Satisfaction_Score])))

Low_Loyalty_Percent =
DIVIDE(CALCULATE(SUM(Data[Satisfaction_Score]), Data[Loyalty_Level] = "Low"), CALCULATE(SUM(Data[Satisfaction_Score])))
```

---

### 🔸 **Calculated Columns**

```dax
Customer_Segment = Data[Age_Group] & "-" & Data[Loyalty_Level]

Is_At_Risk =
IF(Data[Satisfaction_Score] < 4 && Data[Support_Contacted] = "No", "Yes", "No")
```

---

## 📊 Data Tables & Model

- **Main Table:** `Data` (customer info, satisfaction score, loyalty, support, purchase history)
- **Location Table:** `Location` (city, state, region, lat-long mapping)

- **Relationships:**
  - `Data[City]` → `Location[City]` (Many-to-One)
  - Region and Lat-Long used in map visuals

Data Model
![image](https://github.com/user-attachments/assets/017935e7-faa9-4d4e-8b1f-c9b070b1af4d)

---

## 🔍 Some Insights Uncovered

- Adults have the highest at-risk percentage (22.9%)  
- Customers under age 55 are more satisfied overall  
- Packaging and brand reputation are key satisfaction drivers  
- 15% of all customers are at risk, most of whom didn’t contact support  
- 32% of customers are highly loyal — but not all are satisfied  

---

## 🚀 Tech Stack

- Power BI Desktop  
- DAX & Power Query  
- GitHub for versioning  
- Excel for data cleaning  
- ZoomCharts for advanced visuals  
- Custom Icons & Formatting in PowerPoint  
- Figma and PowerPoint for designing. 

---

📬 _Feel free to connect with me if you have feedback, questions, or want to collaborate on data storytelling!_



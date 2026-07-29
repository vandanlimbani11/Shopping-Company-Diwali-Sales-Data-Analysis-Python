# Shopping-Company-Diwali-Sales-Data-Analysis-Python
📌 Project Overview

The Diwali festival is one of the most important shopping periods in India. This project uses Python to analyze customer transactions and uncover patterns that can support better marketing, customer targeting, inventory planning, and sales strategy during the festive season.
The analysis explores customer behaviour across:
Gender
Age group
Marital status
State and geographical zone
Occupation
Product category
Number of orders
Purchase amount

📊 Dataset Snapshot
Metric	Value
Raw records	11,251
Raw columns	15
Clean records	11,239
Analysis columns	13
Missing `Amount` values removed	12
Approximate total sales	₹106.25 million
Approximate total orders	27,981
Average customer age	35.41 years
Average transaction amount	₹9,453.61
Transaction amount range	₹188–₹23,952

Column	Description
`User_ID`	Unique customer identifier
`Cust_name`	Customer name
`Product_ID`	Unique product identifier
`Gender`	Customer gender
`Age Group`	Customer age bracket
`Age`	Customer age
`Marital_Status`	Encoded marital status
`State`	Customer's state
`Zone`	Geographical zone
`Occupation`	Customer's profession
`Product_Category`	Category of the purchased product
`Orders`	Number of orders
`Amount`	Purchase amount in Indian rupees
</details>

🛠️ Technologies Used
Technology	Purpose
Python	Analysis and programming
Pandas	Data loading, cleaning, grouping, and aggregation
NumPy	Numerical operations
Matplotlib	Chart creation and customization
Seaborn	Statistical data visualization
Jupyter Notebook	Interactive analysis environment

🔄 Analysis Workflow
```mermaid
flowchart TD
    A["Load Diwali sales CSV"] --> B["Inspect shape, columns and data types"]
    B --> C["Remove empty columns"]
    C --> D["Detect and remove missing values"]
    D --> E["Convert Amount to integer"]
    E --> F["Perform exploratory data analysis"]
    F --> G["Compare customer segments"]
    G --> H["Extract business insights"]


View the data-cleaning steps
The notebook performs the following preparation before analysis:
Imports the CSV file using `latin1` encoding.
Inspects the dataset with `shape`, `head()`, `info()`, and `describe()`.
Removes the completely empty `Status` and `unnamed1` columns.
Detects 12 missing values in the `Amount` column.
Removes rows containing missing values.
Converts `Amount` from `float` to `int`.
Verifies that the cleaned dataset has 11,239 complete records.
```python
df.drop(["Status", "unnamed1"], axis=1, inplace=True)
df.dropna(inplace=True)
df["Amount"] = df["Amount"].astype("int")
```


🔍 Exploratory Data Analysis
1. Gender Analysis
The analysis compares the number of buyers and total purchase amount by gender.
> **Finding:** Female customers placed more orders and spent more money than male customers.
```python
sales_gender = (
    df.groupby("Gender", as_index=False)["Amount"]
      .sum()
      .sort_values(by="Amount", ascending=False)
)
sns.barplot(data=sales_gender, x="Gender", y="Amount")
```
2. Age-Group Analysis
Customer activity is compared across age groups and further divided by gender.
> **Finding:** Customers aged **26–35**, especially women, form the strongest buyer segment.
3. State Analysis
The analysis compares states by total orders and total purchase amount.
> **Finding:** **Uttar Pradesh** received the highest number of orders, while **Telangana** received the fewest in this dataset.
4. Marital-Status Analysis
Sales are grouped by marital status and gender to identify differences in purchasing behaviour.
> **Finding:** The strongest spending segment is driven by female customers, with marital status providing an additional targeting dimension.
5. Occupation Analysis
The project studies order volume and sales amount across different professions.
> **Business use:** Occupation-level insights can help the company create more focused promotions for high-spending professional groups.
6. Product-Category Analysis
Product categories are compared using both order volume and total sales.
> **Finding:** **Clothing & Apparel** received more orders, but customers spent the highest amount in the **Food** category.
This distinction is important: a category can lead in transaction volume without generating the highest revenue.

💡 Key Business Insights
Business Opportunity
Gender
Women contribute more orders and sales than men.
Prioritize women-focused festive campaigns.
The 26–35 age group is the most active, particularly female customers.
Build offers around the preferences of young working adults.
Uttar Pradesh produces the highest order volume.
Allocate more advertising and inventory to strong regional markets.
Clothing & Apparel leads in orders, while Food leads in spending.
Use apparel for volume and food products for revenue growth.
Gender, age, marital status, state, and occupation reveal distinct buyer groups.
Create personalized campaigns instead of one general promotion.

👤 Target Customer Profile
Female customer
    └── Age: 26–35
        └── Located in a high-performing state such as Uttar Pradesh
            └── Interested in Clothing, Apparel and Food products
```
🚀 Business Recommendations
Target women aged 26–35 with personalized Diwali campaigns.
Maintain higher inventory for Clothing & Apparel because of its strong order volume.
Promote premium or bundled Food products to capitalize on their higher sales value.
Increase marketing investment in high-performing states such as Uttar Pradesh.
Create occupation-based and marital-status-based customer segments.
Use cross-selling offers between popular and high-value product categories.
Compare campaign performance by state and customer segment in future analysis.

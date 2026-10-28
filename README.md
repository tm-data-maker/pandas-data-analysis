📊 Pandas Data Analysis & Manipulation Repository
Welcome to the Pandas Learning & Data Analysis Repository! This project was created as part of the Data Technician Skills Bootcamp. It serves as a comprehensive guide and portfolio showcasing data manipulation, cleaning, exploratory analysis, and visualization using Python and Pandas.
The contents are structured to guide beginners step-by-step from foundational concepts to practical real-world data analysis on retail and sales datasets.

📑 Table of Contents
Repository Structure
Notebook Breakdowns & Examples
1. PandasDataFrames_01.ipynb – Fundamentals
2. PandasDataFrames_02.ipynb – Indexing & Filtering
3. PandasDataFrames_03.ipynb – Data Cleaning
4. Sales_Data_Analysis.ipynb – Aggregation & Grouping
Key Methods Summary
Learning Outcomes
How to Run

📁 Repository Structure
.
├── 📄 README.md                          # Repository documentation & guide
├── 📓 PandasDataFrames_01.ipynb          # Intro to DataFrames & basic properties
├── 📓 PandasDataFrames_02.ipynb          # Slicing, indexing (.loc/.iloc) & filtering
├── 📓 PandasDataFrames_03.ipynb          # Handling missing values & data cleaning
├── 📓 Sales_Data_Analysis.ipynb          # Groupby, aggregation & data visualization
└── 📊 datasets/                          # Project CSV datasets
    ├── penguins.csv
    ├── student.csv
    └── sales_data.csv

🔍 Notebook Breakdowns & Examples

1️⃣ PandasDataFrames_01.ipynb — Intro to Pandas & DataFrame Basics
Focus: Understanding core Pandas structures (Series & DataFrames), loading data, and extracting initial statistical summaries.
💡 Key Concepts & Code Examples:
Creating a DataFrame from a Dictionary:
import pandas as pd

# Creating a simple dataset manually
data = {
    'Product': ['Laptop', 'Mouse', 'Monitor', 'Keyboard'],
    'Price': [1200, 25, 300, 75],
    'Stock': [15, 100, 45, 60]
}
df = pd.DataFrame(data)
print(df)
Inspecting DataFrame Properties:
df.info()        # Overview of columns, data types, and non-null counts
df.shape         # Returns (rows, columns) tuple, e.g., (1000, 8)
df.describe()    # Summary statistics (mean, std, min, max, quartiles)
Creating Calculated Columns:
# Calculating Total Stock Value
df['Total_Value'] = df['Price'] * df['Stock']

2️⃣ PandasDataFrames_02.ipynb — Indexing, Slicing & Filtering
Focus: Mastering precise data selection techniques using .loc[], .iloc[], and conditional logic.
💡 Key Concepts & Code Examples:
Label-Based Indexing with .loc[]: Used to select specific rows and columns by their labels/names.
# Select rows where 'Price' > 100 and only display 'Product' and 'Price' columns
high_value = df.loc[df['Price'] > 100, ['Product', 'Price']]
Position-Based Indexing with .iloc[]: Used to select rows and columns by integer index position (0-indexed).
# Select first 5 rows and first 3 columns
subset = df.iloc[0:5, 0:3]
Boolean Filtering (Multiple Conditions): Combining conditions using & (AND) and | (OR).
# Filter products with Price > 50 AND Stock < 50
filtered_df = df[(df['Price'] > 50) & (df['Stock'] < 50)]
Sorting Data (.sort_values()):
# Sort dataset by Price in descending order
sorted_df = df.sort_values(by='Price', ascending=False)

3️⃣ PandasDataFrames_03.ipynb — Data Cleaning & Missing Values
Focus: Identifying null/missing values, imputing missing data, and handling corrupted values.
💡 Key Concepts & Code Examples:
Detecting Missing Data (.isna() / .isnull()):
# Count total missing values per column
print(df.isna().sum())

# Percentage of missing data per column
missing_pct = (df.isna().sum() / len(df)) * 100
print(missing_pct)
Filling Missing Values (.fillna()):
# Fill missing 'Price' values with the column mean
df['Price'] = df['Price'].fillna(df['Price'].mean())

# Fill missing text categories with 'Unknown'
df['Category'] = df['Category'].fillna('Unknown')
Dropping Missing Data (.dropna()):
# Remove rows where essential identifiers are missing
cleaned_df = df.dropna(subset=['Product_ID'])

4️⃣ Sales_Data_Analysis.ipynb — Data Aggregation & Grouping
Focus: Grouping datasets by categorical variables, performing multi-metric calculations, and building basic plots.
💡 Key Concepts & Code Examples:
Group Analysis (.groupby()):
# Calculate total sales revenue per product category
category_sales = df.groupby('Category')['Total_Value'].sum().reset_index()
print(category_sales)
Multiple Aggregations (.agg()):
# Calculate mean price and total units sold per region
region_summary = df.groupby('Region').agg({
    'Price': 'mean',
    'Stock': 'sum'
}).rename(columns={'Price': 'Avg_Price', 'Stock': 'Total_Units'})
Built-in Visualization (matplotlib integration):
import matplotlib.pyplot as plt

# Plotting total sales by category as a bar chart
category_sales.plot(kind='bar', x='Category', y='Total_Value', color='skyblue')
plt.title('Total Sales Revenue by Category')
plt.xlabel('Category')
plt.ylabel('Revenue ($)')
plt.tight_layout()
plt.show()

🛠️ Key Pandas Methods Quick Reference
Method
Description
Example Usage
pd.read_csv()
Load CSV file into a DataFrame
df = pd.read_csv('data.csv')
.head(n)
View first n rows
df.head(5)
.info()
Summary of structure & data types
df.info()
.loc[]
Select rows/cols by label
df.loc[df['Age'] > 25, 'Name']
.iloc[]
Select rows/cols by integer index
df.iloc[0:10, 1:3]
.isna().sum()
Count missing values
df.isna().sum()
.fillna()
Replace missing values
df['Age'].fillna(df['Age'].median())
.dropna()
Remove missing values
df.dropna()
.groupby()
Group rows by column values
df.groupby('Category').mean()
.sort_values()
Sort rows by values
df.sort_values(by='Sales', ascending=False)


🎓 Learning Outcomes
By completing this repository, I have demonstrated the ability to:
✅ Load, inspect, and understand complex structured datasets.
✅ Perform robust data cleaning, handling missing (NaN) values effectively.
✅ Execute precise filtering, conditional slicing, and index manipulation using .loc[] and .iloc[].
✅ Aggregate and pivot data using .groupby() to generate actionable insights.
✅ Visualize key trends and distributions directly from Pandas DataFrames.

🚀 How to Run These Notebooks
Google Colab (Recommended):
Click on any .ipynb file in this repository.
Click the "Open in Colab" badge at the top of the notebook.
Local Environment (Jupyter Notebook / VS Code):
# Clone repository
git clone https://github.com/your-username/python-pandas-exercises.git

# Navigate into project directory
cd python-pandas-exercises

# Launch Jupyter Notebook
jupyter notebook


eof

---

### Что сделано в этой версии:
1. **Детальные примеры кода (`Python`):** Добавлены реальные фрагменты кода для каждого блока (`loc`/`iloc`, `fillna`, `dropna`, `groupby`, `describe`, `plot`).
2. **Справочная таблица (Quick Reference):** Собрана сводка главных команд Pandas с их понятным описанием для быстрого повторения.
3. **Объяснения для новичка:** Каждая функция сопровождена комментарием, что именно она делает на человеческом языке.
4. **Инструкция по запуску:** Добавлен блок с `git clone` и кнопками Colab.

Можем сразу разобрать любой блок кода подробнее или перейти к оформлению самого блокнота!


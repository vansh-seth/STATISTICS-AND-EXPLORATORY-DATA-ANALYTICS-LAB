# Diwali Sales Data Analysis

This repository contains Python scripts for analyzing Diwali sales data. The analysis includes data cleaning, visualization, and generating insights based on gender, age group, state, marital status, occupation, and product categories.

---

## Requirements

To run the scripts in this repository, you need the following Python libraries:
- `pandas`
- `matplotlib`
- `seaborn`

Install the required packages using:
```bash
pip install pandas matplotlib seaborn
```

---

## Dataset

The dataset used is named `Diwali_Sales_Data.csv`. It contains information about customer demographics, sales, and orders during the Diwali season.

### Key Columns
- `Gender`: Gender of the customer (Male/Female).
- `Age Group`: Age group of the customer.
- `Marital_Status`: Marital status (Married/Unmarried).
- `State`: Customer's state.
- `Occupation`: Customer's profession.
- `Product_Category`: Purchased product category.
- `Amount`: Purchase amount.
- `Orders`: Number of orders.

---

## Steps in the Script

### 1. **Data Cleaning**
- **Drop Irrelevant Columns**: Columns `Status` and `unnamed1` are removed.
- **Handle Missing Data**: Rows with missing values are dropped.
- **Type Conversion**: `Amount` column is converted to integer.
- **Renaming Columns**: `Marital_Status` is renamed to `Shaadi` (optional).

---

### 2. **Gender Distribution**
- Distribution of male and female customers using a bar chart.
- Calculation of total purchase amounts by gender.

### 3. **Age Group Analysis**
- Total purchase amounts per age group visualized using a bar chart.
- Comparison of purchase amounts by age group and gender.

### 4. **State Analysis**
- Top 10 states by total sales visualized using a bar chart.
- Top 10 states by the number of orders.

### 5. **Marital Status Analysis**
- Count of married and unmarried customers.
- Total purchase amounts based on gender and marital status.

### 6. **Occupation Analysis**
- Purchase amounts by occupation, displayed as a bar chart.

### 7. **Product Category Analysis**
- Top 10 product categories based on sales visualized in a bar chart.

---

## Visualizations

1. **Gender Distribution**:
   - Bar chart representing the number of male and female customers.
   - Visualization of total sales by gender.

2. **Age Group Analysis**:
   - Total sales per age group.
   - Comparison of sales between males and females across age groups.

3. **State Analysis**:
   - Top 10 states by sales.
   - Top 10 states by the number of orders.

4. **Marital Status**:
   - Bar chart for marital status distribution.
   - Sales based on gender and marital status.

5. **Occupation**:
   - Bar chart showing purchase amounts for different occupations.

6. **Product Category**:
   - Top 10 product categories visualized as a bar chart.

---

## Usage

1. Place the `Diwali_Sales_Data.csv` file in the working directory.
2. Run the script in a Python environment.
3. Visualizations and outputs will be displayed inline or saved as per your environment.

---

## Example Output

### Gender Distribution
![image](https://github.com/user-attachments/assets/1045f403-4db2-4c7c-a552-493a148bdb15)

### Top States by Sales
![image](https://github.com/user-attachments/assets/4e117e2e-c3c3-46cb-bb0a-408706450f98)


---

## Contributions
Feel free to contribute by adding new analyses or improving visualizations.

---

## License
This project is under the MIT License.

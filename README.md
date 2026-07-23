# Customer Shopping Behavior Analysis

## 📌 Project Overview
This project delivers an end-to-end data analytics solution evaluating customer shopping behavior. Utilizing transactional data from **3,900 purchases** across multiple product categories, the project uncovers actionable insights regarding spending patterns, customer segmentation, product preferences, and subscription retention. 

The workflow transitions seamlessly from **data cleaning and feature engineering in Python**, to **relational database storage and analytical querying in MySQL**, concluding with interactive **data visualization in Power BI**.

---

## 📊 Dataset Summary
* **Scale**: 3,900 rows | 18 columns
* **Key Features**:
  * **Demographics**: Age, Gender, Location, Subscription Status
  * **Transactional Details**: Item Purchased, Category, Purchase Amount, Season, Size, Color
  * **Marketing & Behavior**: Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Shipping Type
* **Data Quality**: Identified and handled 37 missing values in the `Review Rating` column.

---

## 🛠️ Tech Stack
* **Data Prep & Cleaning**: Python (`pandas`, `numpy`)
* **Database Management**: MySQL
* **Database Integration**: `SQLAlchemy` / `mysql-connector-python` or `PyMySQL`
* **Visualization & BI**: Power BI

---

## 🚀 Project Workflow

### 1. Exploratory Data Analysis & ETL (Python)
Data preparation and pipeline building were completed in a Python environment:
* **Exploration**: Used `df.info()` and `df.describe()` to evaluate data structure and summary statistics.
* **Missing Value Imputation**: Imputed the 37 missing `Review Rating` values using the **median rating** calculated per product category to maintain statistical consistency.
* **Standardization**: Converted all column headers to `snake_case`.
* **Feature Engineering**:
  * Generated an `age_group` column by binning customer ages.
  * Calculated a numeric `purchase_frequency_days` field from purchase history details.
* **Deduplication**: Checked redundancy between `discount_applied` and `promo_code_used`; dropped `promo_code_used` to maintain tidy data.
* **Database Migration**: Established a connection to MySQL and programmatically loaded the cleaned DataFrame into a structured SQL table.

---

### 2. Structured Analysis (MySQL)
Key business questions were addressed using MySQL relational queries. Below are the key findings from the analytical runs:

#### 📈 Revenue & Demographics
* **Revenue by Gender**: Male customers generated **$157,890**, while female customers generated **$75,191**.
* **Revenue by Age Group**: 
  * *Young Adults*: $62,143
  * *Middle-aged*: $59,197
  * *Adults*: $55,978
  * *Seniors*: $55,763

#### 🛒 Subscriptions & Shipping
* **Subscribers vs. Non-Subscribers**: Non-Subscribers ($170,436 total revenue) hold a slightly higher average spend ($59.87) than Subscribers ($59.49 average spend; $62,645 total revenue).
* **Shipping Preference Spend**: Customers choosing Express shipping spent slightly more on average (**$60.48**) compared to those using Standard shipping (**$58.46**).

#### 🏷️ Customer Behavior & Promotional Dependencies
* **Customer Segmentation**: Based on purchase history, customers were segmented into:
  * **Loyal**: 3,116 customers
  * **Returning**: 701 customers
  * **New**: 83 customers
* **Discount-Dependent Products**: Identified items purchased most frequently with active discounts:
  1. **Hat** (50.00% discounted purchases)
  2. **Sneakers** (49.66%)
  3. **Coat** (49.07%)
  4. **Sweater** (48.17%)
  5. **Pants** (47.37%)
* **Top Products per Category**:
  * *Accessories*: Jewelry (171 orders), Sunglasses (161 orders), Belt (161 orders)
  * *Clothing*: Blouse (171 orders), Pants (171 orders), Shirt (169 orders)
  * *Footwear*: Sandals (160 orders), Shoes (150 orders), Sneakers (145 orders)
  * *Outerwear*: Jacket (163 orders), Coat (161 orders)

---

### 3. Interactive Visualizations (Power BI)
An interactive executive dashboard was constructed in Power BI to monitor key metrics (KPIs) and filter transactions by subscriber status, location, gender, and category.

#### Executive Summary Tab
* Shows high-level KPIs: **$60 Average Purchase Amount**, **3.75 Average Review Rating**, and **3.9K Total Customers**.
* Includes visual category performance splits (with **Clothing** dominating both revenue and volume) and demographic slices by age.

#### Behavior Deep Dive Tab
* Tracks seasonal revenue trends, showing consistent distribution across Fall, Spring, Winter, and Summer.
* Showcases purchase method allocations alongside purchase category trends across distinct age groups.

---

## 💡 Strategic Business Recommendations

1. **Maximize Subscription Value Proposition**: Since subscribers and non-subscribers display similar average spend profiles, incentivize subscriptions by introducing exclusive perks (e.g., free express shipping, member-only discounts) to drive up subscriber purchase frequency.
2. **Nurture High-Value Segments**: Leverage the massive base of **Loyal** customers (3,116) by launching a tiered loyalty program. Focus targeted retention campaigns on migrating **Returning** customers (701) into the Loyal tier.
3. **Optimize Promotional Strategies**: Items like *Hats* and *Sneakers* are highly discount-dependent (~50% bought with discounts). Gradually transition from flat discounts to bundled offers to preserve profit margins on these items.
4. **Targeted Seasonal & Demographical Campaigns**: Focus marketing spend on **Young Adults** (the highest revenue-generating cohort) and promote top-performing category items like *Jewelry*, *Blouses*, and *Sandals*.

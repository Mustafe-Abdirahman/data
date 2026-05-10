Amazon Product Sales Analysis
This project focuses on performing a comprehensive Data Cleaning and Exploratory Data Analysis (EDA) on an Amazon sales dataset. The goal is to transform raw, "dirty" data into a structured format to uncover insights regarding pricing strategies, product popularity, and revenue generation.

🛠️ Data Cleaning Process
The initial dataset contained several inconsistencies, including non-numeric characters in price columns and duplicate entries that could skew results.

1. Formatting & Type Conversion
We stripped currency symbols (like ₹ or $) and percentage signs to convert strings into float values for mathematical computation.

Python
# Removing unwanted characters and converting to numeric
df['discounted_price'] = df['discounted_price'].astype(str).str.replace(r'[^\d.]', '', regex=True).astype(float)
df['actual_price'] = df['actual_price'].astype(str).str.replace(r'[^\d.]', '', regex=True).astype(float)
df['discount_percentage'] = df['discount_percentage'].astype(str).str.replace('%','', regex=True).astype(float)

# Handling ratings and review counts
df['rating'] = pd.to_numeric(df['rating'], errors='coerce')
df['rating_count'] = pd.to_numeric(df['rating_count'], errors='coerce')
2. Handling Duplicates & Missing Values
To ensure data integrity, we identified and removed duplicate reviews and filled missing values in the rating_count column.

!> Key Metric: We identified 114 duplicate products and 271 duplicate reviews, which were pruned to ensure each customer's voice is represented only once.

📊 Statistical Summary
After cleaning, the dataset profile shifted significantly. The summary statistics below provide a high-level view of the pricing and rating distributions.



Average Discount: The mean discount percentage is approximately 46.5%, showing a highly competitive pricing environment.

Customer Satisfaction: The mean rating sits at 4.08, indicating a generally positive sentiment across the product range.

📈 Key Insights & Exploratory Analysis
Which products contribute the most to total sales?
By calculating revenue (Product of discounted_price and a proxy for volume), we identified the top-performing electronics. Large-screen TVs and premium smartphones dominate the revenue share.

!

What is the product volume by category?
The analysis reveals that Computers & Accessories and Electronics are the most densely populated categories, with USB Cables being the highest volume individual product type.

!
🚀 Conclusion
The cleaning process reduced the noise in the data, allowing for a clear visualization of sales trends. The high volume of affordable accessories like cables, contrasted with high-revenue items like 4K Smart TVs, suggests a "Long Tail" retail strategy where a few high-value items and many low-value items balance the portfolio.

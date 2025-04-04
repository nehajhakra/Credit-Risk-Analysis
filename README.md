📊 Credit Risk Analysis using SQL & Python
🔍 Analyze loan approvals, customer transactions, and payment behaviors to assess credit risk.

🚀 Project Overview
Credit risk analysis is crucial for financial institutions to determine whether a customer is likely to repay loans on time or default. This project explores real-world banking data to extract insights using:
✔ SQL – For database creation, queries, and risk categorization.
✔ Python (Pandas, Matplotlib, Seaborn) – For data visualization and deeper analysis.

🔗 Repository Structure
📁 data/ – Contains raw datasets (customers.csv, loans.csv, transactions.csv, payments.csv).
📁 sql_queries/ – SQL scripts for database setup, queries, and insights.
📁 notebooks/ – Python scripts for data analysis and visualization.
📁 visualizations/ – Saved plots and graphs generated from analysis.
📄 README.md – You're here!

📂 Datasets Used
Dataset	Description
customers.csv	Customer details (age, gender, income, employment type, credit score).
loans.csv	Loan details (loan type, amount, interest rate, approval status).
transactions.csv	Transaction history (amount, type, date).
payments.csv	Loan payment records (due dates, paid dates, statuses).
🔍 SQL Analysis – Key Insights
✅ Total Loan Amount & Average Interest Rate
✅ Loan Approval vs. Rejection Trends
✅ Customers Who Haven’t Taken Loans (LEFT JOIN)
✅ Credit Risk Categorization using CASE Statements
✅ Top 5 Borrowers (ROW_NUMBER Window Function)

📌 Example Query – Identifying High-Risk Customers:

sql
Copy
Edit
WITH high_risk_customers AS (
    SELECT c.customer_id, c.name, c.credit_score, COUNT(p.payment_id) AS missed_payments
    FROM customers c
    LEFT JOIN payments p ON c.customer_id = p.customer_id AND p.status = 'Missed'
    GROUP BY c.customer_id, c.name, c.credit_score
    HAVING c.credit_score < 600 AND COUNT(p.payment_id) > 3
)
SELECT * FROM high_risk_customers;
📊 Python Data Analysis & Visualizations
📌 Key Findings from Data Analysis:
📈 Loan approval rates – Comparing different loan types.
📉 Customer age & income distribution – Who is more likely to borrow?
💰 Transaction trends – High-value vs. low-value transactions.
📊 Loan repayment trends – Who repays on time vs. who defaults?

🔹 Loan Type Distribution:

python
Copy
Edit
import seaborn as sns
import matplotlib.pyplot as plt

sns.countplot(x="loan_type", data=loans, palette="viridis")  
plt.title("Loan Type Count")  
plt.xticks(rotation=45)  
plt.show()
🔹 Customer Age Distribution:

python
Copy
Edit
plt.hist(customers["age"], bins=10, color="lightcoral", edgecolor="black")  
plt.title("Age Distribution of Customers")  
plt.xlabel("Age")  
plt.ylabel("Count")  
plt.show()
🛠️ How to Run the Project
1️⃣ Clone the Repository

bash
Copy
Edit
git clone https://github.com/yourusername/credit-risk-analysis.git
cd credit-risk-analysis
2️⃣ Set Up the SQL Database

Import credit_risk_analysis.sql into MySQL.

Run sql_queries/queries.sql for analysis.

3️⃣ Run Python Analysis

bash
Copy
Edit
python credit_risk_analysis.py
🎯 Future Improvements
✔ Feature Engineering for Better Risk Prediction
✔ Machine Learning Model for Loan Default Prediction
✔ Interactive Dashboards using Tableau or Streamlit

📌 This project is a great example of using SQL and Python for financial data analytics.

⭐ Feel free to fork, contribute, or connect with me on LinkedIn! 🚀


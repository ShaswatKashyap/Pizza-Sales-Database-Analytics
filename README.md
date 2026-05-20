# Pizza Sales Performance & Inventory Analytics (SQL Server & Power BI)

## 📌 Executive KPIs (Key Performance Indicators)
By executing robust data aggregation queries across the transactional database, the following core business foundations were established:
* **Total Revenue:** $817,860.05
* **Average Order Value:** $38.31
* **Total Volume Sold:** 21,350 unique orders
* **Average Volume Per Order:** 2.32 pizzas

---

## 🔍 Advanced Business Analytics & Product Performance

### A. Market Share Breakdown by Pizza Category & Size
To analyze consumer demand distributions, subqueries were engineered to compute dynamic revenue percentage weights:
* **Category Distribution:** Classic leads the market share at **26.91%** ($220,053.10), followed closely by Supreme (**25.46%**), Chicken (**23.96%**), and Veggie (**23.68%**).
* **Size Distribution:** Large (L) pizzas dominate operations, accounting for **45.89%** of total revenue, whereas Extra Large (XL) represents a tiny niche at just **1.72%**.

```sql
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) AS total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category;

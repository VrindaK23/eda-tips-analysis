# Tips Dataset Analysis  

## 📌 Project Overview  
This project performs **Exploratory Data Analysis (EDA)** on the classic **Seaborn Tips dataset**, which records restaurant bills and tips. The goal is to uncover patterns in tipping behavior based on day of the week, smoker status, and bill amounts.  

---

## 📂 Dataset Description  
- **Source**: Built-in Seaborn dataset  
- **Rows & Columns**: Contains information about total bills, tips, gender, smoker status, day, time, and group size.  
- **Missing Values**: None  

**Features:**  
- `total_bill` → Total bill amount in dollars  
- `tip` → Tip amount in dollars  
- `sex` → Gender of the customer  
- `smoker` → Whether the customer is a smoker (Yes/No)  
- `day` → Day of the week (Thur, Fri, Sat, Sun)  
- `time` → Meal time (Lunch/Dinner)  
- `size` → Size of the group  

---

## 📝 Analysis  

### 1. Average Tip  
```python
tips["tip"].mean()
````

**Result**: ≈ **3.00 USD**

---

### 2. Do Smokers Tip More?

```python
tips.groupby("smoker")["tip"].mean()
```

| Smoker | Avg Tip |
| ------ | ------- |
| Yes    | 3.01    |
| No     | 2.99    |

👉 Smokers tipped *slightly more*, but difference is negligible.

---

### 3. Tipping by Day

```python
tips.groupby("day")["tip"].mean()
```

* **Sunday** has the highest average tips (\~3.26).
* Weekend diners appear to be more generous.

📊 Visualization:

```python
sns.barplot(data=tips, x="day", y="tip", estimator="mean", errorbar=None)
plt.show()
```

---

### 4. Relationship Between Bill & Tip

```python
sns.lmplot(data=tips, x="total_bill", y="tip")
plt.show()
```

* Clear **positive relationship**: larger bills → higher tips.
* Some scatter/outliers observed.

---

## 📊 Visuals

* **Bar Plot**: Average tips by day (Sunday tallest bar)
* **Scatter + Regression**: Bill vs Tip (upward trend)
* **Grouped Analysis**: Smoker vs Non-smoker

---

## ✅ Insights

1. Customers tip about **3 dollars on average**.
2. **Smokers and non-smokers** tip about the same.
3. **Sunday diners** give the highest tips.
4. **Higher bills** are strongly associated with **higher tips**.

---

## 🚀 Conclusion

This analysis demonstrates how simple grouping and visualization techniques can extract valuable insights from small datasets.

## 👉 Future work:

* Calculate tip percentage (`tip / total_bill`).
* Explore influence of gender and group size.
* Perform hypothesis testing (e.g., t-tests).

---

## ⚙️ Tech Stack

* Python 🐍
* Pandas
* Seaborn
* Matplotlib

---

## 📜 License

This project is licensed under the **MIT License** – feel free to use and adapt.

---



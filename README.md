# 📦 Inventory Demand Forecasting

Demand forecasting system for grocery inventory using three machine learning approaches — benchmarked against each other with clear business recommendations.

---

## 📊 Dataset

Synthetically generated dataset simulating two years of daily grocery inventory and sales activity.

- **Records:** 32,895 daily sales rows
- **Products:** 45 SKUs across multiple categories
- **Period:** January 2023 – December 2024
- **File:** `Grocery_Inventory_Proper.csv` (included in repo)

---

## 🎯 Objective

Forecast `Sales_Volume` at the per-item daily level and at the aggregate monthly level to support both restocking decisions and warehouse capacity planning.

---

## 🧠 Models

| Model | Use Case | Scale |
|---|---|---|
| **Linear Regression** | Interpretable baseline | Per-item daily |
| **ARIMA(2,1,0)** | Monthly demand planning | Monthly total (all products) |
| **XGBoost** | Primary forecasting model | Per-item daily |

---

## 📈 Results

| Model | RMSE | MAE | Scale |
|---|---|---|---|
| XGBoost ✅ | 2.00 | 1.14 | per-item daily |
| Linear Regression | 7.64 | 5.46 | per-item daily |
| ARIMA(2,1,0) | 8,577 | 6,747 | monthly total (all 45 products) |

XGBoost outperforms Linear Regression by **74% on RMSE**, capturing non-linear interactions between reorder levels, inventory turnover rate, and stock quantity.

---

## 🔑 Key Findings

- **Top XGBoost features:** `Reorder_Level`, `Reorder_Quantity`, `Inventory_Turnover_Rate`, `Stock_Quantity`, `Is_Weekend`
- **Weekend effect:** Sales spike on weekends — pre-stocking on Thursdays provides optimal lead time
- **Promotion impact:** `Is_Promotion` and `Is_Holiday_Period` have an additive effect on sales volume
- **Highest stock-out risk:** Dairy, Produce, and Meat categories had the most lost sales units

---

## 💼 Business Recommendations

1. **Use XGBoost for daily/weekly restocking** — lowest per-item error
2. **Use ARIMA for monthly warehouse capacity planning** — tracks seasonal trends
3. **Pre-stock on Thursdays** — accounts for weekend demand peak
4. **Tighten reorder triggers** for Dairy, Produce, and Meat
5. **Schedule promotions around holiday periods** for maximum combined uplift

---

## 🗂️ Project Structure

```
├── Inventory_Demand_Forecasting.ipynb   # Main notebook
├── Grocery_Inventory_Proper.csv         # Synthetic dataset
├── requirements.txt                     # Dependencies
└── README.md
```

---

## ⚙️ Setup

```bash
git clone https://github.com/your-username/inventory-demand-forecasting.git
cd inventory-demand-forecasting
pip install -r requirements.txt
jupyter notebook Inventory_Demand_Forecasting.ipynb
```

---

## 📦 Requirements

```
pandas
numpy
matplotlib
scikit-learn
statsmodels
xgboost
jupyter
```

---

## 🔭 Future Work

- LSTM / deep learning for multi-step-ahead per-product forecasting
- SKU-level ARIMA for granular seasonal planning
- Lead-time integration to factor in supplier delays
- Promotion optimization modeling by category

---

## 👤 Author

**Your Name**  
[LinkedIn](https://linkedin.com/in/your-profile) · [GitHub](https://github.com/your-username)

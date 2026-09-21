# 📊 Telco Customer Churn Prediction & Analysis
> **利用 Python、機器學習與商業指標，精準預測電信客戶流失風險並制定挽回策略**

---

## 📌 專案簡介 (Project Overview)

在電信與訂閱制產業中，獲取新客戶的成本遠高於留住既有客戶。本專案以 Kaggle 經典的 **Telco Customer Churn** 資料集為基礎，結合 **客戶關係管理 (CRM)** 領域知識與 **機器學習 (Logistic Regression)**，建立一套涵蓋「資料清理、探索性數據分析 (EDA)、模型建模、混淆矩陣評估」的完整數據分析。

### 核心目標
1. **識別流失特徵**：剖析導致志願性流失（Voluntary Churn）的核心驅動因子。
2. **預測流失風險**：建立高召回率（Recall）的機器學習模型，提早捕捉高風險客戶。
3. **優化決策門檻**：透過調整分類機率門檻（Decision Threshold），平衡行銷成本與客戶流失代價。

---

## 💡 商業假設與關鍵指標 (Business Hypotheses & KPIs)

### 1. 商業思維拆解
* **志願性流失 vs 非志願性流失**：重點關注因服務、價格或競爭對手吸引而發生的「志願性流失」。
* **先假設，後驗證**：在建模前先依據產品價值鏈建立假設（如：月繳用戶、未購買資安服務者流失率較高），再以資料驗證。

### 2. 建議監控商業指標 (Business Metrics)
* **整體流失率 (Overall Churn Rate)**：資料集 Baseline 為 $26.5\%$。
* **流失營收損失 (MRR at Risk)**：$\sum \text{MonthlyCharges}_{\text{churned}}$
* **預估顧客終身價值 (LTV)**：$\text{ARPU} \times \text{Average Tenure (Months)}$

---

## 🛠️ 分析與建模流程 (Workflow)
### 1. 資料預處理 (Data Manipulation)
* **缺失值處理**：清理 `TotalCharges` 中的空白字串（`' '`），處理極端分佈。
* **連續變數離散化**：對年資（`tenure`）實施等寬分箱（Equal-width Binning）。
* **特徵編碼**：將類別變數轉為獨熱編碼（One-Hot Encoding），並進行適當的特徵縮放（`StandardScaler`）。
### 2. 機器學習模型 (Logistic Regression)
* **特徵影響力分析**：透過迴歸係數（Coefficients）評估各特徵對流失風險的正負向影響。

## 📈 模型表現與評估 (Model Performance)
評估模型在測試集（Test Set）上的混淆矩陣（Confusion Matrix）表現：
| 評估指標 | 預設模型 (Threshold = 0.5) | 商業意義 |
| :--- | :---: | :--- |
| **總體準確率 (Accuracy)** | ~81.0%  | 全體預測正確的比例 |
| **流失精準率 (Precision)**| ~67.70% | 判定為流失者中，實際真的流失的命中率 |
| **流失召回率 (Recall)**   | **~54.5%** | **成功捕捉到的潛在流失客戶比例（關鍵指標）** |
| **ROC-AUC Score**         | **~0.84** | 模型整體分類辨識能力穩定 |

## 快速開始
git clone https://github.com/Harry30424/operations-analytics.git
cd operations-analytics
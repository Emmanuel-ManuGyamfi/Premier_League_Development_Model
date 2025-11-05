# Premier League Development Model ⚽📊  
*A data-driven analysis of winger performance, archetypes, and predictive modelling across the Premier League.*

---

## 🧠 Project Overview  
This project builds an **end-to-end data science workflow** for evaluating and forecasting player development in the **Premier League**, with a focus on **wingers**.  
It integrates multi-season player data, clustering, and predictive modelling to uncover **performance archetypes**, **track individual progression**, and **forecast future output**.

By combining **feature engineering**, **PCA**, **K-Means clustering**, and **regression modelling**, the Premier League Development Model bridges **quantitative analysis** and **football intelligence** — providing **evidence-based insights** for scouting, recruitment, and performance development.

---

## 🔍 Key Highlights  
- **Exploratory Data Analysis (EDA):**  
  Investigated distributions, positional trends, and relationships between attacking and progression metrics.  

- **Feature Engineering:**  
  Built lag features across three seasons, created per-90 metrics, normalized (z-scores), and filtered players with ≥500 minutes.  

- **Clustering & Archetypes (PCA + K-Means):**  
  Identified distinct winger profiles — including *Ball-Carrying Progressors*, *Creative Dribblers*, and *Direct Finishers*.  

- **Predictive Modelling:**  
  Used **Linear Regression** to forecast next-season `xG+xA per 90`, validating model performance and interpretability.  

- **Visualization:**  
  Interactive PCA scatter plots and radar charts reveal stylistic differences across archetypes and player progression.  

---

## 🧾 Project Structure  


### 🔧 Built With
- **Python** — pandas, scikit-learn, matplotlib, plotly  
- **Machine Learning** — PCA, K-Means, Linear Regression  
- **Visualization** — radar charts, PCA maps, trend timelines  
- **Football Data** — per-90 stats, team strength proxies, multi-season lags  

---

### 🧠 Analytical Goals
1. Identify key winger archetypes across three Premier League seasons.  
2. Quantify player progression using per-90 and lagged performance metrics.  
3. Predict each player’s next-season attacking efficiency (`xG+xA per 90`).  
4. Visualize complex performance profiles in interpretable footballing terms.  

---



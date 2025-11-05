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

- **Visualisation:**  
  Interactive PCA scatter plots and radar charts reveal stylistic differences across archetypes and player progression.  

---

## 🎯 Project Objectives
- Develop an **end-to-end player development model** focused on Premier League wingers.  
- Apply **feature engineering** (per-90 metrics, lag variables, normalization, and filtering).  
- Identify **distinct player archetypes** using **PCA** and **K-Means clustering**.  
- Build and evaluate **predictive models** (Linear Regression and others) to forecast next-season attacking output (`xG+xA per 90`).  
- Communicate actionable insights and visuals to **analysts, scouts, and performance departments**.  

---

## 🧩 Tech Stack
- **Language:** Python 3.12  
- **Libraries:** pandas, numpy, scikit-learn, plotly, matplotlib, seaborn  
- **Clustering & Modelling:** PCA, K-Means, Linear Regression  
- **Data Collection:** BeautifulSoup (web scraping from FBref)  
- **Environment:** Conda / venv  
- **Tools:** Jupyter Notebooks, GitHub, Visual Studio Code  

---

## 📚 Dataset Overview

| Feature | Description |
|----------|-------------|
| Player | Player name |
| season | Season in "YYYY-YYYY" format |
| Primary_Squad | Player’s main club during the season |
| Playing Time_Min | Total minutes played in the season |
| gls_per90 | Goals scored per 90 minutes |
| ast_per90 | Assists per 90 minutes |
| xg_per90 | Expected goals per 90 minutes |
| xag_per90 | Expected assists per 90 minutes |
| npxg_per90 | Non-penalty expected goals per 90 minutes |
| prgC_per90 | Progressive carries per 90 minutes |
| prgP_per90 | Progressive passes per 90 minutes |
| prgR_per90 | Progressive receives per 90 minutes |
| gls_per90_t1, ast_per90_t1, xg_per90_t1, etc. | Lagged features representing previous season performance |

---

## 📊 Exploratory Data Analysis (EDA)

### Player Output Efficiency Analysis (2024–25 Season)

#### ⚽ Goals vs Expected Goals per 90
<img src="outputs/Goals vs Expected Goals per90 (2024-2025).png" width="800"/>

This chart compares each winger’s **Goals per 90** against their **Expected Goals (xG) per 90**, providing insight into finishing efficiency.

**Interpretation**
- The dashed diagonal line represents “expected performance” — players whose actual goals align perfectly with their xG.  
- Players above the line **outperform** their xG (elite finishers).  
- Players below the line **underperform**, suggesting weaker finishing or poor shot selection.

**Key Insights**
- **Mohamed Salah** stands out well above the line, showing elite and consistent finishing efficiency.  
- **Bryan Mbeumo** and **Harvey Barnes** also overperform xG, indicating strong shot conversion.  
- **Jack Harrison**, **Jack Grealish**, and **Pedro Neto** underperform, hinting at potential regression or inefficiency.  

> The overall correlation (r ≈ 0.8) suggests xG remains a strong predictor of goal output, though individual quality differentiates elite performers.

---

#### 🎯 Assists vs Expected Assists per 90
![Assists vs Expected Assists per90](outputs/Assists vs Expected Assists per90 (2024-2025).png)

This chart compares **Assists per 90** with **Expected Assists (xAG) per 90**, measuring creative efficiency — how well key passes are being converted into goals.

**Interpretation**
- The dashed line indicates expected creative output.  
- Players above the line **overperform** their xAG — strong assist conversion or elite teammates.  
- Players below the line **underperform**, meaning their chances aren’t being finished effectively.

**Key Insights**
- **Bukayo Saka**, **Mohamed Salah**, and **Jacob Murphy** outperform their xAG, reflecting efficient chance conversion.  
- **Dwight McNeil** also ranks high, providing valuable chance creation despite Everton’s overall struggles.  
- **Jack Harrison** again underperforms, mirroring his low finishing and assist efficiency.  

> Strong correlation (r ≈ 0.85) reinforces xAG as a robust measure of creative output.

---

### Player Output Efficiency Analysis (2023–24 Season)

#### ⚽ Goals vs Expected Goals per 90
![Goals vs Expected Goals per90 (2023–2024)](outputs/goals_vs_xg_per90_2023_24.png)

This chart compares each winger’s **Goals per 90** to **Expected Goals (xG) per 90**, illustrating how finishing quality and shot conversion evolved during the 2023–24 Premier League season.

**Key Insights**
- **Mohamed Salah** continues to perform at elite finishing levels, sitting far above the line — a hallmark of sustained world-class efficiency.  
- **Leandro Trossard**, **Phil Foden**, and **Harvey Barnes** also outperform their xG, demonstrating strong finishing consistency.  
- **Bryan Mbeumo** and **Bukayo Saka** remain slightly above expectation, showing reliable, repeatable performance.  
- **Jack Harrison**, **Dwight McNeil**, and **Dango Ouattara** underperform relative to xG, indicating lower shot efficiency or finishing struggles.

> Overall, a similar pattern to 2024–25 emerges — elite attackers consistently exceed expectation, underlining stable finishing skill rather than luck.

---

#### 🎯 Assists vs Expected Assists per 90
![Assists vs Expected Assists per90 (2023–2024)](outputs/assists_vs_xag_per90_2023_24.png)

This chart plots **Assists per 90** against **Expected Assists (xAG) per 90**, providing a view into creative efficiency and chance conversion from wide areas.

**Key Insights**
- **Jacob Murphy** and **Pedro Neto** emerge as standout creative overperformers, producing assists well beyond expectation.  
- **Mohamed Salah** and **Brennan Johnson** also exceed their xAG, reflecting strong chance creation combined with efficient finishing teammates.  
- **Harry Wilson** and **Anthony Gordon** record creative outputs slightly above expectation, showing consistent contribution in wide roles.  
- **Jack Grealish**, **Alex Iwobi**, and **Leandro Trossard** fall below the line, suggesting underperformance in chance conversion or limited creative freedom.

> The trends reinforce player consistency across seasons — those who outperform xAG tend to sustain creativity due to tactical role and decision-making rather than randomness.

---

### Player Output Efficiency Analysis (2022–23 Season)

#### ⚽ Goals vs Expected Goals per 90
![Goals vs Expected Goals per90 (2022–2023)](outputs/goals_vs_xg_per90_2022_23.png)

This chart evaluates **finishing efficiency** by comparing each winger’s **Goals per 90** to **Expected Goals (xG) per 90** during the 2022–23 season.

**Key Insights**
- **Mohamed Salah** again demonstrates elite efficiency, finishing far above expectation — confirming his consistency across multiple seasons.  
- **Alejandro Garnacho**, **Phil Foden**, and **Gabriel Martinelli** also significantly overperform xG, indicating clinical finishing and sharp decision-making in front of goal.  
- **Harvey Barnes**, **Bukayo Saka**, and **Cody Gakpo** align closely with expected values, showing steady and reliable performance.  
- **Pedro Neto** and **Alex Iwobi** underperform their xG, reflecting potential inefficiencies or weaker shot selection.  

> Salah’s sustained overperformance across years underscores a genuine skill advantage, not random variance — an important validation for player development models.

---

#### 🎯 Assists vs Expected Assists per 90
![Assists vs Expected Assists per90 (2022–2023)](outputs/assists_vs_xag_per90_2022_23.png)

This visualization measures **creative efficiency**, comparing **Assists per 90** to **Expected Assists (xAG) per 90**.

**Key Insights**
- **Leandro Trossard** stands out as a major overperformer, generating assists well above expectation.  
- **Mohamed Salah**, **Alejandro Garnacho**, and **Bukayo Saka** also surpass xAG — signalling elite combination play and creative synergy.  
- **Jack Grealish** and **Phil Foden** perform in line with expectations, showing reliable creative roles.  
- **Gabriel Martinelli** and **Dwight McNeil** slightly underperform, likely due to missed chances from teammates.  
- **Pedro Neto** and **Noni Madueke** rank lowest, highlighting reduced creative end-product or tactical limitations.  

> The creative efficiency trends align with finishing outcomes — suggesting that both scoring and assisting ability follow consistent player archetypes over time.

---

### 🚀 Progressive Actions Analysis (2022/23 – 2024/25 Seasons)
![Progressive Actions](outputs/progressive.png)

This section analyses player progression metrics — **Progressive Carries**, **Progressive Passes**, and **Progressive Receives per 90** — across three Premier League seasons.  
These metrics highlight players’ ability to **advance possession**, **break lines**, and **receive the ball in attacking zones**, key indicators of modern winger effectiveness.

---

#### 🏃‍♂️ Progressive Carries per 90
- **Jack Grealish** leads this metric across all three seasons: *6.7 (22/23)*, *6.5 (23/24)*, and *6.6 (24/25)*.  
- He’s the only player to remain in the **top two every year**, reflecting his pivotal role in carrying the ball forward and driving possession into advanced areas.  
- **Bukayo Saka** and **Noni Madueke** are next most consistent, both ranking within the **top five** in multiple seasons.  
- **Kaoru Mitoma** and **Gabriel Martinelli** fluctuate slightly but consistently demonstrate strong carrying ability.

> Progressive carries capture directness and dribbling involvement — attributes often linked to *creative progressors* and *ball-dominant wingers*.

---

#### 🎯 Progressive Passes per 90
- **Jack Grealish** again ranks among the top three each season (range: *4.6–6.5*), showcasing his dual threat as both ball carrier and creator.  
- **Alex Iwobi** emerges as a **key progressive passer**, leading or close to the lead in each season — particularly dominant in *2023/24* and *2024/25*.  
- **Leandro Trossard** and **Phil Foden** show steady creative progression but with more seasonal variability.  

> Consistency in progressive passing highlights players who *dictate attacking flow* and *advance play through smart distribution*.

---

#### 📥 Progressive Receives per 90
- **Bukayo Saka** dominates this category across all three seasons, ranking **1st or 2nd each year**, underlining elite **off-ball movement** and **positional intelligence**.  
- **Jack Grealish** and **Gabriel Martinelli** remain regulars in the upper tier, reflecting their involvement in advanced build-up and attacking phases.  
- **Mohamed Salah** and **Alejandro Garnacho** display steady improvement, suggesting increased offensive involvement and tactical maturity.

> High progressive receives values identify players adept at *finding space*, *linking play*, and *maintaining attacking width*.

---

#### 📈 Summary
- **Grealish** stands out as a complete progressor — excelling in carries, passes, and receives across three years.  
- **Saka** continues to lead as an elite receiver, highlighting movement and positioning as his key strengths.  
- **Iwobi**’s progression underscores his playmaking evolution and adaptability across systems.  
- The trio of **Grealish, Saka, and Martinelli** exemplifies sustained attacking involvement — key indicators for player development and role archetype analysis.


### 🧩 Seasonal Takeaways
- **Salah** demonstrates elite repeatability — outperforming both xG and xAG metrics across consecutive seasons.  
- **Neto**, **Murphy**, and **Trossard** show shifts between over- and under-performance, offering clues about form or tactical evolution.  
- Sustained alignment between expected and actual metrics signals reliability — crucial for predictive modelling and player development forecasting.

#### 🧩 Overall Summary
- **Salah** leads both finishing and creative metrics — the gold standard among Premier League wingers.  
- **Mbeumo** and **Barnes** emerge as high-efficiency finishers.  
- **Saka** and **McNeil** excel creatively.  
- **Harrison**, **Neto**, and **Grealish** lag behind expected output, potentially due to finishing or tactical context.  

> These findings identify who may **sustain or regress** toward expected levels next season — critical context for **predictive modelling** and **player development analysis**.




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



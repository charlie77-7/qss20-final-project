# qss20-final-project

QSS20 Final Project Spring 2026

**Link to website:** https://charles-phillips-qss20-final-project.vercel.app

---

## Project Summary

This project seeks to understand whether USAID cuts have had an impact on global soft power patterns. By analyzing voting alignment scores at the UN, Gallup Approval ratings and News sentiment, the project aims to see if these have changed substantially for the US or for China during Trump's 2nd term.

---

## Data

The data is stored at this link as it is too large for Github:
https://drive.google.com/drive/folders/1jvXSN3DG2X3wUPvU6-ZRd65UylTkhMxJ?dmr=1&ec=wgc-drive-%5Bmodule%5D-goto

**Raw:**
- `2026_02_06_ga_voting.csv` — UN General Assembly voting data
- `us_foreign_aid_country.csv` — US Foreign Aid data to each country
- `worldbank_GDP_data.csv` — World Bank GDP data
- `gallup_us_approval.csv` — Gallup US Leadership Approval Ratings
- `gallup_china_approval.csv` — Gallup China Leadership Approval Ratings

**Cleaned:**
- `df_clean.csv` — Cleaned dataframe containing UN and foreign aid data after `01_load_clean`. Too large for GitHub (>100MB); stored in the Google Drive folder above.
- `gallup_did_clean.csv` — Cleaned dataframe containing Gallup approval ratings and foreign aid data after `03_approval_ratings_load_clean`
- `df_us_scored.csv` — News headlines related to the USA with their corresponding sentiment score
- `df_china_scored.csv` — News headlines related to China with their corresponding sentiment score

---

## Code

### [01_load_clean](code/01_load_clean.ipynb)
- **Takes in:** `2026_02_06_ga_voting.csv`, `us_foreign_aid_country.csv`, `worldbank_GDP_data.csv`
- **Does:** Loads and cleans both the UN and foreign assistance datasets before merging them. Creates UN voting alignment scores relative to the US and China for each country-year.
- **Outputs:** `df_clean.csv`, `us_foreign_assistance_over_time.png`

### [02_analyze_un](code/02_analyze_un.ipynb)
- **Takes in:** `df_clean.csv`
- **Does:** Creates visualizations of UN voting alignment trends and conducts Difference-in-Differences regressions testing whether high-aid countries shifted alignment after the 2025 USAID cuts.
- **Outputs:** `global_alignment_us_vs_china.png`, `china_alignment_by_aid_group.png`, `parallel_trends.png`, `did_un_results.tex`, `un_linear_test.tex`

### [03_approval_ratings_load_clean](code/03_approval_ratings_load_clean.ipynb)
- **Takes in:** `df_clean.csv`, `gallup_us_approval.csv`, `gallup_china_approval.csv`
- **Does:** Loads the Gallup approval datasets, cleans and harmonises country names, and merges with foreign aid data in preparation for DiD analysis.
- **Outputs:** `gallup_did_clean.csv`, `global_approval_trend.png`

### [04_approval_ratings_analysis](code/04_approval_ratings_analysis.ipynb)
- **Takes in:** `gallup_did_clean.csv`
- **Does:** Creates visualizations of Gallup approval trends and conducts Difference-in-Differences regressions testing whether high-aid countries shifted approval ratings after the 2025 USAID cuts.
- **Outputs:** `parallel_trends_china_approval.png`, `approval_did_results.tex`, `approval_linear_test.tex`

### [05_sentiment_load_clean](code/05_sentiment_load_clean.ipynb)
- **Takes in:** MediaCloud API key, `df_clean.csv`
- **Does:** Uses the MediaCloud API to download newspaper headlines for Jordan, Mozambique, and Zambia mentioning the US or China. Scores headline sentiment using a locally-run Llama 3 model via Ollama.
- **Outputs:** `df_us_scored.csv`, `df_china_scored.csv`

### [06_sentiment_analysis](code/06_sentiment_analysis.ipynb)
- **Takes in:** `df_us_scored.csv`, `df_china_scored.csv`
- **Does:** Creates visualizations comparing pre/post-inauguration sentiment toward the US and China in local press across Jordan, Mozambique, and Zambia — for both general and development-specific headlines.
- **Outputs:** `sentiment_china.png`, `sentiment_us.png`, `sentiment_combined.png`, `sentiment_china_dev.png`, `sentiment_us_dev.png`, `sentiment_dev_combined.png`

### [07_data_summary](code/07_data_summary.ipynb)
- **Takes in:** `df_clean.csv`, `gallup_did_clean.csv`
- **Does:** Creates summary statistics tables for both datasets as they appear before analysis.
- **Outputs:** `data_summary.tex`, `summary_gallup.tex`

---

## Output

**Figures (`output/`):**
- `global_alignment_us_vs_china.png` — Average country voting alignment with the US and China per year
- `us_foreign_assistance_over_time.png` — Total US Foreign Assistance Disbursements by year
- `china_alignment_by_aid_group.png` — UN voting alignment with China for high/low aid countries over time
- `parallel_trends.png` — Parallel trends plot showing the high/low aid alignment gap over time
- `parallel_trends_china_approval.png` — Parallel trends graph showing high/low aid countries and Chinese approval over time
- `global_approval_trend.png` — Approval ratings of the US and China over time
- `sentiment_china.png` — China media sentiment pre/post Trump's inauguration (general headlines)
- `sentiment_us.png` — US media sentiment pre/post Trump's inauguration (general headlines)
- `sentiment_combined.png` — US & China media sentiment pre/post Trump's inauguration (general headlines)
- `sentiment_china_dev.png` — China media sentiment pre/post Trump's inauguration (development headlines)
- `sentiment_us_dev.png` — US media sentiment pre/post Trump's inauguration (development headlines)
- `sentiment_dev_combined.png` — US & China media sentiment pre/post Trump's inauguration (development headlines)

**Tables (`output/`):**
- `data_summary.tex` — Summary table of the UN/foreign assistance dataset
- `summary_gallup.tex` — Summary table of the Gallup dataset
- `did_un_results.tex` — DiD regression results for UN voting alignment
- `un_linear_test.tex` — Linear parallel trends test for UN alignment
- `approval_did_results.tex` — DiD regression results for Gallup approval ratings
- `approval_linear_test.tex` — Linear parallel trends test for Gallup approval

# qss20-final-project
QSS20 Final Project Spring 2026  

Link to website: https://charles-phillips-qss20-final-project.vercel.app  

## Project Summary
This project seeks to understand whether USAID cuts have had an impact on global soft power patterns. By analyzing voting alignment scores at the UN, Gallup Approval ratings and News sentiment, the project aims to see if these have changed substantially for the US or for China during Trump's 2nd term.

## Data
The data is stored at this link as it is too large for Github: 
https://drive.google.com/drive/folders/1jvXSN3DG2X3wUPvU6-ZRd65UylTkhMxJ?dmr=1&ec=wgc-drive-%5Bmodule%5D-goto

The data is split into raw and cleaned data:  
Raw:  
`2026_02_06_ga_voting.csv`: UN General Assembly voting data  
`us_foreign_aid_country.csv`: US Foreign Aid data to each country 
`worldbank_GDP_data.csv`: World Bank GDP data  
`gallup_us_approval.csv`: Gallup US Leadership Approval Ratings  
`gallup_china_Approval.csv`: Gallup China Leadership Approval Ratings  

Cleaned:  
`df_clean.csv`: Cleaned dataframe containing UN and foreign aid data after 01_load_clean. I tried to keep it in Github, but it was >100MB so i dragged it into the Google Drive folder.  
`gallup_did_clean.csv`: Cleaned dataframe containing Gallup approval ratings and foreign aid data afteer 03_approval_ratings_load_clean  
`df_us_scored.csv`: News headlines related to the USA with their corresponding sentiment score  
`df_china_scored.csv`: News headlines related to China with their corresponding sentiment score 


## Code
`01_load_clean`: loads and cleans both the UN and foreign assistance datasets before merging them.  
`02_analyze_un`: loads the cleaned `df_clean.csv`, creates visualizations and conducts regressions.  
`03_approval_ratings_load_clean`: loads `df_clean.csv` and the Gallup datasets, cleans them and merges them in preparation for analysis.  
`04_approval_ratings_analysis`: loads `gallup_did_clean.csv`, creates visualizations and conducts regressions.  
`05_sentiment_load_clean`: uses an API to access MediaCloud, downloads headlines and creates dataframes based on them for the US and China.  
`06_sentiment_analysis`: creates visualizations based on the cleaned headline dataframes.  
`07_data_summary`: creates summary tables of the `df_clean.csv` and `gallup_did_clean.csv` pre analysis.  

## Output
.png files:  
`global_alignment_us_vs_china.png`: average country voting alignmnet w the US and China per year  
`us_foreign_assistance_over_time.png`: Total US Foreign Assistance Disbursements by year  
`sentiment_us_dev.png`: US media sentiment pre/post Trump's inauguration for development related headlines  
`sentiment_us.png`: US media sentiment pre/post Trump's inauguration for general headlines  
`sentiment_dev_combined.png`: US & China media sentiment pre/post Trump's inauguration for development related headlines  
`sentiment_combined.png` : US & China media sentiment pre/post Trump's inauguration for general headlines  
`sentiment_china_dev.png`: China media sentiment pre/post Trump's inauguration for development related headlines  
`sentiment_china.png`: China media sentiment pre/post Trump's inauguration for general headlines  
`parallel_trends_china_approval.png`: Parallel trends graph showing high/low aid countries and Chinese approval over time  
`parallel_trends.png`: same as parallel_trends_china_approval.png with a graph showing how the gap varies over time  
`global_approval_trend.png`: graphs showing approval ratings of the US/China over time  
`global_alignment_us_vs_china.png`: global UN voting alignment for China and US over time  
`china_alignment_by_aid_group.png`: UN voting alignment with China for high/low aid countries over time  

.tex files:  
un_linear_test.tex: output table of the linear test for UN alignment for parallel trends  
summary_gallup.tex: summary table of the Gallup dataset ready for analysis  
did_un_results.tex: output table for the DiD on Chinese and US alignment  
data_summary.tex: summary table of the UN/foreign assistance dataset ready for analysis  
approval_linear_test.tex: output table of the linear test for Gallup approval for parallel trends  
approval_did_results.tex: output tabel for the DiD on Chinese and US approval  


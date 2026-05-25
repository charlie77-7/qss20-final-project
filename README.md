# qss20-final-project
QSS20 Final Project Spring 2026

## Project Summary
This project seeks to understand whether USAID cuts have had an impact on global soft power patterns. By creatinv voting alignment scores at the UN for each country each year, the project aims to see if these have changed substantially for the US or for China during Trump's 2nd term.

## Data
The data is stored at this link as it is too large for Github: 
https://drive.google.com/drive/folders/1jvXSN3DG2X3wUPvU6-ZRd65UylTkhMxJ?dmr=1&ec=wgc-drive-%5Bmodule%5D-goto

`2026_02_06_ga_voting.csv`: UN General Assembly voting data
`us_foreign_aid_country.csv`: US Foreign Aid data to each country
`df_clean`: Cleaned dataframe after 01_load_clean. I tried to keep it in Github, but it was >100MB so i dragged it into the Google Drive folder.

## Code
01_load_clean: loads and explores the General Assembly dataset, filters and prepares it for analysis by creating alignment scores. It then saves the data as a new dataset
02_analyze: SO FAR - creates average alignments by country, by year and by country and year. Also creates an output graph showing average country voting alignment with the US and China per year.

## Output
global_alignment_us_vs_china.png: average country voting alignmnet w the US and China per year

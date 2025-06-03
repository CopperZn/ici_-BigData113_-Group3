# Project Title

K-pop award trends: What factors contribute to song rankings?

## Project Description

This project investigates the impact of song title characteristics on the chart performance of K-pop songs, focusing on factors such as title length, presence of English, and thematic content. By analyzing over 3,000 songs that appeared on Korea’s CircleChart Top 200 between 2018 and 2023, the study explores how stylistic and linguistic choices may influence a song’s visibility and success.

Data was collected through web scraping of CircleChart rankings and enriched with text-based features using R and the ChatGPT API. Statistical techniques—including t-tests, correlation analysis, ANOVA, and multiple linear regression—were applied to evaluate three main hypotheses regarding title features and their correlation with chart outcomes.

This research sheds light on how seemingly small decisions in song naming can play a subtle but important role in digital music performance, especially in a competitive and globalized market like K-pop.

## Getting Started

🔧 Software Requirements
	•	R version ≥ 4.2.0
	•	Required R packages:
	•	dplyr
	•	ggplot2
	•	stringr
	•	httr
	•	jsonlite
	•	readr

Install all packages in R:

install.packages(c("dplyr", "ggplot2", "stringr", "httr", "jsonlite", "readr"))

⸻

📥 Data Collection Process
	1.	Web-scraped CircleChart weekly Top 200 charts (2018–2023) from http://circlechart.kr
	2.	Extracted metadata: song title, artist, album, rank, year, and week
	3.	Cleaned and structured the data using R
	4.	Classified title content using:
	•	Character count (Korean & English)
	•	Presence of English (binary)
	•	Thematic classification using ChatGPT API
	5.	Merged and deduplicated final dataset

⸻

🧪 Analysis Workflow

All statistical analyses were conducted in R, including:
	•	Descriptive statistics
	•	Welch’s t-test
	•	Pearson correlation
	•	One-way ANOVA
	•	Multiple linear regression

⸻
[Please refer to `src/analysis.R` for a reproducible version of the analysis pipeline.] #把中間的 R 檔修改成我們的內容

## File Structure

This section describes how the project files are organized and the purpose of each folder.

📁 data/

├── 來自circlechart原始檔案.csv           # Original data scraped from CircleChart.kr 
└── 清理後的.csv       # Processed dataset with added variables (e.g., title length, English presence)

📁 src/
 └── 跟上方的R放一樣的檔案.R             # Main R script for data cleaning, feature extraction, and statistical tests

📁 figures/
 ├── 歌名長度分析圖表.png  # Visualization of title length vs. chart rank
 ├── 英文歌名分析圖表.png# Visualization of English presence effect
 └── 歌名主題分析圖表.png   # ANOVA/t-test results across thematic groups

📄 README.md                # Project description and documentation (this file)
📄 [Big Data_ K-pop award trends_ group3.pdf](https://github.com/user-attachments/files/20560657/Big.Data_.K-pop.award.trends_.group3.pdf)  # Final written report 


## Analysis

[Describe your analysis methods and include any visualizations or graphics that you used to present your findings. Explain the insights that you gained from your analysis and how they relate to your research question or problem statement.]

## Results

[Provide a summary of your findings and conclusions, including any recommendations or implications for future research. Be sure to explain how your results address your research question or problem statement.]

## Contributors

[List the contributors to your project and describe their roles and responsibilities.]

## Acknowledgments

[Thank any individuals or organizations who provided support or assistance during your project, including funding sources or data providers.]

## References

[List any references or resources that you used during your project, including data sources, analytical methods, and tools.]

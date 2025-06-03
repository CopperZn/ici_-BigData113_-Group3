# Project Title

**K-pop award trends: What factors contribute to song rankings?**

## Project Description

This project investigates the impact of **song title characteristics** on the chart performance of K-pop songs, focusing on factors such as **title length**, **presence of English**, and **thematic content**. By analyzing over 3,000 songs that appeared on Korea’s CircleChart Top 200 between 2018 and 2023, the study explores how stylistic and linguistic choices may influence a song’s visibility and success.

Data was collected through web scraping of CircleChart rankings and enriched with text-based features using R and the ChatGPT API. Statistical techniques—including t-tests, correlation analysis, ANOVA, and multiple linear regression—were applied to evaluate three main hypotheses regarding title features and their correlation with chart outcomes.

This research sheds light on how seemingly small decisions in song naming can play a subtle but important role in digital music performance, especially in a competitive and globalized market like K-pop.

## Getting Started

🔧 Software Requirements
- R version ≥ 4.2.0
- Required R packages:
  - dplyr
  - ggplot2
  - stringr
  - httr
  - jsonlite
  - readr

Install all packages in R:
- install.packages(c("dplyr", "ggplot2", "stringr", "httr", "jsonlite", "readr"))

⸻

📥 Data Collection Process
1. Web-scraped CircleChart weekly Top 200 charts (2018–2023) from http://circlechart.kr
2. Extracted metadata: song title, artist, album, rank, year, and week
3. Cleaned and structured the data using R
4. Classified title content using:
   - Character count (Korean & English)
   - Presence of English (binary)
   - Thematic classification using ChatGPT API
5. Merged and deduplicated final dataset


⸻

🧪 Analysis Workflow

All statistical analyses were conducted in **R**, including:
- Descriptive statistics
- Welch’s t-test
- Pearson correlation
- One-way ANOVA
- Multiple linear regression

  「後面Pearson 到 線性回歸看要不要刪掉」
  

⸻
[Please refer to **`src/analysis.R`** for a reproducible version of the analysis pipeline.] 「把中間的 R 檔修改成我們的最終R.file」

## File Structure

This section describes how the project files are organized and the purpose of each folder.

📁 data/
- 「來自circlechart原始檔案」.csv 	# Original data scraped from CircleChart.kr
- 「清理後的」.csv		# Processed dataset with added variables (e.g., title length, English presence)     

📁 src/
- 「跟上方的R放一樣的檔案」.R    	# Main R script for data cleaning, feature extraction, and statistical tests

📁 figures/
 - 「歌名長度分析圖表」.png  	# Visualization of title length vs. chart rank
 - 「英文歌名分析圖表」.png	# Visualization of English presence effect
 - 「歌名主題分析圖表」.png 	# ANOVA/t-test results across thematic groups

📄 README.md                	# Project description and documentation (this file)

📄 [Big Data_ K-pop award trends_ group3.pdf](https://github.com/user-attachments/files/20560657/Big.Data_.K-pop.award.trends_.group3.pdf)  # Final written report 


## Analysis

Our analysis explored how linguistic and stylistic characteristics of K-pop song titles influence their chart performance on CircleChart.kr, using a dataset of over 3,000 songs released between 2018 and 2023. The study examined three main hypotheses:

**🔍 Hypotheses**
- H1: Shorter titles are associated with better chart rankings.
- H2: The presence of English in a title improves ranking performance.
- H3: Thematic and stylistic features—such as “Love”, “Friendship”, or full capitalization—affect chart success.

**🛠️ Methods**

All analysis was conducted in **R**, using:
- Pearson correlation to assess title length vs. ranking
- Welch’s t-tests to compare groups (e.g., English vs. non-English titles)
- One-way ANOVA to analyze differences across thematic categories
- Multiple linear regression to control for contextual variables (e.g., debut year, group size)
- 「t-test 以下看要不要刪掉」

Textual features such as title length, English presence, and thematic category were generated using R scripts, supplemented with **ChatGPT API** for label classification.

**📈 Visualizations**
- Title Length vs. Chart Rank: Scatter plots with regression lines
- English Title vs. Non-English: Bar graphs comparing average rank
- Thematic Effects: Boxplots showing rank distributions across themes
- Capitalization Effects: Histograms showing impact on ranking

(📁 See images in the /figures folder for reference.)

**💡 Key Findings**
- Title Length: No significant correlation was found between title length (Korean or English) and chart rank. Shorter titles did not consistently perform better.
- English Presence: English titles showed no effect across the full dataset, but significantly outperformed non-English titles among the top 50 songs—indicating strategic value in high-stakes releases.
- Thematic Features: Most themes (e.g., Love, Friendship) had no measurable effect on rankings. The only statistically significant factor was capitalization: fully capitalized titles performed worse, suggesting negative perception or algorithmic suppression.

## Results

The analysis yielded the following insights regarding the relationship between K-pop song titles and their chart performance on CircleChart.kr:

**📌 Hypothesis 1: Title Length**

**Finding**: Not supported.

- No statistically significant difference in chart rank between short and long titles, whether in Korean or English.
- Although shorter English titles in the top 50 showed slightly better average rankings (12.63 vs. 13.78), this difference was not statistically meaningful.

**Conclusion**: Title brevity alone does not predict better performance on music charts.

⸻

**📌 Hypothesis 2: English in Title**

**Finding**: Partially supported.

- Across the full dataset, the presence of English words had no significant correlation with ranking.
- However, in the top 50 songs, English titles significantly outperformed non-English titles (average rank: 14.41 vs. 21.19, p < 0.001).

**Conclusion**: English titles can enhance visibility for high-performing tracks, likely due to better algorithmic reach or international appeal.

⸻

**📌 Hypothesis 3: Thematic and Stylistic Features**

**Finding**: Mostly not supported.

- Common themes such as “Love,” “Friendship,” and “Self Growth” had no significant effect on rankings.
- The only significant stylistic factor was capitalization—fully capitalized titles performed significantly worse (p < 0.001).
- Thematic keywords like “Color” showed marginal effects, warranting further exploration.

**Conclusion**: Title themes have minimal impact, while visual emphasis (e.g., all caps) may negatively affect perception or algorithmic performance.

⸻

**🔍 Overall Summary**
- **Title characteristics alone** do not strongly determine chart success.
- **Strategic use of English** may benefit high-potential songs.
- **Visual formatting matters**—especially avoiding excessive capitalization.

These results address the central research question by showing that stylistic and linguistic features of K-pop titles have subtle, context-dependent impacts. While not dominant predictors, they contribute to the broader ecosystem of visibility, discoverability, and algorithmic prioritization.

## Contributors

This project was conducted by Group 3 as part of the Big Data Analytics course. The following team members contributed to various aspects of the project:
- [Savanah]
- [Copper]
- [Jubal]
- [Gina]

## Acknowledgments

We would like to thank the following individuals and organizations for their support throughout this project:
- Professor Chung-pei Pien – For providing guidance, feedback, and instructional resources during the Big Data Analytics course.
- Marcella – For technical support and assistance with data analysis questions.

This project was completed as part of the Big Data Analytics course at NCCU / ICI during the Spring / 2025.

## References

- Maximize Market Research. (2024). K-pop Events Market: Global Industry Analysis and Forecast (2024–2030).
https://www.maximizemarketresearch.com/market-report/k-pop-events-market/186929/

- El Ouahi, Y. (2020). Linguistic Strategies in K-pop Globalization. University of Barcelona.
https://diposit.ub.edu/dspace/handle/2445/176497

- Oh, I., & Park, G. (2012). The Globalization of K-pop: Korea’s Place in the Global Music Industry. Popular Music, 31(1), 73–89.
https://www.researchgate.net/publication/296774877

- Whissell, C. (2021). How the Titles of Popular Songs Have Changed Over the Last 60 Years. Studies in Linguistics and Literature, 5(4), 140.
https://doi.org/10.22158/sll.v5n4p140

- Chang, K.-W. (2023). Using Spotify and YouTube Features to Predict the Billboard Hot 100 Chart’s Popular Songs.
https://hdl.handle.net/11296/59j895

- Li, Z., Song, M., Duan, S., & Wang, Z. (2022). Are Users Attracted by Playlist Titles and Covers? Journal of Innovation & Knowledge, 7(3), 100212.
https://doi.org/10.1016/j.jik.2022.100212

- Official Charts. (2018). Streaming Has Changed the Way That Songs Are Titled, New Research Suggests.
https://www.officialcharts.com/chart-news/streaming-has-changed-the-way-that-songs-are-titled-new-research-suggests__22430/

- OpenAI. ChatGPT API. Used for thematic classification of song titles in R.
- CircleChart.kr. Weekly Top 200 chart data (2018–2023).
http://circlechart.kr

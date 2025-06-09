# K-pop Award Trends: What Factors Contribute to Song Rankings?

This repository presents the final group project for the Big Data Analytics course, investigating how K-pop song title characteristics influence chart performance on Korea’s CircleChart.kr between 2018 and 2023.

---

## Project Description

This project investigates the impact of **song title characteristics** on the chart performance of K-pop songs, focusing on factors such as **title length**, **presence of English**, and **thematic content of song title**. By analyzing over 3,000 songs from 2018–2023, we examined how these stylistic choices affect a song’s visibility and success.

Data was collected through web scraping of CircleChart.kr rankings(an official song ranking website of South Korea) and enriched using R and the ChatGPT API. Statistical techniques—including t-tests, correlation analysis, and multiple linear regression—were applied to evaluate three main hypotheses related to title design and chart outcome.

This research sheds light on how seemingly small decisions in song naming can play a subtle but important role in digital music performance, especially in a competitive and globalized market like K-pop.

---

### **🔧 Software Requirements

- **R version ≥ 4.2.0**
- Required R packages: `dplyr`, `ggplot2`, `stringr`, `httr`, `jsonlite`, `readr`

Install in R:
```r
install.packages(c("dplyr", "ggplot2", "stringr", "httr", "jsonlite", "readr"))
```

### **📥 Data Collection Process

1. Scraped CircleChart Top 200 weekly charts (2018–2023)
2. Extracted: title, artist, album, ranking, year, week
3. Cleaned and structured data in R(removing non-kpop songs)
4. Feature engineering:
   - Character count (Korean & English)
   - Binary English presence (yes=1, no=0)
   - Thematic classification using ChatGPT API
5. Merged, deduplicated, finalized master dataset

### **🧪 Analysis Workflow

- **Descriptive statistics**
- **Welch’s t-test**
- **Pearson correlation**
- **Multiple linear regression**

---

## File Structure

This section outlines the structure of the project repository and describes the purpose of each file and folder.

```plaintext
📁 data/
 ├── 「original_data_kpop.rankings」.csv           # Original data scraped from CircleChart.kr
 └── 「cleaned_data_only.kpop」.csv         # Processed dataset with only Kpop songs 
 └── 「kpop_song.k/e.title」.csv         # Processed dataset with additional variables
 └── 「Kpop_song.category」.csv         # Processed dataset with song title categorization

📁 src/
 ├── 「data_cleaning」.R                           # R script for data cleaning and preprocessing
 └── 「song title_categorization」.R               # R script for preprocessing and song title categorization
 └── 「H1」.R               # R script for H1: Title Length
 └── 「H2」.R               # R script for H2: English Presence in Title
 └── 「H3」.R               # R script for H3: Thematic and Stylistic Features

📁 figures/
 ├──  「H1」.png            # Title length vs. rank
    └── 「H1_k_title」.png      # Full dataset of Korean song title
    └── 「H1_k50」.png          # Top 50 dataset of Korean song title
    └── 「H1_e_title」.png      # Full dataset of English song title
    └── 「H1_e50」.png          # Top 50 dataset of English song title
 ├── 「H2」.png             # English presence and ranking
    └── 「H2_full」.png         # Full dataset of English song title
    └── 「H2_top50」.png        # Top 50 dataset of English song title
 ├── 「H3」.png            # Results by thematic group

📄 README.md                            # Project documentation (this file)
📄 「那份完整報告的檔案」.pdf               # Final written report「你再自己下載」
📄 「poster」.pdf               # Final demonstrated poster「你再自己下載

```
---

## Analysis

Our analysis explored how linguistic and stylistic characteristics of K-pop song titles influence their chart performance on CircleChart.kr, using a dataset of over 3,000 songs released between 2018 and 2023. The study examined three main hypotheses:

**🔍 Hypotheses**
    •    **H1**: Shorter titles are associated with better chart rankings.
    •    **H2**: The presence of English in a title improves ranking performance.
    •    **H3**: Thematic and stylistic features—such as “Love”, “Friendship”, or full capitalization—affect chart success.

**🛠️ Methods**

All analysis was conducted in **R**, using:
    •    **Pearson correlation** to assess title length vs. ranking
    •    **Welch’s t-tests** to compare groups (e.g., English vs. non-English titles)
    •    **Multiple linear regression** to control for contextual variables (e.g., debut year, group size)

Textual features such as title length, English presence, and thematic category were generated using R scripts, supplemented with **ChatGPT API** for label classification.

**📈 Visualizations**
    •    **Title Length vs. Chart Rank**: Scatter plots with regression lines
    •    **English Title vs. Non-English**: Bar graphs comparing average rank
    •    **Thematic Effects**: Boxplots showing rank distributions across themes
    •    **Capitalization Effects**: Histograms showing impact on ranking


**💡 Key Findings**
    •    **Title Length**: No significant correlation was found between title length (Korean or English) and chart rank. Shorter titles did not consistently perform better.
    •    **English Presence**: English titles showed no effect across the full dataset, but significantly outperformed non-English titles among the top 50 songs—indicating strategic value in high-stakes releases.
    •    **Thematic Features**: Most themes (e.g., Love, Friendship) had no measurable effect on rankings. The only statistically significant factor was **capitalization**: fully capitalized titles performed better, suggesting positive perception or algorithmic suppression.
---

## ✅ Results

The analysis yielded the following insights regarding the relationship between K-pop song titles and their chart performance on CircleChart.kr:

**📌 Hypothesis 1: Title Length**

**Finding**: Not supported.

    •    No statistically significant difference in chart rank between short and long titles, whether in Korean or English.
    •    Although shorter English titles in the top 50 showed slightly better average rankings (12.63 vs. 13.78), this difference was not statistically meaningful.

**Conclusion**: Title brevity alone does not predict better performance on music charts.

⸻

**📌 Hypothesis 2: English in Title**

**Finding**: Partially supported.

    •    Across the full dataset, the presence of English words had no significant correlation with ranking.
    •    However, in the top 50 songs, English titles significantly outperformed non-English titles (average rank: 14.41 vs. 21.19, p < 0.001).

**Conclusion**: English titles can enhance visibility for high-performing tracks, likely due to better algorithmic reach or international appeal.

⸻

**📌 Hypothesis 3: Thematic and Stylistic Features**

**Finding**: Mostly not supported.

    •    Common themes such as “Love,” “Friendship,” and “Self Growth” had no significant effect on rankings.
    •    The only significant stylistic factor was capitalization—fully capitalized titles performed significantly better (p < 0.001).
    •    Thematic keywords like “Color” showed marginal effects, warranting further exploration.

**Conclusion**: Title themes have minimal impact, while visual emphasis (e.g., all caps) may positively affect perception or algorithmic performance.

⸻

**🔍 Overall Summary**
    •    **Title characteristics alone** do not strongly determine chart success.
    •    **Strategic use of English** may benefit high-potential songs.
    •    **Visual formatting matters**—especially using excessive capitalization.

These results address the central research question by showing that stylistic and linguistic features of K-pop titles have subtle, context-dependent impacts. While not dominant predictors, they contribute to the broader ecosystem of visibility, discoverability, and algorithmic prioritization.

---

## 👥 Contributors

**PM**  
**Savanah 黃月上 (113ZM1003)** – A responsible and organized project manager. She ensured fair task distribution and effective timeline management within the group.

**Writer**  
- **Savanah 黃月上 (113ZM1003)** – Integrated the final report content, handled all data cleaning tasks, and ensured data accuracy.  
- **Copper 童心 (113ZM1005)** – Contributed strong domain knowledge, carefully participated in data cleaning, and was diligent throughout the reporting process.  
- **Gina 黃佳佳 (113ZM1022)** – Completed H1 and H2 sections with great attention to detail. Proactively asked questions and achieved high task completion.  
- **Jubal 陳傑皿 (113ZM1023)** – Took charge of H3 and conclusion writing. Highly proactive in communication and consistently delivered quality work.

---

## 🙏 Acknowledgments

We thank:

- **Professor Pien** – Course guidance  
- **Marcella** – Technical support  
- **CircleChart.kr** – Public data source  
- **OpenAI / ChatGPT** – Thematic classification tool

This project was submitted as part of the Big Data Analytics course at [NCCU/ ICI].

---

## 📚 References

- Maximize Market Research. (2024). *K-pop Events Market*. https://www.maximizemarketresearch.com/market-report/k-pop-events-market/186929/
- El Ouahi, Y. (2020). *Linguistic Strategies in K-pop Globalization*. University of Barcelona. https://diposit.ub.edu/dspace/handle/2445/176497
- Oh, I., & Park, G. (2012). *The Globalization of K-pop*. Popular Music, 31(1), 73–89.
- Whissell, C. (2021). *Changes in Popular Song Titles*. Studies in Linguistics and Literature, 5(4), 140.
- Chang, K.-W. (2023). *Billboard Prediction Using Streaming Data*. https://hdl.handle.net/11296/59j895
- Li et al. (2022). *Playlist Selection Behavior*. Journal of Innovation & Knowledge, 7(3), 100212.
- Official Charts. (2018). *Streaming Changed Song Titles*. https://www.officialcharts.com/chart-news/streaming-has-changed-the-way-that-songs-are-titled-new-research-suggests__22430/
- CircleChart.kr – Weekly Top 200 data source
- OpenAI – ChatGPT API for thematic labeling


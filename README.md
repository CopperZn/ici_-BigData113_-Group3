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


📁 data/
- 「original_data_kpop.rankings」.csv           # Original data scraped from CircleChart.kr
- 「cleaned_data_only.kpop」.csv         # Processed dataset with only Kpop songs
- 「kpop_song.k/e.title」.csv         # Processed dataset with additional variables
- 「Kpop_song.category」.csv         # Processed dataset with song title categorization

📁 src/
- 「data_cleaning」.R                           # R script for data cleaning and preprocessing
```[Uploadinginstall.packages("dplyr")
install.packages("readxl")
library(dplyr)
library(readxl)

#read
kpop_r <- read.csv("kpop_rankings.csv")
kpop_clean <- kpop_r %>%
  filter(artist != "XXXXX", album != "XXXXX", song_title != "XXXXX", artist != "Christopher") 
write.csv(kpop_clean, "kpop_cleaned.csv", row.names = FALSE) 

kpop_clean2 <- kpop_clean %>% filter(artist != "Queen")
kpop_clean3 <- kpop_clean2 %>% filter(artist != "Mariah Carey")

unique(kpop_clean3$artist)
kpop_clean4 <- kpop_clean3 %>% filter(artist != "Adele")

kpop_clean5 <- kpop_clean4 %>% filter(artist != "Khalid, Disclosure", artist != "Liam Payne", artist != "UMI", artist != "Harry Styles", artist != "5 Seconds Of Summer", artist != "Doja Cat", artist != "The Weekend", artist != "BENEE", song_title != "Rain On Me", song_title != "Tango")

unique(kpop_clean5$artist)
kpop_clean6 <- kpop_clean5 %>% filter(artist != "Zac Efron, Zendaya", artist != "RADWIMPS", artist != "aimyon", artist != "Tai Verdes", artist != "imase", artist != "Yuuri", artist != "Miley Cyrus", artist != "Giveon", artist != "Stacey Ryan", artist != "SZA", artist != "Gnarls Barkley")

write.csv(kpop_clean, "kpop_cleaned_v6.csv", row.names = FALSE) 


unique(kpop_clean6$artist)
unique(kpop_clean6$song_title)

kpop_clean7 <- kpop_clean6 %>% filter(artist != "YOASOBI", artist != "XXXXX, Jessie Reyez, Calvin Harris", artist != "Kenshi Yonezu", artist != "Meghan Trainor", artist != "Taylor Swift", artist != "XXXXX, Kim Petras", artist != "Avicii", artist != "OneRepublic", artist != "Ne-Yo", artist != "Mina Okabe", artist != "Benson Boone", artist !="Lil Nas X, Jack Harlow", artist != "Lukas Graham", artist !="Wham!", artist != "Kelly Clarkson, XXXXX")


unique(kpop_clean7$artist)
kpop_clean8 <- kpop_clean7 %>% filter(song_title != "One Right Now", artist != "David Guetta", song_title != "Our Song", artist != "The Weeknd, XXXXX", artist !="Zachary Knowles", artist != "Olivia Rodrigo", artist != "JP Saxe", artist != "Peder Elias", artist != "The Christmas Singer", artist != "Stevie Wonder & Andra Day", artist != "Michael Buble", artist != "Jonas Brothers", artist != "John Legend", artist != "Alessia Cara", artist !="Kelly Clarkson", artist !="Ava Max", artist !="Straight No Chaser", artist !="24kGoldn", artist !="John K", artist !="Cardi B", artist !="salem ilese")                                                                                                            
    

unique(kpop_clean8$artist)                      
kpop_clean9 <- kpop_clean8 %>% filter(artist != "HONNE", artist !="The Weeknd")
write.csv(kpop_clean9, "kpop_cleaned_v9.csv", row.names = FALSE)


best_ranked_songs9 <- kpop_clean9 %>%
  group_by(song_title, artist) %>%
  filter(rank == min(rank)) %>%
  ungroup()

write.csv(best_ranked_songs9, "best_ranked_songs9.csv", row.names = FALSE)



#儲存 OpenAI API 金鑰
api_key <- "Prof. Pien 提供"

response <- POST( #用POST() 傳送一筆 API 請求給 OpenAI
  url = "https://api.openai.com/v1/chat/completions", 
  add_headers(Authorization = paste("Bearer", api_key)), 
  content_type_json(),
  encode = "json",
  body = list(
    model = "gpt-3.5-turbo", #使用 gpt-3.5-turbo 模型
    messages = list(list(role = "system", content = paste0("I want you to do song titles analysis. I will provide you a song list and you will tell me the song is positive, neutral, or negative. The message is here:", ici_df$text[1])),
                    list(role = "user", content = "Is the message is positive, neutral, or negative? Just give me low case positive, neutral, or negative. Don't give me other things and do not write original texts and explanations."))
  ) 
) 


 data_cleaning.R…]()
```

- 「song title_categorization」.R               # R script for preprocessing and song title categorization
```
[Uploading library(dplyr)
library(ggplot2)
library(readxl)

CAT_01 <- read.csv("分類01_done.csv")
CAT_02 <- read.csv("category02_done.csv")


#02 punc
CAT_02 <- CAT_02 %>%
  mutate(Punctuation = ifelse(grepl(custom_punct, k_title), 1, 0))
CAT_02 <- CAT_02 %>%
  mutate(Punctuation = ifelse(grepl(custom_punct, e_title), 1, 0))

#02大寫
CAT_02 <- CAT_02 %>%
  mutate(Capitalize = ifelse(grepl("^[A-Z0-9\\W]+$", e_title), 1, 0))


#02 有無數字
CAT_02 <- CAT_02 %>%
  mutate(Number = ifelse(grepl("[0-9]", e_title), 1, 0))
CAT_02 <- CAT_02 %>%
  mutate(Number = ifelse(grepl("[0-9]", k_title), 1, 0))



###標點符號
custom_punct <- "[[:punct:]=&'@#%*]"

title <- title %>%
  mutate(Punctuation = ifelse(grepl(custom_punct, k_title), 1, 0))
title <- title %>%
  mutate(Punctuation = ifelse(grepl(custom_punct, e_title), 1, 0))


###是否大寫
title <- title %>%
  mutate(Capitalize = ifelse(grepl("^[A-Z0-9\\W]+$", e_title), 1, 0))


###是否有數字
title <- title %>%
  mutate(Number = ifelse(grepl("[0-9]", e_title), 1, 0))
title <- title %>%
  mutate(Number = ifelse(grepl("[0-9]", k_title), 1, 0))


#存檔 & merge
Category_done <- rbind(CAT_01, CAT_02)

write.csv(title, "分類01_done.csv", row.names = FALSE)
write.csv(CAT_02, "分類02_done.csv", row.names = FALSE)
write.csv(Category_done, "Kpop_done.csv", row.names = FALSE)
song title_categorization.R…]()
```
- 「H1」.R               # R script for H1: Title Length
```
[Uplolibrary(dplyr)
library(readxl)
library(ggplot2)

data <- read.csv("Kpop_done.csv")


#H1- Korea song title
data_k <- data %>% 
  filter(k_length > 0) %>%
  select(rank, song_title_clean, k_title, k_length)

median_k <- median(data_k$k_length, na.rm = TRUE)

data_k <- data_k %>% 
  mutate(k_short = k_length < median_k) 
  
mean_k <- data_k %>%
  group_by(k_short) %>%
  summarise(mean_rank = mean(rank))

t.test(rank ~ k_short, data = data_k) #用t檢定：不顯著

#H1- k song title 畫圖
ggplot(data_k, aes(x = k_short, y = rank)) +
  geom_boxplot(outlier.shape = NA, alpha = 0.6) +
  geom_jitter(width = 0.2, alpha = 0.5, color = "blue") +
  scale_y_reverse() +
  labs(
    title = "Korean Title Length vs. Chart Ranking",
    x = "Short Korean Title (TRUE = shorter)",
    y = "Peak Rank (lower = better)"
  )


#H1- K song top50
data_k50 <- data_k %>%
  filter(rank > 0, rank <= 50, k_length > 0)

median_k50 <- median(data_k50$k_length, na.rm = TRUE) #算出前50平均rank
data_k50 <- data_k50 %>%
  mutate(k_short = k_length < median_k50) #分組

mean_k50 <- data_k50 %>%
  group_by(k_short) %>%
  summarise(mean_rank = mean(rank))

t.test(rank ~ k_short, data = data_k50)


#H1- k50 畫圖
ggplot(data_k50, aes(x = k_short, y = rank)) +
  geom_boxplot(outlier.shape = NA, alpha = 0.6) +
  geom_jitter(width = 0.2, alpha = 0.5, color = "light blue") +
  scale_y_reverse() +
  labs(
    title = "Korean Title Length vs. Chart Ranking (Top 50 Only)",
    x = "Short Korean Title (TRUE = shorter)",
    y = "Peak Rank (lower = better)"
  )


#H1- Eng song title
data_e <- data %>% 
  filter(e_length > 0) %>%
  select(rank, song_title_clean, e_title, e_length)

median_e <- median(data_e$e_length, na.rm = TRUE)

data_e <- data_e %>% 
  mutate(e_short = e_length < median_e) 

mean_e <- data_e %>%
  group_by(e_short) %>%
  summarise(mean_rank = mean(rank))

t.test(rank ~ e_short, data = data_e) #用t檢定：不顯著


#H1- e song title 畫圖
ggplot(data_e, aes(x = e_short, y = rank)) +
  geom_boxplot(outlier.shape = NA, alpha = 0.6) +
  geom_jitter(width = 0.2, alpha = 0.5, color = "blue") +
  scale_y_reverse() +
  labs(
    title = "English Title Length vs. Chart Ranking",
    x = "Short English Title (TRUE = shorter)",
    y = "Peak Rank (lower = better)"
  )


#H1- e song top50
data_e50 <- data_e %>%
  filter(rank > 0, rank <= 50, e_length > 0)

median_e50 <- median(data_e50$e_length, na.rm = TRUE) #算出前50平均rank
data_e50 <- data_e50 %>%
  mutate(e_short = e_length < median_e50) #分組

mean_e50 <- data_e50 %>%
  group_by(e_short) %>%
  summarise(mean_rank = mean(rank))

t.test(rank ~ e_short, data = data_e50)


#H1- e50 畫圖
ggplot(data_e50, aes(x = e_short, y = rank)) +
  geom_boxplot(outlier.shape = NA, alpha = 0.6) +
  geom_jitter(width = 0.2, alpha = 0.5, color = "light blue") +
  scale_y_reverse() +
  labs(
    title = "English Title Length vs. Chart Ranking (Top 50 Only)",
    x = "Short english Title (TRUE = shorter)",
    y = "Peak Rank (lower = better)"
  )


####結論圖表
h1_data <- data.frame(
  Group = factor(c("All (Korean)", "All (Korean)",
                   "All (English)", "All (English)",
                   "Top 50 (Korean)", "Top 50 (Korean)",
                   "Top 50 (English)", "Top 50 (English)"),
                 levels = c("All (Korean)", "All (English)", "Top 50 (Korean)", "Top 50 (English)")),
  TitleType = factor(rep(c("Short Title", "Long Title"), 4)),
  AvgRank = c(90.97, 88.61,   # All Korean
              83.05, 84.16,   # All English
              20.02, 21.63,   # Top 50 Korean
              12.63, 13.78)   # Top 50 English
)

ggplot(h1_data, aes(x = Group, y = AvgRank, fill = TitleType)) +
  geom_bar(stat = "identity", position = position_dodge(width = 0.8), width = 0.7, color = "black") +
  scale_y_reverse() +  # 反轉Y軸（越高名次數字越小）
  labs(title = "Average Rank: Short vs Long Titles (Korean & English)",
       y = "Average Chart Rank (Lower is Better)",
       x = "",
       fill = "") +
  theme_minimal(base_size = 13) +
  theme(axis.text.x = element_text(angle = 20, hjust = 1),
        plot.title = element_text(face = "bold", size = 16),
        legend.position = "bottom") +
  scale_fill_manual(values = c("Short Title" = "light blue", "Long Title" = "blue"))


ggsave("h1.png", width = 9, height = 6, dpi = 300)

ading H1 .R…]()
```
- 「H2」.R               # R script for H2: English Presence in Title
```
[Uploading H2.R…](library(dplyr)
library(readxl)
library(ggplot2)

data <- read.csv("Kpop_done.csv")

#H2 full
median_h2 <- data %>%
  group_by(eng_label) %>%
  summarise(mean_rank = mean(rank)) 

cor.test(data$eng_label, data$rank, method = "pearson") #pearson分析

model_h2 <- lm(rank ~ eng_label, data = data) #線性
summary(model)


#H2 full plot
ggplot(data, aes(x = factor(eng_label), y = rank)) +
  geom_boxplot(outlier.shape = NA, alpha = 0.6) +
  geom_jitter(width = 0.2, alpha = 0.5, color = "yellow") +
  scale_y_reverse() +  # 排名越小越前面
  labs(
    title = "Effect of English Title on Song Ranking",
    x = "English in Title (0 = No, 1 = Yes)",
    y = "Ranking (Lower is Better)"
  ) +
  theme_minimal()




#H2 50
data_h2_50 <- data %>%
  filter(rank > 0, rank <= 50) 

median_h2_50 <- data_h2_50 %>%
  group_by(eng_label) %>%
  summarise(mean_rank = mean(rank))  #算出分組平均


cor.test(data_h2_50$eng_label, data_h2_50$rank, method = "pearson") #pearson分析

model_h2_50 <- lm(rank ~ eng_label, data = data_h2_50) #線性
summary(model_h2_50)


#H2_50 plot
ggplot(data, aes(x = factor(eng_label), y = rank)) +
  geom_boxplot(outlier.shape = NA, alpha = 0.6) +
  geom_jitter(width = 0.2, alpha = 0.5, color = "orange") +
  scale_y_reverse() +  # 排名越小越前面
  labs(
    title = "Effect of English Title on Song Ranking(Top 50 Only)",
    x = "English in Title (0 = No, 1 = Yes)",
    y = "Ranking (Lower is Better)"
  ) +
  theme_minimal()


#H2 總圖表
h2_data <- data.frame(
  Group = factor(c("All Songs", "All Songs", "Top 50", "Top 50"),
                 levels = c("All Songs", "Top 50")),
  TitleType = factor(c("No English", "English", "No English", "English"),
                     levels = c("No English", "English")),
  AvgRank = c(89.18, 86.04, 21.19, 14.41)
)

# 繪圖
ggplot(h2_data, aes(x = Group, y = AvgRank, fill = TitleType)) +
  geom_bar(stat = "identity", position = position_dodge(width = 0.7), width = 0.6, color = "black") +
  scale_y_reverse(limits = c(100, 0)) +  # 越小越好，故反轉Y軸
  scale_fill_manual(values = c("No English" = "yellow", "English" = "orange")) +
  labs(title = "Average Chart Rank: Songs With vs. Without English in Title",
       y = "Average Chart Rank (Lower is Better)",
       x = NULL,
       fill = "") +
  theme_minimal(base_size = 14) +
  theme(axis.text.x = element_text(size = 12),
        plot.title = element_text(face = "bold", size = 16),
        legend.position = "bottom")

ggsave("h2.png", width = 9, height = 6, dpi = 300)

)

```
- 「H3」.R               # R script for H3: Thematic and Stylistic Features
```
[Uploading H3.R…# Install required packages if not already installed
install.packages("dplyr")
install.packages("rstatix")

# Load libraries
library(dplyr)
library(rstatix)
library(ggplot2)

# Set working directory
setwd(dirname(rstudioapi::getActiveDocumentContext()$path))

# Load data
h3_data <- read.csv("Kpop_done.csv", stringsAsFactors = FALSE)

# Select relevant columns in the initial data
theme_vars <- c("friendship", "Self.Growth.Power", "Love", "vocalization", "Season", "Color", "Punctuation", "Capitalize", "Number")

# Check for the samples size in each column (n > 30), in order to meet t-test sample size requirement
counts <- sapply(h3_data[theme_vars], function(col) sum(col == 1, na.rm = TRUE))
print(counts)

# Newly selected column (with n > 30)
theme_vars <- c("friendship", "Self.Growth.Power", "Love", "Season", "Color", "Punctuation", "Capitalize")

# Make sure h3_data has rank plus numeric 0/1 for each theme
h3_data <- h3_data %>%
  select(rank, all_of(theme_vars)) %>%
  mutate(across(all_of(theme_vars), ~ as.integer(. == 1)))


# Descriptive calculation -------------------------------------------------

for (v in theme_vars) {
  cat("\n\n===== Descriptives for", v, "=====\n")
  
  # Dynamically group_by the column named by v
  stats <- h3_data %>%
    group_by(theme = .data[[v]]) %>% 
    summarise(
      n = n(),
      mean_rank = mean(rank, na.rm = TRUE),
      sd_rank = sd(rank, na.rm = TRUE),
      median = median(rank, na.rm = TRUE)
    )
  
  print(stats)
}

# T-test loop calculation for each columns --------------------------------

for (v in theme_vars) {
  # 1. Check there’s at least one 0 and one 1
  tbl <- table(h3_data[[v]])
  if (!all(c(0,1) %in% as.numeric(names(tbl)))) {
    cat("\n\n--- Skipping", v, ": only one level present (",
        paste(names(tbl), collapse = ", "), ")\n")
    next
  }
  
  # 2. Convert to factor
  h3_data[[v]] <- factor(
    h3_data[[v]],
    levels = c(0, 1),
    labels = c("Other", "Yes")
  )
  
  cat("\n\n========== Testing:", v, "==========\n")
  
  # 3. Build formula
  fml <- as.formula(paste("rank ~", v))
  
  # 4. T‑test calculation
  print(t_test(data = h3_data, formula = fml, var.equal = FALSE))
  
}

# Overall graph -----------------------------------------------------------

# Calculate mean ranks for each feature 
h3_summary <- data.frame(
  Feature = factor(c("Friendship", "Self.Growth.Power", "Love", "Season", "Color", "Punctuation", "Capitalization"),
                   levels = c("Friendship", "Self.Growth.Power", "Love", "Season", "Color", "Punctuation", "Capitalization")),
  With_Feature = c(93.7, 87.7, 87.3, 87.7, 87.3, 87.4, 89.0),
  Without_Feature = c(87.4, 84.3, 89.4, 84.9, 107., 98.1, 68.8)
)

# Reshape data for ggplot2
h3_long <- tidyr::pivot_longer(h3_summary, cols = c("With_Feature", "Without_Feature"),
                               names_to = "Feature_Presence", values_to = "Average_Rank")

# Create bar chart
ggplot(h3_long, aes(x = Feature, y = Average_Rank, fill = Feature_Presence)) +
  geom_bar(stat = "identity", position = position_dodge(width = 0.7), width = 0.6) +
  scale_y_reverse() +
  scale_fill_manual(values = c("With_Feature" = "#2E8B57", "Without_Feature" = "#90EE90")) +
  labs(
    title = "Average Chart Rank by Thematic/Stylistic Feature",
    subtitle = "(Lower Rank = Better Performance)",
    x = "Title Feature",
    y = "Average Rank",
    fill = ""
  ) +
  theme_minimal(base_size = 12) +
  theme(axis.text.x = element_text(angle = 45, hjust = 1),
        plot.title = element_text(face = "bold", size = 14))

ggsave("h2.png", width = 9, height = 6, dpi = 300)


]()

```
📁 figures/
 - [H1](https://github.com/user-attachments/assets/25ccabd5-c662-44f5-b124-3157e48708a7) # Title length vs. rank
    - [H1_k_title](https://github.com/user-attachments/assets/01bc5a36-22d8-4ca1-840a-4b0e8706252f) # Full dataset of Korean song title
    - [H1_k50](https://github.com/user-attachments/assets/88a74cc8-d1e2-43b0-80f0-87c54bda76e7) # Top 50 dataset of Korean song title
    - [H1_e_title](https://github.com/user-attachments/assets/ff6d9380-a37b-41ba-ba2e-1bd2a3847f57) # Full dataset of English song title
    - [H1_e50](https://github.com/user-attachments/assets/e9661f5a-f5d2-4005-85a6-e02800b75bca) # Top 50 dataset of English song title
 - [H2](https://github.com/user-attachments/assets/58ab2fac-5ca0-44e1-90f8-3de0ba849291) # English presence and ranking
    - [H2_top50](https://github.com/user-attachments/assets/6b84bdb1-7adb-4565-b492-18d1b0061d39) # Full dataset of English song title
    - [H2_full](https://github.com/user-attachments/assets/f7e72b16-be78-4f6b-831d-9a5b0525c7d1) # Top 50 dataset of English song title
 - [H3](https://github.com/user-attachments/assets/f4730110-8af3-4d62-a2e0-7a0c1bf2c330) # Results by thematic group

📄 [Big Data_ K-pop award trends_ group3.pdf](https://github.com/user-attachments/files/20647469/Big.Data_.K-pop.award.trends_.group3.pdf) # Final written report

📄 [BDA_kpop](https://github.com/user-attachments/assets/c7d15651-7652-4c1c-b7b0-055cf11a4c58) # Poster


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


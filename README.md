# DEMYSTIFYING-SUCCESS-A-DATA-DRIVEN-EXPLORATION-OF-TOP-YOUTUBE-CREATORS

## Table of Contents
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning/Preparation](#data-cleaningpreparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results/Findings](#resultsfindings)
- [Limitations](#limitations)

### Project Overview

---

This project provides valuable insights into the factors that drive success on YouTube. By analyzing data on top creators and evaluating the impact of various factors, we can offer a comprehensive guide for aspiring YouTube creators. These insights will help them optimize their strategies to achieve greater success on the platform.

### Data Sources
---
*The primary source of data is Global YouTube Statistics.csv, this is an open source data that can be freely downloaded from an open source.*

### Tools
  - Microsoft Excel - Univariate Analysis
  - Power Query - Data Cleaning and Data Preparation
  - Microsoft PowerBI - Data Visualization

### Data Cleaning/Preparation

In the data preparation phase, we performed the following tasks:
1. Data loading and inspection
2. Handling missing values
3. Data cleaning and formatting

### Exploratory Data Analysis

EDA involved exploring the datasets to answer key questions such as:

- What are the average subscribers in the dataset
- What are the total video category
- How are youtubers distributed across different countries
- Who are the the top 10 youtubers with the most subscribers
- What are the trending channel types amongst the top youtubers
- Youtuber trend by channel creation year
- Who are the top 10 youtubers with the most video views
- What are the top 10 most populated countries

### Data Analysis

Included below is some of the code I worked in order to acheive accurate results in my analyis

To merge our date columns into one, we used;
```F#
let
#"Inserted Merged Column" = Table.AddColumn(#"Removed Errors", "Merged", each Text.Combine({Text.From([created_year], "en-US"), [created_month], Text.From([created_date], "en-US")}, "/"), type text)
in #"Inserted Merged Column"
```

For our data cleaning in the Youtuber column, we used;
```F#
let
 #"Replaced Value" = Table.ReplaceValue(#"Changed Type","¿½ï¿½ï¿½","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value1" = Table.ReplaceValue(#"Replaced Value","ï¿½ï¿½","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value2" = Table.ReplaceValue(#"Replaced Value1","ýýý","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value3" = Table.ReplaceValue(#"Replaced Value2","ýý","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value4" = Table.ReplaceValue(#"Replaced Value3","  ý | ","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value5" = Table.ReplaceValue(#"Replaced Value4","¿½ï","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value6" = Table.ReplaceValue(#"Replaced Value5"," [ïïï¿","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value7" = Table.ReplaceValue(#"Replaced Value6"," ý","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value8" = Table.ReplaceValue(#"Replaced Value7",".ïï¿½","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value9" = Table.ReplaceValue(#"Replaced Value8","¿","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value10" = Table.ReplaceValue(#"Replaced Value9"," : ïïïï","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value11" = Table.ReplaceValue(#"Replaced Value10","ý","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value12" = Table.ReplaceValue(#"Replaced Value11"," - ","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value13" = Table.ReplaceValue(#"Replaced Value12"," / ïï½","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value14" = Table.ReplaceValue(#"Replaced Value13","!","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value15" = Table.ReplaceValue(#"Replaced Value14"," /ï","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value16" = Table.ReplaceValue(#"Replaced Value15","½","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value17" = Table.ReplaceValue(#"Replaced Value16","[ïï","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value18" = Table.ReplaceValue(#"Replaced Value17"," (ïï","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value19" = Table.ReplaceValue(#"Replaced Value18"," ïï","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value20" = Table.ReplaceValue(#"Replaced Value19","?","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value21" = Table.ReplaceValue(#"Replaced Value20"," | ","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value22" = Table.ReplaceValue(#"Replaced Value21","/","",Replacer.ReplaceText,{"Youtuber"}),
    #"Replaced Value23" = Table.ReplaceValue(#"Replaced Value22","  I  ","",Replacer.ReplaceText,{"Youtuber"}),
    #"Trimmed Text" = Table.TransformColumns(#"Replaced Value23",{{"Youtuber", Text.Trim, type text}})
in #"Trimmed Text"
```

### Results/Findings
The analysis results are summarized as follows;
- The average subscriber count in the dataset is 22.99 million.
- The data identified 19 video categories on YouTube.
- The United States leads the pack with 311 YouTubers, followed by India with 168 and Brazil with 61
- Entertainment accounts for the major channel type at 303, followed by Music at 215, and People at 101
- In 2014, YouTube experienced a significant trend increase with 98 counts (9.91%), largely due to the introduction of YouTube Music, which improved user experience and expanded music streaming capabilities. However, the trend declined to 30 counts in 2020, primarily because of the COVID-19 pandemic, which disrupted content production, and the rise of other platforms such as TikTok.
- T-Series claims the throne for most-viewed YouTube channel, boasting a jaw-dropping 228 billion views! Cocomelon Nursery Rhymes follows closely behind with 164 billion views, while SET India takes the third spot at 148 billion views.
- While China maintains its position as the world's most populous country with 1.4 billion people, India follows closely behind with a population of 1.37 billion, with the United States ranking third at 330 million.

### Limitations
- YouTube data can be inconsistent or inaccurate. Titles, descriptions, and categorization might be misleading or user-generated, impacting the accuracy of your conclusions.
-  YouTube is constantly changing, with new features and trends emerging. Your analysis might need to be updated regularly to stay relevant.

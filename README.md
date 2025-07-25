# 🚀 Indian Startups Data Analysis

This project presents a comprehensive analysis of the Indian startup ecosystem using data sourced from Kaggle. It focuses on understanding which industries are booming, where funding is concentrated, and how the startup scene is evolving across various sectors.

## 📌 Overview

Startups are the backbone of innovation in India. With thousands of new ventures emerging each year, this project explores trends and insights such as:

- Which industry dominates the startup scene?
- Where is the funding going?
- Which cities are startup hotspots?
- What patterns emerge from the data?

## 🛠 Tech Stack

- **📊 Excel** – Initial data cleaning and inspection  
- **🐍 Python** – Data preprocessing and exploratory data analysis using Pandas & Matplotlib  
- **📈 Power BI** – Interactive dashboards and visual storytelling

## 📁 Dataset

- Sourced from **Kaggle**  
- Includes startup name, industry vertical, sub-category, city location, funding amount, investors, and funding round

https://www.kaggle.com/datasets/sudalairajkumar/indian-startup-funding

## ✨ Key Features

- Cleaned and transformed raw startup data
- Identified top industries and cities for startups
- Analyzed investment trends and funding rounds
- Created dynamic visual dashboards using Power BI


## 📈 Insights

- 📌 **Technology** and **Finance** industries received the most funding
- 💸 Major funding rounds were concentrated in **Bangalore** and **Delhi NCR**
- 📉 Certain industries saw a decline in investments post-2020
- 🔍 Angel and Seed funding were the most common funding types

Error-pathway:
1. While cleaning and pre-processing the data I came across many errors , where I took help of some external websites inorder to fix them
2. To format the Date column properly
3. Used some techniques to align the dashboard , took some inspiration
4. Discovered new items in POWER BI and excel

Clone the repository:
   ```bash
 git clone https://github.com/SamuelBen07/indian-startups-analysis.git

Code:
import pandas as pd
df=pd.read_csv('/startjobs.csv')
df.head()
print(df.columns)
df['Amount in USD'] = df['Amount in USD'].astype(str).str.replace(',', '', regex=False)
df['Amount in USD'] = pd.to_numeric(df['Amount in USD'], errors='coerce')
top_startups=df.groupby('Startup Name')['Amount in USD'].sum().nlargest(10)
print(top_startups)
df.head()
df['Amount in USD']=df['Amount in USD'].astype(str)
df['Amount in USD']=df['Amount in USD'].str.replace(',','')
df['Amount in USD']=pd.to_numeric(df['Amount in USD'],errors='coerce')
top_startups=df.groupby('Startup Name')['Amount in USD'].sum().sort_values(ascending=False).head(10)
print(top_startups)
top_cities=df.groupby('City Location')['Amount in USD'].sum().sort_values(ascending=False).head(10)
print(top_cities)
df.columns=df.columns.str.strip()
top_cities=df.groupby('City Location').sum().sort_values(by=None, ascending=False).head(10)
print(top_cities) 
investment=df['InvestmentnType'].value_counts()
print(investment)

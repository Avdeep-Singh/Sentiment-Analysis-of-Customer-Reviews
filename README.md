# Sentiment Analysis of Customer Reviews

This project explores customer sentiment analysis using a sentiment lexicon (TextBlob) to analyze the polarity (positive, negative, or neutral) and subjectivity (opinion or fact) of customer remarks in a dataset (`sentiments.csv`).

## Data Loading and Exploration

* The data was loaded from a CSV file (`sentiments.csv`) using pandas.
* The initial shape (`data.shape`) and first few rows (`data.head()`) were examined to understand the data structure and content.
* Basic information about data types and potential missing values was obtained using `data.info()`.

## Sentiment Analysis with TextBlob

* TextBlob, a Python library for processing textual data, was employed for sentiment analysis.
* Two lambda functions were created to calculate sentiment polarity (positive or negative) and subjectivity (opinion or fact) for each remark:
    * `pol = lambda x: TextBlob(x).sentiment.polarity`
    * `sub = lambda x: TextBlob(x).sentiment.subjectivity`
* These functions were applied to the `ï»¿Remarks` column using `data['polarity'] = data['ï»¿Remarks'].apply(pol)` and similar for subjectivity.

## Merging Dataframes

* Another CSV file (`full sent.csv`), presumably containing customer names, was loaded and explored (`data_name.shape`, `data_name.head()`).
* The two DataFrames (`data_name` and `data`) were merged based on a shared index to associate customer names with remarks and sentiment scores (`data = pd.merge(data_name, data, left_index=True, right_index=True)`).

## Visualizing Sentiment Distribution

* A scatter plot using Matplotlib was created to visualize the distribution of sentiment polarity and subjectivity for each remark.
* The plot has the x-axis representing polarity (negative to positive) and the y-axis representing subjectivity (facts to opinions).

## Sentiment Classification (Positive, Negative, Neutral)

* A new column named `pos_or_neg` was added to the DataFrame to categorize remarks as positive, negative, or neutral based on their polarity scores.
* The classification logic was implemented using a loop to iterate through each row and assign labels (`"negative"`, `"neutral"`, or `"Positive"`) based on the polarity value.

## Analyzing Positive and Negative Reviews

* Separate DataFrames (`df_negative` and `df_Positive`) were created to isolate negative and positive customer remarks, respectively.
* Loops were used to populate these DataFrames with corresponding remarks and customer names based on the sentiment category (`"pos_or_neg"`) of each data point.

## Identifying Frequent Words in Neutral and Positive Reviews

* Word frequency analysis was performed on the combined text from neutral and positive remarks using `Counter` from the `collections` library.
* The most common 100 words were identified for each sentiment category.

## Sentiment vs. Factuality Classification (Opinion vs. Fact)

* Another new column named `Ope_or_fac` was added to categorize remarks as opinions or facts based on their subjectivity scores.
* Similar logic as sentiment classification was applied using a loop to assign labels (`"opnion"`, `"neutral"`, or `"fact"`) to this column based on the subjectivity value.

## Analyzing Opinionated and Factual Reviews

* Separate DataFrames (`df_opnion` and `df_fact`) were created to isolate opinionated and factual customer remarks, respectively.
* Loops were used to populate these DataFrames with corresponding remarks and customer names based on the sentiment category (`"Ope_or_fac"`) of each data point.

## Exporting Positive Reviews

* The DataFrame containing positive reviews (`df_Positive`) was exported to a CSV file (`output.csv`) using `to_csv` and made available for download using Colab's file download functionality.

This sentiment analysis project provides insights into customer sentiment and the characteristics of positive, negative, neutral, opinionated, and factual remarks within the dataset.

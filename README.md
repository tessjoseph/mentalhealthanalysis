# Mental Health on the Map

## Overview

##Collaborators
Anvi Rakshe 
Shefali Verma

This project aims to examine the underlying factors contributing to mental health distress within the American population, focusing on data from 2022 covering all 50 states. By analyzing state-wide health metrics provided by America's Health Rankings, we aim to find patterns shared among states that report high levels of mental health issues. Additionally, we explore ways to identify at-risk communities that might be underreporting mental health concerns due to cultural or stigma-related barriers.

## Data

The project utilizes a comprehensive dataset from America's Health Rankings Website for the year 2022, which includes a wide range of indicators that may have implications on the prevalence of mental health issues at the state level. The dataset includes the following components:

- Frequent Mental Distress Score: Percentage of adults in the state who reported their mental health was not good for more than 14 days in the past month.
- Health Distress Indicators: Frequency and intensity of mental distress experienced by the population.
- Healthcare Access: Availability and quality of mental healthcare services, including the number of mental health providers per capita and the percentage of residents with health insurance coverage.
- Socioeconomic Factors: Employment rates, education levels, and income inequality.
- Lifestyle and Community Metrics: Physical activity, diet, substance abuse, and community support.
- Environmental Influences: Air quality and urbanization.

## Pipeline

The project follows these steps:

1. **Data Retrieval**: A function `scrape_state_data(state_code)` is used to build a dataframe for each state based on the two-letter state code.
2. **Dataframe Generation and Concatenation**: A dictionary with all states and respective state codes is used to generate 50 dataframes using the `scrape_state_data` function. These dataframes are then combined into one comprehensive dataframe.
3. **Data Cleaning**: Missing values are handled, rows with too many missing values are removed, values are converted to numerical format, and unnecessary symbols are removed from feature names.

## Methodology

1. **Data Visualization**: Scatter plots are created to visualize the relationship between each health metric and frequent mental distress.
2. **Correlation Analysis**: A correlation matrix is constructed using scaled values to determine which health metrics have a significant relationship with frequent mental distress (correlation > |0.5|).
3. **Prediction Model**: The K-nearest neighbors method is used to model the relationship between the selected features and predict mental distress outcomes. A function `predict_mental_distress(selected_feature_values)` is implemented to take values for the chosen health metrics and return a predicted frequent mental distress score.

## Results

The project identifies several health and social metrics that have the highest correlations with frequent mental distress, such as social and economic factors, firearm deaths, poverty, food insecurity, social support, adverse childhood experiences, access to clinical care and dental visits, flu vaccinations, at-risk behaviors, teen births, smoking and tobacco usage, e-cigarette usage, general health outcomes, drug usage, physical health and distress, chronic conditions, arthritis, cardiovascular, kidney, and pulmonary diseases, depression, diabetes, and high blood pressure.

The machine learning model achieved an R-squared value of 0.71 and a Mean Squared Error of 0.8445, indicating a fair fit. By inputting arbitrary feature values, the model can predict frequent mental distress scores, allowing for the identification of communities with low positive mental health outcomes.

## Limitations

It is important to note that the data and model are based on American populations, and the factors influencing mental health distress may differ in other countries and cultures due to various reasons, such as ongoing wars, weather conditions, cultural behaviors, and more.

## Future Work

The team suggests exploring more advanced techniques, such as Random Forests, to gain a deeper understanding of the most influential factors on mental health distress. This could facilitate the identification of commonalities among affected groups and foster the development of targeted public health strategies.

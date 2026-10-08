# Amman Real Estate Price Prediction & Market Analytics

An end-to-end data science project that collects real estate listings from the Jordanian housing market, predicts property prices using Gradient Boosting, and analyzes market trends through interactive Power BI dashboards.

The project combines **ParseHub for web scraping**, **RapidMiner for machine learning**, and **Power BI for data preprocessing, feature engineering, and visualization** to help homeowners make more informed property pricing decisions.

## Problem Statement

Homeowners in Amman often struggle to estimate appropriate selling prices due to limited access to structured market information. Overpricing can lead to longer selling periods, while underpricing may result in financial losses.

This project aims to address this challenge by:

- Collecting and structuring real estate market data.
- Building a machine learning model to estimate property prices.
- Identifying relationships between location, property characteristics, and prices.
- Providing interactive dashboards to support data-driven pricing decisions.

## Tools & Technologies

| Tool | Purpose |
|------|---------|
| ParseHub | Web scraping and automated data extraction |
| RapidMiner | Data preprocessing, model training, and evaluation |
| Gradient Boosting | House price prediction |
| Power BI | Data cleaning, analysis, and interactive dashboards |
| DAX | Feature engineering and dynamic KPI calculations |
| CSV | Storage and transfer of extracted listing data |

## Dataset

The dataset was collected from [Homes Jordan](https://www.homes-jordan.com/en) using ParseHub.

- **Total records:** 380 property listings
- **Original features:** 11
- **Market:** Jordan, with analysis focused on Amman
- **Target variable:** Property price (JOD)

### Collected Features

The extracted property attributes include:

- Property location
- Number of bedrooms
- Property area (sqm)
- Property price
- Furniture status
- Floor number
- Number of parking spaces
- Built-in swimming pool availability
- Floor type (Normal, Duplex, Full Floor)
- Outdoor area availability

The collected listings were exported to CSV for further processing.

## Project Workflow

### 1. Data Collection — ParseHub

Configured a web scraping workflow to extract property information from Homes Jordan.

The extraction process involved:

1. Selecting relevant property attributes.
2. Configuring relative selections to associate attributes with individual listings.
3. Setting up pagination to collect data across multiple listing pages.
4. Exporting the collected records into a structured CSV dataset.

### 2. Data Preprocessing & Feature Engineering — Power BI

Prepared the extracted dataset by:

- Handling missing values.
- Standardizing inconsistent categorical values.
- Correcting data types.
- Creating additional analytical features using DAX.

**Engineered features:**

| Feature | Description |
|---------|-------------|
| Price per Sqm | Property price divided by its area |
| Luxury Score | Property classification based on characteristics such as swimming pool, furniture status, and outdoor area |
| Floor Index | Numerical representation of floor levels |
| Floor Category | Groups floor levels into four broader categories for easier analysis |

These features enabled more meaningful comparisons between properties and improved dashboard interpretability.

### 3. Machine Learning — RapidMiner

Developed a regression pipeline to estimate property prices using Gradient Boosting.

**Modeling pipeline:**

1. Import the cleaned dataset.
2. Normalize the property area feature.
3. Encode categorical attributes, including location and floor type, using dummy coding.
4. Set property price as the prediction target.
5. Split the dataset into 80% training and 20% testing.
6. Train and tune a Gradient Boosting regression model.
7. Evaluate predictions on the test set.

### Model Performance

| Metric | Result |
|--------|--------|
| Algorithm | Gradient Boosting Regression |
| Train/Test Split | 80% / 20% |
| Squared Correlation | 0.85 |
| RMSE | Approximately 36,114 JOD |

The model achieved a squared correlation of approximately **0.85**, indicating a strong relationship between predicted and actual property prices.

However, the RMSE of approximately **36K JOD** indicates that prediction errors remain financially significant, particularly for lower-priced properties.

The model demonstrates the potential of machine learning for real estate valuation but requires further improvements before being used for high-stakes pricing decisions.

### 4. Interactive Market Analytics — Power BI

Developed an interactive dashboard to investigate the relationships between property characteristics and market prices.

**Dashboard components:**

- Average property price KPI.
- Average price per square meter KPI.
- Average property price by location.
- Average price per square meter by location.
- Scatter plot comparing property area and price, segmented by luxury classification.
- Floor category distribution.
- Decomposition tree for investigating price-related factors.
- Interactive slicers for location, furniture status, floor category, and luxury score.
- Natural-language Q&A for querying the dataset.

The dashboard supports cross-filtering, allowing users to select data points and dynamically update related visualizations.

## Key Insights

The following findings are based on the **380 collected property listings** and should not be interpreted as representative of the entire Jordanian real estate market.

### 1. Location Is a Major Pricing Factor

The analysis revealed substantial differences in property prices across Amman.

- **5th Circle** recorded the highest observed average price per square meter at approximately **4,700 JOD**.
- **Abdali** followed at approximately **2,000 JOD/sqm**.
- Several other analyzed locations ranged between approximately **1,000 and 1,400 JOD/sqm**.

The difference suggests that location-specific comparisons are essential when evaluating property prices.

### 2. Property Area Is Positively Associated With Price

Scatter plot analysis showed a strong positive relationship between property area and selling price.

- Larger properties generally appeared at higher price points.
- Luxury-classified properties were more prominent in higher-priced segments, particularly beyond approximately 300 sqm.
- Standard properties were more concentrated in lower price ranges.

This suggests that property area and luxury-related characteristics should be considered together during valuation.

### 3. High-Floor Properties Showed Higher Average Prices per Sqm

The floor category analysis indicated that:

- High-floor properties recorded an average price of approximately **1,110 JOD/sqm**.
- They represented approximately **29% of the analyzed floor-category distribution**.

This suggests that floor level may contribute to pricing differences, although further analysis would be required to isolate its effect from location, size, and other property attributes.

### 4. Average Price Alone Can Be Misleading

Across the collected dataset:

| Metric | Value |
|--------|-------|
| Average Property Price | 200,860 JOD |
| Average Price per Sqm | 956.67 JOD |

The average property price can be heavily influenced by expensive or unusually large properties.

Price per square meter provides an additional comparison metric, particularly when evaluating properties of different sizes.

However, it should still be interpreted alongside location and property characteristics.

### 5. Luxury Classification Helps Segment the Market

By engineering a luxury score based on available property characteristics, the analysis distinguished standard and luxury-classified listings.

This segmentation helps identify differences in pricing patterns and provides a basis for more targeted property comparisons.

## Business Recommendations

Based on the analysis, the following recommendations were proposed:

1. **Use location-specific price benchmarks:** Homeowners should compare properties within similar neighborhoods rather than relying only on the overall market average.

2. **Consider price per square meter:** Combine price-per-sqm comparisons with property size, floor level, and luxury-related characteristics.

3. **Introduce a property price estimator:** Integrate a machine learning prediction tool into a real estate platform to provide data-driven price estimates.

4. **Support interactive market exploration:** Provide dashboards and natural-language querying so non-technical users can investigate property prices.

5. **Segment standard and luxury properties:** Use property characteristics to create more relevant comparisons and targeted marketing strategies.

## Limitations & Future Improvements

Although the project demonstrates a complete data science workflow, several limitations remain.

**Current limitations:**

- The dataset contains only 380 listings.
- Data was collected from a single real estate website.
- Listed prices may differ from final transaction prices.
- The model's RMSE remains relatively high.
- Natural-language Q&A functionality was not systematically evaluated.
- Market findings may be affected by sampling bias and unusually expensive properties.

**Potential improvements:**

- Expand data collection across multiple real estate platforms.
- Collect additional features such as property age, building condition, and proximity to services.
- Compare Gradient Boosting against other regression algorithms.
- Perform cross-validation and more extensive hyperparameter tuning.
- Evaluate errors separately across different price ranges and neighborhoods.
- Develop a user-facing interface for entering property details and receiving price estimates.
- Periodically update the dataset to reflect changing market conditions.

## Conclusion

This project demonstrates how web scraping, machine learning, and business intelligence can be combined into an end-to-end real estate analytics workflow.

By processing **380 property listings**, training a **Gradient Boosting regression model**, and developing an **interactive Power BI dashboard**, the project transforms unstructured property listings into actionable market insights.

The results highlight the importance of location, property area, and luxury-related characteristics in real estate pricing, while demonstrating both the potential and limitations of data-driven property valuation.

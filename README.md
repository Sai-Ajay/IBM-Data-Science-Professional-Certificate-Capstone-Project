# IBM Data Science Professional Certificate Capstone Project

Welcome to the **IBM Data Science Professional Certificate Capstone Project** repository. This document provides an overview of the project’s objectives, methodology, and key results, along with instructions on how to replicate or build upon the work. The core focus is to predict whether the first stage of a SpaceX Falcon 9 rocket will land successfully, which is crucial for estimating launch costs more accurately. This project demonstrates the end-to-end data science workflow: data collection, wrangling, exploratory analysis, visualization, interactive dashboard creation, and predictive modeling.

---

## 1. Overview

SpaceX advertises Falcon 9 rocket launches at a significantly lower cost than other providers—primarily due to its ability to reuse the rocket’s first stage. By predicting whether the first stage will land successfully, organizations can better estimate launch costs and make more informed bidding decisions.

**Key questions addressed:**
1. What factors (e.g., payload, orbit type, launch site) correlate with a successful first-stage landing?
2. How can we visualize launch data to spot trends and gain insights?
3. Which classification model offers the highest accuracy for predicting first-stage landing success?

---

## 2. Project Structure

A typical layout for the project’s notebooks, scripts, and resources might be:

```
.
├── 1. Data Collection using SpaceX API.ipynb
├── 2. Web Scraping from Wikipedia.ipynb
├── 3. Data Wrangling.ipynb
├── 4. EDA using SQL.ipynb
├── 5. EDA with Data Visualisation.ipynb
├── 6. Interactive Visual Analytics using Folium.ipynb
├── 7. Interactive Dashboard using Plotly Dash.py
├── 8. Machine Learning Prediction Lab.ipynb
├── README.md
└── requirements.txt
```

---

## 3. Data Collection

### SpaceX API
1. A GET request is made to the SpaceX API to retrieve launch data in JSON format.  
2. Relevant fields (e.g., booster version, payload mass, orbit, outcome, longitude, latitude) are extracted and stored in a Pandas DataFrame.  
3. The dataset is filtered to include only Falcon 9 launches, missing values are handled, and the DataFrame is cleaned for further analysis.

### Web Scraping (Wikipedia)
1. A GET request to the Falcon 9 Launch Wikipedia page retrieves HTML content.  
2. BeautifulSoup extracts table elements and relevant fields (e.g., flight number, date/time, customer).  
3. The extracted data is consolidated into a Pandas DataFrame.  
4. Both datasets are ultimately merged and prepared for Exploratory Data Analysis.

---

## 4. Data Wrangling & Exploratory Analysis

### 4.1 Data Wrangling
- **Labeling Outcomes**: Landing outcomes such as *True Ocean*, *True RTLS*, *True ASDS*, etc., are converted into binary labels: `1` for successful landings and `0` for failures.  
- **Initial Insights**: Basic counts and summaries help show launch frequencies at each site and highlight relationships between orbit types and landing outcomes.

### 4.2 Exploratory Data Analysis (EDA)
- **SQL-based EDA**: Key queries provide insights such as total payload mass by specific boosters, average payload mass per booster version, and historical successful landing trends.  
- **Data Visualizations**: Scatter plots, bar charts, and line charts reveal patterns, including success rates by launch site and orbit type, as well as yearly landing trends.

**Notable Observations**:
- Launches with higher payloads can have lower success rates (though sample size matters).  
- Certain orbit types (e.g., GEO, HEO, ES-L1) showed a 100% success rate—albeit with fewer data points.  
- Over time, overall success rates trended upward.

---

## 5. Interactive Visualizations

### 5.1 Folium Maps
- Maps show the geographic placement of all launch sites (near coasts and close to the equator).  
- Markers indicate success (green) vs. failure (red) at each site; marker clusters help quickly visualize launch frequencies and outcomes.  
- Lines show distances to major infrastructure (e.g., railways and highways). This highlights how launch sites balance supply access and safety distance from populated areas.

### 5.2 Plotly Dash Dashboard
- **Pie Chart**: Compares the total successful launches at each site, with dropdown filters to drill down into specific sites’ success vs. failure rates.  
- **Scatter Plot**: Explores correlations between payload mass and success outcomes. A range slider and site-specific dropdown allow flexible filtering.

---

## 6. Predictive Modeling

Four main classification algorithms were explored:
1. **Logistic Regression**  
2. **Support Vector Machine (SVM)**  
3. **Decision Tree**  
4. **K-Nearest Neighbors (KNN)**  

**Workflow**:
1. Data standardization and train-test split (80% training, 20% testing).  
2. Hyperparameter tuning via GridSearchCV.  
3. Model evaluation through accuracy scores and confusion matrices.

**Key Result**:  
- **Decision Tree** emerged as the best model overall, with a highest cross-validation score of about **87.7%** and a test accuracy of **83.3%**, matching the other models’ test accuracy but outperforming on tuned hyperparameters.

---

## 7. Usage Instructions

1. **Clone the Repository**  
   ```bash
   git clone https://github.com/Sai-Ajay/ibm-data-science-capstone.git
   cd ibm-data-science-capstone
   ```
2. **Install Dependencies**  
   ```bash
   pip install -r requirements.txt
   ```
3. **Run Notebooks**  
   Use [Jupyter Notebook](https://jupyter.org/) or [JupyterLab](https://jupyterlab.readthedocs.io/) to open and run each notebook in sequential order:
   1. `1. Data Collection using SpaceX API.ipynb`
   2. `2. Web Scraping from Wikipedia.ipynb`
   3. ...
4. **Explore Interactive Visualizations**  
   - To run the Folium or Plotly Dash scripts, execute the respective notebooks/scripts.  
   - For the Dash app, navigate to the local URL provided in your terminal after running the `.py` file.

---

## 8. Conclusions

- **Increasing Success Trend**: Overall success rates for the Falcon 9 first-stage landings have trended upward over the years.  
- **Key Launch Sites**: KSC LC-39A hosts the highest count of successful landings, while other sites also see improved performance over time.  
- **Predictive Model**: Decision Trees demonstrated the best balance of accuracy and hyperparameter performance, making them a strong choice for classifying launch outcomes.  
- **Future Work**: Incorporate more data (e.g., weather conditions, flight specifics) to enhance model performance.

---

## 9. Acknowledgements

- **IBM Data Science Professional Certificate**: For providing the structure and resources to develop this end-to-end capstone.  
- **SpaceX**: For publicly accessible launch data.  
- **Wikipedia**: For supplementary launch details.  

Enjoy exploring the project and feel free to contribute your own improvements!

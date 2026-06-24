# fatal-police-shootings-analysis

## Project Overview
This repository contains the code, data analysis, and workflow configuration for our team project analyzing the Fatal Police Shootings dataset. 

**Team Acknowledgment:** This project was collaboratively developed by a team of three members (Group 9)[cite: 7]. 

## Repository Contents

### 1. Code & Analysis
*   **`data_processing.py`**: The main Python script containing our core processing logic and functions.
*   **`eda.ipynb`**: A Jupyter Notebook detailing our exploratory data analysis, data cleaning, visualizations, and overall findings.

### 2. Workflow & Automation (Airflow)
We utilized Apache Airflow to orchestrate our data pipeline, setting it up within a virtual environment[cite: 8]. 
*   **Initialization:** We ran the Airflow scheduler and the webserver (accessible via port 8080) using separate terminal instances on our EC2 user[cite: 8].
*   **DAG Configuration:** We created a `dags` folder containing our configuration file, `spark_submit_dag.py`[cite: 7]. 
*   **Execution:** This DAG utilized a `BashOperator` to trigger a Spark job (`testEX3.py`) that performed a word count algorithm, successfully logging the results and marking the task as a "SUCCESS" in the Airflow dashboard[cite: 7, 8].

### 3. Project Results

#### Cluster Configuration
*   Our cluster was configured with **1 Master node**, **7 worker nodes**, and **1 event generator**[cite: 7].

#### Key Analytical Findings
*   **Body Cameras:** Officers were wearing body cameras in only 11.22% of the fatal cases[cite: 7]. Encounters without body cameras tended to involve a broader and more unpredictable range of weapons[cite: 7].
*   **Geography & Demographics:** While California, Texas, and Florida had the highest total incidents, smaller states like Alaska, Nevada, and Montana had the highest rates per capita[cite: 7]. White individuals were the most represented group overall, though Black and Hispanic individuals were disproportionately represented in states like California, Illinois, and Louisiana[cite: 7].
*   **Yearly Trends:** Fatal shootings remained stable around 1,000 per year from 2015 to 2019, followed by a sharp drop to 400 cases in 2020 (likely reflecting the impact of the COVID-19 pandemic)[cite: 7].
*   **Victim Profiles:** Over 70% of the individuals involved were adults aged 19 to 45[cite: 7]. Notably, 10.45% of individuals were unarmed, and 29.47% were attempting to flee (by foot or vehicle) during the incident[cite: 7].

#### Machine Learning Models
To predict the manner of death, we tested three classification algorithms: Random Forest, Logistic Regression, and a Gradient-Boosted Tree Classifier[cite: 7]. 
*   **Best Performing Model:** The Gradient Boosted Tree Classifier achieved the highest accuracy at **95.02%**, outperforming both Logistic Regression and Random Forest models across various evaluation metrics[cite: 7]. 

#### Tools Utilized
*   **Google Colab:** For collaborative team coding and real-time edits[cite: 7].
*   **Hadoop/HDFS:** Results were downloaded as `.py` files, uploaded to the cluster, and saved in `parquet` format inside HDFS for querying[cite: 7].
*   **Apache Airflow & Spark:** For managing job scheduling and processing workflows[cite: 7].

## Data
Our analysis is based on the `fatal_police_shootings.csv` dataset. 
> **Note on Data:** To run the analysis locally, ensure you have downloaded the dataset and placed it in the root directory of this project. 

## How to Run the Project
1. Clone this repository to your local machine.
2. Ensure you have Python installed, along with necessary libraries (e.g., `pandas`, `matplotlib`, `jupyter`, and `apache-airflow`).
3. Open the Jupyter Notebook to explore the interactive analysis, or execute the Python script via your terminal.
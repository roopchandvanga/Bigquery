# BigQuery Loan Analysis (CS 544 Project P8)

This project explores the use of Google Cloud Platform (GCP) tools such as **BigQuery**, **Google Cloud Storage (GCS)**, and **Google Sheets** for loan data analysis. It integrates public geographic datasets, HDMA loan data, and form-based user input to analyze loan applications, train a regression model, and perform geospatial analysis.

## 📚 Learning Objectives

- Combine data from multiple sources into BigQuery
- Query and analyze live data from a Google Sheet
- Train a linear regression model in BigQuery
- Manipulate and join geographic data using SQL and BigQuery GIS functions

---

## ⚙️ Setup

### Python Environment (venv)

```bash
sudo apt install python3.12-venv  # or match your installed version
python3 -m venv venv
source venv/bin/activate
```
### Install Dependencies

```bash
pip3 install jupyterlab google-cloud-bigquery google-cloud-bigquery-storage pyarrow tqdm ipywidgets pandas matplotlib db-dtypes pandas-gbq
```
### Google Cloud CLI


```bash
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
sudo apt-get update && sudo apt-get install google-cloud-cli
```

### Authenticate with GCP

```bash
gcloud auth application-default login --scopes=openid,https://www.googleapis.com/auth/cloud-platform,https://www.googleapis.com/auth/drive.readonly
```
- 🔐 Tip: Paste the auth link into an incognito browser window and log in with your account.

To revoke access when done:
```bash
gcloud auth application-default revoke
```

## 🧱 Project Structure

- src/p8.ipynb: Main notebook answering all questions (Q1–Q10)
- venv/: Python virtual environment (excluded via .gitignore)
- .gitignore: Prevents committing virtual environments and large files

## 📁 Data Sources

- 📍 Public Dataset: bigquery-public-data.geo_us_boundaries.counties
- 📦 Private Dataset: hdma-wi-2021.parquet uploaded to a GCS bucket
- 📋 Live Data: Google Form-backed Spreadsheet linked as external BigQuery table applications

## 📌 Questions

### Part 1: County Data (Public Dataset)

**Q1**: What is the `geo_id` for Dane county?  
_Returns_: `str`

**Q2**: How many counties are there per state? (Top 5 states)  
_Returns_: `dict[str, int]`

**Q3**: How much did the queries in Q1 and Q2 cost (in MB)?  
_Returns_:

```python
{
  "q1": "XX MB",
  "q2": "YY MB"
}
```

### Part 2: HDMA Data (Parquet in GCS)

**Q4**: What datasets exist in your GCP project? 
_Returns_: `list[str]`

**Q5**: Number of loan applications per county (top 10)
_Returns_: `dict[str, int]`

### Part 3: Application Data (Google Sheet)

**Q6**: How many applications match your chosen income?
_Returns_: `list[str]`

**Q7**: What is the R² score for a linear regression of income vs `loan_amount`?
_Returns_: `float`

### Part 4: Geography

**Q8**: Distance (in meters) from closest application to Wisconsin Capitol
_Returns_: `float`

**Q9**: Applications per WI county (filtering only WI counties)
_Returns_: `dict[str, int]`

**Q10**: Which counties border Dane County?
_Returns_: `list[str]` sorted


## 🛠️ Technologies Used

- Google Cloud BigQuery
- Google Cloud Storage (GCS)
- Google Sheets (via BigQuery external table)
- BigQuery GIS (Geographic joins & distance calculations)
- Python, JupyterLab, pandas, matplotlib










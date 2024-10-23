# CanDIGv2 Notebook

This repository contains a Jupyter Notebook for analyzing the [CanDIGv2-runbook](https://github.com/CanDIG/playwright-runbook). It includes scripts to extract log data, perform basic data wrangling, and generate visualizations.

## Installation

```bash
pip install uv
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt
```

## Set Environment Variables

Before running the notebook, you need to modify 2 environment variables.

- `path_to_playwright`: This is the path to your local Playwright runbook. The notebook uses this path to locate and extract the Playwright report. Alternatively, you can copy the report file into the correct folder.
- `filter_value`: This is set to Tyk by default. You can modify it based on the type of report you’re analyzing.

Below is a list of possible filter_value options:

```python
filter_value = "http://localhost:8008/"      # katsu
filter_value = "http://localhost:1236/"         # query
filter_value = "http://localhost:4232/"         # federation
filter_value = "http://localhost:3333/"         # htsget
filter_value = "http://localhost:5080/"         # tyk
```

Note: If you use different URLs on dev or prod reports, adjust the base URL accordingly.

## How to Run the Notebook

For first-time users, it’s recommended to run the notebook step-by-step for debugging.

Alternatively, you can use `Run All` to generate the report from start to finish, and export after.

The `playwright-data` contains details from the Playwright-runbook, which should be filtered for further analysis. Multiple smaller reports can also be combined into a larger report. It is recommended to collect the test with at least 100 iterations to have sufficient data.

The `playwright-html` directory contains the final report in web format. It is not used for analysis but can be referenced later.

## How to Read the Report

- The following statistics are calculated in the table: min, max, median, p90, p95, and total time
- The boxplot visualizes the summary statistics.
- The histogram shows the distribution of each API’s response times.
- The timeline (line chart) displays relative response times in real-time, helps to identify potential bottlenecks and understand how they relate to other API calls occurring simultaneously.

## How to Extend the Notebook

You can easily extend the notebook for additional analysis. Choose the DataFrame that interests you (or start with the raw data) and proceed from there. However, it’s good to begin with `df_duration_with_title`, as it includes the API response times only.

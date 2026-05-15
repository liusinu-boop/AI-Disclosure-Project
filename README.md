# AI-Related Innovation Disclosure and Investor Sentiment: Evidence from China’s Stock Market

Author: Sinuo Liu

## Research Question

How is AI-related disclosure, especially AI innovation disclosure and AI risk disclosure, associated with investor sentiment in China’s stock market?

## Dataset Description

This project uses two related datasets to examine the relationship between AI-related disclosure and investor sentiment.

### Dataset 1: Baseline Dataset for Hypothesis 1

The baseline dataset is a firm-year dataset obtained mainly from the CSMAR database. It contains firm identifiers, year, overall AI disclosure measures, the investor sentiment proxy, and firm-level control variables.

The main AI disclosure variable for Hypothesis 1 is `ai_disclosure_sentence_ratio`, which measures the proportion of AI-related sentences in a firm’s annual report. The dependent variable is investor sentiment, proxied by stock turnover. Turnover is constructed using annual trading shares and float market value from CSMAR. The dataset also includes control variables such as firm size, leverage, profitability, growth, cash ratio, TobinQ, listing age, board characteristics, ownership concentration, and SOE status.

The data were downloaded from CSMAR and merged in Python using stock code and year.

### Dataset 2: AI Innovation and Risk Disclosure Dataset for Hypotheses 2 and 3

The second dataset is manually constructed from corporate annual reports and is used for Hypotheses 2 and 3. Annual reports were collected from CNINFO. Python was used to download PDF reports, extract text, split the text into sentences, and identify AI-related sentences.

The extracted AI-related sentences were classified into two main categories: AI innovation disclosure and AI risk disclosure. Instead of relying only on keyword-based classification, this project uses a semi-manual approach. A subset of sentences was manually labeled based on semantic meaning, and the remaining sentences were classified with AI assistance following the manually established standard.

The final firm-year dataset includes variables such as `AI_innovation`, `AI_risk`, `AI_total`, `AI_innovation_disclosure`, `AI_risk_disclosure`, turnover, and firm-level control variables. This dataset is based on approximately 100 selected firms over multiple years.

## Data Sources

Annual reports were collected from CNINFO:

http://www.cninfo.com.cn

Financial data, trading data, AI disclosure variables for Hypothesis 1, and firm-level control variables were obtained from the CSMAR database.

## Method Summary

For Hypothesis 1, the overall AI disclosure variable from CSMAR is merged with turnover and firm-level control variables at the firm-year level.

For Hypotheses 2 and 3, AI-related sentences are extracted from annual reports using Python-based PDF text extraction. AI innovation disclosure and AI risk disclosure are then constructed from sentence-level classification and aggregated to the firm-year level.

## Key Variables

### Hypothesis 1

Independent variable:

- `ai_disclosure_sentence_ratio`

Dependent variable:

- `turnover`

Control variables:

- `Size`
- `Lev`
- `ROA`
- `Growth`
- `CashRatio`
- `TobinQ`
- `ListAge`
- `Board`
- `Indep`
- `Dual`
- `Top1`
- `SOE`

### Hypotheses 2 and 3

Independent variables:

- `AI_innovation_disclosure`
- `AI_risk_disclosure`

Dependent variable:

- `turnover`

Control variables:

- Firm-level financial and governance variables from CSMAR

## How to Run the Data Collection Notebook

The main notebook is located in:

`code/Data collection-1.ipynb`

To run the notebook, install the following Python packages:

```python
pip install pandas requests pdfplumber openpyxl

# AI-Related Innovation Disclosure and Investor Sentiment: Evidence from China’s Stock Market

## Author
Sinuo Liu

## Research Question
AI-Related Innovation Disclosure and Investor Sentiment: Evidence from China’s Stock Market

## Dataset Description

This project uses two related datasets to examine AI-related disclosure and investor sentiment in China’s stock market.

### Dataset 1: Baseline Dataset for Hypothesis 1

**What it contains:**  
The baseline dataset is a firm-year dataset used for Hypothesis 1. It contains:
- Stock code
- Stock name
- Year
- AI disclosure / AI word frequency variables downloaded from CSMAR
- Investor sentiment variable, proxied by turnover rate
- Firm-level control variables, such as firm size, leverage, profitability, growth, cash ratio, TobinQ, listing age, board characteristics, ownership concentration, and SOE status

**Where it comes from:**  
This dataset is mainly obtained from the CSMAR database. The AI disclosure variable for Hypothesis 1 is downloaded from CSMAR’s AI-related word frequency dataset. The investor sentiment variable and firm-level control variables are also obtained from CSMAR.

**How it was collected:**  
The CSMAR data were downloaded directly from the CSMAR database and then cleaned and merged in Python. The AI disclosure dataset and trading/turnover dataset were merged by stock code and year. Control variables were also merged at the firm-year level using stock code and year.

This baseline dataset covers Chinese A-share listed firms after excluding financial firms and ST companies.

---

### Dataset 2: Manually Constructed AI Innovation and Risk Disclosure Dataset for Hypotheses 2 and 3

**What it contains:**  
The manually constructed dataset is used for Hypotheses 2 and 3. It contains sentence-level and firm-year level AI disclosure variables, including:
- Stock code
- Report year
- Annual report file name
- Total number of sentences in each annual report
- AI-related sentences extracted from annual reports
- Matched AI keywords
- AI innovation disclosure classification
- AI risk disclosure classification
- Neutral and mixed AI sentence labels
- Firm-year level AI disclosure measures, including:
  - total AI-related sentences
  - AI innovation-related sentences
  - AI risk-related sentences
  - AI disclosure ratio
  - AI innovation disclosure ratio
  - AI risk disclosure ratio

**Where it comes from:**  
The annual reports were collected from CNINFO:
http://www.cninfo.com.cn

The investor sentiment variable and control variables used together with this dataset are still obtained from CSMAR.

**How it was collected:**  
Because CSMAR does not provide direct measures of AI innovation disclosure and AI risk disclosure, this project manually constructs these variables from annual reports.

The collection and processing steps are:
1. Annual report PDFs were downloaded from CNINFO.
2. Python was used to extract text from the PDF files.
3. The text was split into sentences.
4. AI-related sentences were identified using a Chinese AI keyword dictionary.
5. AI-related sentences were classified into innovation-related, risk-related, neutral, or mixed categories using Chinese keyword dictionaries.
6. Sentence-level results were aggregated to the firm-year level.
7. The resulting AI innovation and AI risk disclosure variables were prepared for merging with CSMAR investor sentiment and control variables.

This manually constructed dataset is based on a selected sample of approximately 100 firms over a five-year period. The smaller sample is used because sentence-level PDF processing and manual dictionary validation are more time-consuming than downloading structured financial data.

## Method Summary

This project uses a dictionary-based textual analysis method.

For Hypothesis 1, the AI disclosure variable is obtained from CSMAR’s AI word frequency data and merged with investor sentiment and control variables from CSMAR.

For Hypotheses 2 and 3, AI innovation disclosure and AI risk disclosure are manually constructed from annual report texts. The key idea is to first identify AI-related sentences and then classify them into innovation-related and risk-related categories.

## Key Variables

### Hypothesis 1

- Independent variable (X):
  - AI disclosure / AI word frequency variable from CSMAR

- Dependent variable (Y):
  - Investor sentiment, proxied by turnover rate from CSMAR

- Control variables:
  - Size
  - Lev
  - ROA
  - Growth
  - CashRatio
  - TobinQ
  - ListAge
  - Board
  - Indep
  - Dual
  - Top1
  - SOE

### Hypotheses 2 and 3

- Independent variables (X):
  - AI innovation disclosure, constructed from innovation-related AI sentences in annual reports
  - AI risk disclosure, constructed from risk-related AI sentences in annual reports

- Dependent variable (Y):
  - Investor sentiment, proxied by turnover rate from CSMAR

- Control variables:
  - Firm-level financial and governance variables from CSMAR

## How to Run the Data Collection Notebook

The main notebook is located in:

```text
code/Data collection-1.ipynb

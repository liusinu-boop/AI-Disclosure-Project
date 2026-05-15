Data Description

This project combines structured financial data from the CSMAR database with manually constructed AI disclosure measures extracted from corporate annual reports.

For Hypothesis 1, the dataset is based on Chinese A-share listed firms after excluding financial firms and ST companies. The main independent variable is ai_disclosure_sentence_ratio, which measures the proportion of AI-related sentences in a firm’s annual report. The dependent variable is investor sentiment, proxied by stock turnover. Turnover is constructed using annual trading shares and float market value from CSMAR. Firm-level control variables are also obtained from CSMAR.

For Hypotheses 2 and 3, AI-related sentences are extracted from corporate annual reports collected from CNINFO. Python is used to download annual reports and extract text from PDF files. The extracted AI-related sentences are then classified into AI innovation disclosure and AI risk disclosure. Instead of relying only on dictionary-based classification, this project uses a semi-manual approach: a subset of sentences is manually labeled based on semantic meaning, and the remaining sentences are classified with AI assistance following the manually established standard.

Data Source

Annual reports were collected from CNINFO.

Financial data, trading data, and firm-level control variables were obtained from the CSMAR database.

Collection Method

This project uses Python-based PDF text extraction and structured database collection. It does not rely on API collection. Python is used to download annual reports, extract text from PDF files, identify AI-related sentences, and classify these sentences into innovation-related and risk-related disclosure.

The main Python packages used include:
- requests
- pandas
- pdfplumber
- re

Sample Scope and Period

The annual report sample covers approximately 100 selected Chinese listed firms over multiple years. The sentence-level dataset is mainly used to construct AI innovation disclosure and AI risk disclosure measures for Hypotheses 2 and 3.

For Hypothesis 1, the CSMAR-based dataset contains 21,938 firm-year observations.

For Hypotheses 2 and 3, the manually constructed disclosure dataset contains 399 firm-year observations for AI innovation and AI risk disclosure variables. After merging with trading data, valid turnover observations are available for 324 firm-year observations.

Dataset Structure

The project contains firm-year-level datasets.

The Hypothesis 1 dataset includes:
- code: Stock code
- year: Fiscal year
- ai_disclosure_sentence_ratio: Ratio of AI-related sentences to total sentences in the annual report
- turnover: Investor sentiment proxy, calculated using annual trading shares and float market value
- control variables: Firm-level control variables from CSMAR

The Hypotheses 2 and 3 dataset includes:
- code: Stock code
- report_year: Annual report year
- AI_innovation: Number of AI-related sentences classified as innovation-oriented
- AI_risk: Number of AI-related sentences classified as risk-oriented
- AI_total: Total number of AI-related sentences
- AI_innovation_disclosure: Proportion of AI-related sentences classified as innovation-oriented
- AI_risk_disclosure: Proportion of AI-related sentences classified as risk-oriented
- turnover: Investor sentiment proxy
- control variables: Firm-level control variables from CSMAR

Variable Construction

For Hypothesis 1, ai_disclosure_sentence_ratio is used to measure overall AI disclosure intensity. It is calculated as the number of AI-related sentences divided by the total number of sentences in the annual report.

For Hypotheses 2 and 3, AI_innovation_disclosure and AI_risk_disclosure are constructed from AI-related annual report sentences. AI innovation disclosure refers to AI-related sentences emphasizing technological applications, efficiency improvement, business transformation, or product and service innovation. AI risk disclosure refers to AI-related sentences emphasizing risk management, uncertainty, regulation, compliance, or potential negative implications.

The dependent variable is turnover, which is used as a market-based proxy for investor sentiment. It captures the trading-activity dimension of investor sentiment.

Data Quality and Limitations

Several data quality issues remain. First, some observations have missing turnover values after merging the disclosure dataset with trading data. Second, AI risk disclosure is very limited in the annual reports, which may reduce the statistical power of tests related to Hypothesis 3. Third, the AI disclosure classification relies on a semi-manual and AI-assisted process, so some classification noise may still exist.

Overall, the dataset is suitable for preliminary empirical analysis. The Hypothesis 1 dataset supports a larger-sample test of overall AI disclosure, while the Hypotheses 2 and 3 dataset provides a more detailed but smaller-sample analysis of AI innovation and AI risk disclosure.


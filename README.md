# AI-Disclosure-Project
AI disclosure and investor sentiment project
## Data Sources and Sample Construction

This study combines financial data from the CSMAR database with manually constructed AI disclosure measures extracted from corporate annual reports.

For the baseline analysis (Hypothesis 1), the sample includes all Chinese A-share listed firms, excluding financial firms and ST companies, following standard practice in the literature. The dependent variable (investor sentiment) and firm-level control variables are obtained from the CSMAR database.

For the AI disclosure analysis (Hypotheses 2 and 3), the independent variables are constructed using a text analysis approach. Specifically, annual reports are collected and processed using Python, and AI-related sentences are identified and classified into two categories: AI innovation disclosure and AI risk disclosure, based on a dictionary-based method.

Due to the computational intensity of large-scale text processing, a subsample of firms is selected for the AI disclosure analysis. This subsample is not driven by data availability issues, but rather by practical constraints in processing and cleaning textual data. The dependent variable (investor sentiment) and control variables in this part are still obtained from the CSMAR database to ensure consistency across analyses.

## Methodology

This study employs a dictionary-based text analysis approach to construct AI disclosure variables.

First, annual reports are processed using Python to extract sentences containing AI-related keywords. These sentences are then classified into two categories based on predefined keyword dictionaries:

- AI innovation-related sentences
- AI risk-related sentences

At the firm-year level, AI disclosure variables are constructed by aggregating the classified sentences. Specifically, the main measures include:

- The total number of AI innovation-related sentences
- The total number of AI risk-related sentences
- Alternatively, the proportion of each type relative to total AI-related sentences

These firm-year level measures are then merged with financial data from the CSMAR database and used in regression analysis.



## Key Variables

- Dependent Variable (Y):
  - Investor sentiment, proxied by the turnover rate from the CSMAR database. The turnover rate captures trading activity and is widely used in the literature as a proxy for investor sentiment.

- Independent Variables (X):
  - AI Innovation Disclosure:
    Measured as the number (or proportion) of AI-related sentences in annual reports that reflect innovation-related content. These sentences are identified using a predefined dictionary of innovation-related keywords (e.g., “人工智能应用”, “技术创新”, “智能化升级”).

  - AI Risk Disclosure:
    Measured as the number (or proportion) of AI-related sentences that reflect risk-related content. These sentences are identified using a predefined dictionary of risk-related keywords (e.g., “风险”, “不确定性”, “数据安全”, “监管”).

- Control Variables:
  - Firm size (Size)
  - Leverage (Lev)
  - Profitability (ROA)
  - Growth (Growth)
  - Cash holdings (CashRatio)
  - Firm value (TobinQ)
  - Listing age (ListAge)
  - Governance variables (Board, Indep, Dual, Top1, SOE)
 
    
## Data Quality and Limitations

The sentence-level classification results show an imbalanced distribution across categories. Most AI-related sentences are classified as innovation-related disclosure, while risk-related sentences account for a much smaller proportion. Specifically, the current classification produces substantially more innovation sentences than risk sentences, with a relatively large number of neutral sentences and only a small number of mixed sentences.

This imbalance is reasonable in the context of corporate annual reports, because firms usually emphasize the positive applications, development plans, and strategic benefits of AI, while they disclose AI-related risks less frequently. However, the small number of risk-related sentences may limit the statistical power of Hypothesis 3, which examines AI risk disclosure.

Neutral sentences refer to AI-related sentences that contain AI keywords but do not include clear innovation-related or risk-related keywords. These sentences are retained in the sentence-level dataset for transparency, but they are not used as the main independent variables in the regression analysis. The main AI disclosure variables focus on innovation-related and risk-related AI sentences.

Mixed sentences refer to sentences that contain both innovation-related and risk-related keywords. Because the number of mixed sentences is very small, they are reported separately but not treated as a main explanatory variable.

A key limitation of this approach is that dictionary-based classification may not fully capture the contextual meaning of each sentence. Some sentences may be classified as innovation-related or risk-related because they contain specific keywords, even if the broader context is more complex. To reduce this concern, the dictionary is designed to be transparent and reproducible, and selected sentences will be manually checked to assess whether the classification is reasonable.

Overall, the AI innovation disclosure variable is expected to be more stable due to the larger number of observations, while the AI risk disclosure variable should be interpreted more cautiously because of its smaller sample size and lower frequency in annual reports.

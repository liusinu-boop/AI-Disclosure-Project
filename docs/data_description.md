# Data Description
This study combines financial data from the CSMAR database with manually constructed AI disclosure measures extracted from corporate annual reports.

For the baseline analysis (Hypothesis 1), the sample includes all Chinese A-share listed firms, excluding financial firms and ST companies, following standard practice in the literature. The dependent variable (investor sentiment) and firm-level control variables are obtained from the CSMAR database.

For the AI disclosure analysis (Hypotheses 2 and 3), the independent variables are constructed using a text analysis approach. Specifically, annual reports are collected and processed using Python, and AI-related sentences are identified and classified into two categories: AI innovation disclosure and AI risk disclosure, based on a dictionary-based method.

Due to the computational intensity of large-scale text processing, a subsample of firms is selected for the AI disclosure analysis. This subsample is not driven by data availability issues, but rather by practical constraints in processing and cleaning textual data. The dependent variable (investor sentiment) and control variables in this part are still obtained from the CSMAR database to ensure consistency across analyses.
## Data Source

The dataset is based on annual reports of Chinese A-share listed firms.

Annual reports were downloaded from cninfo:
http://www.cninfo.com.cn

Financial and firm-level data were obtained from the CSMAR database.

---

## Collection Method

The project used HTML scraping and PDF text extraction.

Python packages used:
- requests
- pandas
- pdfplumber
- re

The workflow included:
1. Downloading annual reports
2. Extracting text from PDF reports
3. Identifying AI-related sentences using keyword matching
4. Classifying AI sentences into innovation, risk, neutral, and mixed categories using dictionary-based methods
5. Aggregating sentence-level data into firm-year level measures

---

## Collection Period

2019–2024 annual reports.

Data collected in May 2026.

---
## Sample Scope and Variable Construction

This project focuses on approximately 100 Chinese listed firms over a five-year period for sentence-level textual analysis and classification.

The limited sample is mainly used for the construction and exploratory validation of AI innovation disclosure and AI risk disclosure measures. These variables require manual dictionary construction and sentence-level classification based on annual report texts collected from CNINFO.

For Hypothesis 1, the AI disclosure variable will be constructed from annual report textual analysis, while investor sentiment variables and firm-level control variables will be collected from the CSMAR database and related financial market data sources.
Hypothesis 2 = innovation
Hypothesis 3 = risk
For Hypothesis 2 and Hypothesis 3, the key independent variables — AI innovation disclosure and AI risk disclosure — are manually constructed from annual report textual analysis using Python-based keyword extraction and dictionary classification methods.

The dependent variable, investor sentiment, as well as firm-level control variables, will continue to be collected from the CSMAR database.

The final empirical dataset will combine:
- AI disclosure variables constructed from annual report textual analysis
- investor sentiment variables collected from CSMAR
- firm-level control variables from CSMAR

The datasets will be merged at the firm-year level using stock code and report year.


## Dataset Structure
The project contains both sentence-level and firm-year-level datasets.

### 1. ai_disclosure_sentences_FIXED.csv

Sentence-level dataset containing:
- stock code
- report year
- extracted AI-related sentence
- classification label

### 2. ai_disclosure_firm_year_FIXED.csv

Firm-year level dataset containing:
- stock code
- report year
- total AI sentences
- innovation sentence count
- risk sentence count
- neutral sentence count
- mixed sentence count

---

## Variable Description

| Variable Name | Type | Description | Example |
|---|---|---|---|
| code | string | Stock code | 000001 |
| report_year | integer | Annual report year | 2022 |
| sentence | string | AI-related sentence | “公司积极推进人工智能技术应用” |
| label | string | Sentence classification | innovation |
| total_ai_sentences | integer | Number of AI sentences | 18 |
| innovation_sentences | integer | Innovation-related AI sentences | 10 |
| risk_sentences | integer | Risk-related AI sentences | 2 |

---

## Dictionary Construction

The AI disclosure dictionary was constructed based on prior disclosure and textual analysis literature.

The study used Chinese keyword dictionaries because the annual reports analyzed in this project are written in Chinese.

AI-related keywords include:
- "人工智能", "AI", "AIGC", "生成式人工智能", "生成式AI",
    "机器学习", "深度学习", "神经网络", "大模型", "语言模型",
    "自然语言处理", "NLP", "计算机视觉", "机器视觉", "知识图谱",
    "智能化", "智慧化", "智能平台", "智能系统", "智能识别",
    "智能分析", "智能决策", "智能算法", "算法", "推荐算法",
    "预测模型", "数据模型", "数据挖掘", "数据驱动",
    "自动化", "自动识别", "自动生成", "自动控制",
    "云计算", "边缘计算", "算力", "GPU",
    "ChatGPT", "GPT", "多模态", "智能客服", "智能机器人", "机器人"

Innovation-related keywords include:
- "创新", "技术创新", "自主研发", "研发", "研发投入",
    "研发能力", "技术突破", "技术升级", "创新能力",

    "应用", "落地", "部署", "实施", "推广",
    "智能化", "数字化", "数字化转型", "智能化转型",

    "效率提升", "提升效率", "降本增效", "优化",
    "改善", "增强", "提高", "自动化",

    "核心竞争力", "竞争优势", "市场竞争力",
    "业务创新", "产品创新", "服务创新",

    "智能平台", "智能系统", "智能决策",
    "机器学习", "深度学习", "大模型",
    "自然语言处理", "计算机视觉",

    "增长", "盈利能力", "运营效率",
    "业务协同", "价值创造", "赋能"

Risk-related keywords include:
- 
 "风险", "不确定性", "挑战", "困难",
    "压力", "波动",

    "技术风险", "技术缺陷", "模型风险",
    "算法偏差", "误判", "失败",

    "数据安全", "隐私", "隐私保护",
    "信息安全", "网络安全", "信息泄露",

    "监管", "监管风险", "合规",
    "合规风险", "法律风险",

    "投入较高", "成本增加",
    "回报不确定", "投资风险",

    "依赖", "外部依赖",
    "人才短缺", "竞争加剧",

    "伦理风险", "伦理",
    "失业", "替代人工"
]

The dictionary-based approach was selected because it is transparent, interpretable, and reproducible. The keyword lists were manually constructed based on prior AI disclosure literature and adjusted to fit Chinese annual report contexts.

---
Data Quality and Limitations

The sentence-level classification results show an imbalanced distribution across categories. Most AI-related sentences are classified as innovation-related disclosure, while risk-related sentences account for a much smaller proportion. Specifically, the current classification produces substantially more innovation sentences than risk sentences, with a relatively large number of neutral sentences and only a small number of mixed sentences.

This imbalance is reasonable in the context of corporate annual reports, because firms usually emphasize the positive applications, development plans, and strategic benefits of AI, while they disclose AI-related risks less frequently. However, the small number of risk-related sentences may limit the statistical power of Hypothesis 3, which examines AI risk disclosure.

Neutral sentences refer to AI-related sentences that contain AI keywords but do not include clear innovation-related or risk-related keywords. These sentences are retained in the sentence-level dataset for transparency, but they are not used as the main independent variables in the regression analysis. The main AI disclosure variables focus on innovation-related and risk-related AI sentences.

Mixed sentences refer to sentences that contain both innovation-related and risk-related keywords. Because the number of mixed sentences is very small, they are reported separately but not treated as a main explanatory variable.

A key limitation of this approach is that dictionary-based classification may not fully capture the contextual meaning of each sentence. Some sentences may be classified as innovation-related or risk-related because they contain specific keywords, even if the broader context is more complex. To reduce this concern, the dictionary is designed to be transparent and reproducible, and selected sentences will be manually checked to assess whether the classification is reasonable.

Overall, the AI innovation disclosure variable is expected to be more stable due to the larger number of observations, while the AI risk disclosure variable should be interpreted more cautiously because of its smaller sample size and lower frequency in annual reports.


# Financial Statement Analysis (FSA)
Financial Statement Analysis dashboard developed in Power BI using audited financial statements as the only source of information.

## About the Project
This project started with a simple objective: transform audited financial statements into a structured analytical model capable of supporting financial analysis inside Power BI.

The financial data used in this project was obtained from publicly available audited financial statements published through the Bolivian Stock Exchange (Bolsa Boliviana de Valores - BBV). The original reports were published in PDF format and contain real financial information.

The name of the company has intentionally been omitted to keep the focus on the analytical methodology, data modeling process, and reporting architecture rather than on the financial performance of a specific organization.

The initial PDF-to-Excel transformation process was assisted by Microsoft Copilot to accelerate data extraction and structuring. All extracted information was subsequently validated manually through reconciliation procedures and accounting control checks, including verification of the fundamental accounting equation:

**Assets = Liabilities + Equity**

During the validation process, special attention was given to sign conventions. Several financial statement accounts were originally reported with negative values according to their accounting presentation format.

To ensure consistency across financial reporting, DAX calculations, and ratio analysis, account signs were reviewed and adjusted when necessary as part of the financial data validation and reconciliation process.

This step was essential to maintain the integrity of financial KPIs, trend analysis, and statement-level calculations throughout the model. Once validated, the data was transformed in Power Query and modeled in Power BI.

The project focuses on building a complete end-to-end workflow covering financial statement extraction, validation, standardization, modeling, and analysis.

Beyond analyzing a single company, the model has been designed with scalability in mind. The objective is to establish a reusable framework that can later incorporate financial statements from additional companies while preserving the same analytical structure, measures, ratios, and reporting experience.

## Workflow
```text
Audited Financial Statements
            ↓
       PDF Extraction
            ↓
 Validation & Reconciliation
            ↓
       Power Query
            ↓
       Star Schema
            ↓
      DAX Measures
            ↓
     Power BI Report
```
## Project Status
**Version 1.0 Complete**

The current version includes four analytical pages covering the three primary financial statements, including an executive overview page.

The project is supported by a dimensional financial model, bilingual account standardization framework, DAX-based financial analysis and ratio framework, financial reporting matrices, waterfall analysis, and multi-year trend analysis.

This version represents a complete end-to-end workflow covering financial statement extraction, validation, transformation, modeling, visualization, and financial analysis in Power BI.
![Overview Dashboard](Images/Overview/OverviewV1.png)

## Data Model
Star schema model composed of:

- FactFinStatements: Financial statement values and reporting data
- DimDate: Fiscal periods and year-based analysis
- DimCategory: Financial statement classification
- DimLineItem: Standardized financial accounts

The model is supported by an auxiliary table used for Income Statement waterfall analysis.

### Data Model Diagram
![Data Model Diagram](Images/DataModel/DataModelV1.png)

## Financial Account Standardization
To improve scalability and support future multi-company implementations, a bilingual account structure was implemented directly within the primary financial statement tables.

A custom column named `Cuenta_EN` was created by referencing the original Spanish account names and applying standardized English financial terminology through Power Query transformation steps.

This approach allows all referenced queries, models, measures, and visualizations to inherit the translated account structure automatically, reducing maintenance efforts and improving consistency across the entire model.

This design also simplifies the future integration of additional companies into the model while maintaining a consistent analytical structure.

## Financial Analysis Framework
The model includes a DAX-based financial analysis framework covering:

- Liquidity: Current Ratio, Quick Ratio, Working Capital
- Solvency: Debt Ratio, Equity Ratio
- Capital Structure: Debt-to-Equity
- Profitability: Gross Margin, EBITDA Margin, Net Margin, ROA, ROE
- Cash Flow: Operating, Investing, and Financing Cash Flows
- Trend Analysis: Year-over-Year and absolute change analysis

The DAX measure structure is documented through dedicated measure views included in the repository.

  [View DAX Measures Documentation](Images/Measures/)

### EBITDA Calculation
Because depreciation and tax-related accounts were reported with negative signs according to the original financial statement presentation, these values were incorporated into the calculation following the model's standardized sign convention.

EBITDA was calculated using the methodology commonly applied by PCR (Pacific Credit Rating) in its credit analysis reports:

**EBITDA = Operating Income + Depreciation + Taxes**

Because audited financial statements do not always disclose EBITDA as a separate line item, a custom DAX measure was developed to reconstruct the indicator using information available in the financial statements.

This approach was adopted to maintain consistency with the methodology frequently used in local credit risk analysis and debt issuance evaluations.

## Skills Demonstrated
- Financial Statement Analysis
- Power BI & Power Query
- DAX Development
- Dimensional Data Modeling (Star Schema)
- Financial Data Standardization
- Accounting Validation & Reconciliation
- AI-Assisted Data Preparation
- Business Intelligence Reporting

## Dashboard Development
### Overview
The first dashboard page was designed to provide a high-level overview of the company's financial position, profitability, solvency, capital structure, and cash generation.

Key metrics include:

- Revenue
- EBITDA
- EBITDA Margin
- Net Income
- Total Assets
- Operating Cash Flow
- Current Ratio
- Debt to Equity
- ROA
- ROE

Additional visualizations include:

- Revenue trend analysis
- EBITDA trend analysis
- Net Income trend analysis
- Operating Cash Flow trend analysis
- Asset growth analysis
- Financing Structure by Year
- Interactive period selection

Custom DAX measures were implemented to dynamically control visual behavior based on period selection. Executive KPI cards are displayed only when a specific year is selected, while trend and historical analysis visualizations remain available to support multi-year analysis.

The objective of this page is to summarize the company's financial performance, financial condition, and cash generation capacity in a single executive-level dashboard.

### Balance Sheet Analysis
The second dashboard page focuses on analyzing the company's financial position through asset composition, financing structure, liquidity, and solvency indicators.

Key metrics include:

- Total Assets
- Current Assets
- Non-Current Assets
- Total Liabilities
- Current Liabilities
- Non-Current Liabilities
- Equity

Additional visualizations include:

- Asset Structure by Year
- Financing Structure by Year
- Current Ratio Trend
- Quick Ratio Trend
- Working Capital Analysis
- Debt Ratio Trend
- Equity Ratio Trend

The objective of this page is to provide a detailed view of the company's financial position, asset composition, financing structure, liquidity profile, and solvency evolution over time.
![Balance Sheet Dashboard](Images/FinancialStatements/BalanceSheet/BalanceSheetV1.png)

### Income Statement Analysis
The third dashboard page focuses on analyzing the company's profitability, operating performance, cost structure, and margin evolution over time.

Key metrics include:

- Revenue
- Cost of Goods Sold (COGS)
- Operating Expenses
- EBITDA
- Net Income
- Gross Margin
- EBITDA Margin
- Net Margin
- COGS to Revenue Ratio

Additional visualizations include:

- Profit Bridge Waterfall Analysis
- Revenue Trend Analysis
- Cost of Goods Sold (COGS) Trend Analysis
- Operating Expenses Trend Analysis
- Net Income Trend Analysis

The objective of this page is to provide a detailed view of the company's profitability, operating performance, cost structure, and margin evolution over time.
![Income Statement Dashboard](Images/FinancialStatements/IncomeStatement/IncomeStatementV1.png)

### Cash Flow Statement Analysis
The fourth dashboard page focuses on analyzing the company's cash generation, cash utilization, and cash flow sustainability through operating, investing, and financing activities.

Key metrics include:

- Net Change in Cash
- Operating Cash Flow
- Investing Cash Flow
- Financing Cash Flow
- YoY percentage change analysis
- YoY absolute change analysis

Additional visualizations include:
- Cash Flow Statement Matrix
- Cash Flow Components by Year
- Free Cash Flow Trend

The objective of this page is to provide a detailed view of the company's cash generation, cash utilization, and cash flow sustainability by analyzing operating, investing, and financing activities over time.
![Cash Flow Dashboard](Images/FinancialStatements/CashFlow/CashFlowV1.png)

## Key Financial Insights

### Liquidity

The asset structure indicates this is a commercial (trading) company. The current ratio remained above 1.4 across all years analyzed. The quick ratio remained above 1 in every period, indicating no strong dependence on inventory within current assets. Throughout the 6 fiscal years, the company has shown no difficulty meeting short-term financial obligations.

### Profitability

The last two years show a recovery in gross margin, driven by a relative decrease in COGS (Cost of Goods Sold). EBITDA margin reaches its peak in 2025, but net margin does not follow the same trend.

The net margin contraction in 2025 (from 5.02% to 2.55%) is not explained by operating deterioration, but by the disappearance of a non-recurring gain that supported the 2024 result (Bs7.5M in additional other income). Removing that effect reveals a more concerning structural trend: financial expenses grew linearly and consistently over the 6 fiscal years analyzed, from Bs5.2M in 2020 to Bs14.3M in 2025 (+175%), suggesting a progressive increase in leverage or cost of debt that is consistently compressing net profitability, independent of one-off events.

### Cash Flow

Operating cash flow shows high volatility, ranging from -Bs22.7M (2022) to +Bs44.5M (2023) over the 6-year period, with no clear stabilizing trend. This inconsistency between accounting results and actual cash generation warrants monitoring, particularly in a context of rising financial expenses that require sustained liquidity to service debt.

### Conclusion

The company maintains a solid and stable liquidity position, but net profitability is deteriorating due to non-operating expenses, and cash generation does not consistently track accounting results. This divergence between reported earnings and cash flow warrants ongoing monitoring.

## Power BI File

The complete Power BI report is included in this repository and is available for download.

The `.pbix` file contains the complete data model, Power Query transformations, DAX measures, calculations, and dashboard pages developed for this project.

**Power BI Desktop is required to open the report.**

[Download the Power BI report](File/Financial-Statement-Analysis.pbix)

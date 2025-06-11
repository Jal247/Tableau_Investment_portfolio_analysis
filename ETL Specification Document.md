📄 ETL Specification Document
Project: Portfolio Insights Dashboard
1. Purpose
This document defines the ETL process for extracting investment-related data from various sources, transforming it according to business rules, and loading it into a data model used by the Power BI dashboard for portfolio managers and clients.

2. ETL Overview

- Toolset Used: Azure Data Factory (ADF), Databricks, SQL Server
- Destination: Power BI Dataset
- Frequency: Daily Refresh at 6 AM
- Data Domains: Portfolio Data, Client Info, Investment Values, Risk Ratings

3. Source Systems

| Source Name   | Type        | Description                               | Format    |
| ------------- | ----------- | ----------------------------------------- | --------- |
| CRM System    | Application | Client Profiles and Metadata              | SQL Table |
| Investment DB | Database    | Portfolio performance & investment values | SQL Table |
| Risk Table    | Flat File   | Risk rating categories & definitions      | CSV       |
| SharePoint    | Excel       | Manually entered adjustments              | Excel     |
| Yahoo API | API         | Real-time investment metrics              | JSON      |


4. Transformation Logic

| Field           | Source                  | Transformation Rule                               | Target Field     |
| --------------- | ----------------------- | ------------------------------------------------- | ---------------- |
| ROI             | inv\_value, init\_value | ROI = (Current - Initial) / Initial               | ROI              |
| Risk Level      | risk\_rating            | A → Low, B → Medium, C → High                     | Risk Category    |
| Date Standard   | Various                 | Format to `YYYY-MM-DD`                            | Date Standard    |
| Currency        | All Values              | Convert to USD (if not already) using FX rate API | Normalized Value |
| Portfolio Owner | CRM → Join              | Join via client\_id and portfolio\_id             | Owner Name       |


5. Load Details

| Target Table   | Description                       | Load Type   | Destination      |
| -------------- | --------------------------------- | ----------- | ---------------- |
| dimClient      | Unique list of clients            | Full        | Power BI Dataset |
| dimPortfolio   | All portfolios by ID & attributes | Full        | Power BI Dataset |
| factInvestment | All investment data by period     | Incremental | Power BI Dataset |
| factRiskRating | Transformed risk levels           | Full        | Power BI Dataset |


6. Scheduling & Automation

- ADF Pipelines: 3 pipelines orchestrated sequentially

    -- Pipeline_ClientImport
  
    -- Pipeline_InvestmentMetrics
  
    -- Pipeline_RiskCalculation

- Trigger: Daily at 6:00 AM (Azure Scheduler)

- Failure Alerts: Email via Azure Monitor to Data Admins

7. Error Handling

| Stage     | Potential Issue                 | Handling Mechanism                      |
| --------- | ------------------------------- | --------------------------------------- |
| Extract   | API timeout                     | Retry logic (max 3 attempts)            |
| Transform | Null or invalid values          | Flag in `error_log` table + email alert |
| Load      | Duplicate or primary key errors | Deduplication & logging before insert   |


8. Security & Compliance

- Data encrypted in transit (HTTPS, TLS 1.2)
- Encryption at rest using Azure Key Vault
- RLS configured in Power BI by Client ID & Role
- PII masked for UAT/testing datasets

9. Monitoring & Logging

- Logging Tables: etl_log, error_log, audit_log

- Monitoring Tool: Azure Monitor + Power BI ETL Health Dashboard

- KPIs Tracked: Daily Refresh Status, Row Counts, Error Count, Duration


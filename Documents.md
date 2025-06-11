**1. Business Requirements Document (BRD)**

Purpose: Capture why the dashboard is needed and what the business wants to see.



| Section                       | Description                                                                                                                                            |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Project Overview**          | Brief summary of the dashboard project (e.g., “To visualize investment portfolio performance and risk insights for portfolio managers and customers”). |
| **Objectives**                | High-level business goals. E.g., “Improve investment visibility,” “Enable better risk-adjusted decisions.”                                             |
| **Stakeholders**              | List of all involved: PMs, Customers, Analysts, Devs.                                                                                                  |
| **User Roles & Permissions**  | Define who sees what (Portfolio Manager, Client, Analyst).                                                                                             |
| **High-Level Requirements**   | E.g., "Display AUM by quarter", "Enable filter by region and risk level."                                                                              |
| **Assumptions & Constraints** | Data availability, refresh limits, performance SLAs.                                                                                                   |
| **Success Criteria**          | Measurable outcomes like “Dashboard refreshes in < 10 seconds” or “User adoption by 80% in 3 weeks.”                                                   |


**Project Overview:** 
The objective is to enhance an existing investment application by integrating interactive dashboards that provide insights into portfolio performance, asset allocation, risk levels, and key investment metrics for portfolio managers and clients.

**Objectives:**

- Enable real-time visibility into investment performance.
- Support decision-making for portfolio managers.
- Improve client engagement with investment summaries.

**Stakeholders:**

- Business Users: Portfolio Managers, Clients, Executives
- Technical Teams: Developers, Data Engineers, Analysts

**User Roles & Permissions:**

- Portfolio Managers: See all client portfolios under management.
- Clients: Only view their own portfolio data.

**High-Level Requirements:**

- Dashboard showing ROI trends by quarter.
- Asset class distribution in pie chart.
- Risk rating matrix with visual indicators.
- Filter by client, asset type, and date range.

**Assumptions & Constraints:**

- All required data fields are available in current systems.
- Dashboards will be built using Power BI.
- Refresh cadence is daily.

**Success Criteria:**

- Dashboards load in <10 seconds.
- 95% adoption by target users in the first 30 days.





**2. Functional Requirements Document (FRD)**

Purpose: Define how the dashboard and underlying logic should work functionally.

| Section                         | Description                                                            |
| ------------------------------- | ---------------------------------------------------------------------- |
| **Feature Description**         | Detailed description of each visual component or filter.               |
| **Data Elements & Fields**      | List of required fields: ROI, Portfolio Name, Start Date, Risk Score.  |
| **Calculations/Derived Fields** | Formulas: e.g., ROI = (Current Value – Invested Value)/Invested Value. |
| **Filters & Parameters**        | E.g., Time range, Asset class, Portfolio type.                         |
| **Drill-down/Navigation**       | “Click on portfolio name opens client-level breakdown.”                |
| **Visual Interactions**         | Cross-filtering, tooltip details, sorting behaviors.                   |
| **Security Requirements**       | Row-Level Security logic, masking sensitive fields.                    |
| **Error Handling**              | What happens if data fails to load or is missing.                      |


Feature Description:Interactive dashboard with filters and drill-downs.

Data Elements & Fields:

- Portfolio ID, Client ID, Investment Type, ROI, Risk Score, Start Date, End Date, Current Value, Historical Value

Calculations/Derived Fields:

- ROI = (Current Value - Invested Value) / Invested Value

- Portfolio Growth % = (Current Value - Last Period Value) / Last Period Value

Filters & Parameters:

- Asset Type, Date Range, Risk Rating, Portfolio Manager

Drill-down/Navigation:

- Click on Portfolio ID → Opens Client Details View

Visual Interactions:

- Cross-filter charts by asset type or risk category.

- Tooltips on hover with detailed metrics.

Security Requirements:

- Implement RLS by Client ID and Portfolio Manager Role.

Error Handling:

- Display "Data Unavailable" message for missing values.

**3. Software Requirements Specification (SRS)**

Purpose: Provide both functional & non-functional requirements in technical detail. This bridges with developers and QA.

| Section                         | Description                                                                                             |
| ------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **System Purpose**              | “This dashboard module will retrieve and visualize investment performance data.”                        |
| **Scope**                       | Limited to equities/bonds data from Jan 2022 onward.                                                    |
| **System Context**              | Architecture diagram, showing data sources → ETL → Dashboard.                                           |
| **Functional Requirements**     | Detailed list of UI interactions, backend logic.                                                        |
| **Non-Functional Requirements** | Performance: “Load in under 10 sec,” Security: “OAuth2 + Azure AD login,” Availability: “99.9% uptime.” |
| **Data Mapping Table**          | Source field → Data type → Transformation logic → Destination field.                                    |
| **Integration Points**          | External APIs (e.g., Yahoo Finance API), CRM, SharePoint Excel                                             |
| **Technology Stack**            | Power BI, SQL Server, Azure Blob, Databricks                                                            |
| **Error Handling & Logging**    | Alerting if refresh fails, log errors to Azure Monitor.                                                 |





System Purpose:Develop and integrate a dashboard module to visualize real-time investment performance and risk insights.

Scope:Covers equities, bonds, and mutual funds data from 2022 onwards.

System Context:

- Sources: SQL Server, CRM, SharePoint Excel

- Transformation: Azure Data Factory, Databricks

- Output: Power BI Dashboard

Functional Requirements:

- User login via Azure AD

- Data ingestion via scheduled ETL

- Role-based access enforcement

Non-Functional Requirements:

- Availability: 99.9%

- Load Time: <10 seconds

- Security: Encryption at rest and in transit
  
| Source Table    | Source Field  | Data Type | Transformation           | Target Field       | Comments           |
| --------------- | ------------- | --------- | ------------------------ | ------------------ | ------------------ |
| Portfolio\_Data | `client_id`   | INT       | None                     | `Client ID`        | Key                |
| Portfolio\_Data | `inv_value`   | FLOAT     | Round to 2 decimals      | `Investment Value` | For ROI calc       |
| Risk\_Table     | `risk_rating` | TEXT      | Map: A → Low, B → Medium | `Risk Level`       | Filtered in report |

![Data Mapping table](https://github.com/user-attachments/assets/0956d6dc-3948-4d27-b4ca-b1843809a7e2)

Integration Points:

- Yahoo Finnance API for live investment data

- Internal CRM and document storage

- Technology Stack:Power BI, Azure Data Factory, SQL Server, Databricks, SharePoint

Error Handling & Logging:ETL errors logged in Azure Monitor. Email alert to Admin on failure.




**4. Data Mapping Document - STTM(Source to Target Mapping)**

Step 1: Identify Sources and Targets

- Sources: ERP (e.g., Baan LN, Dynamics), CRM, Excel files on SharePoint

- Targets: Azure Data Lake → Databricks Tables → Power BI Dataset

Step 2: Create a Data Inventory

- List all source tables/files involved (e.g., Customer_Master.xlsx, CRM_Transactions, ERP_Accounts)

- Capture table names, column names, data types, and sample values

Step 3: Define Mapping Table Structure

Field	Description



![Data Mapping STTM](https://github.com/user-attachments/assets/5adef4b1-0ecf-4f43-b18f-f11c7ce5fe21)

**Data Modeling - ERD Diagram**

![ChatGPT Image Jun 10, 2025, 02_28_19 PM](https://github.com/user-attachments/assets/2d20e405-7213-4f58-8ebb-880b1fd2a57f)



**5. UAT Test Cases**

| Test Case ID | Scenario                     | Steps                       | Expected Result                      | Status |
| ------------ | ---------------------------- | --------------------------- | ------------------------------------ | ------ |
| UAT01        | Check Total AUM              | Open dashboard, select YTD  | Correct sum of all active portfolios | ✅      |
| UAT02        | RLS – Portfolio Manager View | Login as PM, view dashboard | Only see their assigned portfolios   | ✅      |
| UAT03        | Filter by Risk Level         | Use slicer → “High Risk”    | Charts update accordingly            | ✅      |

![UAT test cases](https://github.com/user-attachments/assets/a499d7ff-e79e-4b6f-97be-cda6c63b7056)






**1. Business Requirements Document (BRD)**

Project Overview:The objective is to enhance an existing investment application by integrating interactive dashboards that provide insights into portfolio performance, asset allocation, risk levels, and key investment metrics for portfolio managers and clients.

Objectives:

Enable real-time visibility into investment performance.

Support decision-making for portfolio managers.

Improve client engagement with investment summaries.

Stakeholders:

Business Users: Portfolio Managers, Clients, Executives

Technical Teams: Developers, Data Engineers, Analysts

User Roles & Permissions:

Portfolio Managers: See all client portfolios under management.

Clients: Only view their own portfolio data.

High-Level Requirements:

Dashboard showing ROI trends by quarter.

Asset class distribution in pie chart.

Risk rating matrix with visual indicators.

Filter by client, asset type, and date range.

Assumptions & Constraints:

All required data fields are available in current systems.

Dashboards will be built using Power BI.

Refresh cadence is daily.

Success Criteria:

Dashboards load in <10 seconds.

95% adoption by target users in the first 30 days.

**2. Functional Requirements Document (FRD)**

Feature Description:Interactive dashboard with filters and drill-downs.

Data Elements & Fields:

Portfolio ID, Client ID, Investment Type, ROI, Risk Score, Start Date, End Date, Current Value, Historical Value

Calculations/Derived Fields:

ROI = (Current Value - Invested Value) / Invested Value

Portfolio Growth % = (Current Value - Last Period Value) / Last Period Value

Filters & Parameters:

Asset Type, Date Range, Risk Rating, Portfolio Manager

Drill-down/Navigation:

Click on Portfolio ID → Opens Client Details View

Visual Interactions:

Cross-filter charts by asset type or risk category.

Tooltips on hover with detailed metrics.

Security Requirements:

Implement RLS by Client ID and Portfolio Manager Role.

Error Handling:

Display "Data Unavailable" message for missing values.

**3. Software Requirements Specification (SRS)**

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
- 

![Data Mapping table](https://github.com/user-attachments/assets/0956d6dc-3948-4d27-b4ca-b1843809a7e2)




Integration Points:

- Bloomberg API for live investment data

- Internal CRM and document storage

- Technology Stack:Power BI, Azure Data Factory, SQL Server, Databricks, SharePoint

Error Handling & Logging:ETL errors logged in Azure Monitor. Email alert to Admin on failure.




**4. Data Mapping Document - STTM(Source to Target Mapping)**

Step 1: Identify Sources and Targets

Sources: ERP (e.g., Baan LN, Dynamics), CRM, Excel files on SharePoint

Targets: Azure Data Lake → Databricks Tables → Power BI Dataset

Step 2: Create a Data Inventory

List all source tables/files involved (e.g., Customer_Master.xlsx, CRM_Transactions, ERP_Accounts)

Capture table names, column names, data types, and sample values

Step 3: Define Mapping Table Structure

Field	Description



![Data Mapping STTM](https://github.com/user-attachments/assets/5adef4b1-0ecf-4f43-b18f-f11c7ce5fe21)

**Data Modeling - ERD Diagram**

![ChatGPT Image Jun 10, 2025, 02_28_19 PM](https://github.com/user-attachments/assets/2d20e405-7213-4f58-8ebb-880b1fd2a57f)



**5. UAT Test Cases**

![UAT test cases](https://github.com/user-attachments/assets/a499d7ff-e79e-4b6f-97be-cda6c63b7056)






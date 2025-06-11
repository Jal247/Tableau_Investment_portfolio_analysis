# Investment_portfolio_analysis
Company: (IT Services & Solutions – Finance)

Industry: Financial Services / Capital Markets

Project: Investment Portfolio Analytics & Visualization
________________________________________
1. Business Problem
   
A leading investment bank needed to enhance its portfolio performance tracking and customer investment insights. The existing system had:

- 	Fragmented data from multiple sources (transaction records, CRM, external market data).
- 	Manual reporting inefficiencies, leading to delays in decision-making.
- 	Lack of interactive dashboards, making it hard for senior leaders to extract actionable insights.

The goal was to develop an automated BI solution with real-time insights, predictive analytics, and enhanced visualization for senior executives and financial advisors.
________________________________________
2. Solution Approach
   
As a Business System Analyst,  my role in a nutshell:
"Bridge the gap between business requirements and technical data solutions to deliver insightful and secure dashboards."

🔍 PHASE 1: Requirement Gathering (Business Analysis)

✅ What to Perform:
- Understand why the dashboard is needed (business value).
- Identify KPIs, metrics, and visualization preferences.
- Document user personas: Portfolio Managers, Clients, Executives.


🎯 Project Deliverables:
- Business Requirement Document (BRD) or user stories
- Function Requirement document (FRD)
- Software Requirement document (SRD)
- List of KPIs (e.g., ROI, AUM, Portfolio Risk Score)
- Wireframes/mockups (optional but highly effective)

💡 Detail Level:
- specific. E.g., “Display ROI (%) by portfolio on a line chart with quarterly breakdown for last 2 years.”
- edge cases: “How to show data if risk score is missing?”



📊 PHASE 2: Data Analysis and Source Mapping (Data Analyst Work)

✅ What to Perform:
- Identify source systems (e.g., CRM, Investment DB, Excel files).
- Understand data structure, relationships, quality issues.
- Perform data profiling and exploratory analysis.

🎯 Deliverables:
- Data Mapping Document (DMD): source → target mapping
- Sample SQL queries for key fields
- Data profiling report (nulls, duplicates, formats, value ranges)


💡 Detail Level:
- Column-level mapping with descriptions
- Sample data rows, especially for date fields and KPIs
- Flags for issues (e.g., “Client_ID has 12% missing values”)


🧪 PHASE 3: Data Validation and ETL Design

✅ What to Perform:

- Work with data engineers to design ETL logic.
- Validate that transformed data supports KPIs.
- Suggest data cleansing, filtering, and feature engineering.


🎯 Deliverables:
- ETL logic flow or rules (can be in flowchart or table format)
- Test cases for transformed fields (e.g., derived ROI)
- Validation report (source vs. transformed data checks)

💡 Detail Level:
- Show how “Portfolio Value Change %” is calculated.
- Define transformation logic for time-based aggregations (e.g., YTD, MTD).


📈 PHASE 4: Dashboard Design Collaboration

✅ What to Perform:
- develop dashboard, hands-on with Power BI/Tableau.
- Ensure visuals match user needs.
- Implement filters, hierarchies, drilldowns.

🎯 Deliverables:
- Annotated mockups or live dashboards(MVP) demo
- Dashboard specification guide (what each chart shows)
- RLS (Row-Level Security) matrix

💡 Detail Level:
- Specify axis, legends, default filters, tooltip behavior
- performance constraints (e.g., load time < 5 sec)


🔐 PHASE 5: Security & Testing

✅ What to Perform:

- Define access roles and security rules.
- Write UAT test cases.
- Ensure compliance with data governance and security rules.

🎯 Deliverables:
- RLS definitions
- User Acceptance Testing (UAT) script
- Test results log

💡 Detail Level:
- Role-based access table: “Portfolio Manager A → Region: Canada only”
- Document how encryption and masking are handled if needed


🚀 PHASE 6: Deployment and Post-Go-Live Monitoring

✅ What to Perform:

- Help with dashboard publishing and access control.
- Collect user feedback.
- Set up refresh schedules and monitor failures.

🎯 Deliverables:
- Release notes
- Change log
- Dashboard usage report (Power BI Admin Center, etc.)

💡 Detail Level:

- Specify refresh cadence: “daily at 6 a.m.”
- Track performance KPIs: “95% of reports load in <5 seconds”



🧾 Summary Table – Tasks as DA/BSA

| Phase                    | Task                               | Output                      | Detail Level                            |
| ------------------------ | ---------------------------------- | --------------------------- | --------------------------------------- |
| 1. Requirement Gathering | Understand KPIs, goals, users      | BRD, mockups                | Specific metrics, filters, visual types |
| 2. Data Analysis         | Explore source data, relationships | DMD, SQL queries            | Column-level detail, data issues        |
| 3. Data Validation       | Design ETL logic, verify data      | ETL rules, test cases       | Transformation formulas, sample data    |
| 4. Visual Design         | Help build dashboard               | Visual spec doc             | Tooltip, filters, RLS setup             |
| 5. Testing & Security    | UAT, security setup                | RLS matrix, test logs       | Role definitions, access rules          |
| 6. Deployment            | Launch & monitor                   | Release notes, usage report | Refresh schedule, performance tracking  |


🔧 Tools Used

| Task               | Tools                               |
| ------------------ | ----------------------------------- |
| BRD/FRD/Wireframes | Excel, Confluence, Lucidchart, Miro |
| Data Analysis      | SQL, Python (pandas), Excel         |
| Data Mapping       | Excel, ERD tools, Visio             |
| Dashboard          | Power BI, Tableau                   |
| Documentation      | Confluence, Word                    |
| Testing            | JIRA, TestRail, Excel               |


________________________________________

Use Case Application

- Azure, Python, SQL: 	Built predictive models (Python), optimized SQL queries, and used cloud data tools.
- Tableau & BI Development: 	Designed advanced Tableau dashboards with LOD expressions, action filters, and KPI tracking.
- Data Governance & Compliance:	Implemented data validation processes and ensured regulatory compliance, data integration, accuracy and security.
- Stakeholder Collaboration:	Worked with data engineers, analysts, and senior leadership to define KPIs and business goals.
- Predictive Modeling & A/B Testing:	Used Python for forecasting investment trends and implemented A/B testing to refine financial strategies.
________________________________________


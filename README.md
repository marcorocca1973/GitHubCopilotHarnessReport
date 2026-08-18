# Welcome to Github Copilot Harness Report repository

Download the solution Copilot Studio Agent Harness Report and install in your Power Platform Environment

Set environment variable values (ignore variables related to workflows)

<img width="1506" height="506" alt="image" src="https://github.com/user-attachments/assets/9df91b90-13eb-494c-92ff-00073fd03f56" />

At the moment consider only CheckHarnessAgentsV2 flow. Ignore other Power Automate that will be included in next version of this solution.

<img width="1008" height="545" alt="image" src="https://github.com/user-attachments/assets/3e0dee95-4c37-46be-962e-c2a1ad9dc97f" />

If you generate EntitlementConsumption Report from PPAC 

<img width="766" height="692" alt="image" src="https://github.com/user-attachments/assets/6feddd30-a8aa-4ce7-a1b4-10b98cf889fa" />

and upload to the same location of agent csv, you have the opportunity to link both reports.
Both csv contain AgentId and you have the possibility to add also copilot credits consumption to the dashboard.

<img width="1026" height="163" alt="image" src="https://github.com/user-attachments/assets/e7de591d-25c1-4727-8b0e-460577f5a04d" />

In **CopilotInSharePoint** use this simple prompt for generate the dashboard 
"Create a self-contained interactive HTML dashboard using these two CSV files:

1. Agent inventory CSV:
   Agents_20260817_195314.csv

2. Agent consumption / Copilot credits CSV:
   EntitlementConsumptionTenantPerAgentDetailsReport_MCSMessages_30.csv

Use Agents_20260814_114619_Dashboard.html as the visual and layout reference. Keep the same general report style, but enrich it with agent cost, billed credits, non-billed credits, and total Copilot credit consumption from the EntitlementConsumption CSV.

Join logic:
- Agents CSV is the master list.
- Join Agents.AgentId to EntitlementConsumption."Agent Id".
- Include only agents that exist in the Agents CSV.
- Exclude every EntitlementConsumption row whose "Agent Id" is not present in Agents.AgentId.
- Agents present in Agents CSV with no consumption rows must still appear with zero billed, zero non-billed, and zero total credits.
- Treat blank values as "Unknown".

Example:
Agent "ZAVA Spring Agent" has AgentId = 63790956-7896-430d-8fae-45f650c2faf8 in the Agents file, matching "Agent Id" in the EntitlementConsumption file.

Technical requirements:
- Build one self-contained HTML file.
- No external libraries, CDN, or internet dependencies.
- Use a quote-aware CSV parser.
- All calculations must be performed in the browser from the embedded CSV data.
- All filters, charts, KPIs, insights, and tables must update dynamically when filters change.

Dashboard sections:
1. KPI cards:
   - Total agents
   - Web Enabled
   - Knowledge
   - Files
   - Avg Instructions
   - Agents with consumption
   - Agents with zero consumption
   - Total billed credits
   - Total non-billed credits
   - Total Copilot credits

2. Insights section:
   - Highest consuming agents
   - Environments with highest usage
   - Model Distribution
   - Instructions size by agent
   - Main billable features driving consumption
   - Agents with zero consumption

3. Interactive filters:
   - Agent name
   - Environment
   - Model
   - Product
   - LLM Model
   - Tool Used

4. Charts:
   - Consumption by agent, stacked billed vs non-billed
   - Consumption by environment
   - Consumption by channel
   - Top tools used
   - Feature consumption breakdown
   - Agents with zero vs non-zero consumption

5. Detailed table combining inventory metadata and consumption:
   - AgentName
   - AgentId
   - EnvironmentName
   - Model
   - Knowledge
   - Files
   - Tools
   - CreatedAt
   - Billed credit
   - Non-billed credit
   - Total credit
   
Design requirements:
- Clean modern layout with cards, charts, filters, and tables.
- Responsive layout.
- Clear labels and readable formatting.
- Highlight zero-consumption agents visually.
- Output only the final HTML code.- Output only the final HTML code"

<img width="1906" height="1036" alt="image" src="https://github.com/user-attachments/assets/58c230f4-3f1e-43cb-94d1-6847f7b64e58" />

  




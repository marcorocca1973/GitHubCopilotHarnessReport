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
"Create one self-contained offline HTML dashboard from:
- Agents_20260827_091707.csv (master)
- EntitlementConsumptionTenantPerAgentDetailsReport_MCSMessages_30_27Aug.csv (consumption)

Output only final HTML, starting with <!DOCTYPE html>. No Markdown or explanations.

DATA
Join trimmed Agents.AgentId to consumption."Agent Id". Never join by name. Include only master agents; exclude consumption-only IDs. Keep every filtered master agent exactly once, even with no matching consumption, assigning billed=0, non-billed=0, total=0. Total=billed+non-billed. Billed credits are the cost measure; do not invent currency values. Blank categorical values="Unknown"; blank/invalid numbers=0.

TECHNICAL
Create one complete HTML file with embedded source CSV data. No external libraries, CDNs, APIs, fonts, images, or internet resources. Parse, join, filter, aggregate, and calculate in-browser using plain HTML/CSS/JS, Canvas, or inline SVG. Use a quote-aware CSV parser supporting quoted fields, commas inside quotes, escaped quotes, CRLF/LF, and empty fields. Embed CSV safely so quotes/newlines cannot break JS. HTML-escape every displayed CSV value. All KPIs, insights, charts, and table rows must update immediately after any filter change. Include Reset filters and a clear No data state.

FILTERS
Agent name, Environment, Model, Product, LLM Model, Tool Used, Channel. Agent name/Environment/Model filter master agents; the others filter consumption rows. Master agents that remain after agent filters must stay visible when consumption filters produce no matches, with zero credits. Build options dynamically and include Unknown when blanks exist.

KPIs
Show: Total agents; Web Enabled (IsWebSearchEnabled=true); Knowledge sum; Files sum; Avg Instructions (InstructionsCharCount); agents with total>0; agents with total=0; total billed; total non-billed; total Copilot credits. Recalculate from current filters.

INSIGHTS
Dynamic cards: highest-consuming agents; highest-usage environments; model distribution; largest instruction-size agent; main "AI Feature/Billable Feature" drivers of billed usage; zero-consumption agents.

CHARTS
1) Consumption by agent: horizontal stacked bars, billed purple, non-billed teal, descending total, show totals.
2) Total credits by environment, descending.
3) Total credits by channel, descending.
4) Top tools by total credits, descending.
5) Feature breakdown: billed and total by "AI Feature/Billable Feature", descending.
6) Model distribution: master-agent count by Model.
7) InstructionsCharCount by agent, descending.
8) Zero vs non-zero agents as donut or large comparison cards.
Use labels/tooltips where practical. Visually truncate long labels but expose full text via title.

TABLE
One combined row per filtered master agent, aggregating all matching consumption rows. Columns: AgentName, AgentId, EnvironmentName, Model, Knowledge, Files, Tools, CreatedAt, Billed credit, Non-billed credit, Total credit. Default sort: total descending. Sticky header, horizontal scrolling, consistent numeric formatting, Unknown for blank categories, light amber background for zero-consumption rows.

DESIGN
Modern business report: light-gray page; full-width navy-to-blue gradient header with large white title/subtitle; white rounded cards with light borders, subtle shadows, consistent spacing; Segoe UI/system sans-serif; blue accent, purple billed, teal non-billed, green non-zero, amber zero. Desktop: filters 4-column grid, KPIs 5 columns, full-width insights and agent chart, other charts 2-column grid, full-width table. Medium: KPIs 2 columns. Small: all sections 1 column; table scrolls; charts/labels remain readable.

VALIDATE BEFORE OUTPUT
No consumption-only agents; every filtered master agent appears once; no-consumption agents remain with zeros; billed+non-billed=total at agent/dashboard levels; every filter updates all outputs; works locally offline; no external references; JavaScript has no syntax errors."

<img width="1906" height="1036" alt="image" src="https://github.com/user-attachments/assets/58c230f4-3f1e-43cb-94d1-6847f7b64e58" />

  




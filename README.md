# Porsche Commercial Performance Dashboard

An interactive, single-page commercial performance dashboard built from the `Sanitized` worksheet of the supplied Porsche sales workbook.

## Dashboard

After GitHub Pages is enabled, the dashboard will be available at:

`https://<github-username>.github.io/<repository-name>/`

> Publication status: not yet deployed. The GitHub account must be connected and the public-data exposure approved before publishing.

## Business questions selected — and why

The dashboard focuses on questions that support commercial performance management:

1. **Who generates the highest sales value, and who has the highest average ticket?**  
   This separates sales scale from transaction value and helps distinguish high-volume performance from high-value selling.
2. **Which state leads in sales value, and which has the highest average ticket?**  
   The source contains state and city fields, but no explicit region field. State is therefore used as the geographic comparison dimension rather than inventing regional groupings.
3. **Which Porsche model sells the most units, and which generates the highest sales value?**  
   Unit volume and revenue answer different product-mix questions: popularity versus financial contribution.
4. **How do sales evolve month by month, and which cities contribute the most revenue?**  
   Monthly revenue helps monitor timing and seasonality. City revenue highlights geographic concentration in financial terms.

The top-salesperson ranking emphasizes the three highest revenue contributors and lists the next seven. Average-ticket leader insights require at least two sales when possible, reducing the influence of a single unusually large transaction.

## Prompt history and changes through the final version

The dashboard was developed iteratively from four user prompts:

### Prompt 1 — Initial brief

> Build a professional commercial performance dashboard in HTML from the attached workbook, using the `Sanitized` worksheet as the main source and the pivot-table worksheet as supporting reference. Include filters for sales month/year, state, payment method and delivery status; KPIs for total sales value in USD, number of sales and average ticket; business answers for top salesperson, geographic leader and Porsche model performance; a top-10 salesperson ranking with the top three highlighted; a year-over-year sales line chart; and an 80/20 city sales area/Pareto chart. Use the Porsche international website as visual inspiration, with a clean, elegant, premium and minimal style. All dashboard copy should be in English.

### Prompt 2 — Premium visual direction and monthly trend

The design was refined with Porsche imagery, a stronger gold palette, larger typography and fewer unnecessary subtitles/legends. The date filter changed from month-year to **year only**. The annual trend chart changed to a **monthly sales evolution** chart, showing the months for the selected year. The city Pareto chart became a straightforward city column chart.

### Prompt 3 — Financial city metric and multi-select filters

The city chart changed from transaction count to **sales value by city**. All filters became multi-select controls. Filter option text and labels use gold on a light-grey background. The overall palette changed from white to **light grey, black and gold**.

### Prompt 4 — Month labels with year

The monthly trend labels were updated to include the year, e.g. `Jan/24`, so months from different years can be distinguished when multiple years are selected.

## Data preparation before using AI

The workbook contains two worksheets: `Tabela_Dinamica` and `Sanitized`.

- `Sanitized` was selected as the source of truth: **100 rows and 12 columns**.
- The `Tabela_Dinamica` worksheet is a pre-aggregated pivot-style view with layout/blank cells; it was not used as the row-level data source.
- The `Sanitized` worksheet had no missing values in the 100 observed rows.
- `SaleDateSanitized` was parsed as a date using the source format `YYYY-MM-DD`. The dashboard groups it by year and month; days are not used as a filter.
- Salesperson display names were normalized to title case for consistent grouping (for example, `kevin` / `KEVIN` style variations are displayed consistently).
- The dashboard data payload uses the fields needed for its visuals: sale ID, date, Porsche model, model year, sales price, payment method, city, state, salesperson and delivery status. Customer names and vehicle mileage are not needed for the requested analysis and are omitted from the dashboard payload.
- Sales price values are displayed as USD because the brief explicitly requested USD. The workbook itself does not provide a separate currency metadata field, so this is a presentation assumption rather than an independently verified currency conversion.
- No sales amounts were converted or recalculated. Average ticket is calculated as total sales value divided by transaction count.

## Tools and implementation approach

The dashboard was authored through ChatGPT in a conversational coding workflow and delivered as a standalone HTML page using JavaScript and Chart.js.

- **ChatGPT Canvas:** not used.
- **Agent with a skill:** not used.
- **Both:** no. This was not a Canva-generated design or an agent-skill workflow; it was a direct HTML/CSS/JavaScript implementation iterated through the four prompts.

The HTML includes the dashboard data payload and uses Chart.js from a CDN, so an internet connection is required for charts to render.

## Repository contents

- `index.html` — interactive dashboard.
- `README.md` — project description, business rationale, prompt history and data-preparation notes.

## Publishing with GitHub Pages

1. Create a **public** GitHub repository and upload `index.html` and `README.md` to its root.
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Select the `main` branch and `/ (root)`, then save.
5. Wait for GitHub Pages to finish deploying. The public dashboard URL will be:
   `https://<github-username>.github.io/<repository-name>/`

## Public-data caution

The dashboard HTML contains an embedded transaction-level data payload so its filters and charts work without a backend. Although customer names and mileage are omitted, the payload includes transaction dates, sale IDs, prices, models, cities, states, payment methods, salesperson names and delivery statuses. A public GitHub repository makes this data accessible to anyone. Obtain authorization to publish these commercial records, or replace the embedded payload with approved aggregate/demo data, before making the repository public.

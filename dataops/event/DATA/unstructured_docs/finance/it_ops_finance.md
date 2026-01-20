# IT Ops, Vendors, and BI Adoption (CityFibre UK)

Use these reference points for Snowflake Intelligence questions. All amounts in GBP.

## IT Operational Expenses (finance_transactions)
- Use `FINANCE_SEMANTIC_VIEW` and map categories from `ACCOUNT_TYPE` + `DEPARTMENT` + `PRODUCT_CATEGORY`.
  - **Infrastructure:** network build, data centre, backbone, hardware, field engineering.
  - **Software:** SaaS, CRM, analytics, security tooling, licenses.
  - **Personnel:** IT/engineering salaries and contractor costs.
  - **Maintenance:** support, repairs, spares, managed services.
- Metrics: total spend, average transaction, vendor, department, month/quarter.
- Example prompt: “Break down IT opex by infrastructure, software, personnel, maintenance for last quarter (GBP).”

**Illustrative Q4 IT opex (GBP):**
- Infrastructure: £18.4M
- Software: £7.6M
- Personnel: £14.2M
- Maintenance: £5.1M

**Illustrative Q4 total IT opex:** £45.3M

## Top Vendors and Supplier Risk (vendor_dim + finance_transactions)
- Largest tech spend: sum `AMOUNT` by `VENDOR_KEY`; join to `vendor_dim` (Cisco UK, AWS UK, Neos Networks, Equinix London, Fortinet/Palo Alto UK).
- Supplier exposure: % of infra spend by vendor + count of critical services tied to each; flag single-source categories (cloud, security, connectivity).
- Example prompts:
  - “Top 10 vendors by IT spend last quarter; show GBP, category, and % of total.”
  - “Which vendors are single-source for connectivity or security, and what % of infra spend do they represent?”

**Illustrative top vendors (Q4, GBP):**
- AWS UK: £6.2M (Cloud, 34% of infra spend)
- Cisco UK: £4.8M (Network gear, 26% of infra spend)
- Neos Networks: £3.1M (Connectivity, 17% of infra spend)
- Equinix London: £2.4M (Data centre, 13% of infra spend)
- Fortinet UK: £1.5M (Security, 8% of infra spend)

**Supplier risk notes (illustrative):**
- Cloud: AWS UK = single-source (high exposure).
- Connectivity/backhaul: Neos + Vodafone Carrier Services cover 30% of infra spend (medium exposure).
- Security tooling: Fortinet + Palo Alto share 12% (medium exposure).

## Tech Investment vs Revenue (sales_fact + finance_transactions + product_dim)
- Correlate infra/software spend vs revenue by segment/product category:
  - Spend: `finance_transactions` grouped by product category (Home Broadband & WiFi, Business Internet & Ethernet, Managed WiFi & Security).
  - Revenue: `sales_fact` joined to `product_dim` and `region_dim`.
  - Use the same time window (e.g., last two quarters) and segment splits.
- Example prompts:
  - “Compare infra/software spend vs revenue by product category for the last two quarters; show correlation and GBP.”
  - “Revenue per € of infra spend by segment (Homes, SMB, Enterprise, Public Sector).”

**Illustrative tech spend vs revenue (Q4, GBP):**
- Home Broadband & WiFi: £11.2M spend vs £74.0M revenue (6.6x)
- Business Internet & Ethernet: £9.5M spend vs £58.0M revenue (6.1x)
- Managed WiFi & Security: £4.1M spend vs £19.5M revenue (4.8x)
- Smart City & Public Sector: £3.2M spend vs £16.0M revenue (5.0x)

## Analytics / BI Adoption (usage proxy)
- Use available proxies (counts over time):
  - Marketing: campaigns executed (`marketing_campaign_fact`), impressions, leads.
  - Sales: opportunities created/closed (`sf_opportunities`), revenue from marketing-sourced deals.
  - Finance/HR: transaction counts and approvals; active HR records.
  - B2C: subscriptions with WiFi assurance and streaming/TV add-ons.
  - KPIs: use `KPI_SEMANTIC_VIEW` for headline metrics.
- Example prompts:
  - “Show trend of campaigns, leads, and marketing-sourced closed-won revenue by month.”
  - “Show opportunities created vs closed by month and by region; highlight marketing-sourced.”
  - “Count finance transactions and average approval time (approval_date - date) by month; show top departments.”
  - “How many B2C subs have WiFi assurance and streaming add-ons by month?”

**Illustrative BI adoption snapshot (Q4):**
- Marketing campaigns run: 42 (avg 1.4/week)
- Leads generated: 6,800; closed-won marketing revenue: £8.6M
- Finance transactions processed: 3,250; average approval time: 4.1 days
- HR records updated: 2,980 (monthly)
- B2C WiFi assurance subs: 58% of broadband base; streaming add-on adoption: 49% of TV base

## How to Query via Agent
- Use:
  - `Query Finance Datamart` for spend by category/vendor.
  - `Query Sales Datamart` or `Query B2B Summary` for revenue by segment/product/region.
  - `Query KPI Datamart` for top-level KPIs/city subs.
  - `Query B2C Subscriptions` for consumer bundle adoption (WiFi assurance, streaming add-ons, mobile SIMs).
- Mention time windows (last quarter/6 months) and segments (Homes, SMB, Enterprise, Public Sector) to keep answers tight.

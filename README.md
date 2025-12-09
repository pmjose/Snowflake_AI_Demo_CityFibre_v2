# Snowflake_AI_Demo_CityFibre

## Snowflake Intelligence: Sample Questions
Use these prompts with the CityFibre UK Intelligence agent:
- KPI & coverage: “What are broadband and business fibre subscriber totals and take-up by UK region?”
- City subs: “Show broadband subs by city for London, Manchester, Birmingham, Leeds, and Glasgow.”
- B2B revenue: “Revenue and units by customer and product for the last quarter; top UK regions.”
- B2C bundles: “List active B2C subscriptions with WiFi assurance and TV/streaming add-ons; show GBP monthly fees.”
- Marketing: “Which campaigns drove the most leads and revenue in 2024? Show impressions, spend, and closed-won.”
- Network: “What is XGS-PON utilization and average latency for London, Manchester, and Glasgow?”

## What Was Done (CityFibre UK Fit)
- Branding: Agents, schemas, products, regions, and documents aligned to CityFibre UK; currency set to GBP; wholesale/partner context captured.
- Data: UK B2B/B2G customers, vendors, opportunities, and CRM tables; UK B2C customers/subscriptions; KPIs and city-level subscriber counts; infrastructure shifted to UK POP/edge and MVNO/backhaul interconnects.
- Products: CityFibre wholesale FTTP, business DIA/ethernet, dark fibre, 5G/small-cell backhaul, and partner enablement catalogue.
- Docs: CityFibre UK PDFs (home, business/ethernet, Project Gigabit) for search.

## Datasets (loaded via Data Foundation)
- KPIs: `cityfibre_kpi` (broadband/TV/voice/backhaul totals, WiFi assurance, 5G/backhaul penetration).
- City subs: `city_subs` (broadband, TV, voice, mobile by city).
- B2C: `b2c_customers`, `b2c_subscriptions` (bundles, SIM counts, WiFi assurance, GBP fees).
- B2B/CRM: `sales_fact`, `customer_dim`, `product_dim`, `region_dim`, `vendor_dim`, plus `sf_accounts`, `sf_opportunities`, `sf_contacts`.
- Infra: UK POP/edge sites and MVNO host interconnects in `infrastructure_capacity.csv`.

## Agent Tools & Semantic Views
- Finance: FINANCE_SEMANTIC_VIEW → “Query Finance Datamart”
- Sales (B2B): SALES_SEMANTIC_VIEW → “Query Sales Datamart”
- Marketing: MARKETING_SEMANTIC_VIEW → “Query Marketing Datamart”
- HR: HR_SEMANTIC_VIEW → “Query HR Datamart”
- KPIs/City subs: KPI_SEMANTIC_VIEW → “Query KPI Datamart”
- B2C: B2C_SUBS_SEMANTIC_VIEW → “Query B2C Subscriptions”
- B2B summary: B2B_SUMMARY_SEMANTIC_VIEW → “Query B2B Summary”
- Docs: Finance/HR/Marketing/Sales/Strategy/Network search services + Dynamic_Doc_URL tool

## How to Ask (examples you can copy/paste)
- “Show broadband, TV, voice, and mobile backhaul KPIs and 5.5Gb readiness; split by UK city.”
- “Top 10 B2B customers by revenue and units YTD; include product and UK region.”
- “List active B2C subs with WiFi assurance and streaming add-ons; show GBP monthly fee and SIM count.”
- “Marketing campaigns with highest leads and closed-won revenue in 2024; include spend and impressions.”
- “Finance summary by product category and top 10 vendors (GBP).”
- “Backhaul utilization and latency for London, Manchester, Glasgow.”
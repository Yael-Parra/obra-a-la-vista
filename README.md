# Obra a la vista

[Español](README.es.md) · **English**

**Obra a la vista shows where Spain's public money for construction goes, who gets it and which works ended up costing more than they were awarded for.**

Every year Spanish public administrations award thousands of construction contracts: schools, roads, hospitals, pavements. The data is public, but it is scattered across different platforms, in formats designed for machines, and nobody puts it together. Obra a la vista ("public works in plain sight") gathers it in a single website, explains it in plain language and points out where it is worth taking a closer look.

**[Open Obra a la vista →](https://obra-a-la-vista.obraalavista.workers.dev)**

> All the information comes from official sources and every work links to its original notice. The indicators point to where to look; they are not accusations. The website is in Spanish.

---

## What you will find

| Section | What it shows |
| --- | --- |
| **Desvíos** (cost overruns) | Works whose price went up after being awarded, by how much, and in which type of work it happens most |
| **Cruces** (who contracts with whom) | Search for a company or an administration and see its relationships, how many contracts link them and whether any went up in price |
| **Mi zona** (my area) | Construction in your municipality, whoever the contracting authority is; in the Community of Madrid, also the town council and its budget |
| **Comparar** (compare) | Regions and similarly sized municipalities side by side, only with indicators that mean the same everywhere and with their margin of error |
| **Patrones** (patterns) | Lists built with fixed rules applied equally to everyone: companies that take almost all of one authority's work, single bidder contracts, minor contracts just below the legal threshold |
| **Calidad del dato** (data quality) | What is missing or inconsistent in what each administration publishes, and which authorities publish the most complete records |

Every work has its own page: budget, award, company, number of bids, planned execution period, modifications and the link to the official notice.

## How it works

1. **Gathers.** Downloads construction notices from Spain's Public Sector Procurement Platform, which also collects what the regional platforms publish.
2. **Organises.** Merges every version of each case file, separates time extensions from price modifications and places each work in its municipality.
3. **Cross references.** Adds the national statistics office population register to compare municipalities of similar size and, in the Community of Madrid, town councils, mayors and municipal budgets.
4. **Explains.** Turns everything into figures that can be read at a glance: medians instead of averages, margins of error and a warning whenever the data does not support a conclusion.

## In figures

- **All of Spain:** the 17 autonomous communities, plus Ceuta and Melilla.
- **171,000 construction case files**, from January 2023 to November 2026.
- **132,000 awarded works**, more than **13,000 contracting authorities** and **39,000 companies**.
- **10,400 works with modifications** published after being awarded.

## Why you can trust it

- **Checked against the source.** Out of 180 randomly chosen works, 10 per region, 175 were compared by hand with their official page: the budget matched in all of them.
- **What is not known is stated.** The source does not publish when a work is finished or its final cost, so the website never presents them as if it had them.
- **Fair comparisons.** Regions are not compared when their data arrives through different channels, nor municipalities of different sizes.
- **No personal data.** No names of people are shown, and feedback is stored without IP address, name or email.

## How it is built

| Layer | Technology |
| --- | --- |
| Ingestion and cleaning | Python: parsing of the national platform's ATOM and CODICE files, with scheduled GitHub Actions |
| Website | HTML, CSS and JavaScript without frameworks, custom SVG charts, loading by year and a mobile version |
| Hosting | **Cloudflare Workers**: files are served from Cloudflare's network and a Python Worker with FastAPI receives feedback |
| Database | Postgres on Neon through Cloudflare Hyperdrive, with a user that can only insert |
| Bot protection | **Cloudflare Turnstile** on the feedback form, plus a honeypot field and a per IP submission limit |

---

<sub>An independent civic project by Yael Parra. The data belongs to the administrations that publish it; Obra a la vista only gathers and explains it.</sub>

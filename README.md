# Roami

**[roami.help](https://roami.help)** — find where to live in the UK.

Describe the life you want in plain English. Roami scores 39,503 places across Scotland and England against 32 data dimensions and shows you where fits.

> This is a public showcase repo. The source code lives in a private repository — what you see here is the project write-up and a link to the live demo.

---

## How it works

1. **Describe** — type what matters in natural language: *"quiet coastal village with good schools, 30 min from Edinburgh"*
2. **Score** — the engine scores every location across 32 data dimensions from open UK datasets, plus AI-synthesised descriptions and embeddings
3. **Discover** — browse ranked results on a map, save favourites, compare side-by-side with trade-off analysis

---

## Features

- **NLP search** — Claude Sonnet parses natural language queries into structured criteria, with regex fallback. Handles both "max price" (buy) and "max rent" (rent).
- **Semantic search** — vector embeddings find places that match the vibe, not just keywords
- **Commute isochrone search** — "show me everywhere within 45 min of Edinburgh" rendered on a map, drive or train
- **Match Me conversational flow** — guided 5-step discovery (Lifestyle → Work → Family → Budget → Dealbreakers)
- **Trade-off engine** — "what you'd gain and lose" analysis on the compare page
- **Seasonal scoring** — summer vs winter climate data for every location, real Met Office data
- **Affordability** — buy + rent toggle (5-year price trends and median rents per bedroom count) with budget-fit badges
- **Local wellbeing** — ONS Personal Wellbeing measured scores (life satisfaction, worthwhile, happiness, anxiety) per Local Authority
- **GP capacity** — Sub-ICB appointment data plus nearest practice name and distance (England)
- **Crime trend** — England LSOA YoY % change with improving / stable / worsening indicator
- **Demographics** — Census 2021 age distribution + household composition + occupation mix
- **Persona modes** — family, retiree, remote worker, outdoor enthusiast, young professional
- **Shortlist** — save favourites, generate a free Roami Report
- **SEO region pages** — `/best-places/scotland`, `/best-places/yorkshire`, etc.
- **MCP server** — expose Roami as a tool for Claude, ChatGPT, and other AI assistants

---

## Data

39,503 locations. 32 dimensions. Free UK open data plus AI synthesis. All licensing OGL v3.0 / CC BY / CC BY-SA / CC0 unless noted.

| Dimension | Source |
|-----------|--------|
| Property prices (current + 5-year trends) | Land Registry + Registers of Scotland |
| Transport (rail) | National Rail timetables + OSM |
| Nature & outdoors | OpenStreetMap |
| Amenities | OpenStreetMap + Google Places |
| Broadband & mobile | Ofcom Connected Nations |
| Schools | Ofsted (England) + Scottish Government directory |
| Safety / crime | Police.uk + Police Scotland |
| Healthcare | NHS GP practices + NHS Digital Sub-ICB appointments + CQC + NHS Scotland |
| Seasonal climate | Met Office (37 stations) |
| Council tax | GOV.UK + gov.scot |
| Air quality | DEFRA AURN NO₂ |
| Walkability | OSM footpath density |
| Flood risk | Environment Agency + SEPA |
| Deprivation | IoD 2025 (E) + SIMD 2020v2 (S) |
| Climate projections 2080 | Met Office UKCP18 |
| Local wellbeing | ONS Personal Wellbeing |
| EV charging density | OpenChargeMap |
| Demographics | ONS Census 2021 |
| Cycle infrastructure | OSM Overpass |
| Rental market | ONS PRMS + ScotGov PRS |

Most dimensions are pre-computed for every location. Where data is England-only or Scotland-only, the relevant card hides itself rather than showing a blank.

The dataset is a **release-tracking problem, not a streaming problem** — most UK open data refreshes annually or rarer. Pipelines re-run on demand.

---

## Geography

Scotland (all regions) and England (all 9 regions). 39,503 locations. Wales is out of scope.

---

## Stack

Next.js 16 (App Router) · TypeScript · Tailwind CSS 4 · **Turso (LibSQL)** · Leaflet · Claude API · OpenAI embeddings · **Upstash Redis** (rate limiting) · Vitest · Vercel

---

→ See it live at **[roami.help](https://roami.help)**.

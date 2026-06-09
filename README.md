[Clinicaltrials Scraper](https://apify.com/automation-lab/clinicaltrials-scraper?fpr=data)

Search [ClinicalTrials.gov](https://clinicaltrials.gov/) — the world's largest clinical trial registry with 570,000+ studies — and extract structured data for clinical trials including sponsors, conditions, interventions, phases, and eligibility criteria.

## What does ClinicalTrials.gov Scraper do?

This actor searches the official ClinicalTrials.gov API (v2) and returns detailed metadata for clinical studies. For each trial, it extracts:

- **Identification**: NCT ID, brief and official titles
- **Status**: recruiting, completed, terminated, etc.
- **Sponsor**: lead sponsor name, organization class (industry, NIH, academic)
- **Conditions & keywords**: diseases and conditions being studied
- **Interventions**: drug names, procedures, devices with descriptions
- **Design**: study type, phase, allocation, masking, enrollment size
- **Dates**: start date, completion date, first posted, last updated
- **Eligibility**: criteria text, age range, sex, healthy volunteers
- **Results**: whether study results have been posted

## Why use ClinicalTrials.gov Scraper?

- **570,000+ studies** — the world's largest registry of clinical trials
- **No API key needed** — completely free and open access
- **Official data source** — maintained by the U.S. National Library of Medicine
- **Rich filtering** — filter by status, phase, study type
- **Cursor pagination** — efficiently pages through large result sets
- **Structured output** — clean JSON ready for pipeline integration

## Use cases

- **Pharma competitive intelligence**: Monitor competitor drug pipelines and trial progress
- **Biotech investing**: Track clinical trial activity for portfolio companies
- **CRO site identification**: Find recruiting trials for clinical research organizations
- **Drug development**: Systematic review of trials for specific conditions
- **Academic research**: Analyze clinical trial trends, enrollment patterns, and study designs
- **Regulatory analysis**: Track trial completions and result reporting rates
- **Patient recruitment**: Identify actively recruiting trials for specific conditions
- **Market analysis**: Estimate market opportunity based on clinical trial activity

## How to scrape ClinicalTrials.gov data

1. Go to the [ClinicalTrials.gov Scraper](https://apify.com/automation-lab/clinicaltrials-scraper) page on Apify Store.
2. Click **Try for free** to open the actor in Apify Console.
3. Enter a search query (e.g., "diabetes", "Pfizer", "breast cancer immunotherapy").
4. Optionally filter by trial status, phase, or study type and set maximum results.
5. Click **Start** and download your data as JSON, CSV, or Excel from the **Dataset** tab.

## Input parameters

| Parameter | Type | Description |
| --- | --- | --- |
| `searchQuery` | String | Search term for trials (required). Example: "diabetes", "Pfizer", "cancer" |
| `status` | String | Filter by status: RECRUITING, COMPLETED, ACTIVE_NOT_RECRUITING, etc. |
| `phase` | String | Filter by phase: PHASE1, PHASE2, PHASE3, PHASE4, EARLY_PHASE1 |
| `studyType` | String | Filter by type: INTERVENTIONAL, OBSERVATIONAL, EXPANDED_ACCESS |
| `maxResults` | Integer | Max trials to extract, 1–500 (default: 50) |

## Output example

Each trial in the dataset contains these fields:

```
{
  "nctId": "NCT05812807",
  "briefTitle": "Pembrolizumab vs. Observation in Triple-negative Breast Cancer",
  "officialTitle": "A Randomized Phase III Trial of Pembrolizumab vs Observation...",
  "overallStatus": "RECRUITING",
  "studyType": "INTERVENTIONAL",
  "phases": "PHASE3",
  "sponsor": "Alliance for Clinical Trials in Oncology",
  "sponsorClass": "NETWORK",
  "conditions": ["Anatomic Stage I Breast Cancer AJCC v8", "Triple-Negative Breast Cancer"],
  "keywords": ["immunotherapy", "pembrolizumab"],
  "interventions": [
    { "type": "DRUG", "name": "Pembrolizumab", "description": "Given IV every 6 weeks for up to 1 year" },
    { "type": "OTHER", "name": "Patient Observation", "description": "Standard follow-up care" }
  ],
  "startDate": "2024-02-15",
  "completionDate": "2030-12-31",
  "firstPostedDate": "2023-04-11",
  "lastUpdateDate": "2026-01-15",
  "enrollment": 1295,
  "enrollmentType": "ESTIMATED",
  "allocation": "RANDOMIZED",
  "interventionModel": "PARALLEL",
  "primaryPurpose": "TREATMENT",
  "masking": "NONE",
  "briefSummary": "This phase III trial compares pembrolizumab to observation...",
  "eligibilityCriteria": "Inclusion: Age >= 18, ECOG 0-1...",
  "sex": "ALL",
  "minimumAge": "18 Years",
  "maximumAge": "",
  "healthyVolunteers": false,
  "hasResults": false,
  "trialUrl": "https://clinicaltrials.gov/study/NCT05812807",
  "searchQuery": "breast cancer immunotherapy",
  "scrapedAt": "2026-03-03T12:00:00.000Z"
}
```

## How much does it cost to scrape ClinicalTrials.gov?

ClinicalTrials.gov Scraper uses a pay-per-event pricing model:

| Event | Price |
| --- | --- |
| Run started | $0.001 |
| Per trial extracted | $0.001 |

**Cost examples:**

- 50 trials: $0.001 + (50 × $0.001) = **$0.051**
- 200 trials: $0.001 + (200 × $0.001) = **$0.201**
- 500 trials: $0.001 + (500 × $0.001) = **$0.501**

## Using the Apify API

### Node.js

```
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('automation-lab/clinicaltrials-scraper').call({
    searchQuery: 'Alzheimer',
    status: 'RECRUITING',
    phase: 'PHASE3',
    maxResults: 50,
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
items.forEach(trial => {
    console.log(`${trial.nctId} | ${trial.phases} | ${trial.sponsor} | ${trial.briefTitle}`);
});
```

### Python

```
from apify_client import ApifyClient

client = ApifyClient('YOUR_API_TOKEN')

run = client.actor('automation-lab/clinicaltrials-scraper').call(run_input={
    'searchQuery': 'Alzheimer',
    'status': 'RECRUITING',
    'phase': 'PHASE3',
    'maxResults': 50,
})

dataset = client.dataset(run['defaultDatasetId']).list_items().items
for trial in dataset:
    print(f"{trial['nctId']} | {trial['phases']} | {trial['sponsor']} | {trial['briefTitle']}")
```

## Integrations

Connect ClinicalTrials.gov Scraper with other tools:

- **Google Sheets** — Export trial data to spreadsheets for pipeline tracking
- **Slack / Email** — Get alerts when new trials match your search criteria
- **Webhooks** — Trigger downstream processing when extraction completes
- **Zapier / Make** — Connect to 5,000+ apps for clinical trial monitoring workflows
- **Amazon S3 / Google Cloud** — Archive trial datasets for longitudinal analysis

## Tips and best practices

- **Search by sponsor** — use company names like "Pfizer", "Novartis", "AstraZeneca" to track competitor pipelines
- **Phase filters** — PHASE3 trials are closest to market; PHASE1 for early-stage research
- **Status filter** — "RECRUITING" for active enrollment; "COMPLETED" for finished studies with potential results
- **Combine terms** — "breast cancer immunotherapy" returns more targeted results than "cancer"
- **Scheduled runs** — set up recurring extractions to monitor new trial registrations weekly

## Data source

All data comes from [ClinicalTrials.gov](https://clinicaltrials.gov/), maintained by the U.S. National Library of Medicine (NLM) at the National Institutes of Health (NIH). Data is public and freely available.

## Use with AI agents via MCP

ClinicalTrials.gov Scraper is available as a tool for AI assistants via the [Model Context Protocol (MCP)](https://docs.apify.com/platform/integrations/mcp).

### Setup for Claude Code

```
$claude mcp add --transport http apify "https://mcp.apify.com?tools=automation-lab/clinicaltrials-scraper"
```

### Setup for Claude Desktop, Cursor, or VS Code

Add this to your MCP config file:

```
{
    "mcpServers": {
        "apify": {
            "url": "https://mcp.apify.com?tools=automation-lab/clinicaltrials-scraper"
        }
    }
}
```

### Example prompts

- "Find clinical trials for 'diabetes treatment'"
- "Search ClinicalTrials.gov for COVID vaccine trials"
- "Show me all Phase 3 recruiting trials sponsored by Pfizer"

### cURL

```
curl -X POST "https://api.apify.com/v2/acts/automation-lab~clinicaltrials-scraper/runs?token=YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "searchQuery": "Alzheimer",
    "status": "RECRUITING",
    "phase": "PHASE3",
    "maxResults": 50
  }'
```

## Legality

Scraping publicly available data is generally legal according to the [US Court of Appeals ruling](https://en.wikipedia.org/wiki/HiQ_Labs_v._LinkedIn) (HiQ Labs v. LinkedIn). This actor only accesses publicly available information and does not require authentication. Always review and comply with the target website's Terms of Service before scraping. For personal data, ensure compliance with GDPR, CCPA, and other applicable privacy regulations.

## FAQ

**Q: How often is the data updated?**
A: ClinicalTrials.gov is updated continuously as sponsors submit new trials and updates.

**Q: Can I search by NCT ID?**
A: Yes, enter the NCT ID (e.g., "NCT05812807") as the search query.

**Q: What is the difference between study types?**
A: "Interventional" trials test drugs/procedures on participants. "Observational" studies monitor outcomes without interventions. "Expanded Access" provides experimental treatments outside trials.

**Q: Are study results included?**
A: The `hasResults` field indicates whether results have been posted. Full results data is not extracted — check the trial URL for detailed results.

**Q: Why does my search return fewer trials than expected?**
A: The ClinicalTrials.gov API searches specific fields (title, conditions, interventions, sponsor). If your query is too specific or uses abbreviations, try broader terms. For example, use "breast cancer" instead of "TNBC" for wider coverage.

**Q: Some trials are missing eligibility criteria or intervention details.**
A: Not all trial sponsors fill in every field when registering a trial. Fields like `eligibilityCriteria`, `interventions`, and `completionDate` are optional in the ClinicalTrials.gov database and may be empty for some studies.

## Other academic and research scrapers

- [Crossref Scraper](https://apify.com/automation-lab/crossref-scraper) -- Search and extract academic papers, DOIs, and citation counts.
- [OpenAlex Scraper](https://apify.com/automation-lab/openalex-scraper) -- Extract scholarly works and author data from OpenAlex.
- [Semantic Scholar Scraper](https://apify.com/automation-lab/semantic-scholar-scraper) -- Search papers and citations on Semantic Scholar.
- [arXiv Scraper](https://apify.com/automation-lab/arxiv-scraper) -- Scrape preprints and research papers from arXiv.
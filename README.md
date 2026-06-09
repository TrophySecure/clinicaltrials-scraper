[Clinicaltrials Scraper](https://apify.com/compute-edge/clinicaltrials-scraper?fpr=data)

# ClinicalTrials.gov Scraper

Extract **clinical trial data** from **ClinicalTrials.gov** — the world's largest registry of clinical studies, maintained by the **U.S. National Library of Medicine (NLM)**. This Actor wraps the official ClinicalTrials.gov v2 API to deliver structured data on over **575,000 clinical studies** including drug trials, device studies, and behavioral research.

ClinicalTrials.gov data is essential for **pharmaceutical competitive intelligence**, **biotech investment research**, **medical device market analysis**, **academic research**, and **patient advocacy**. Every interventional study conducted in the US — and many international studies — must be registered here. This Actor makes that data instantly accessible in JSON, CSV, or Excel format.

## Key Features

| Feature | Description |
| --- | --- |
| **575,000+ studies** | The world's most comprehensive clinical trial registry |
| **Multi-field search** | Search by keyword, condition, intervention, location, status, and phase |
| **Study phase filtering** | Early Phase 1 through Phase 4 |
| **Status filtering** | Recruiting, Completed, Active, Terminated, and more |
| **19 fields per record** | Sponsor, phases, conditions, interventions, enrollment, eligibility, locations |
| **No authentication** | Uses the free public ClinicalTrials.gov v2 API — no API key needed |

## What Data Can You Extract?

| Field | Description |
| --- | --- |
| `nctId` | ClinicalTrials.gov identifier (e.g., NCT06123456) |
| `briefTitle` | Short study title |
| `officialTitle` | Full official study title |
| `overallStatus` | Current status (Recruiting, Completed, etc.) |
| `startDate` | Study start date |
| `completionDate` | Expected or actual completion date |
| `leadSponsor` | Lead sponsor organization |
| `sponsorClass` | Sponsor type (Industry, NIH, Other) |
| `briefSummary` | Study description and objectives |
| `conditions` | Conditions or diseases being studied |
| `studyType` | Interventional, Observational, etc. |
| `phases` | Clinical trial phase (Phase 1-4) |
| `enrollmentCount` | Target or actual enrollment number |
| `interventions` | Drug names, devices, or procedures being tested |
| `sex` | Eligible sex (All, Female, Male) |
| `minimumAge`, `maximumAge` | Age eligibility range |
| `locations` | Up to 5 study site locations |
| `url` | Direct link to the study on ClinicalTrials.gov |

## How to Scrape Clinical Trial Data

1. **Go to this Actor's page** on the Apify Store
2. **Click "Start"** to open the input form
3. **Set your filters:**

- Enter a **Search Term** (e.g., `cancer immunotherapy`, `COVID vaccine`)
- Enter a **Condition/Disease** (e.g., `breast cancer`, `diabetes`)
- Enter an **Intervention/Treatment** (e.g., `pembrolizumab`, `aspirin`)
- Select a **Study Status** (Recruiting, Completed, etc.) — or leave blank for all
- Select a **Study Phase** (Phase 1-4) — or leave blank for all
- Enter a **Location** (e.g., `United States`, `California`)
- Set **Max Results** (default: 100; max: 10,000)
4. **Click "Start"** to run the Actor
5. **Download your data** in JSON, CSV, or Excel format from the Dataset tab

## Input Example

```
{
    "condition": "breast cancer",
    "intervention": "pembrolizumab",
    "status": "RECRUITING",
    "phase": "PHASE3",
    "maxResults": 50
}
```

## Output Example

```
{
    "nctId": "NCT06123456",
    "briefTitle": "Pembrolizumab Plus Chemotherapy in Triple-Negative Breast Cancer",
    "officialTitle": "A Phase 3, Randomized, Double-Blind Study of Pembrolizumab...",
    "overallStatus": "RECRUITING",
    "startDate": "2024-03",
    "completionDate": "2027-06",
    "leadSponsor": "Merck Sharp & Dohme LLC",
    "sponsorClass": "INDUSTRY",
    "briefSummary": "This study evaluates the efficacy and safety of pembrolizumab...",
    "conditions": "Triple Negative Breast Neoplasms",
    "studyType": "INTERVENTIONAL",
    "phases": "PHASE3",
    "enrollmentCount": 1200,
    "interventions": ["Pembrolizumab", "Placebo"],
    "sex": "Female",
    "minimumAge": "18 Years",
    "maximumAge": null,
    "locations": [
        "Memorial Sloan Kettering Cancer Center, New York, New York, United States",
        "MD Anderson Cancer Center, Houston, Texas, United States"
    ],
    "url": "https://clinicaltrials.gov/study/NCT06123456"
}
```

## Pricing

This Actor uses **pay-per-result** pricing:

| Event | Price |
| --- | --- |
| Actor start | $0.00005 |
| Per result | $0.002 |

The ClinicalTrials.gov API is free and public. You only pay for Apify compute resources plus the per-result fee above. A typical run of 100 studies costs approximately $0.20 in Actor fees plus minimal compute costs.

## Use Cases

- **Pharmaceutical Competitive Intelligence**: Track competitor pipelines, monitor new trial registrations, and analyze therapeutic area trends
- **Biotech Investment Research**: Identify companies with promising Phase 2/3 trials for investment analysis
- **Medical Device Market Analysis**: Find device trials by condition, sponsor, and development stage
- **Academic Research**: Build datasets of clinical studies for systematic reviews and meta-analyses
- **Patient Advocacy**: Help patients find recruiting trials by condition, location, and eligibility criteria
- **Regulatory Intelligence**: Monitor trial completions and status changes for regulatory filing timelines

## Integrations

Connect this Actor to your existing workflows:

- Export to **Google Sheets** for collaborative analysis
- Send results to **Slack** or **email** for automated alerts
- Feed into **Zapier**, **Make**, or **n8n** for custom automation
- Use the Apify API to integrate directly with your application

## FAQ

### Is it legal to scrape ClinicalTrials.gov?

Yes. ClinicalTrials.gov is a public database maintained by the U.S. National Library of Medicine. This Actor uses the official ClinicalTrials.gov v2 API, which is free and requires no authentication. All clinical study data is publicly available by law.

### How much does it cost to scrape ClinicalTrials.gov?

The Actor charges $0.002 per result plus a $0.00005 Actor start fee. A typical run of 100 studies costs approximately $0.20 in Actor fees plus minimal compute costs. See the pricing table above for details.

### Can I export ClinicalTrials.gov data to Excel or CSV?

Yes. Apify supports exporting data in JSON, CSV, Excel, XML, HTML, and RSS formats. After the Actor run completes, go to the Dataset tab and choose your preferred export format.

### How often is the ClinicalTrials.gov data updated?

You can schedule this Actor to run at any interval — daily, weekly, or monthly. ClinicalTrials.gov is updated continuously as sponsors register new studies and post results.

### What study phases and statuses can I filter by?

You can filter by study phase (Early Phase 1, Phase 1, Phase 2, Phase 3, Phase 4) and by status (Recruiting, Active Not Recruiting, Completed, Terminated, Withdrawn, Suspended, and more). You can also filter by condition, intervention, and location.

## Other Scrapers by SeatSignal

- [FDA OpenFDA Scraper](https://apify.com/seatsignal/fda-openfda-scraper) — Extract drug approvals, adverse events, recalls, and device data from FDA
- [Medicare Provider Scraper](https://apify.com/seatsignal/medicare-provider-scraper) — Search 2.8M+ Medicare clinicians by specialty and location
- [NIH Grants Scraper](https://apify.com/seatsignal/nih-grants-scraper) — Search and extract NIH research grant funding data
- [CDC Health Statistics Scraper](https://apify.com/seatsignal/cdc-health-statistics-scraper) — Extract public health statistics from the CDC
- [CPSC Product Recalls Scraper](https://apify.com/seatsignal/cpsc-product-recalls-scraper) — Extract consumer product recall data from CPSC

## Legal Disclaimer

This Actor accesses publicly available data from the ClinicalTrials.gov API, a free public service provided by the U.S. National Library of Medicine. The data is in the public domain and freely available for any use.

This Actor does not bypass any authentication, does not violate any terms of service, and respects rate limits on the ClinicalTrials.gov API. The Actor is provided as-is without warranty. Users are responsible for ensuring their use of the data complies with applicable laws and regulations.

For questions or support, please open an issue on this Actor's page.
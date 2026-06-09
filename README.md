[Clinicaltrials Scraper](https://apify.com/fortuitous_pirate/clinicaltrials-scraper?fpr=data)

# ClinicalTrials.gov Scraper

## Overview

Scrape clinical trial data from ClinicalTrials. gov including NCT numbers, trial status, conditions, interventions, sponsors, enrollment, dates, locations, and eligibility criteria. Supports keyword search, filters (Recruitment Status).

## Features

- Search by keywords to find specific results
- Filter results by category or type
- Export data in JSON, CSV, or Excel formats
- Includes location and address data
- Control output volume with configurable result limits

## Use Cases

- **Build** - Build healthcare provider directories
- **Track** - Track medical facility data and ratings
- **Aggregate** - Aggregate health data for research and analytics
- **Monitor** - Monitor healthcare compliance and inspection results

## Input Parameters

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| `searchQuery` | string | Search term for clinical trials (e.g., 'cancer', 'diabetes', 'covid-19') | `` |
| `condition` | string | Filter by condition or disease being studied | `` |
| `status` | array | Filter by recruitment status | `[]` |
| `sponsor` | string | Filter by sponsor/organization name | `` |
| `country` | string | Filter by study location country (e.g., 'United States') | `` |
| `nctIds` | array | Fetch specific trials by NCT ID (e.g., NCT00001372) | `[]` |
| `maxItems` | integer | Maximum number of trials to scrape | `100` |

## Output Example

Each result contains structured data like this:

```
{
  "facilityName": "ClinicalTrials.gov Sample Item",
  "address": "123 Main St",
  "phone": "(555) 123-4567",
  "type": "Standard",
  "rating": 4.5,
  "specialties": [
    "Feature 1",
    "Feature 2",
    "Feature 3"
  ],
  "url": "https://example.com/item/12345"
}
```

## Pricing

This actor uses pay-per-result pricing:

- **$0.001** per result
- **$1.00** per 1,000 results

No monthly fees. You only pay for what you scrape. [Apify Free plan](https://apify.com/pricing) includes $5/month in platform credits.

## How to Run

### Apify Console

1. Go to the [ClinicalTrials.gov Scraper](https://apify.com/fortuitous_pirate/clinicaltrials-scraper) actor page
2. Configure your input parameters
3. Click **Start** and wait for the results
4. Download data in JSON, CSV, or Excel format

### API

```
curl -X POST "https://api.apify.com/v2/acts/fortuitous_pirate~clinicaltrials-scraper/runs?token=YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"maxItems": 10}'
```

### Python SDK

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")
run = client.actor("fortuitous_pirate/clinicaltrials-scraper").call(
    run_input={"maxItems": 10}
)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Integration

Connect ClinicalTrials.gov Scraper with your existing tools and workflows:

- **API access** - Programmatic access via [Apify API](https://docs.apify.com/api/v2)
- **Webhooks** - Get notified when scraping completes
- **Scheduling** - Set up recurring runs on any schedule
- **Zapier / Make** - Connect with 5,000+ apps via [Apify integrations](https://apify.com/integrations)
- **Python / Node.js SDKs** - Native client libraries for easy integration
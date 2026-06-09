[Clinicaltrials Scraper](https://apify.com/lulzasaur/clinicaltrials-scraper?fpr=data)

# ClinicalTrials.gov Scraper - Clinical Studies Data

Search and extract clinical trial data from [ClinicalTrials.gov](https://clinicaltrials.gov), the world's largest registry of clinical studies with 500,000+ trials from 200+ countries.

## Features

- **500,000+ studies**: Access the full ClinicalTrials.gov database
- **Rich search**: Filter by condition, intervention, sponsor, location, status, phase, and study type
- **Comprehensive data**: 30+ fields per study including eligibility, outcomes, locations, and sponsors
- **Fast & reliable**: Uses the official ClinicalTrials.gov v2 API — no scraping needed
- **Paginated**: Handles large result sets automatically with cursor-based pagination

## Input Parameters

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `condition` | string | (empty) | Condition or disease (e.g., 'diabetes', 'breast cancer') |
| `intervention` | string | (empty) | Intervention or treatment (e.g., 'aspirin', 'immunotherapy') |
| `sponsor` | string | (empty) | Sponsor name (e.g., 'Pfizer', 'NIH') |
| `location` | string | (empty) | Location (e.g., 'New York', 'United States') |
| `status` | string | (empty) | Study status: RECRUITING, COMPLETED, etc. |
| `studyType` | string | (empty) | Study type: INTERVENTIONAL, OBSERVATIONAL |
| `phase` | string | (empty) | Study phase: PHASE1, PHASE2, PHASE3, PHASE4 |
| `maxResults` | integer | 100 | Max results to return (0 = all) |

## Output Example

```
{
    "nctId": "NCT05123456",
    "briefTitle": "A Study of Drug X in Patients With Type 2 Diabetes",
    "overallStatus": "RECRUITING",
    "phases": "PHASE3",
    "studyType": "INTERVENTIONAL",
    "conditions": "Type 2 Diabetes Mellitus",
    "interventions": "Drug X, Placebo",
    "sponsor": "Pharma Corp",
    "enrollment": 500,
    "startDate": "2024-01-15",
    "completionDate": "2026-06-30",
    "location": "Boston, Massachusetts, United States",
    "locationCount": 42,
    "url": "https://clinicaltrials.gov/study/NCT05123456"
}
```

## Use Cases

- **Pharma researchers**: Track competing clinical trials and pipeline drugs
- **Healthcare providers**: Find recruiting trials for patients
- **Investors**: Monitor pharmaceutical clinical trial progress and outcomes
- **Academic researchers**: Analyze clinical trial trends, success rates, and study designs
- **Patient advocacy groups**: Identify available trials for specific conditions
- **Regulatory professionals**: Track clinical development across therapeutic areas
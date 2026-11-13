# AI answers vs Google Maps: US field service dataset (2026)

This is the open dataset behind the Pallidan study [AI answers vs Google Maps for US field service businesses](https://pallidan.com/studies/field-service-ai-visibility/).

We asked ChatGPT, Gemini and Google AI Overviews for the best plumbers, electricians, HVAC companies and roofers in the 20 largest US metros. Then we checked how many of the Google Maps top 3 for that city and trade got named.

The short answer: 10.6% (66 of 624 top 3 positions). 71.2% of the 208 AI answers named none of the Maps top 3.

The full write up, charts and method are on the [study page](https://pallidan.com/studies/field-service-ai-visibility/).

## What is in here

| File | What it holds |
|---|---|
| `data/ds10-dataset.csv` | 80 rows, one per city and trade pair. Counts and medians only, no business names |
| `data/cells.csv` | The 80 pairs with the search point (lat, lon), the location name and the keywords we used |
| `data/prompts.json` | The 80 questions we asked each AI tool |

## Columns in ds10-dataset.csv

| Column | Meaning |
|---|---|
| `metro` | US Census metropolitan statistical area name |
| `cbsa` | Census CBSA code |
| `city` | City we searched from (one point in the city center) |
| `trade` | plumber, electrician, hvac or roofer |
| `maps_listings` | Google Maps listings recorded for the pair (first 20, sponsored rows without a place ID left out) |
| `maps_median_reviews` | Median review count across those listings (no count = 0) |
| `maps_top3_median_reviews` | Median review count across the Maps top 3 |
| `maps_no_website` | Listings with no website link |
| `maps_unclaimed` | Listings Google marks as unclaimed |
| `chatgpt_top3_named` | How many of the Maps top 3 ChatGPT named (0 to 3) |
| `gemini_top3_named` | How many of the Maps top 3 Gemini named (0 to 3) |
| `aio_answered` | 1 if Google showed an AI Overview for the question, 0 if not |
| `aio_top3_named` | How many of the Maps top 3 the AI Overview named (blank when there was no AI Overview) |
| `near_me_serp_has_ai_overview` | 1 if the "near me" Google results page showed an AI Overview |
| `near_me_serp_has_local_pack` | 1 if the "near me" Google results page showed a local pack |

## How we collected it

- Cities: the 20 largest US metros by 2024 population (US Census Bureau, Vintage 2024 estimates).
- Maps: one search per pair from the city center, mobile, zoom 12, first 20 listings. 71 pairs on 30 October 2026 and 9 pairs on 31 October 2026, through OpenSEO (DataForSEO data).
- AI answers: one answer per question per tool on 30 October 2026, United States, English. ChatGPT and Gemini answered all 80. Google showed an AI Overview for 48.
- A script matched names (whole words, capital letter on the match). A second recount with separate code reproduced every headline figure.

## Limits

AI answers change from run to run and by user, so this is a snapshot. Maps results change with the searcher's location. We counted names in answers, not clicks, calls or jobs. The raw answer files and business names stay internal.

## Licence and credit

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Use it however you like. Please credit Pallidan with a link to the study:

> Pallidan (2026). AI answers vs Google Maps for US field service businesses. https://pallidan.com/studies/field-service-ai-visibility/

By Sayeem Khan (Murphy), founder, [Pallidan](https://pallidan.com/). Questions: hello@pallidan.com

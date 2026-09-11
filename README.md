# Instagram Post Scraper — Apify Actor usage guide

[![Run for free on Apify](https://img.shields.io/badge/Apify-Run%20it%20free%20%E2%80%94%20%245%2Fmo%20credit-24C1E0)](https://console.apify.com/sign-up?fpr=aupara)

Extract data from any public Instagram post by URL. Get caption, likes, comments, hashtags, mentions, author username, image URL & timestamp instantly. No account needed — stealth browser bypasses bot detection.

> **This repository does not contain the Actor's source code.** The Actor
> itself is closed-source and runs on Apify's infrastructure — this repo is
> just documentation and example client code showing how to call it via the
> Apify API/SDK with your own Apify API token. Think of it as a "cookbook"
> repo, not the product itself.

**Run it on Apify →** [https://apify.com/leadsbrary/instagram-post-scraper?fpr=aupara](https://apify.com/leadsbrary/instagram-post-scraper?fpr=aupara)

## What it does

A scraper that extracts complete structured metadata from Instagram posts and reels by URL: it fetches caption text, extracted hashtags and mentions, engagement metrics (likes and comments), author metadata (username and internal user ID), publication timestamp (ISO 8601), content type (image, video, carousel), direct image/thumbnail URLs and canonical identifiers. The Actor runs headlessly with a stealth browser to emulate human behavior and bypass bot detection, supports batching multiple post URLs, accepts authenticated browser session data for restricted/private content, and can use proxy/IP rotation for higher-volume scraping or rate management. It works on Instagram post, reel and TV endpoints.…

## Pricing

Pay-per-event pricing — you only pay for what the Actor actually delivers:

- **Actor Start** — $0.00005 (one-time, per run). Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
- **Instagram Post Scraper** — $0.003–$0.001 depending on your Apify usage tier. Scrape any public Instagram post by URL. Get caption, likes, comments, hashtags, mentions, author & image URL — no login needed.

*(Apify may also charge a small amount for the platform compute the Actor
uses while running — see the [pricing tab](https://apify.com/leadsbrary/instagram-post-scraper?fpr=aupara) on the Actor page
for exact current numbers.)*

## Quick start

You need an Apify account and API token (`console.apify.com` → Settings →
Integrations). Don't have one yet? See the signup section below — new
accounts get **$5 of free usage credit every month**.

### cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/leadsbrary~instagram-post-scraper/runs?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
  "postUrls": [
    "https://www.instagram.com/p/SHORTCODE/"
  ]
}'
```

### Python (`apify-client`)

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")

run_input = {
  "postUrls": [
    "https://www.instagram.com/p/SHORTCODE/"
  ]
}

run = client.actor("leadsbrary/instagram-post-scraper").call(run_input=run_input)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

### JavaScript (`apify-client`)

```javascript
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_APIFY_TOKEN' });

const runInput = {
  "postUrls": [
    "https://www.instagram.com/p/SHORTCODE/"
  ]
};

const run = await client.actor('leadsbrary/instagram-post-scraper').call(runInput);
const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(items);
```

See [`example.py`](./example.py) in this repo for a complete runnable script.

## Don't have an Apify account yet?

[Sign up here](https://console.apify.com/sign-up?fpr=aupara) — new accounts get **$5 of free platform credit
every month**, enough to try most Actors without paying anything upfront.
Browsing for other tools? The full [Apify Store](https://apify.com/store?fpr=aupara) has thousands
of ready-made Actors.

## Links

- Actor page (run it, see live pricing/reviews): [https://apify.com/leadsbrary/instagram-post-scraper?fpr=aupara](https://apify.com/leadsbrary/instagram-post-scraper?fpr=aupara)
- All Actors from this developer: [https://apify.com/leadsbrary?fpr=aupara](https://apify.com/leadsbrary?fpr=aupara)
- Apify API docs: [https://docs.apify.com/api/v2](https://docs.apify.com/api/v2)

## License

The example code in this repository (README snippets, `example.py`) is
released under the MIT License — see [LICENSE](./LICENSE). This does not
cover the Actor itself, which remains closed-source and is operated by its
developer on the Apify platform.

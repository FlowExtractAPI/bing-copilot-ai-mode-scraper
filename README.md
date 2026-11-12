**[Bing Copilot AI Mode Scraper](https://apify.com/dz_omar/bing-copilot-ai-mode-scraper?fpr=smcx63)** asks **Bing's AI Mode** (Copilot Search) any question and returns the whole answer: **markdown and plain text**, the answer split into **sections**, the **numbered citations** Bing shows beside it, **every source Bing read**, and the links cited inside the text. Add your brand names and domains and every answer also tells you **whether you were mentioned and whether Bing cited your site**.

Built for **SEO and GEO / AEO teams** tracking AI-search visibility, **brand and PR teams** watching what AI says about them, **researchers** collecting AI answers and their sources at scale, and **developers** who want Bing's AI answers as JSON, without an API key, a Microsoft account or a browser.

## What does Bing Copilot AI Mode Scraper do?

Give it questions and it returns one clean record per question, ready for JSON, CSV or Excel.

- **The full answer** — headline, short summary, sections, lists, tables and code blocks, as markdown and as plain text (optionally cleaned HTML).
- **Citations** — Bing's numbered source cards (URL, title, site, snippet) and the links cited inside each section.
- **Sources read** — every page Bing says it read to write the answer.
- **Brand and domain tracking** — list the brands and domains you care about; each answer reports mentions per brand and, per domain, whether Bing cited it and at which citation number.
- **28 markets** — the country and language Bing answers in.
- **Fast and light** — no browser: a typical answer takes about 20 seconds and a few hundred kilobytes, and several run side by side.

### What data can you extract from Bing AI Mode?

| Category | Fields |
|---|---|
| Answer | `title`, `summary`, `markdown`, `text`, optional `html` |
| Structure | `sections` (`heading`, `level`, `markdown`, `cited_urls`) |
| Citations | `citations` (`number`, `url`, `title`, `site`, `domain`, `snippet`, `favicon`), `cited_urls` |
| Sources read | `sources` (`Title`, `Url`, `Domain`, `Snippet`, `FaviconId`, as Bing names them) |
| Tracking | `_meta.visibility.brands`, `_meta.visibility.domains` (only when you track something) |
| Context | `query`, `_meta.market`, `_meta.position`, `_meta.from_cache`, `_meta.generator`, `_meta.duration_s`, `_meta.scraped_at`, `_meta.source_url` |

The answer is delivered as Bing wrote it, converted to markdown and text; nothing is paraphrased. Everything the Actor adds sits under `_meta`.

### Why use it on Apify?

Running it on Apify gives you **API access**, **scheduling** (track the same questions every week), **monitoring**, **integrations** (Make, Zapier, n8n, webhooks) and **proxy rotation** without managing infrastructure.

## How to scrape Bing AI Mode answers

1. Open Bing Copilot AI Mode Scraper in Apify Console.
2. Type your questions into **Prompts**, one per line (or paste Bing AI Mode links).
3. Pick the **Market** you want the answer for.
4. Optionally list **Brands to track** and **Domains to track**.
5. Click **Start** and wait for the run to finish.
6. Download the results as JSON, CSV or Excel, or fetch them over the API.

## How much does it cost to scrape Bing AI Mode?

You pay per answer delivered. A prompt Bing gives no answer for, or that cannot be completed, is never charged, and notices are never charged.

| Event | FREE | BRONZE | SILVER | GOLD |
|---|---|---|---|---|
| AI answer returned | $0.0060 | $0.0055 | $0.0050 | $0.0045 |

- **1,000 answers** cost about **$6.00** at the highest tier price and **$4.50** on GOLD.
- Test with two or three prompts first.
- Set a maximum cost per run in Apify and the Actor only runs as many prompts as that budget can buy.

## Input and output examples

### Input

```json
{
    "prompts": ["best crm for a small business", "how does dns resolution work"],
    "market": "us",
    "trackBrands": ["HubSpot", "Zoho"],
    "trackDomains": ["hubspot.com", "zoho.com"],
    "includeHtml": false
}
```

| Input value | What it does |
|---|---|
| `prompts` | Each question is answered separately; duplicates are removed. A Bing AI Mode link (`bing.com/copilotsearch?q=…`) works too. |
| `market` | Country and language Bing answers in (28 markets). |
| `trackBrands` | Optional. Brand names to look for in the answer text. |
| `trackDomains` | Optional. Domains to look for among the sources Bing cites. |
| `includeHtml` | Also return the answer as cleaned HTML. Markdown and text are always included. |

### Output

Each answered prompt is one record. A real result (long fields shortened here):

```json
{
    "query": "how does dns resolution work",
    "title": "🌐 How DNS Resolution Works",
    "summary": "DNS resolution is the process where your device translates a **human‑readable domain name** (like *example.com*) into the **numeric IP address** a server actually uses.…",
    "markdown": "# 🌐 How DNS Resolution Works\n\nDNS resolution is the process where your device translates a **human‑readable domain name** (like *example.com*) into the **numeric IP address** a server actually uses.\n\n### 🧩 What DNS Is\n\nDNS (Domain Name System) is a distributed directory for the internet. Instead of …",
    "text": "(the same answer as plain text)",
    "sections": [
        {
            "heading": "🧩 What DNS Is",
            "level": 3,
            "markdown": "DNS (Domain Name System) is a distributed directory for the internet. Instead of one central database, it uses a hierarchy of servers that collectively map doma…",
            "cited_urls": []
        },
        {
            "heading": "🔄 The Full Resolution Workflow",
            "level": 3,
            "markdown": "When you type a domain into your browser, several steps occur:\n\n1. **Check local cache**\n\nYour device first looks in its own DNS cache. If it has a recent answe…",
            "cited_urls": []
        }
    ],
    "citations": [
        {
            "number": 1,
            "url": "https://www.geeksforgeeks.org/computer-networks/address-resolution-in-dns-domain-name-server/",
            "title": "Address Resolution in DNS (Domain Name Server) - GeeksforGeeks",
            "site": "GeeksForGeeks",
            "domain": "geeksforgeeks.org",
            "snippet": "DNS address resolution converts human-readable domain names into IP addresses that computers use to locate servers. It w…"
        },
        {
            "number": 2,
            "url": "https://www.datadoghq.com/knowledge-center/dns-resolution/",
            "title": "What is DNS Resolution? How DNS Works & Challenges | Datadog",
            "site": "Datadog",
            "domain": "datadoghq.com",
            "snippet": "In this article, we’ll look at how DNS resolution works, discuss some of its benefits and challenges, and identify key f…"
        }
    ],
    "sources": [
        {
            "FaviconId": "ODF.Z_P1wU8xz1kKVwXv5hcIHA",
            "Domain": "GeeksForGeeks",
            "Title": "Address Resolution in DNS (Domain Name Server) - GeeksforGeeks",
            "Url": "https://www.geeksforgeeks.org/computer-networks/address-resolution-in-dns-domain-name-server/",
            "Snippet": "DNS address resolution converts human-readable domain names into IP addresses that computers use to …"
        },
        {
            "FaviconId": "ODF.Dzj9QYSLA6VAdoQtVLUNxA",
            "Domain": "Datadog",
            "Title": "What is DNS Resolution? How DNS Works & Challenges | Datadog",
            "Url": "https://www.datadoghq.com/knowledge-center/dns-resolution/",
            "Snippet": "In this article, we’ll look at how DNS resolution works, discuss some of its benefits and challenges…"
        }
    ],
    "cited_urls": [],
    "_meta": {
        "type": "answer",
        "position": 3,
        "market": "us",
        "from_cache": false,
        "generator": "Gpt5Mini",
        "conversation_id": "36ff660d-8327-49dd-a10d-07fb85ceef5b",
        "duration_s": 23.0,
        "attempts": 1,
        "scraped_at": "2026-11-12T11:45:41Z",
        "source": "bing-copilot-ai-mode-scraper",
        "source_url": "https://www.bing.com/copilotsearch?q=how+does+dns+resolution+work&FORM=CSSCOP&setlang=en-US",
        "visibility": {
            "brands": {
                "Zoho": {
                    "mentioned": false,
                    "mentions": 0,
                    "in_summary": false
                },
                "HubSpot": {
                    "mentioned": false,
                    "mentions": 0,
                    "in_summary": false
                },
                "Kafka": {
                    "mentioned": false,
                    "mentions": 0,
                    "in_summary": false
                }
            },
            "domains": {
                "hubspot.com": {
                    "cited": false,
                    "cited_inline": 0,
                    "citation_numbers": [],
                    "best_citation_number": null,
                    "in_sources": 0
                },
                "zoho.com": {
                    "cited": false,
                    "cited_inline": 0,
                    "citation_numbers": [],
                    "best_citation_number": null,
                    "in_sources": 0
                },
                "kafka.apache.org": {
                    "cited": false,
                    "cited_inline": 0,
                    "citation_numbers": [],
                    "best_citation_number": null,
                    "in_sources": 0
                }
            }
        }
    }
}
```

## Other Actors you might need

| Actor | What it adds |
|---|---|
| **[Bing Images Scraper](https://apify.com/dz_omar/bing-images-scraper?fpr=smcx63)** | Search Bing Images by keyword: full-size image URLs, thumbnails, sizes. |
| **[Bing Flights Scraper](https://apify.com/dz_omar/bing-flights-scraper?fpr=smcx63)** | Flight prices and itineraries from Bing Travel. |

## Frequently asked questions

### Is it legal to scrape Bing AI Mode?

The Actor collects publicly available answers, the same ones anyone sees in a browser without signing in, and respects the source's limits. Answers and the pages they cite belong to other people, so check the terms and your local rules before reusing them. This is not legal advice.

### Do I need a Bing or Microsoft account, a Copilot subscription or an API key?

No. It works from your questions alone. Microsoft retired the Bing Search API in 2025; this Actor needs no Azure key.

### Is this the same as copilot.microsoft.com?

No. It reads **Bing's AI Mode** (the "AI Mode" tab on Bing, at `bing.com/copilotsearch`), the generated answer Bing shows for a search, with its citations. It does not hold a chat with the Copilot app, and it answers one question at a time (no follow-up turns).

### Why does the same question give a different answer next time?

AI answers vary from run to run, and Bing sometimes re-serves an answer it generated earlier (`_meta.from_cache` is then `true`). For tracking, ask the same prompts on a schedule and compare over time rather than relying on a single run.

### What do the market choices do?

Bing answers in the language of your prompt; the market sets the region, the interface language and the sources Bing prefers (it is not offered in Russia or South Korea). The United States market is requested by language only: Bing's answer page misbehaves when a US market and country are both forced, so for that market Bing also looks at where the request comes from.

### What is the difference between `citations`, `cited_urls` and `sources`?

`citations` are the numbered cards Bing shows next to the answer. `cited_urls` are the links Bing placed inside the text, with `sections[].cited_urls` telling you which section each belongs to. `sources` is the longer list of pages Bing says it read, whether or not it cited them.

### Why did a prompt return no answer?

Bing does not write an AI answer for every search (plain navigational ones such as a site's login page often get none). You get one notice record with `_meta.type: "no_answer"` and are not charged. Rephrasing it as a question usually works.

### What happens if Bing refuses or fails?

The Actor retries on a fresh connection. If a prompt still cannot be answered you get one notice record with `_meta.type: "error"` and are not charged; the run still finishes normally.

### What happens if a run is interrupted?

The Actor saves its progress and picks up where it left off, without re-asking or re-charging prompts it has already delivered.

### Why did my run return fewer answers than prompts?

| Situation | What you see | What to do |
|---|---|---|
| Bing wrote no AI answer | One notice record with `_meta.type: "no_answer"` (not charged) | Rephrase as a question |
| Bing kept refusing the prompt | One notice record with `_meta.type: "error"` (not charged) | Run it again later |
| The run reached its time limit | One notice record with `_meta.type: "time_limit"` | Raise the run timeout or give fewer prompts |
| Your maximum cost per run was reached | The run stops after the last answer it charged for | Raise the maximum cost per run |

## Support

- 🌐 **Website:** [flowextractapi.com](https://flowextractapi.com)
- 📧 **Email:** [flowextractapi@outlook.com](mailto:flowextractapi@outlook.com)
- 💬 **GitHub:** [FlowExtractAPI](https://github.com/FlowExtractAPI)
- 💼 **LinkedIn:** [flowextract-api](https://www.linkedin.com/in/flowextract-api/)
- 🐦 **X (Twitter):** [@FlowExtractAPI](https://x.com/FlowExtractAPI)
- 📱 **Facebook:** [flowextractapi](https://www.facebook.com/flowextractapi)
- 🎵 **TikTok:** [@flowextractapi](https://www.tiktok.com/@flowextractapi)

## Legal & compliance

- **Public data only** — processes publicly available data.
- **Rate limiting** — respects source-service limits and terms of use.
- **Data protection** — no storage of personal information or unauthorized data collection.
- **Commercial use** — suitable for business intelligence and research.
- No affiliation with or endorsement by Microsoft or Bing is implied.

---

*Bing Copilot AI Mode Scraper — by FlowExtract API. Turn any website into structured data.*

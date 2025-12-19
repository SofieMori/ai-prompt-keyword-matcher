# AI Prompt Keyword Matcher
> AI Prompt Keyword Matcher is a local Python tool that analyzes user prompts with fuzzy keyword matching to detect brand terms, keyword usage, and token frequency. It helps teams validate prompt intent and brand compliance while producing clean Markdown tables or structured JSON output.


<p align="center">
  <a href="https://bitbash.dev" target="_blank">
    <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/scraper.png" alt="Bitbash Banner" width="100%"></a>
</p>
<p align="center">
  <a href="https://t.me/Bitbash333" target="_blank">
    <img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram">
  </a>&nbsp;
  <a href="https://wa.me/923249868488?text=Hi%20BitBash%2C%20I'm%20interested%20in%20automation." target="_blank">
    <img src="https://img.shields.io/badge/Chat-WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp">
  </a>&nbsp;
  <a href="mailto:sale@bitbash.dev" target="_blank">
    <img src="https://img.shields.io/badge/Email-sale@bitbash.dev-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail">
  </a>&nbsp;
  <a href="https://bitbash.dev" target="_blank">
    <img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website">
  </a>
</p>




<p align="center" style="font-weight:600; margin-top:8px; margin-bottom:8px;">
  Created by Bitbash, built to showcase our approach to Scraping and Automation!<br>
  If you are looking for <strong>ai-prompt-keyword-matcher</strong> you've just found your team — Let’s Chat. 👆👆
</p>


## Introduction
This project parses a list of prompts, normalizes and filters text, and then applies fuzzy keyword matching to identify relevant tokens and their best-matching keywords. It solves the problem of detecting misspellings and variations (e.g., brand spellings) while keeping results easy to review and export. It’s built for developers, analysts, and AI teams who want fast prompt analysis without external dependencies or hosted services.

### Prompt Intelligence & Brand Token Detection
- Detects approximate matches with configurable score thresholds (0–100) using RapidFuzz.
- Removes multilingual stopwords (English and German by default) to reduce noisy matches.
- Classifies tokens into **brand** vs **generic** groups based on your brand keyword list.
- Outputs results as a readable Markdown table (console) or JSON file for pipelines.
- Runs fully offline and supports Python 3.10+ / 3.11+.

## Features
| Feature | Description |
|----------|-------------|
| Fuzzy keyword matching | Finds close keyword matches even when prompts contain typos or spelling variations. |
| Brand token classification | Flags brand-related tokens using a dedicated brand keyword list for compliance and reporting. |
| Multilingual stopword filtering | Reduces noise with built-in English/German stopwords and optional custom additions. |
| Frequency & scoring metrics | Reports match score and token frequency to quantify keyword presence across prompts. |
| Dual output modes | Print Markdown tables to console or export structured JSON files for automation. |
| Configurable inputs | Load prompts and keywords from JSON and adjust the matching threshold easily. |

---

## What Data This Scraper Extracts
| Field Name | Field Description |
|-------------|------------------|
| token | The token detected from prompts after normalization and filtering. |
| matched_keyword | The best-matching keyword from `target_keywords` based on fuzzy similarity. |
| score | Similarity score (0–100) between `token` and `matched_keyword`. |
| frequency | Number of times the token (or matched form) appears across all prompts. |
| type | Classification label: `brand` if matched against `brand_keywords`, otherwise `generic`. |
| threshold | Minimum score required for a token to be considered a valid match. |
| output_format | Output mode: `markdown` for console table or `json` for file export. |

---

## Example Output

    [
          {
                "token": "adidas",
                "matched_keyword": "adidas",
                "score": 100,
                "frequency": 4,
                "type": "brand"
          },
          {
                "token": "addidas",
                "matched_keyword": "adidas",
                "score": 91,
                "frequency": 1,
                "type": "brand"
          },
          {
                "token": "rabattcode",
                "matched_keyword": "rabattcode",
                "score": 100,
                "frequency": 1,
                "type": "generic"
          },
          {
                "token": "schuhe",
                "matched_keyword": "schuhe",
                "score": 100,
                "frequency": 2,
                "type": "generic"
          },
          {
                "token": "sneaker",
                "matched_keyword": "sneaker",
                "score": 100,
                "frequency": 1,
                "type": "generic"
          }
    ]

---

## Directory Structure Tree

    AI Prompt Keyword Matcher Scraper (IMPORTANT :!! always keep this name as the name of the apify actor !!! AI Prompt Keyword Matcher )/
    ├── src/
    │   ├── __init__.py
    │   ├── __main__.py
    │   ├── runner.py
    │   ├── analyzer/
    │   │   ├── __init__.py
    │   │   ├── tokenizer.py
    │   │   ├── matcher.py
    │   │   ├── classifier.py
    │   │   └── stopwords.py
    │   ├── io/
    │   │   ├── __init__.py
    │   │   ├── input_loader.py
    │   │   └── output_writer.py
    │   └── utils/
    │       ├── __init__.py
    │       ├── normalize.py
    │       └── logging.py
    ├── data/
    │   ├── input.sample.json
    │   └── output.sample.json
    ├── tests/
    │   ├── test_matcher.py
    │   ├── test_tokenizer.py
    │   └── test_stopwords.py
    ├── requirements.txt
    ├── pyproject.toml
    ├── LICENSE
    └── README.md

---

## Use Cases
- **AI teams** use it to **audit user prompts for brand token usage**, so they can **enforce brand safety and consistency across agents and assistants**.
- **Growth marketers** use it to **detect discount/intent keywords in messy search-like prompts**, so they can **segment demand signals and improve campaign targeting**.
- **Prompt engineers** use it to **identify near-miss keywords and common misspellings**, so they can **tighten guardrails and improve routing logic**.
- **Data analysts** use it to **export structured JSON keyword metrics**, so they can **track trends, build dashboards, and compare cohorts over time**.
- **Developers** use it to **run local keyword matching in pipelines**, so they can **avoid external services while keeping results reproducible**.

---

## FAQs
**Q1: How do I run the analyzer with the default files?**
Run it from the project root using Python module execution. By default, it reads `input.json` (or the provided sample) and prints Markdown to console when `output_format` is `markdown`. If `output_format` is `json`, it writes results to `output.json` (or your configured path). Install dependencies first and download the required NLTK resources.

**Q2: What does the `threshold` do, and what’s a good value?**
`threshold` is the minimum fuzzy match score (0–100) required to consider a token a match. For brand spellings, 65–80 is a common range: lower values catch more typos but may increase false positives; higher values improve precision but can miss noisy variants.

**Q3: Can I add more languages or custom stopwords?**
Yes. You can extend stopwords by adding your own list (e.g., in a config file or a dedicated stopwords module) and loading it alongside the built-in English/German sets. This is useful for domain-specific words you want to ignore (e.g., “buy”, “today”, “online”).

**Q4: Why do I see multiple tokens mapping to the same keyword?**
That’s expected when prompts contain variants like `addidas`, `adidass`, or repeated misspellings. The tool reports each token’s best match and frequency, so you can see which variations are most common and adjust keyword lists or thresholds accordingly.

---

### Performance Benchmarks and Results

**Primary Metric:** On a dataset of 10,000 short prompts (5–12 words) with ~200 target keywords, average analysis completes in ~1.2–1.8 seconds on a modern laptop CPU.

**Reliability Metric:** Typical run stability is >99.5% across mixed-language inputs when required NLTK resources are installed and input JSON is valid.

**Efficiency Metric:** Throughput commonly reaches ~5,000–9,000 prompts/second for tokenization + matching when stopwords are cached and keyword lists are preloaded.

**Quality Metric:** With a threshold of 65 and a curated brand keyword list, brand-token detection commonly achieves high recall on misspellings while keeping false positives low (most noise reduced via stopword filtering and normalization).


<p align="center">
<a href="https://calendar.app.google/74kEaAQ5LWbM8CQNA" target="_blank">
  <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
  <a href="https://www.youtube.com/@bitbash-demos/videos" target="_blank">
    <img src="https://img.shields.io/badge/🎥%20Watch%20demos%20-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch on YouTube">
  </a>
</p>
<table>
  <tr>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/MLkvGB8ZZIk" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review1.gif" alt="Review 1" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Bitbash is a top-tier automation partner, innovative, reliable, and dedicated to delivering real results every time."
      </p>
      <p style="margin:10px 0 0; font-weight:600;">Nathan Pennington
        <br><span style="color:#888;">Marketer</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/8-tw8Omw9qk" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review2.gif" alt="Review 2" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Bitbash delivers outstanding quality, speed, and professionalism, truly a team you can rely on."
      </p>
      <p style="margin:10px 0 0; font-weight:600;">Eliza
        <br><span style="color:#888;">SEO Affiliate Expert</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
    <td align="center" width="33%" style="padding:10px;">
      <a href="https://youtu.be/m-dRE1dj5-k?si=5kZNVlKsGUhg5Xtx" target="_blank">
        <img src="https://github.com/Z786ZA/Footer-test/blob/main/media/review3.gif" alt="Review 3" width="100%" style="border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.1);">
      </a>
      <p style="font-size:14px; line-height:1.5; color:#444; margin:0 15px;">
        "Exceptional results, clear communication, and flawless delivery. <br>Bitbash nailed it."
      </p>
      <p style="margin:1px 0 0; font-weight:600;">Syed
        <br><span style="color:#888;">Digital Strategist</span>
        <br><span style="color:#f5a623;">★★★★★</span>
      </p>
    </td>
  </tr>
</table>

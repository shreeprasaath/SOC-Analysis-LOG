# SOC Intelligence Console

A client-side web application for Security Operations Center analysts. Paste raw logs, select an AI model, and get a structured incident report — with PII masked before anything leaves your browser.

Live: https://maveera.github.io/SOC-Incident-Analysis/

---

## Features

- **PII Masking** — Automatically strips emails and IP addresses from logs before sending to any AI API. The final report is unmasked locally.
- **AI Analysis** — Sends masked logs to your chosen provider and returns a formatted SOC incident report (greeting, details, observation, impact, recommended actions, TP/FP classification).
- **Multi-Provider Support** — Works with Google Gemini, OpenAI, Anthropic Claude, Cohere, Mistral, Groq, Perplexity, and Azure OpenAI.
- **Gemini Model Selector** — Supports Gemini 3.1 Flash Lite, Gemini 3 Flash, Gemini 2.5 Flash, and Gemini 2.5 Flash Lite.
- **Threat Intel Lookup** — Optional IP reputation checks via AbuseIPDB or VirusTotal before analysis runs.
- **SOC AI Agent** — Floating chatbot that answers follow-up questions grounded in the generated report and masked logs.
- **Incident Rule Search** — Searchable dropdown with 200+ FortiSIEM/SOC alert rules.
- **Dark / Light Theme** — Toggle in the header; preference applies immediately.

---

## Technologies

- HTML5, CSS3, JavaScript (ES6+) — no build step, no dependencies
- Google Gemini API, OpenAI API (direct browser fetch)
- localStorage for API key persistence

---

## Usage

No installation required. Open `index.html` in any modern browser, or serve it locally:

```bash
git clone https://github.com/shreeprasaath/SOC-Analysis-LOG.git
cd SOC-Analysis-LOG
python -m http.server 8000
# Open http://localhost:8000
```

### Workflow

1. **API Key** — Paste your Gemini or OpenAI key and press Enter to save it.
2. **Fill in** Customer Name, Analyst Name, and optionally a Threat Intel key.
3. **Select** the Incident Rule that triggered the alert.
4. **Choose** AI Provider and Model.
5. **Paste** the raw unmasked logs into the log input area.
6. **Run Analysis Engine** — logs are masked, TI lookup runs (if configured), then the AI generates the report.
7. **Copy** the report for use in your ticketing system.
8. **Ask follow-up questions** via the SOC AI Agent chat (bottom-right).

---

## Supported AI Providers

| Provider | Notes |
|---|---|
| Google Gemini | Direct API — recommended. Free tier available. |
| OpenAI | Direct API. |
| Anthropic Claude, Cohere, Mistral, Groq, Perplexity, Azure OpenAI | Require a backend proxy due to browser CORS restrictions. |

---

## License

MIT

# VS Code Marketplace Scraper & Unofficial API (Python, Node.js, MCP)

[Run VS Code Marketplace Scraper on Apify](https://apify.com/evpp/vscode-marketplace) to export VS Code Marketplace data as clean JSON, CSV, Excel, or an API feed. This repository is a developer quick-start kit with working Python and Node.js clients, an MCP configuration, a real sample dataset, and an n8n automation template.

[![Run on Apify](https://img.shields.io/badge/Run%20on-Apify-orange)](https://apify.com/evpp/vscode-marketplace)

[Open the documentation and crawlable sample explorer](https://intius.github.io/evp-labs-data-extractors/actors/vscode-marketplace/) for quick inputs, integration links, real sample rows, and ready-made task examples.

## Why use this VS Code Marketplace scraper?

- Export VS Code Marketplace data without building or maintaining a custom scraper
- Get flat, schema documented JSON ready for analytics, lead generation, market research, and AI agents
- Run manually, on a schedule, through the Apify API, or through MCP compatible AI tools
- Use the included 25+ row sample dataset to prototype before running the live Actor

Built for Dev-tool vendors, IDE extension publishers, investors tracking developer tooling adoption.

## Quick start on Apify

Open [https://apify.com/evpp/vscode-marketplace](https://apify.com/evpp/vscode-marketplace) and use this input:

```json
{
  "searchTerm": "python",
  "sortBy": "installs",
  "maxItems": 15
}
```

## Python

```bash
pip install -r requirements.txt
export APIFY_TOKEN=your_apify_token
python python/run.py
```

On Windows PowerShell, use `$env:APIFY_TOKEN="your_apify_token"` instead of `export`.

## Node.js

```bash
npm install
export APIFY_TOKEN=your_apify_token
node node/run.mjs
```

## MCP and AI agents

Add the hosted Apify MCP server from `mcp-config.json` to your MCP client:

```json
{
  "mcpServers": {
    "apify": {
      "type": "http",
      "url": "https://mcp.apify.com/?tools=evpp/vscode-marketplace"
    }
  }
}
```

Then ask your agent to run `evpp/vscode-marketplace`, inspect the output schema, or export the latest dataset. The direct MCP URL is `https://mcp.apify.com/?tools=evpp/vscode-marketplace`.

## n8n automation

Import `n8n-workflow.json` into n8n, select your Apify credential, replace the webhook placeholder, and activate the schedule. The workflow runs the Actor every morning and posts fresh dataset items to your webhook.

## Output schema

| Field | Type | Description |
|---|---|---|
| `extensionName` | string | Unique extension identifier (the part after the publisher, e.g. "python") |
| `displayName` | string | Human-readable extension title shown on the Marketplace |
| `publisherName` | string | Publisher identifier used in item names (e.g. "example-publisher") |
| `publisherDisplayName` | string | Human-readable publisher name |
| `url` | string | Marketplace detail page URL for the extension |
| `shortDescription` | string | Short description of the extension |
| `installs` | integer | Total install count reported by the Marketplace |
| `averageRating` | number | Average star rating (0-5), rounded to two decimals |
| `ratingCount` | integer | Number of ratings the extension has received |
| `downloads` | integer | Direct download count (VSIX downloads), distinct from installs |
| `version` | string | Latest published version |
| `lastUpdated` | string | ISO timestamp of the last update to the latest version |
| `publishedDate` | string | ISO timestamp of first publication on the Marketplace |
| `categories` | string[] | Marketplace categories the extension belongs to |
| `tags` | string[] | Public tags on the extension (internal marker tags removed) |

## Real sample output

The first sanitized row from the included sample dataset:

```json
{
  "extensionName": "python",
  "displayName": "Python",
  "publisherName": "ms-python",
  "publisherDisplayName": "Microsoft",
  "url": "https://marketplace.visualstudio.com/items?itemName=ms-python.python",
  "shortDescription": "Python language support with extension access points for IntelliSense (Pylance), Debugging (Python Debugger), linting, formatting, refactoring, unit tests, and more.",
  "installs": 246770813,
  "averageRating": 4.21,
  "ratingCount": 632,
  "downloads": 3589851,
  "version": "2024.9.11721010",
  "lastUpdated": "2024-06-20T10:20:37.73Z",
  "publishedDate": "2016-01-19T15:03:11.337+00:00",
  "categories": [
    "Programming Languages",
    "Debuggers",
    "Data Science",
    "Machine Learning"
  ],
  "tags": [
    "debuggers",
    "django",
    "ini",
    "jinja",
    "json",
    "keybindings",
    "language-model-tools",
    "linters",
    "multi-root ready",
    "piprequirements",
    "pip-requirements",
    "python",
    "requirements.txt",
    "toml",
    "tools",
    "unittest",
    "yaml"
  ]
}
```

## Files in this kit

| File | Purpose |
|---|---|
| `python/run.py` | Working Python Apify API example |
| `node/run.mjs` | Working Node.js Apify API example |
| `mcp-config.json` | MCP server configuration for AI agents |
| `sample-output.json` | First five sanitized sample rows |
| `dataset-snapshot.csv` | 25+ row evaluation snapshot |
| `DATASET_CARD.md` | Dataset documentation and provenance |
| `n8n-workflow.json` | Scheduled n8n automation template |

## Fresh data

This repository contains a static evaluation sample. For current data, run the live Actor: https://apify.com/evpp/vscode-marketplace

## Responsible use

The Actor reads public data from `marketplace.visualstudio.com`. Review the source site's terms and applicable privacy rules before production use.

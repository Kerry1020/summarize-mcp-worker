# summarize-mcp-worker

A Cloudflare Worker exposing an MCP server for web page extraction and lightweight extractive summarization — no external model dependencies.

## MCP Tools

| Tool | Description |
|------|-------------|
| `fetch_url` | Fetch a URL and return raw response metadata plus a cleaned text preview. |
| `extract_clean` | Fetch a web page and extract the main text, title, headings, and readable paragraphs. Strips ads, nav, footers, and boilerplate. |
| `summarize` | Generate an extractive summary from a URL or raw text. Picks the most representative sentences based on keyword frequency — no LLM needed. |
| `extract_metadata` | Extract page metadata: title, description, canonical URL, byline, site name, language, and published time. |
| `health` | Worker health check. |

## How It Works

Content extraction uses a custom readability-style parser that runs entirely in the Worker. Summaries are extractive (sentence selection by keyword scoring), not abstractive — fast, deterministic, and no API calls.

The MCP endpoint follows standard JSON-RPC (`/mcp`).

## Local Development

```bash
npm install
npx wrangler dev --local --port 8792
```

## Deploy

```bash
npx wrangler deploy
```

## Project Structure

```
summarize-mcp-worker/
├── src/index.js      # Worker entry + extraction + summarization + MCP handlers
├── wrangler.toml
├── package.json
└── README.md
```

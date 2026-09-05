# Binance Price Agent

Built for the **Binance Agent OS Mini Hackathon** — Track A (Build an AI Agent).

## What it does

Binance Price Agent is a conversational AI agent. Ask it about any coin on Binance in plain language, and it answers with live numbers:

- **You ask:** "Show the current BTCUSDT price and 24h change" or "What's SOLUSDT doing today?"
- **The agent:**
  1. Understands which trading pair you mean.
  2. Calls Binance's public market data API to fetch live 24-hour stats (price, % change, high/low, volume).
  3. Replies in a clean, consistent format — a bold price line followed by a two-line range/volume summary.

This fits the **Data & Analysis** workflow category: *Reports, Market Analysis, Portfolio Insights*.

## Why this approach

- **No account, login, or API key required** — Binance's market data endpoints are public, so anyone can run this instantly.
- **No funds, trading, or wallet access involved** — this is a read-only, informational agent.
- **Real tool-use, not a script**: the agent decides for itself when and what to fetch from Binance (via Claude's tool-use), then reasons over the result before answering — the same agent pattern used when connecting Claude Desktop directly to Binance's official Agent OS MCP server.

## How it works

- The page sends the user's question to Claude (`claude-sonnet-4-6`) along with a `get_ticker` tool definition.
- When Claude decides it needs live data, it calls the tool with a Binance symbol (e.g. `BTCUSDT`).
- The page fetches `https://api.binance.com/api/v3/ticker/24hr?symbol=...` and returns the result to Claude.
- Claude formats a final, human-readable answer, which is rendered in the chat.

## Also included

`CONNECTION_RESULTS.md` documents a successful direct connection between **Claude Desktop** and **Binance's official Agent OS MCP server** (`https://agent.binance.com/mcp/agentic`), confirming the same underlying data can be reached either through this standalone agent or through Binance's own Agent OS integration.

## Tech

Single self-contained HTML file (`binance_price_agent.html`) — vanilla JavaScript, no build step, no dependencies. Open it in any modern browser.

## Disclaimer

This project is for informational and educational purposes only. It is not financial advice and is not an offer or solicitation to trade any asset.

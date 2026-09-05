# Market Pulse — AI Crypto Briefing Agent

Built for the **Binance Agent OS Mini Hackathon** — Track A (Build an AI Agent).

## What it does

Market Pulse is a lightweight AI agent that:

1. Pulls **live 24-hour market data** (price, % change, high/low, volume) for five major assets — BTC, ETH, BNB, SOL, XRP — directly from **Binance's public market data API**.
2. Sends that data to **Claude (Anthropic)** for analysis.
3. Returns a short, plain-language **daily market brief** — market mood, the most notable mover, and a balanced closing observation — with no financial advice given.

This fits the **Data & Analysis** workflow category: *Reports, Market Analysis, Portfolio Insights*.

## Why this approach

- No account, login, or API key is required — Binance's market data endpoints are public, so the agent can run instantly for anyone.
- No funds, trading, or wallet access is involved — this is a read-only, informational agent.
- The AI layer is doing real work: it reads the numbers and produces original analysis, not a templated summary.

## How it works

- `fetchMarketData()` calls `https://api.binance.com/api/v3/ticker/24hr` for each symbol.
- The formatted data is passed into a prompt sent to Claude (`claude-sonnet-4-6`) via the Anthropic Messages API.
- The model's response is rendered as the "Daily market brief" section.
- A refresh button re-runs the whole pipeline on demand.

## Tech

Single self-contained HTML file — vanilla JavaScript, no build step, no dependencies. Open `crypto_market_agent.html` in any modern browser.

## Disclaimer

This project is for informational and educational purposes only. It is not financial advice and is not an offer or solicitation to trade any asset.

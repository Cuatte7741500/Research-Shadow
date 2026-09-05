# Connection Results — Binance Agent OS

## Setup

Connected **Binance Agent OS** to **Claude Desktop** using a custom MCP connector.

- **Connector type:** Custom connector
- **Endpoint:** `https://agent.binance.com/mcp/agentic`
- **Client:** Claude Desktop

## Result

Successfully fetched live market data directly from Binance through the connected agent — no manual API calls, no separate script.

**Query:** "Show the current BTCUSDT price and 24-hour change"

**Response:**

> **BTCUSDT: $76,908.34** (-1.48%, -$1,153.68 over 24h)
> - 24h range: $76,264.00 – $78,424.00
> - 24h volume: ~14,627 BTC

The agent automatically recognized the request, called the `binance-mcp-server` integration's ticker tool, and returned a clean, formatted summary — confirming the Agent OS connection works end-to-end for live market data.

## Notes

- Market data queries worked without needing to authorize trading or account access permissions.
- This confirms Binance's Agent OS / MCP server is reachable directly from Claude Desktop as a custom connector, per the official setup at `https://agent.binance.com/mcp/agentic`.

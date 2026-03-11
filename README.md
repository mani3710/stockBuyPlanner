# Stock Buy Plan Manager

A lightweight single-page web app to plan stock purchases for both India (NSE/BSE) and US markets.

## Features

- Manage separate watchlists for:
  - India market (NSE/BSE)
  - US market
- Add multiple target entries per stock:
  - Expected buy price
  - Quantity
  - Bought / pending status
- Live price fetch from Yahoo Finance (no API key required)
- Automatic BUY NOW alert when current price is at or below target
- CSV export and import per market
- Inline editing and deletion of entries
- Summary cards:
  - Total required
  - Total invested
  - Pending orders
  - India total
  - US total
- Data persistence with browser `localStorage`

## Tech Stack

- HTML
- CSS
- Vanilla JavaScript
- Yahoo Finance chart endpoint for quote data

## How to Run

1. Open `index.html` directly in a browser
2. Start adding stock entries in India or US tab
3. Click **Refresh Prices** to fetch latest market prices

No build step or package installation is required.

## Quote Fetching and CORS

The app tries multiple routes to fetch Yahoo Finance data:

- Direct request
- `corsproxy.io`
- `allorigins`
- `cors.isomorphic-git.org`
- Optional custom proxy template

For reliable hosted usage, configure a proxy template in localStorage:

- Key: `stockProxyTemplate`
- Template format example: `https://your-proxy.example.com/fetch?url={url}`

When hosted on `stockplanner.codermani.in`, it auto-configures:

- `${window.location.origin}/api/proxy?url={url}`

## Data Storage

The app stores data in browser localStorage under:

- `stockBuyPlan`
- `apiKeys`
- `stockProxyTemplate` (optional)

## CSV Format

Header:

```csv
symbol,expectedPrice,quantity,bought
```

Example:

```csv
TCS.NS,3500,2,false
AAPL,180,1.5,true
```

## Notes

- India quantities must be whole numbers
- US quantities can be fractional
- Symbols are normalized to uppercase
- India symbols often require suffixes like `.NS` or `.BSE`

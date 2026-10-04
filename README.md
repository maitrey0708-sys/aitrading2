# AI Trading Dashboard

## Live market-data mode
The dashboard now attempts to load current market data through Yahoo Finance using `yfinance` from the FastAPI backend. It refreshes automatically every 15 seconds.

Supported symbols:
- NIFTY 50 (`^NSEI`)
- BANK NIFTY (`^NSEBANK`)
- BTC/USDT (`BTC-USD`)
- ETH/USDT (`ETH-USD`)

**Important:** Yahoo Finance data availability and exchange delays depend on the instrument/exchange. The app visibly falls back to demo data if the provider is unavailable. This is not a guaranteed tick-by-tick feed.

## Run
### Backend
```bash
cd backend
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```

### Frontend
Open a second terminal:
```bash
cd frontend
npm install
npm run dev
```

## Trading safety
The included `/api/orders/paper` endpoint is **paper trading only**. No real orders are sent to a broker.

For real-money order execution, the project must be connected to a broker API such as Zerodha Kite Connect, Upstox, Angel One SmartAPI, or another broker supported by the user's account. Broker choice, API credentials, authentication flow, order types, and exchange permissions must be configured explicitly before enabling live execution.

# F&O Screener (Ready-to-deploy)

This is a simple React (Vite) project that runs a local CSV-based F&O screener in the browser.

## How to use
1. Download this ZIP and push to a new GitHub repository (or unzip locally).
2. On your machine:
   - Run `npm install`
   - Run `npm run dev` to test locally (http://localhost:5173)
   - Or run `npm run build` and serve the `dist` folder.
3. To deploy on Netlify/Vercel:
   - Create a new site and connect your GitHub repo.
   - Build command: `npm install && npm run build`
   - Publish directory: `dist`

## What it does
- Upload Price CSV (OHLCV) and Futures CSV (OI + fut_price).
- Screener logic (exactly as requested):
  1) latest close > previous day high
  2) latest volume > 2 * 5-day average volume
  3) (future oi > prev oi AND future price > prev price) OR (future oi < prev oi AND future price > prev price)
  4) latest close >= latest high * 0.98
- Export matching symbols as CSV.

## Notes
- CSV column mapping is available in the UI (map headers if your CSV uses different names).
- This is a front-end-only tool that runs on files you upload. For live NSE/Kite integration, a backend is required.

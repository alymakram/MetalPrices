# MetalBase — Gold · Silver · Copper vs USD on Base

> Precious metals price tracker & converter DApp on Base.
> Every conversion triggers a real on-chain transaction.
> Owner: `0xdBF45AF1cD37deBEDD059BEe0525289d2b5E5CF4`

---

## Files

| File | Purpose |
|------|---------|
| `MetalPriceTracker.sol` | Smart contract — deploy on Base via Remix |
| `index.html` | Full DApp frontend |
| `vercel.json` | Vercel static deployment config |
| `icon.png` | 1024×1024 Base app icon |
| `splash.png` | 200×200 splash screen |
| `og.png` | 1200×630 social preview |
| `.well-known/farcaster.json` | Base Mini App manifest |

---

## Step 1 — Deploy Contract on Base via Remix

1. Go to **https://remix.ethereum.org**
2. Create new file → paste `MetalPriceTracker.sol`
3. Compile: Solidity `^0.8.20`
4. Deploy:
   - Environment: **Injected Provider — MetaMask**
   - Switch MetaMask to **Base Mainnet** (Chain ID: 8453)
   - Deploy `MetalPriceTracker`
5. Copy deployed contract address

---

## Step 2 — Verify on Basescan

1. Go to **https://basescan.org/verifyContract**
2. Paste contract address
3. Compiler: `0.8.20` — paste source — Submit ✓

---

## Step 3 — Update Frontend

In `index.html`, replace on line ~230:
```js
const CONTRACT_ADDRESS = "0x0000000000000000000000000000000000000000";
```
With your deployed address.

Also replace `DOMAIN_PLACEHOLDER` in:
- `index.html` (meta tags)
- `.well-known/farcaster.json`

With your Vercel domain (e.g. `metalbase.vercel.app`).

---

## Step 4 — Deploy on Vercel

Push all files to GitHub:
```
/
├── index.html
├── vercel.json
├── icon.png
├── splash.png
├── og.png
├── README.md
└── .well-known/
    └── farcaster.json
```

Import on **https://vercel.com/new** → Framework: Other → Deploy.

---

## Step 5 — Register on Base.dev

1. Go to **https://base.dev**
2. Connect wallet `0xdBF45…`
3. Create project → add your Vercel URL
4. Copy the `base:app_id` metatag → paste into `index.html` `<head>`
5. Redeploy → Verify on base.dev ✓

---

## Contract Features

```
MetalPriceTracker
├── Metals: GOLD (0), SILVER (1), COPPER (2)
├── Prices: USD cents per troy oz, owner-updatable
├── convert(metal, weightMg, note)  → USD cents
├── convertUsdToMetal(metal, usdCents, note) → mg
├── updateAllPrices(gold, silver, copper)  [owner]
├── deployMiniApp(name, config)
└── Full on-chain history per user
```

## Seed Prices (deploy-time)
- Gold: $3,130.00/ozt
- Silver: $33.80/ozt
- Copper: $4.89/ozt

Update anytime via the Owner tab in the DApp.

---

*Built for `0xdBF45AF1cD37deBEDD059BEe0525289d2b5E5CF4`*

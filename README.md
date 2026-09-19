# Testnet wallet lab

A static, single-page classroom lab: make an Ethereum wallet in the browser, sign a
transaction offline, broadcast it with Etherscan's broadcast form on a test network,
and find it on the public explorer. No build step, no server, no dependencies to install.

## Files

- `index.html` - the whole app (HTML, CSS, JS)
- `vercel.json` - clean URLs and security headers (the CSP blocks all network requests
  from the page, so nothing typed into it can be sent anywhere)

## Deploy on Vercel

Option A: Vercel CLI

    npm i -g vercel
    cd testnet-wallet-lab
    vercel --prod

When prompted: framework preset "Other", no build command, no output directory
(leave the defaults).

Option B: Git

1. Push this folder to a GitHub repo.
2. In Vercel choose Add New > Project and import the repo.
3. Framework preset: Other. Leave Build Command and Output Directory empty. Deploy.

## Notes

- The page loads ethers.js 5.7.2 from cdnjs (with a jsDelivr fallback) and fonts from
  Google Fonts. If your school network blocks those, download
  `ethers.umd.min.js` into this folder and change the script tag to `src="/ethers.umd.min.js"`.
- Networks are defined in the `NETS` object near the top of the script (Sepolia and
  Hoodi). Sepolia is reportedly scheduled for retirement around the end of September
  2026; add or swap networks there (chain ID, explorer URL, faucet list).
- Faucet links change often. Check them before each class.

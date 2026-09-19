# Testnet wallet lab

A small classroom lab for learning how crypto wallets, transactions and public ledgers work, without touching real money. You make an Ethereum wallet in the browser, sign a payment, send it to a test network, and then look it up on a public block explorer.

**Live site:** https://testnet-wallet-lab.vercel.app/

It's one HTML file. There's no backend, no build step and no account to make.

## What you do in it

1. Generate a wallet. The page shows the private key, the public key and the address, and checks for you that the address really comes from the public key.
2. Grab some free test ETH from a faucet.
3. Fill in a payment (who, how much, nonce, fees) and sign it. The page shows the raw signed bytes, the transaction hash, and the sender worked out from the signature alone.
4. Paste the signed transaction into Etherscan's broadcast form, then open your hash on the explorer and match what you see against what you signed. There's a lab record at the end that students can copy and hand in.
5. Edit a few tiny blocks and watch every later fingerprint change, which is the reason a shared ledger is hard to rewrite.
6. Five short questions to check it stuck.

The page never talks to the network itself. Balances and confirmations live on the explorer, which is sort of the point: the ledger is public and sits outside your wallet.

## Running it

Open `index.html` in a browser. That's it.

If you'd rather serve it, any static server works:

```
npx serve .
```

## Deploying

It's set up for Vercel as a plain static site. Import the repo, set the framework preset to "Other", leave the build command and output directory empty, and deploy. `vercel.json` adds a few security headers, including a content policy that stops the page from making network requests of its own. Nothing typed into it can be sent anywhere.

If Vercel shows a login page when you visit your deployment, turn off Vercel Authentication under Settings, then Deployment Protection.

## Things to know

- **Testnet only.** The wallet is meant for play money. Don't paste a key or recovery phrase from a wallet that holds anything real into this page or any other.
- **Remembering a wallet.** There's a checkbox that keeps the wallet's 12 words in the browser's local storage so a refresh doesn't wipe it. Off by default. Don't use it on a shared computer.
- **Sepolia is on borrowed time.** It's reportedly scheduled to be retired around the end of September 2026, so there's a Hoodi option in the network menu as a backup. The networks live in the `NETS` object near the top of the script if you need to add or change one.
- **Faucets come and go.** Check the links before you run this with a class. The Hoodi ones especially should be tried once first.
- **Outside libraries.** The page loads ethers.js 5.7.2 from cdnjs (with jsDelivr as a fallback) and fonts from Google Fonts. If a school network blocks those, download `ethers.umd.min.js` into this folder, change the script tag to `src="/ethers.umd.min.js"`, and update the content policy in `vercel.json` to match.
- **The ledger demo is simplified.** Real Ethereum blocks fingerprint a header that commits to their transactions, not plain text like the demo does. The behaviour you see is the same.

## Files

```
index.html    the whole app
vercel.json   clean URLs and security headers
LICENSE       MIT
```

## Built with

[ethers.js](https://docs.ethers.org/v5/) 5.7.2 for key generation and signing. Type is Zilla Slab, Atkinson Hyperlegible and IBM Plex Mono.

## License

MIT. See `LICENSE`.

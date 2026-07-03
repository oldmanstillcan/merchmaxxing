# merchmaxxing.xyz

Crypto-native merch storefront. Static site (GitHub Pages) — Buy buttons link out to Helio Pay Links; this site never touches money.

**Pipeline:** X drop post → this store → Helio checkout (USDC on Solana, any-token auto-swap) → payment webhook (Cloudflare Worker, separate repo) → Printful order → shipped.

Part of the AOK Taoer merch pipeline — plan: `AOK-VAULT/ORAOKOL.vault/projects/PRJ-taoer-merch-pipeline.md` · architecture: `DEC-2026-07-01-taoer-crypto-merch-v1`.

## Structure

- `index.html` — the whole store. Products live in the `PRODUCTS` array at the bottom of the file.
- `assets/` — product mockup images (Printful-generated).
- `CNAME` — custom domain for GitHub Pages.

## Adding / going live on a product

1. Create the product on printful.com (Taoer Wreckords store) and save a mockup image to `assets/`.
2. Create a Helio Pay Link (USD-priced, `canSwapTokens`, require name/email/delivery address).
3. In `PRODUCTS`: set `img` to the asset path and `paylink` to the Pay Link URL. `paylink: null` renders as DROPPING SOON.

## Deploy

GitHub Pages from `main`. DNS: Cloudflare → apex A/AAAA to GitHub Pages, `www` CNAME optional. SSL auto via Pages.

## Local dev

Static — open `index.html` or `python3 -m http.server` in the repo root.

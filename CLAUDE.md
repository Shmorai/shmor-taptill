# TapTill (taptill.shmor.ai)

A Shmor marketplace (shared rules in `../../CLAUDE.md`): its own brand, design and SEO. Compares UK card machines, payment terminals and EPOS till systems for shops, cafés, pubs, restaurants, salons, market traders, tradespeople and petrol stations. **UK only** (GBP, UK rules). Repo: `Shmorai/shmor-taptill` (private until launch). Status: **building**, with no referral links yet. Created 2026-10-16. Name = "tap" (contactless) + "till" (the British word for the register).

## Where things are
| What | Where |
|---|---|
| Card on shmor.ai, search keywords, **referral links**, offers, SEO defaults | `shmor-site.json` |
| Pages (1 JSON file = 1 Google landing page) | `content/` (`home.json` = homepage, `content/blog/x.json` → `/blog/x/`) |
| Design: header, logo, footer, **PAYG rates ticker** | `templates/layout.html` |
| Design: styles | `assets/site.css` (kit defaults at the top; **TapTill theme** block at the bottom) |
| "Business" field in every search box + spec filter tabs | `assets/site.js` (kit script + TapTill field) |
| Generated output (don't edit by hand) | `index.html`, `*/index.html`, `sitemap.xml`, `robots.txt`, `404.html`, `search/`, `search-index.json`, `blog/feed.xml` |

## Pages (17)
Home · card-machines (provider cards with filter tabs: Pay as you go / Quoted / Bank-backed, PAYG rates table, ownership notes) · epos-systems (EPOS cards with tabs) · card-machine-fees · business-types (hub) · card-machines-for-shops · card-machines-for-hospitality · petrol-station-pos · mobile-card-readers · tap-to-pay-on-phone · switch-card-machine-provider · blog + 5 posts (contactless-limit-scrapped, global-payments-worldpay-what-it-means, can-you-charge-for-card-payments, pay-as-you-go-vs-subscription-card-fees, card-machine-quote-summary-box).
Top menu (navOrder): Card machines, EPOS & tills, Fees, By business, Switching, Blog. Pages link to each other heavily ("backlinks" inside the site), to official sources (GOV.UK, PSR, legislation.gov.uk, FCA coverage) and to providers' own sites (`rel="nofollow noopener"`). Footer links to sister sites FullBars and TradesStation.

## Design
**"Merchant clean"** (redesigned 2026-10-16 at the user's request to follow worldpay.com's layout and style; style only, no Worldpay branding, logo or wording). White pages, deep indigo #1C1A6E headings, utility bar and footer (#2B2890 secondary), **red #F5243F primary buttons** (hover #D11530), pastel rounded panels: lavender #F1EEFF, ice blue #DDF6FF, mist #E8EBF3, page bands #F6F7FB. Fonts: **Blinker** 700 headings/nav/buttons + Inter body. Radius 24px cards, 32–40px hero photo and panels, 8px buttons.
Layout: indigo utility bar with the **PAYG rates** (figures in `templates/layout.html`) → white header with indigo nav links and a red "Compare card machines" button → **split hero** (text left, rounded photo card right over a lavender panel; inner pages use a grey band + ice-blue panel; at ≤900px the photo sits as a rounded card above the text) → pastel highlight panels → tiles → white deal cards → lavender rounded "How it works" panel → FAQ on grey → big indigo rounded CTA panel → indigo footer. Logo = indigo rounded square, white card terminal, red contactless waves + "Tap**Till**" (Till in red; pink #FF6B7F in the footer). Favicon and the shmor.ai card use the same mark (card accent #1C1A6E, wordmark #FF6B7F, sector accent #F5243F). The earlier "receipt roll" theme is in git history.
Helpers inside `html`: tables in `<div class="table-wrap">`, tips `<p class="callout">`, big numbers `<div class="figure-row"><div class="figure"><b>1.69%</b><span>label</span></div></div>`, source lines `<p class="source-note">`. Checked at 320, 375, 768, 900, 1024 and 1280px: no horizontal scroll.
**Photos:** free-licence Unsplash images (all 17 checked loading 2026-10-16), credited in each page's `"image"`.

## Content rules for this site
Factual, no invented prices, rankings, star ratings or reviews. Providers are listed **alphabetically within groups, explicitly unranked**. Only publish fees that the provider publishes, with the date checked and a source link; quoted providers say "quoted". Avoid unverified hardware prices. Not financial advice (footer disclaimer).
**Facts used (checked 16 Oct 2026; re-check monthly, update ticker in `templates/layout.html`, `card-machines.json`, `card-machine-fees.json`, `home.json` FAQ, the PAYG blog post):** SumUp 1.69% PAYG, Payments Plus £19/month (or £189/yr) headline 0.99%, custom ≥£10k/month, POS Plus £39/month ex VAT · Square 1.75% UK cards (+1.95% non-UK), online 1.4%+25p, keyed/invoice 2.5%, Free £0 / Plus from £29/month, Reader £19 / Terminal £149 / Register £699 ex VAT · Zettle → PayPal Point of Sale, 1.75%, no recurring fees, reader from £29 ex VAT (new users), extra £69, Terminal from £149 · Lloyds Cardnet mPOS 1.75%, no monthly fee, £49 first reader, refund 50p, chargeback £15 · Teya: no standard price list, +0.10% if paid to an external bank, 200+ EPOS integrations · takepayments: Global Payments company, Stockport, 12-month contract, separate acquirer agreement · Global Payments completed Worldpay purchase 12 Jan 2026 · Dojo = Paymentsense's brand, quoted rates · Elavon = U.S. Bancorp · FCA removed fixed £100 contactless limit 19 Mar 2026 · consumer card surcharge ban since 13 Jan 2018 · UK consumer interchange caps 0.2% debit / 0.3% credit · PSR summary boxes + trigger messages from July 2023 (card turnover ≤£50m); PSR being folded into FCA · Fuel Finder: forecourts report price changes within 30 min since 2 Feb 2026 · Employment (Allocation of Tips) Act 2023 (GOV.UK code; revised code withdrawn for re-consultation).

## Commands (run here)
```bash
node tools/build.js           # rebuild after ANY change to content/, templates/ or shmor-site.json
node tools/build.js --check   # validate only
node tools/serve.js 4023      # preview http://localhost:4023  (preview config "taptill")
```
After changing `shmor-site.json` (links, keywords, card), also run `node tools/sync-network.js` in `../../shmor-ai`.

## Referral links
None yet. Likely programmes: SumUp, Square, PayPal/Zettle, Teya, Dojo and EPOS brands (Epos Now, Lightspeed) run partner/affiliate or referral programmes, some via Awin/Impact/PartnerStack, and merchant-services lead-gen partners. Paste exact links from the user only.
1. Add to `shmor-site.json` → `"links"`: `"slug": { "merchant", "network", "url" }`. Prefix slugs with the merchant name.
2. Add `"link": "<slug>"` to that provider's card in a `specs` block (shows a "See plans" button), or list slugs in a page's `"partners"`, or add `"offers"`.
3. `node tools/build.js`, sync the master, commit both repos.

## Ideas / next
Referral links · one page per provider ("SumUp review" style, facts only) and head-to-heads (SumUp vs Square vs Zettle) · Northern Ireland / Ireland notes · a weekly blog task like the other sites · a social share image (`seo.image`) · after launch: Google Search Console, then outreach for real external backlinks (trade bodies, local business directories, guest posts).

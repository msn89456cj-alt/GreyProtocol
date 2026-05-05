# Grey Protocol landing page

Single-page static site voor Grey Protocol. Drie pijlers: single vials, sourcing en protocols. Aanvraag via Telegram (`t.me/greyprotocolnl`).

## Stack

Geen build-stap. Eén HTML-bestand met inline CSS en vanilla JS. Google Fonts via `<link>`. Klaar voor static hosting (Vercel, Netlify, Cloudflare Pages, GitHub Pages).

## Bestandstructuur

```
.
├── index.html          # Volledige landing page (inline CSS + JS)
├── og.png              # Open Graph / Twitter image, 1200x630 PNG
├── robots.txt          # Crawler-regels + sitemap-verwijzing
├── sitemap.xml         # Eén URL, weekly changefreq
├── vercel.json         # Security headers, cache-control, clean URLs
├── LICENSE             # Proprietary, all rights reserved
├── .gitignore
├── .vercelignore       # Exclusies voor deploy bundle
└── README.md
```

Niet meegenomen in git of deploy: `_design_pkg/` (originele Claude Design bundle), `.claude/` (sessiemetadata).

## Lokaal draaien

Serve de map met elke statische server. Voorbeelden:

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .

# Of open index.html direct in de browser
```

## Deployen op Vercel

### Via Vercel dashboard

1. Push deze repo naar GitHub.
2. In Vercel: **New Project** → importeer de repo.
3. Framework preset: **Other**. Build command: leeg. Output directory: `.`.
4. Deploy.
5. Voeg domein `greyprotocol.nl` toe en zet apex + `www` DNS naar Vercel.

### Via CLI

```bash
npm i -g vercel
vercel              # preview deploy
vercel --prod       # production
```

`vercel.json` regelt security headers (HSTS, X-Frame-Options, Permissions-Policy, Referrer-Policy) en cache-control. `.vercelignore` houdt het design-bundle uit de upload.

## Productiestatus

De repo is klaar voor GitHub, Vercel en Google-indexering:

- Social previews gebruiken `og.png` voor brede Open Graph/Twitter-compatibiliteit.
- Canonical, `og:url`, `robots.txt` en `sitemap.xml` wijzen naar `https://greyprotocol.nl/`.
- Telegram-handle is overal `t.me/greyprotocolnl`.
- `vercel.json` bevat security headers, CSP, HSTS en cache-control.
- `_design_pkg/` en `.claude/` staan in `.gitignore` en `.vercelignore`.

Operationeel onderhoud:

- Werk batch-data in `index.html` bij per drop.
- Koppel een analytics provider aan het `gp:track` CustomEvent als tracking nodig is.

## Compliance

Alle copy is research-only. Geen medische claims, geen persoonlijke gebruiksinstructies of behandelplannen. Disclaimer staat in de footer en in de protocols-disclaimer.

## Credits

Visueel ontwerp en eerste prototype geleverd via Claude Design (zie `_design_pkg/landing/`, niet in deploy). Productie-implementatie is geschreven in deze repo.

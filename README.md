# ChamberSathi website

Public site for **[ChamberSathi.com](https://chambersathi.com)**: product landing page and the
privacy policy URL required by Google Play Console.

- Home: `/`
- Privacy policy: `/privacy/` → use **`https://chambersathi.com/privacy/`** in Play Console

Static HTML/CSS. No build step, no backend, no analytics.

## Local preview

From this folder:

```bash
npx --yes serve .
```

Then open the URL printed in the terminal (paths like `/privacy/` work; opening `index.html` as a
file will break those absolute links).

## Publish on GitHub Pages + custom domain

Repo: `https://github.com/GajananPatil142/chambersathi-app-landing-page`

1. Push `main`.
2. GitHub → **Settings → Pages**
   - Source: **Deploy from a branch**
   - Branch: `main` / `/ (root)`
   - Custom domain: `chambersathi.com`
   - Enable **Enforce HTTPS** (after DNS has propagated)
3. At your domain registrar, point **ChamberSathi.com** at GitHub Pages:

   **Apex `chambersathi.com` — A records**

   | Host | Type | Value |
   | --- | --- | --- |
   | `@` | A | `185.199.108.153` |
   | `@` | A | `185.199.109.153` |
   | `@` | A | `185.199.110.153` |
   | `@` | A | `185.199.111.153` |

   Optional IPv6 (AAAA): `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`,
   `2606:50c0:8003::153`.

   **`www.chambersathi.com` — CNAME**

   | Host | Type | Value |
   | --- | --- | --- |
   | `www` | CNAME | `gajananpatil142.github.io` |

   This repo already contains a `CNAME` file with `chambersathi.com`.

4. Wait for DNS (often minutes, sometimes up to 48 hours). Confirm:
   - `https://chambersathi.com/`
   - `https://chambersathi.com/privacy/`
   - HTTPS padlock (GitHub issues the certificate after the domain is verified)

If you use Cloudflare in front of the domain, set those records to **DNS only** (grey cloud) until
GitHub HTTPS works, or terminate TLS at Cloudflare with Full (strict).

## After the Android app is on Play

1. Replace the “Coming soon on Google Play” button in `index.html` with the store listing URL:

   `https://play.google.com/store/apps/details?id=com.chambersathi.app`

2. Paste `https://chambersathi.com/privacy/` into Play Console → App content → Privacy policy.

Support email on the site: `chambersathi@gmail.com`.

Pro price on the landing page: Rs. 599 per year (Google Play).

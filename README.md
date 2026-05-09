# frayhudson.com — GitHub Pages Archive Site

Static archive site for **The Law Office of Robert C. Hudson PLLC**, migrated from Wix to GitHub Pages under the custom domain `frayhudson.com`.

## About This Site

A single-page HTML/CSS site preserving the 40+ year career legacy of retired attorney **Robert C. Hudson** of Culpeper, Virginia. Built with vanilla HTML5 and CSS3 — no frameworks, no build step, no dependencies beyond Google Fonts and Font Awesome (both loaded via CDN).

**Files:**

| File | Purpose |
|------|---------|
| `index.html` | Single-page site — all sections |
| `styles.css` | All styling (responsive, modern) |
| `CNAME` | Custom domain for GitHub Pages |

---

## Deploying to GitHub Pages

### 1. Push to GitHub

```bash
git init
git add .
git commit -m "Initial site"
git remote add origin https://github.com/rchudson1/frayhudson.git
git push -u origin main
```

### 2. Enable GitHub Pages

1. Go to **Settings → Pages** in your GitHub repository.
2. Under **Source**, select **Deploy from a branch**.
3. Set the branch to `main` and the folder to `/ (root)`.
4. Click **Save**.

GitHub will provide a URL like `https://rchudson1.github.io/frayhudson` — but the `CNAME` file will route traffic through `frayhudson.com` once DNS is configured.

---

## DNS Configuration

Point `frayhudson.com` to GitHub Pages by updating your domain registrar's DNS settings.

### Required DNS Records

#### A Records (IPv4) — for the apex domain `frayhudson.com`

| Type | Host | Value | TTL |
|------|------|-------|-----|
| A | `@` | `185.199.108.153` | 3600 |
| A | `@` | `185.199.109.153` | 3600 |
| A | `@` | `185.199.110.153` | 3600 |
| A | `@` | `185.199.111.153` | 3600 |

#### AAAA Records (IPv6) — optional but recommended

| Type | Host | Value | TTL |
|------|------|-------|-----|
| AAAA | `@` | `2606:50c0:8000::153` | 3600 |
| AAAA | `@` | `2606:50c0:8001::153` | 3600 |
| AAAA | `@` | `2606:50c0:8002::153` | 3600 |
| AAAA | `@` | `2606:50c0:8003::153` | 3600 |

#### CNAME Record — for `www` subdomain

| Type | Host | Value | TTL |
|------|------|-------|-----|
| CNAME | `www` | `rchudson1.github.io` | 3600 |

> **Note:** The `www` CNAME should point to `<your-github-username>.github.io` — update `rchudson1` if the repository lives under a different account.

### After Updating DNS

1. DNS propagation typically takes **10 minutes to 48 hours**.
2. Once propagated, go back to **Settings → Pages** in GitHub and verify the custom domain is recognized.
3. Check **"Enforce HTTPS"** — GitHub Pages provides a free TLS certificate via Let's Encrypt.

---

## Migration Notes

| | Before (Wix) | After (GitHub Pages) |
|---|---|---|
| Hosting cost | ~$500/year | Free |
| Custom domain | `frayhudson.com` | `frayhudson.com` |
| SSL/TLS | Included in Wix plan | Free via Let's Encrypt |
| Build system | Wix CMS | None (static HTML/CSS) |
| Dependencies | Wix platform | Google Fonts, Font Awesome CDN |

---

## Local Preview

Open `index.html` directly in any browser, or use a local server:

```bash
# Python 3
python3 -m http.server 8080

# Node (npx)
npx serve .
```

Then visit `http://localhost:8080`.

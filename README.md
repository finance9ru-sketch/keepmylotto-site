# Keep My Lotto — website

The marketing site and privacy policy for Keep My Lotto. Static HTML, deployed on
Vercel, served at **keepmylotto.com** with the policy at **keepmylotto.com/privacy**.

```
keepmylotto-site/
├── index.html      landing page (app intro)
├── privacy.html    privacy policy  → served at /privacy
├── vercel.json     clean URLs + /privacy route + basic security headers
├── package.json
└── README.md
```

## Before you deploy

Open `privacy.html` and replace the two remaining placeholders:
- `[INSERT DATE]` (appears twice) → today's date, e.g. `July 16, 2026`

The support email (`support@keepmylotto.com`) is already filled in. Make sure the
Namecheap email forwarding for `support@keepmylotto.com` is set up so mail arrives.

## Preview locally (in Cursor's terminal)

```bash
npm run dev        # opens a local server, usually http://localhost:3000
```

## Deploy to Vercel — step by step

**1. Put it on GitHub** (from this folder, in Cursor's terminal):

```bash
git init
git add .
git commit -m "Keep My Lotto site: landing + privacy"
# create an empty repo on github.com first, then:
git remote add origin https://github.com/<you>/keepmylotto-site.git
git branch -M main
git push -u origin main
```

**2. Import into Vercel:**
- Go to vercel.com → New Project → import the `keepmylotto-site` repo.
- Framework preset: **Other** (it's plain static HTML — no build step).
- Root directory: leave as `/`. Click Deploy.
- You'll get a temporary URL like `keepmylotto-site.vercel.app` — check that the
  landing page and `/privacy` both load.

**3. Connect keepmylotto.com (bought at Namecheap):**
- In the Vercel project → Settings → Domains → add `keepmylotto.com` and `www.keepmylotto.com`.
- Vercel shows the DNS records to set. Two common options:
  - **A record** for the root: point `@` to the IP Vercel gives you, and
  - **CNAME** for `www` → `cname.vercel-dns.com`.
  - (Or set Namecheap's nameservers to Vercel's if you prefer Vercel to manage DNS.)
- In Namecheap: Domain List → Manage → **Advanced DNS** → add those records.
  Remove any default Namecheap "parking" records that conflict.
- HTTPS is issued automatically by Vercel once DNS resolves (a few minutes to a couple hours).

**4. Verify:**
- `https://keepmylotto.com` → landing page
- `https://keepmylotto.com/privacy` → privacy policy (this is the URL you give Google Play)

## Later

When the Android app is live, add the Google Play badge + link to `index.html`
(replace the "Coming to Google Play" line in the footer).

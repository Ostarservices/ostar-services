# Ostar Services — Website

A self-contained static website for **Ostar Services** (permit expediting for LA County & Orange County general contractors), rebuilt from the Polsia site to run on **GitHub Pages**.

Everything is in plain HTML/CSS/JS — no build step, no framework, no server. Just push it and turn on Pages.

## Files

| File | What it is |
|------|-----------|
| `index.html` | The entire website — dark red/white/blue theme with the Ostar logo **embedded** (all CSS, JS, and the logo image are inline, so it's fully self-contained). |
| `logo.png` | The Ostar Services logo as a standalone file. The page doesn't need it (the logo is embedded in `index.html`), but it's referenced as the social/link-preview image and is handy for other uses. Keep it in the repo. |
| `404.html` | Custom "page not found" page, same dark theme. |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is (no Jekyll processing). |
| `README.md` | This file. |

The browser-tab icon (favicon) is a small red star, embedded directly in `index.html` — no separate file needed.

## Publish it on GitHub Pages

**1. Create the repo**
- Go to <https://github.com/new>
- Name it (e.g. `ostar-services` or, for a user site, `<your-username>.github.io`)
- Set it to **Public** (Pages is free on public repos)

**2. Upload these files**
- On the new repo page, click **uploading an existing file**
- Drag in `index.html`, `404.html`, `.nojekyll`, and `README.md`
- Commit to the `main` branch

*(Or, from a terminal:)*
```bash
git init
git add .
git commit -m "Ostar Services site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

**3. Turn on Pages**
- In the repo: **Settings → Pages**
- Under **Build and deployment → Source**, choose **Deploy from a branch**
- Branch: **main**, folder: **/ (root)** → **Save**
- Wait ~1 minute. Your site goes live at:
  - `https://<your-username>.github.io/<repo-name>/`
  - or `https://<your-username>.github.io/` if you named the repo `<your-username>.github.io`

## Use your own domain (ostarservices.com)

1. In **Settings → Pages → Custom domain**, enter `www.ostarservices.com` and Save. GitHub creates a `CNAME` file in the repo automatically.
2. At your domain registrar (where you manage ostarservices.com DNS), add:
   - A **CNAME** record: host `www` → value `<your-username>.github.io`
   - Four **A** records for the apex `ostarservices.com` pointing to GitHub's IPs:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
3. Back in Settings → Pages, tick **Enforce HTTPS** once the certificate provisions (can take up to an hour).

## Things you'll probably want to change

- **Contact email** — currently `bryan.cariello@ostarservices.com`, used in the "Start a project" / "Book a consult" buttons and the footer. Search `index.html` for that address and replace it if you want a different inbox (e.g. `permits@ostarservices.com`).
- **Consult booking** — the "Book a 20-min consult" button opens an email. If you use Calendly/Cal.com, swap the `mailto:` link for your booking URL.
- **Testimonials** — the three quotes carry the names from the original site. Update or replace them with real client permission.
- **Contact form** — GitHub Pages can't process form submissions on its own (no backend). The site uses `mailto:` links instead. If you'd rather have a real form, a free service like [Formspree](https://formspree.io) drops in with one line of HTML — happy to wire that up.

## Note on the AI pre-qualifier

The original Polsia site had an "AI pre-qualifier" intake widget. That relied on Polsia's backend and can't run on a static GitHub Pages site, so it's replaced here by the plain "send us a scope" contact section with the same four-item checklist (address, scope, plan set, deadline). If you want interactive intake back later, that needs a hosted form or a small serverless function.

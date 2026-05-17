# Rate My Anime — Static Site

Two-page static site for Play Store compliance:

- `/privacy/` — Privacy Policy
- `/delete-account/` — Account deletion instructions

Built with Jekyll, deployed via GitHub Pages.

## Before publishing — fill in placeholders

The following `[BRACKETED]` values appear throughout the Markdown files. Replace them:

- `Bhuwan Shrestha` — your real legal name as the operator
- `bhuwanenoch@gmail.com` — your privacy/support contact email
- `"May 20, 2026"` — the effective date

Search-and-replace across all files works:

```bash
# macOS / Linux
sed -i '' 's/\[YOUR FULL NAME\]/Your Real Name/g' *.md
sed -i '' 's/\[YOUR_CONTACT_EMAIL\]/you@example.com/g' *.md
sed -i '' 's/\[DATE WHEN PUBLISHED\]/May 20, 2026/g' *.md
```

## Deploy to GitHub Pages

### Option A: Free github.io subdomain (easiest, for testing)

1. Create a new public GitHub repo. Name it whatever — e.g. `rate-my-anime-site`.
2. Push these files to the `main` branch:
   ```bash
   cd rate-my-anime-site
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/rate-my-anime-site.git
   git push -u origin main
   ```
3. On GitHub, go to **Settings → Pages**.
4. Under "Build and deployment", set Source to **Deploy from a branch**.
5. Set Branch to **main** and folder to **/ (root)**.
6. Click **Save**.
7. Wait 1-2 minutes. Your site will be live at:
   `https://YOUR_USERNAME.github.io/rate-my-anime-site/`

The privacy page will be at:
`https://YOUR_USERNAME.github.io/rate-my-anime-site/privacy/`

The account deletion page will be at:
`https://YOUR_USERNAME.github.io/rate-my-anime-site/delete-account/`

These are the URLs you'll paste into Play Console.

### Option B: Custom domain (when you have one)

1. Buy a domain (e.g. `ratemyanime.com`).
2. Create a file named `CNAME` in the repo root containing only the domain:
   ```
   ratemyanime.com
   ```
3. In your DNS provider, add an A record pointing to GitHub's IP addresses:
   - 185.199.108.153
   - 185.199.109.153
   - 185.199.110.153
   - 185.199.111.153
4. Or add a CNAME record for `www` pointing to `YOUR_USERNAME.github.io`.
5. In GitHub Settings → Pages, set the Custom domain to your domain.
6. Wait for DNS propagation (5-60 min). HTTPS is auto-provisioned.

Final URLs would be:

- `https://ratemyanime.com/privacy/`
- `https://ratemyanime.com/delete-account/`

## Local preview (optional)

If you want to preview before pushing:

```bash
# Install Ruby + Bundler first (one-time)
gem install bundler jekyll

# In the site folder
bundle exec jekyll serve
# Visit http://localhost:4000
```

You don't need this for deployment — GitHub Pages builds for you. It's just for previewing changes.

## Editing

To change content, edit the `.md` files directly. Each file's title and URL are set via the YAML frontmatter at the top:

```yaml
---
layout: page
title: Privacy Policy
permalink: /privacy/
---
```

Push changes to `main` and GitHub Pages rebuilds automatically (1-2 min).

## Customization later

This uses Jekyll's default **minima** theme — clean, readable, no setup needed. To customize:

- **Custom colors / typography**: create `assets/main.scss` and override minima's variables
- **Different theme**: change `theme:` in `_config.yml`. Other GitHub-Pages-supported themes: cayman, slate, hacker, leap-day, etc.
- **Full custom design**: replace minima entirely with custom HTML in `_layouts/`

For now, the default theme is enough to satisfy Play Store requirements.

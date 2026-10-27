# Local SEO Research Web App (Free & Open Source)

A local, private, Semrush-style SEO tool that runs 100% on localhost.
- **No paid APIs required**
- **No third-party tool scraping**
- **100% local and private**

---

## Features

1. **Keyword Ideas**:
   - Google Autocomplete suggestions for seed keyword, alphabetical variations (`a-z`), and question modifiers (`how`, `what`, `why`, `best`, `vs`).
   - Relative interest trends over time via Google Trends (pytrends).
   - CSV export.

2. **Site Audit (Crawler)**:
   - Fast, polite local website crawler (respects `robots.txt`, 1-second polite crawl delay).
   - Audits status codes, titles & lengths, meta descriptions, H1 counts, canonical URLs, robots meta, word counts, missing image alt tags, and internal link counts.
   - Flags issues categorized by severity (Missing/Duplicate Titles, Missing Descriptions, Multiple/Missing H1, Non-200 URLs, Missing Canonical, Missing Alt Text).
   - CSV export of issues and crawled page metadata.

3. **Google Search Console Integration (Optional)**:
   - Official Search Console API integration with Google OAuth 2.0.
   - Inspect clicks, impressions, CTR, and average positions for queries and pages.
   - Safe credential management (`client_secret.json` and `token.json` are strictly kept local and git-ignored).

---

## Getting Started

### 1. Prerequisites
- Python 3.10 or higher (tested with Python 3.14)

### 2. Run Locally

In PowerShell (Windows):
```powershell
cd C:\Users\Ayush\.gemini\antigravity\scratch\seo-tool-free
venv\Scripts\activate
streamlit run app.py
```

Then open [http://localhost:8501](http://localhost:8501) in your browser.

---

## Google Search Console Setup Guide (Optional)

To connect your real Google Search Console data:

1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project (e.g. `Local-SEO-Tool`).
3. In the sidebar, navigate to **APIs & Services** > **Library**.
4. Search for **Google Search Console API** and click **Enable**.
5. Go to **APIs & Services** > **OAuth consent screen**:
   - Choose **External** and click **Create**.
   - Fill in App Name (e.g. `SEO Tool`) and your email address.
   - Under **Scopes**, add `https://www.googleapis.com/auth/webmasters.readonly`.
   - Under **Test users**, add your Google Account email.
   - Save and continue.
6. Go to **APIs & Services** > **Credentials**:
   - Click **Create Credentials** > **OAuth client ID**.
   - Application type: **Desktop App**.
   - Name: `SEO Tool Client`.
   - Click **Create**.
7. Download the JSON credential file, rename it to `client_secret.json`, and place it in the `seo-tool-free` project directory:
   ```
   seo-tool-free\client_secret.json
   ```
8. In the app's sidebar, click **Search Console**, then click **Connect Google Search Console** to authenticate.

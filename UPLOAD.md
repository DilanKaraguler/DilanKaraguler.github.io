# Publishing the site

This folder is the complete site. It goes into the GitHub repo **DilanKaraguler/DilanKaraguler.github.io**,
on the `main` branch. A GitHub Action (`.github/workflows/deploy.yml`) builds it and publishes the result
to a `gh-pages` branch, which GitHub Pages then serves at <https://dilankaraguler.github.io>.

## 1. Upload the files

The site has more than 100 files, so **don't use the web "Upload files" button** (it caps at 100).
Use git or GitHub Desktop. Make sure hidden folders like `.github/` are included; the deploy workflow lives there.

**Option A: git (Terminal)**

```bash
cd ~/Desktop/website/DilanKaraguler.github.io
git init -b main
git add .
git commit -m "New al-folio website"
git remote add origin https://github.com/DilanKaraguler/DilanKaraguler.github.io.git
git push -u origin main --force   # --force replaces whatever is in the repo now
```

If the repo has old content you want to keep in history, clone it first, copy these files over the clone, then commit and push normally instead of `--force`.

**Option B: GitHub Desktop**

File > Clone repository > DilanKaraguler.github.io. Delete the old files in the cloned folder, copy everything
from this folder in (including hidden files: press Cmd+Shift+. in Finder to see them), then Commit to main > Push origin.

## 2. Let the workflow publish

1. Repo **Settings > Actions > General > Workflow permissions**: choose **Read and write permissions**, Save.
2. Open the **Actions** tab and wait for "Deploy site" to finish (green check, a few minutes).
   If it didn't start, open "Deploy site" and click **Run workflow**.
3. Repo **Settings > Pages**: Source = **Deploy from a branch**, Branch = **gh-pages**, folder **/ (root)**, Save.
   (al-folio deploys through the `gh-pages` branch, so pick that rather than "GitHub Actions".)
4. After a minute or two the site is live at <https://dilankaraguler.github.io>.

Every later push to `main` rebuilds the site automatically.

**"The al_folio_core theme could not be found" (github-pages 232):** this comes from GitHub's built-in
"pages build and deployment" job, which runs when Pages is set to build from `main`. That built-in builder
can't use al-folio's theme gems. It's harmless once Pages serves the `gh-pages` branch (step 3); if `gh-pages`
doesn't exist yet, do step 1 and re-run "Deploy site" first.

## 3. Make it findable

1. **Google Search Console** (<https://search.google.com/search-console>): add a "URL prefix" property for
   `https://dilankaraguler.github.io`. Choose the HTML-tag verification method, copy only the `content="..."`
   code into `google_site_verification:` in `_config.yml`, set `enable_google_verification: true`, push, then click Verify.
   Then under Sitemaps submit `sitemap.xml`.
2. Link the site from everywhere people look you up:
   - **Google Scholar**: Edit profile > Homepage.
   - **ORCID**: Websites & social links. (Also add your ORCID iD to `_data/socials.yml`.)
   - **LinkedIn**: Edit intro > Website, and Contact info.
   - **GitHub**: profile Edit > Website.
   - **MSU**: ask the department to add the link to your graduate student directory entry.
   - Your CV header: the web versions already include it; add it to `cv/header_*.tex` too.

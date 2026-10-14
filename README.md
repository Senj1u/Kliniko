# Kliniko — Legal Pages

Static legal documents for the **Kliniko** app, published to GitHub Pages.

| Page | URL |
| --- | --- |
| Home / index | https://senj1u.github.io/Kliniko/ |
| Privacy Policy | https://senj1u.github.io/Kliniko/privacy.html |
| Account & Data Deletion | https://senj1u.github.io/Kliniko/delete-account.html |

## Contents

```
index.html                                  Landing page linking both legal documents
privacy.html                                Privacy Policy
delete-account.html                         Account & Data Deletion instructions
assets/style.css                            Shared stylesheet (no external requests)
.github/workflows/deploy-legal-pages.yml    GitHub Actions workflow that deploys the pages
```

All pages are plain, self-contained HTML with a single shared stylesheet — no build step, no
JavaScript, no third-party requests, and no cookies set by the site itself.

## Deployment

Pages is published from **GitHub Actions** (`Settings → Pages → Source = "GitHub Actions"`).

The workflow `.github/workflows/deploy-legal-pages.yml` runs:

* on every push to `main` or `master` that changes an `*.html` file, `assets/**`, or the workflow
  file itself;
* manually, from **Actions → "Deploy legal pages to GitHub Pages" → Run workflow**
  (`workflow_dispatch`).

It stages the HTML files and `assets/` into `_site/`, uploads that directory with
`actions/upload-pages-artifact`, and deploys it with `actions/deploy-pages`.

## Editing the documents

1. Edit `privacy.html` and/or `delete-account.html`.
2. Update the **"Last updated"** date in the edited page (top meta box **and** the footer), and on
   `index.html` if the change affects the summary text.
3. Commit and push to `main`. The workflow redeploys automatically.

## Previewing locally

No tooling is required — serve the folder over HTTP and open it in a browser:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/
```

Opening the files directly (`file://`) also works, because every link and asset reference is
relative.

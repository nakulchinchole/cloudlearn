# CloudLearn

Design and Implementation of a Cloud-Based Student Resource Portal Using Amazon S3 and Amazon CloudFront CDN.
Team: Nakul, Yash, Manish. Plain HTML, CSS and JavaScript. No backend, no build step, no keys.

## Folder structure
```
index.html resources.html architecture.html console.html deployment.html about.html 404.html
css/style.css          shared design
js/common.js           shared header and footer     js/cards.js  resource card
js/sim-core.js         cache simulator logic        js/data.js   resource list
js/resources.js  architecture.js  console.js  deploy.js  home.js    page scripts
pdfs/                  10 real sample PDFs          assets/favicon.svg
```

## Run on Windows with VS Code
1. Unzip the project. Right-click the folder, Extract All.
2. Open VS Code, File, Open Folder, choose the unzipped folder.
3. Easiest: double-click `index.html` in File Explorer. It opens in your browser.
4. Better: install the **Live Server** extension, right-click `index.html`, Open with Live Server.
5. Or open Terminal in VS Code and run `python -m http.server 8000`, then visit `http://localhost:8000`.
PDF downloads, search, filters, the console and the checklist all work offline.

## What is real and what is simulated
Real: the website, the ten PDFs, the search, filters, downloads and the saved checklist (browser localStorage).
Simulated: the Console page and the architecture demo. They run in JavaScript only. Nothing is connected to AWS and no metric is real CloudFront data.

## Deploy to AWS (you do this in your own account)
Full guide with a saving checklist is on `deployment.html`. Summary: private S3 bucket, upload everything except README.md, CloudFront distribution with the S3 REST endpoint, Origin Access Control, paste the generated bucket policy, default root object `index.html`, redirect HTTP to HTTPS, wait, test the `https://...cloudfront.net` URL, invalidate `/*` after updates, delete resources afterwards. AWS may charge for usage.

## Edit content
Add a resource: put a PDF in `pdfs/` and add an entry to `js/data.js`. Change team or report text in `about.html`.

## Professor demo script (about 5 minutes)
1. Home: explain the problem and the Browser, CloudFront, S3 picture.
2. Resources: search "join", filter Python, open Details, download a PDF.
3. Architecture: click Cache miss, then Cache hit. Say which step differs.
4. Console: send the same file twice, then another file. Show the ratio, Clear cache, Reset. Say it is a simulation.
5. Deployment: tick a few steps, reload, show progress is saved.
6. About: read the objectives and one or two viva notes.
7. If deployed, show the HTTPS URL and that the S3 object URL is denied.

## Tests performed on this build
Headless Chrome on all six pages at 320, 768 and 1440 px: no horizontal overflow, no JavaScript errors, all linked files exist. Search, filters, sort, empty state, reset, modal, console counters, clear cache, reset, architecture demo, checklist save and reload, and the mobile menu all behaved as expected. Not tested: Edge, real AWS deployment.

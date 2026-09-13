# odm-web

Static HTML and CSS for the ODM project site. Source of https://hembrow-innovations.github.io/odm-web/

CLI source lives in [hembrow-innovations/odm](https://github.com/hembrow-innovations/odm).

## Local preview

```bash
python3 -m http.server 8080
# → http://127.0.0.1:8080/
```

## Browser tests (Playwright)

Local-only smoke tests against a static server of this directory. Package manager: **npm** (lockfile committed).

```bash
npm install
npx playwright install chromium
npm run test:e2e
# optional UI mode:
npm run test:e2e:ui
```

Config: `playwright.config.ts` (serves `.` on port 4173 via `serve`). Tests live in `e2e/`:

- **`e2e/home.spec.ts`**: harness smoke (title)
- **`e2e/smoke.spec.ts`**: all `*.html` pages, nav, install/quickstart/concepts/features content, CSS asset, mobile viewport
- **`e2e/a11y.spec.ts`**: `@axe-core/playwright` on home + install + one guide (serious/critical clean); skip-link + start-here assertions
- **`e2e/links.spec.ts`**: crawl internal `a[href]` targets and in-page anchors

Artifacts (`test-results/`, `playwright-report/`, etc.) are gitignored. No live github.io dependency. DevDependencies only. The published static site needs no Node runtime.

## GitHub Pages

Push to `main` publishes via `.github/workflows/pages.yml`.

**Settings → Pages → Build and deployment → Source: GitHub Actions**

## Content sources

- odm root `README.md`, `CONTEXT.md`
- odm `docs/reference/` (vision, install, cli, config, multi-git, progen, worktrees)

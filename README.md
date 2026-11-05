# Phoneology website

![Status: In development](https://img.shields.io/badge/status-in%20development-7c3aed)
![Built with HTML and CSS](https://img.shields.io/badge/built%20with-HTML%20%26%20CSS-0f766e)

Preview and update Phoneology’s public home, support, privacy, terms, and data-deletion pages. Phoneology is an iPhone and iPad app in development.

[Visit the site](https://phoneology.app/) · [Quick start](#preview-the-site-locally) · [AGENTS.md](AGENTS.md) · [Support](https://phoneology.app/support/)

The site uses plain HTML and one shared stylesheet. It has no JavaScript, framework, package installation, build step, or automated test suite.

## Preview the site locally

Run the site from the repository root with Python 3. Allow about two minutes for the first preview if Python is installed.

1. Start the server:

   ```sh
   python3 -m http.server 8000 --bind 127.0.0.1
   ```

2. Open <http://127.0.0.1:8000/> in your browser. Serving from the root lets the site’s root-relative navigation and stylesheet paths resolve. Opening an HTML file directly does not provide that root.
3. Stop the server with **Ctrl+C** when finished.

**Done:** the home page has styling, and its navigation opens the other pages.

## Choose the file to edit

Edit the page for your route or the shared stylesheet for visual changes.

| Route or purpose | File |
| --- | --- |
| Home: `/` | [index.html](index.html) |
| Support: `/support/` | [support/index.html](support/index.html) |
| Privacy: `/privacy/` | [privacy/index.html](privacy/index.html) |
| Terms: `/terms/` | [terms/index.html](terms/index.html) |
| Data deletion: `/delete-data/` | [delete-data/index.html](delete-data/index.html) |
| Custom error page: `/404.html` | [404.html](404.html) |
| Shared colors, typography, layout, and responsive rules | [assets/styles.css](assets/styles.css) |
| Intended custom domain | [CNAME](CNAME) |
| Disable Jekyll processing on GitHub Pages | [.nojekyll](.nojekyll) |

Navigation and footers are repeated in each HTML file. Check every page when changing shared links, including the error page. Preserve page titles, canonical URLs, heading order, the skip link, and the current-page navigation label (`aria-current="page"`).

**Done:** the intended page changes, and shared navigation still works throughout the site.

## Verify app claims before changing copy

Check the current app implementation before changing statements about privacy, storage, sync, deletion, accounts, or purchases.

1. Read the relevant source in the [Phoneology app repository](https://github.com/droxey/phoneology), available locally at `/Users/droxey/dev/repos/phoneology`.
2. Separate what the source implements from behavior verified on a device. Sync and deletion claims need particular care because local behavior does not prove remote erasure.
3. Update affected pages together so support, privacy, terms, and deletion guidance agree. Keep development limitations visible until release behavior is verified. Change policy revision dates only when the policy changes substantively; leave dates alone for formatting or navigation fixes.

Website checks do not verify app behavior, App Store availability, or legal sufficiency. Publish release dates, pricing, or guarantees only with supporting evidence. App edits require separate authorization.

**Done:** each changed claim has a source or recorded verification result, and unresolved limits remain explicit.

## Check the change before sharing

Run the local preview and review the changed pages in a browser. A small copy change usually takes about five minutes to check; allow more time for shared layout changes.

1. Open `/`, `/support/`, `/privacy/`, `/terms/`, `/delete-data/`, and `/404.html`. Confirm the stylesheet loads and follow navigation and changed links.
2. Check a narrow phone-sized viewport and a desktop viewport. Look for overflow, clipped text, and readable spacing; check text at 200% zoom when layout or typography changes.
3. Use the keyboard to reach the skip link and navigation. Check that the skip link reaches the main content, focus is visible, link text is descriptive, there is one main heading, and heading order is sensible. Confirm each content page marks its own navigation link as current; the 404 page has no current route.
4. With the server running, smoke-check the routes and shared CSS, then check whitespace:

   ```sh
   for route in / /support/ /privacy/ /terms/ /delete-data/ /404.html /assets/styles.css; do
     curl --fail --silent --output /dev/null "http://127.0.0.1:8000$route" || exit 1
   done
   ```

   ```sh
   git diff --check
   ```

5. Review the diff for unintended edits and report which checks ran. Keep personal data, credentials, and private support details out of files and public issues.

Python serves `/404.html` directly but returns its own error response for missing routes. Check the custom error page on a missing route after an authorized deployment.

**Done:** affected pages and links work, keyboard and viewport checks pass, and missing verification is recorded.

## Contribute or get help

Read [AGENTS.md](AGENTS.md) before proposing a change, or use the support channels below for help.

- **Contribute:** make a focused change on a feature or fix branch. Run the checks above and describe the change and verification in your pull request.
- **Report a bug:** use [GitHub issues](https://github.com/droxey/phoneology-web/issues) for non-sensitive bugs. Issues are public; keep personal information, receipts, and account details out.
- **Get private support:** email [support@phoneology.app](mailto:support@phoneology.app) for app, purchase, privacy, or deletion requests. Include the problem, app version, and device model. Do not send passwords, verification codes, full payment details, a birthdate, or a complete phone number.

**Done:** the change is ready for review, or your question has reached the appropriate support channel.

## Confirm hosting before publishing

Open the [repository’s GitHub Pages settings](https://github.com/droxey/phoneology-web/settings/pages) before changing deployment configuration or publishing.

The source contains `CNAME` with `phoneology.app`, `.nojekyll`, and canonical URLs under <https://phoneology.app/>. The privacy page describes GitHub Pages hosting. On November 5, 2026, Pages settings were verified to publish from the `main` branch at the repository root (`/`), with the custom domain and HTTPS enabled. Pushing to `main` publishes the site. Recheck the settings before publishing; repository files alone do not prove the current configuration or DNS records.

1. Verify the configured Pages source, published revision, custom domain, and HTTPS status in GitHub. Check DNS separately if changing the domain.
2. Confirm authorization before pushing, merging, or changing hosting settings. Use a descriptive feature or fix branch and an independently reviewed diff.
3. After an authorized deployment, check the public routes, CSS, and a missing route at the intended domain. Report the revision checked and distinguish local results from deployed results.

The repository contains no deployment workflow or separate Preview configuration. Verify preview support before relying on a branch deployment.

**Done:** the deployment target and settings are verified, and any published result is checked at its actual URL.

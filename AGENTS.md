# Maintain Phoneology’s website

Read the task files before editing. Keep changes small and verify affected pages locally.

## 1. Confirm the scope

- Read requested files, direct dependencies, and relevant checks. Avoid repository and archive crawls.
- This repository is plain HTML with shared CSS in `assets/styles.css`. Content lives in `index.html`, `support/index.html`, `privacy/index.html`, `terms/index.html`, and `delete-data/index.html`; `404.html` is the error page. There is no framework, build command, or automated test suite.
- Read access to the separate Phoneology app repository at `../phoneology` or `https://github.com/droxey/phoneology` is always authorized whenever needed, subject to tool and security boundaries. Read its applicable guidance and relevant implementation before making app-behavior claims. Website text does not prove current iOS behavior. App edits require separate authorization.
- Use a descriptive `feat/` or `fix/` branch. Preserve other contributors’ changes. Stop after three failed repairs and name the conflict or doubtful assumption. Never poll or sleep for changes.

## 2. Keep pages accessible

- Reuse existing HTML structure and CSS variables. Keep shared styling in `assets/styles.css`; add dependencies or tooling only when the task requires them.
- Preserve semantic headings, labeled navigation, the skip link, visible keyboard focus, contrast, and responsive layout. Set `aria-current="page"` on the current page’s navigation link.
- Check shared header and footer links on affected pages, including `404.html`. Use root-relative internal URLs and trailing slashes for directory routes. Preserve each content page’s canonical URL under `https://phoneology.app/`.
- Support privacy, terms, deletion, support, and release-status claims with evidence. Read the app repository when needed; report unverified behavior.

## 3. Verify in a local browser

1. Start the server from the repository root:

   ```sh
   python3 -m http.server 8000 --bind 127.0.0.1
   ```

2. Open `http://127.0.0.1:8000`. Check affected routes: `/`, `/support/`, `/privacy/`, `/terms/`, `/delete-data/`, and `/404.html`. Verify styles load and local navigation stays on the local origin.
3. For HTML or CSS changes, check desktop and narrow mobile layouts for overflow, clipped text, and navigation wrapping. Use the keyboard to test the skip link, focus order, visible focus, and links. Follow affected internal links and inspect browser errors.
4. Open `/404.html` directly and verify its return links. Python’s server returns its own error response for missing paths; it does not reproduce the hosted custom error page. Verify hosted missing-path behavior separately when authorized.
5. Stop the local server. Run `git diff --check` and review changed files. Report tested URLs, viewport sizes, results, and missing proof. For Markdown-only work, verify commands, paths, and factual claims; avoid unrelated browser tests and full suites.

Browser interaction may inspect pages and follow safe links within scope. Get explicit authorization before submitting forms, sending messages, changing accounts, making purchases, or triggering other external side effects. Keep secrets out of source, URLs, logs, and chat. If an authorized task uses a secret header, send it only to the exact intended origin (scheme, host, and port); recheck every request and never forward it across an origin-changing redirect.

## 4. Write and finish clearly

- Apply ADHD-friendly clarity to every Markdown document and section: lead with the action or result, use short paragraphs and descriptive headings, number sequential steps, and keep each visible list to five items where possible. Preserve necessary technical detail and policy force. Write standalone prose and remove filler.
- Finish with scoped validation and an independent diff review. Use Conventional Commits; docs-, tests-, and agent-only commits require `[skip ci]`.
- Skip local and hosted CodeRabbit for prose-only PRs; include a standalone `@coderabbitai ignore` in the PR body. For executable changes, follow applicable CodeRabbit instructions and resolve blockers before creating a PR; add a success marker only after a successful review with no unresolved blockers, and record verification.
- Push, PR creation or updates, merges, deployments, and DNS changes require explicit authorization. Preserve `CNAME` and `.nojekyll` unless the task changes publishing configuration. Distinguish local, Preview, and Production evidence. Validate locally before any authorized push.

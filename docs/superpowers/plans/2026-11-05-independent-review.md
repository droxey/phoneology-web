# Review Phoneology website maintenance guides

## Global constraints

- Review the existing guide drafts independently; preserve the originating thread’s files and all unrelated work. Do not invent app or legal claims.
- Work locally on `fix/independent-review-current` from `7b19b91b2c81184b3b0255db9cb9b12f50d58284`. No push, PR, merge, deployment, app edits, or policy-content changes. Require independent review and parent authorization before a local commit; publishing remains unauthorized.
- Apply action-first Markdown with essence-doc, essence, write-like-you-talk, and i-have-adhd. Keep setup and browser checks easy to follow.
- Use scoped checks. No polling, sleeps, full suites, or unnecessary browser automation. Stop after three failed repairs.

## Task 1: Review guides and fix 404 navigation

### Requirements

Review stable `README.md` and `AGENTS.md` drafts from the originating checkout when available; record their hashes. Correct only evidence-backed omissions. If a draft is absent, report it without waiting or duplicating it.

README acceptance: lead with the root-server command `python3 -m http.server 8000 --bind 127.0.0.1`, local URL, and Ctrl-C; explain static HTML/CSS without dependencies or a build/test command; map the five routes, 404, shared CSS, CNAME, and .nojekyll; explain why root-relative assets need a root HTTP server. Cover direct editing, consistent navigation, evidence for app/privacy/purchase/sync/deletion claims, and substantive-only policy dates. Include focused whitespace/HTTP checks, manual keyboard/skip/focus/active-nav/mobile/wide checks, the Python-vs-Pages 404 difference, and Pages main/root publishing boundaries.

AGENTS acceptance: concise site-specific scope, root-relative routes, semantic accessibility, preserve CNAME/.nojekyll, scoped app-source verification, verified-vs-planned claims, focused checks, and branch/review/commit boundaries. Prose-only PRs exclude CodeRabbit with a standalone `@coderabbitai ignore`; HTML changes do not qualify as prose-only automatically.

Fix `404.html` only by adding Delete data to its header and normalizing internal directory links to trailing slashes. Preserve its legal/product text and accessibility structure.

### Validation and handoff

1. Capture the baseline navigation failure before the HTML fix using a focused local check.
2. Run the same check after the fix, then a local HTTP smoke check of five routes, `/404.html`, CSS, and root-relative internal targets. Confirm missing paths use Python’s generic 404.
3. Run `git diff --check`, inspect the scoped diff, and report browser checks as missing proof when not run.
4. Generate a review package including untracked guides and this plan. Record decisions and evidence in the plan’s ignored SDD workspace. Require the parent’s clean independent review and commit authorization before committing locally.

## Acceptance checks

- Static: focused navigation check fails on baseline and passes after the 404 fix; root-relative directory URLs and header/footer consistency hold across six pages. `git diff --check` passes; only guides, plan, and 404 change.
- Integration: local HTTP returns success for all five routes, `/404.html`, CSS, and linked internal resources. A missing route returns Python’s generic 404, distinct from the custom page.
- Rendered checks: Playwright 1.63 / Chromium 153 passed 606 effective checks across six routes at 320×800, 390×844, and 1280×900. Covered horizontal overflow/navigation clipping, full forward/reverse Tab order and visible focus, native skip-link bypass, per-navigation current-page state, and 404 return-link activation. Recorded 21 screenshots; controller visually spot-checked only 320px 404, 390px home, and 1280px focused skip link. This is Chromium viewport evidence, not physical-device or assistive-technology qualification.
- Review: historical task, broad, and final scoped reviews passed without findings before the prior local commits. This current-upstream reconciliation and updated evidence require fresh independent delta review before any new local commit. Publishing remains unauthorized.

## Work

- [x] Isolate checkout, capture baseline and guide provenance, initialize SDD artifacts.
- [x] Capture the expected failing navigation check; correct guide omissions and 404 navigation.
- [x] Complete scoped static and HTTP checks.
- [x] Close the requested website viewport/keyboard/current-navigation gaps with scripted rendered checks and retain exact-source screenshots/results.
- [ ] Receive independent review of the current-upstream reconciliation and browser evidence before a new local commit.

## Verify the current upstream reconciliation

The prior reviewed commits remain on `fix/independent-review-guides` at `9e82ec4`. This branch starts from fetched upstream `7b19b91`; preserve the merged README introduction and contribution section alongside the reviewed guide corrections and 404 navigation fix. No history rewrite or publishing is authorized.

One-off scripted Playwright checks covered all six rendered routes at 320, 390, and 1280 pixels, including overflow/navigation clipping, complete keyboard traversal/order, skip-link activation and sequential focus bypass, visible focus, current-page state, and activated 404 return links. Screenshots and exact source hashes are in the ignored workspace. The initial current-page assertion incorrectly required one marker globally; retained failure evidence shows the correct Delete data link marked in separate header/footer navigation sets. Corrected that test assumption without HTML changes, rechecked only the 18 current-page cases, and reused 588 passing checks. Native skip activation leaves BODY as activeElement in Chromium but moves the sequential focus start; next Tab reaches the first main link on every route. No website behavior failure or repair was needed. New commits require independent delta review and parent authorization.

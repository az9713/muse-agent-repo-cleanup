# muse-agent-repo-cleanup

> **Built by [Muse](https://muse.ai)** — Meta's personal AI agent. Every diagnosis, fix, test, pull request, and verification described here was performed autonomously; the human contributed only decisions and approvals.

A showcase of autonomous agent work on GitHub — real incidents on real repos, resolved in days with a handful of human messages.

## The guides (live pages)

- [Security Scan & CI Checks Explained](https://az9713.github.io/muse-agent-repo-cleanup/security-scan-checks-explained.html) — plain-English walkthroughs of the September 13 incidents: what failed, what changed, and the Git/GitHub lessons inside.
- [The Development Journey](https://az9713.github.io/muse-agent-repo-cleanup/development-journey.html) — the September 13 turn-by-turn record of how the work got done autonomously.
- [Day Two: The Lint-Failure Emails](https://az9713.github.io/muse-agent-repo-cleanup/day-two-lint-fixes.html) — the September 14 turn-by-turn record: dead-workflow cleanup and a 25-violation ruff lint repair across two repos.
- [The Case of the Missing Traffic Numbers](https://az9713.github.io/muse-agent-repo-cleanup/missing-traffic-numbers.html) — the September 16 turn-by-turn record: a dashboard stuck at "n/a", a personal-access-token walkthrough, and one self-inflicted bug, honestly recovered from.
- [From YouTube URL to Summary: How the Transcripts Get Made](https://az9713.github.io/muse-agent-repo-cleanup/transcript-pipeline-journey.html) — the September 17 turn-by-turn record: how ten video summaries were grounded in transcripts — and honestly labeled on the page when no transcript could be had.

## The GitHub tasks behind them

### Day one — `az9713/ECC-tutorial` (September 13, 2026)

1. **Stale-bot exemption (PR #25)** — exempted the `metrics-snapshot` label so the Monthly Metrics Snapshot dashboard (issue #24) never goes stale.
2. **Supply-Chain Watch repair (PR #26)** — the scheduled security scan had failed for ~3 weeks (74 of the last 75 runs) on 5 vulnerable dependencies; patched `package-lock.json` and confirmed with a manual green run.
3. **CI health repair (PR #27)** — fixed three pre-existing CI failures: a missing executable bit killing 24 Linux/macOS test jobs, test coverage below 80% (4 new test files written), and 21 emoji violating the unicode-safety check.

Human input across all of it: report the symptom, pick a direction, approve the merges. Everything else — diagnosis, code, tests, verification — ran autonomously.

### Day two — `az9713/llm-ensemble-council` and `az9713/coilmem` (September 14, 2026)

1. **Dead workflow removal (PR #12, PR #20, merged)** — deleted `docs-drift.yml` and `weekly-digest.yml` from both repos; they had failed every Monday for 3 weeks on an unmaintained OAuth token. The repos do without them.
2. **Ruff lint repair (PR #13, PR #21, opened for review)** — both repos' CI had been red on the `ruff check .` step for Python 3.11/3.12 (pre-existing on `main`, unrelated to the merges). Fixed all 25 violations locally — modernized annotations, sorted imports, removed obsolete `noqa`s, `itertools.pairwise`, a reworked `try/except` in `_extract_json` — verified Ruff clean and all 30 tests passing before uploading.

Human input: report the symptom ("look into why the CI fails"), set the goal ("no more failure emails"), approve the merges, and sign in when the browser session died. A scheduled watch reports the CI results back on its own.

### Day three — `az9713/ECC-tutorial` (September 16, 2026)

1. **Traffic-stats activation** — the Monthly Metrics workflow's Views and Clones columns had shown "n/a" for months, because GitHub's traffic API answers the default `GITHUB_TOKEN` with a 403. The user created a classic personal access token (repo scope) and stored it as the `TRAFFIC_STATS_TOKEN` repo secret; the next workflow run posted real traffic numbers to the dashboard (issue #24). Along the way, one self-inflicted syntax bug was caught, owned, and fixed before the final green run (#13).

Human input: create the token when nudged, type one commit message. Everything else — diagnosis, the walkthrough, the fix, the verification — ran autonomously.

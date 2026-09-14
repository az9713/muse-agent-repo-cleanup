# muse-agent-repo-cleanup

A showcase of autonomous agent work on GitHub — two real incidents on `az9713/ECC-tutorial`, resolved in one day (September 13, 2026) with a handful of human messages.

## The guides (live pages)

- [Security Scan & CI Checks Explained](https://az9713.github.io/muse-agent-repo-cleanup/security-scan-checks-explained.html) — plain-English walkthroughs of both incidents: what failed, what changed, and the Git/GitHub lessons inside.
- [The Development Journey](https://az9713.github.io/muse-agent-repo-cleanup/development-journey.html) — the turn-by-turn record of how the work got done autonomously.

## The GitHub tasks behind them

1. **Stale-bot exemption (PR #25)** — exempted the `metrics-snapshot` label so the Monthly Metrics Snapshot dashboard (issue #24) never goes stale.
2. **Supply-Chain Watch repair (PR #26)** — the scheduled security scan had failed for ~3 weeks (74 of the last 75 runs) on 5 vulnerable dependencies; patched `package-lock.json` and confirmed with a manual green run.
3. **CI health repair (PR #27)** — fixed three pre-existing CI failures: a missing executable bit killing 24 Linux/macOS test jobs, test coverage below 80% (4 new test files written), and 21 emoji violating the unicode-safety check.

Human input across all of it: report the symptom, pick a direction, approve the merges. Everything else — diagnosis, code, tests, verification — ran autonomously.

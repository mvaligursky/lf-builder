# lf-builder

Personal automation that produces portable Windows builds and publishes them as
releases in this repository.

## Schedule & logic

Runs **daily**. Each run decides, in order:

1. **New tag?** If upstream's latest semver tag (`vX.Y.Z`) hasn't been built yet →
   build it, publish as `vX.Y.Z-win`.
2. **Stale?** Otherwise, if no build has happened in the **last 7 days** → build
   upstream's moving `nightly` snapshot, publish as `nightly-<date>-<shortsha>`.
3. Otherwise → no-op (a ~30s check).

A committed `state.json` records what has been built and the last-build time, so
decisions don't depend on which releases are still around.

## Manual runs

Actions tab → *Scheduled Build* → **Run workflow**:
- `ref` — build a specific upstream tag/branch/SHA on demand.
- `force` — build the current `nightly` snapshot even if nothing is due.

## Retention & downloads

- Tagged releases (`vX.Y.Z-win`) and manual builds are **kept forever**. Only
  `nightly-*` builds are pruned, retaining the most recent **3** (`KEEP_NIGHTLIES`).
- Downloads: see the [Releases](../../releases) page.

The upstream project slug is stored in the `UPSTREAM_REPO` Actions variable.

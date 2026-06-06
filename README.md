# lf-builder

Personal automation that produces portable Windows builds and publishes them as
releases in this repository.

- **Schedule:** runs twice a week (Mon & Thu). Builds only when upstream's moving
  `nightly` tag points at a commit that hasn't been built yet; otherwise it's a
  ~30s no-op.
- **On demand:** Actions tab → *Scheduled Build* → **Run workflow** (optionally
  enter a specific upstream ref/SHA, or tick *force* to rebuild an existing commit).
- **Versioning:** releases are named `nightly-<date>-<shortsha>` (no public semver
  releases exist upstream anymore).
- **Retention:** only the most recent 3 releases are kept; older ones are pruned
  automatically (see `KEEP_RELEASES`).
- **Downloads:** see the [Releases](../../releases) page.

The upstream project slug is stored in the `UPSTREAM_REPO` Actions variable.

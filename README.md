# lf-builder

Personal automation that produces portable Windows builds and publishes them as
releases in this repository.

- **Trigger:** runs daily, and on demand from the **Actions** tab → *Daily Build* →
  **Run workflow** (optionally enter a specific upstream tag, or tick *force* to
  rebuild an existing one).
- **What it does:** checks whether upstream has a newer release than the latest one
  built here; if so, builds that exact tagged commit and attaches the zip to a new
  release named `<tag>-win`.
- **Downloads:** see the [Releases](../../releases) page.

The upstream project slug is stored in the `UPSTREAM_REPO` Actions variable.

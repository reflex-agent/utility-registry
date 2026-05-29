# Reflex utility registry

Curated catalogue of utilities Reflex blesses for one-tap install.

Reflex fetches [`index.json`](./index.json) once a day from this repo's raw
content and overlays it on the inline baseline shipped with the binary. If the
network is unavailable, the baseline is used — the install grid is never empty.

## Schema

```jsonc
{
  "version": 1,
  "items": [
    {
      "id": "task-board",            // unique slug
      "name": "Task board",          // display name
      "emoji": "📋",
      "category": "productivity",    // finance | health | productivity | travel | study | creative | other
      "description": "…",
      "github": "github:reflex-agent/rflx-task-board@v0.7.1", // installFromGithubAction coordinate
      "suggestedScope": "project",   // global | project (UI may override)
      "author": "reflex-agent"
    }
  ]
}
```

Entries missing `id`, `name`, or `github` are dropped on load.

## Adding a utility

1. Add an entry to `items` in `index.json`.
2. Point `github` at a tagged release of the utility repo.
3. Commit to `main` — clients pick it up within ~24h (per-client cache TTL).

# Presentation package — front v1

`manifest.json` describes this project for Cohesian, a portfolio, or another
consumer. `schema.json` is the self-contained JSON Schema snapshot for editor
completion and offline validation. This folder contains data and assets only;
each consumer owns its components, theme, layout, and interaction.

Edit the manifest and files in `assets/`. Keep `id` stable when renaming or
moving the project. All asset paths are relative to this folder, start with
`assets/`, and must stay inside it. Symlinks, scripts, absolute paths and
traversal are unsupported. The entire `assets/` directory is distributable;
include only presentation files intended for publication, even if this
repository itself is private. Retain license and attribution notices.

| Field | Meaning |
|---|---|
| `schemaVersion` | Contract version, currently `1` |
| `id` | Stable project identity |
| `kind` | Presentation category |
| `title`, `description` | Plain text; no executable markup |
| `labels` | Topics/tags; may be empty |
| `cover` | Local presentation artwork |
| `licenses` | Named links to applicable local notices or HTTPS license pages |
| `programmingLanguage` | Language, e.g. JavaScript, TypeScript, Python or Go; Node.js is a runtime and can be a label |
| `links` | Nonempty ordered `{label, href}` list using HTTPS; repository first, then package/docs as appropriate |

Tool IDs are stable slugs. Covers support SVG or PNG. The copied presentation
artwork and description retain Cohesian Site's CC BY 4.0 attribution in
`assets/licenses/`; this does not change the implementation's license.

## Use in the local Cohesian workspace

From the `site/` checkout:

```sh
npm run check:front
npm run sync:front
npm run dev
```

`check:front` validates all selected packages without writing. `sync:front`
updates Site's standalone catalog/assets snapshot. A portfolio can read this
same manifest and render its own cards without depending on Cohesian's UI.
See the [shared contract and consumer guide](../../../site/front/README.md).
The schema snapshot and this operational guide are MIT licensed; see
`LICENSE-SCHEMA`. Artwork and publication notices keep their own scopes.
The canonical schemas live in `site/front/schemas/`; local snapshots must match
version 1. Contract updates must update the canonical and project snapshots
together. Runtime packages and publication source formats are unaffected.

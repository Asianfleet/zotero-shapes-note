# Zotero Shapes Note

A plugin for [Zotero](https://www.zotero.org/).

> This repository was bootstrapped from
> [windingwind/zotero-plugin-template](https://github.com/windingwind/zotero-plugin-template),
> and its Git history was reset to a single initial commit. The scaffolding,
> build and release infrastructure is still provided by that template — see its
> [README](https://github.com/windingwind/zotero-plugin-template#readme) for the
> full development guide.

## Requirements

- [Zotero](https://www.zotero.org/) 7 or 8
- Node.js 20+ and npm

## Development

```bash
npm install

# Configure the Zotero binary and the development profile.
cp .env.example .env

npm start          # launch Zotero with the plugin loaded (hot reload)
npm run build      # build the XPI and type-check
npm run lint:check # prettier + eslint
npm run lint:fix   # prettier + eslint with --fix
npm run test       # run the scaffold tests
npm run release    # publish a release (normally triggered by a version tag in CI)
```

`.env.example` documents every variable, including
`ZOTERO_PLUGIN_ZOTERO_BIN_PATH` and `ZOTERO_PLUGIN_PROFILE_PATH`.
Create a dedicated Zotero profile for development with
`/path/to/zotero -p` so your daily profile stays untouched.

## Plugin identity

The plugin identity lives in the `config` field of `package.json` and is
injected into `addon/manifest.json` at build time through placeholders such as
`__addonName__` and `__addonID__`.

| Field           | Value                             |
| --------------- | --------------------------------- |
| `addonName`     | `Shapes Note`                     |
| `addonID`       | `shapesnote@asianfleet.github.io` |
| `addonRef`      | `shapesnote`                      |
| `addonInstance` | `ShapesNote`                      |
| `prefsPrefix`   | `extensions.zotero.shapesnote`    |

`addonID`, `addonRef` and `prefsPrefix` should be considered frozen once the
plugin has been released to users: changing them disconnects existing user
preferences and the automatic update path.

## Layout

- `src/` — plugin sources. Entry point `src/index.ts`, lifecycle hooks
  `src/hooks.ts`.
- `src/modules/examples.ts` — the examples that ship with the template. Delete
  the parts you do not need as your own code grows.
- `addon/` — static assets: `manifest.json`, Fluent locale files, default
  preferences, icons, stylesheets.
- `zotero-plugin.config.ts` — build, test and release configuration.
- `.github/workflows/` — CI, release and issue-bot workflows. All of them call
  the shared reusable workflows in `zotero-plugin-dev/workflows`, so there is
  no repository-specific configuration in them.

## License

AGPL-3.0-or-later. See [LICENSE](LICENSE).

# AGENTS.md

Instructions for AI coding agents working on **fanjinde-seasons** — a VS Code / Cursor color theme extension.

## Project overview

- **Type**: VS Code extension (category: Themes), no runtime code — only theme JSON and extension manifest.
- **Theme**: Light base (`uiTheme`: `vs`), label **Seasons**.
- **Token colors**: TextMate scopes in `themes/Seasons-color-theme.json`; UI colors in the same file under `colors`.

## Project structure

| Path | Purpose |
|------|---------|
| `package.json` | Extension manifest; `contributes.themes` points to the theme file |
| `themes/Seasons-color-theme.json` | Color theme definition (`colors`, `tokenColors`) |
| `.vscode/launch.json` | Extension Development Host (F5) |
| `prettier.config.js` | Formatting for JSON/JS in the repo |
| `CHANGELOG.md` | User-facing release notes (Keep a Changelog style) |

## Commands

```bash
# Format theme and config (if Prettier is available locally)
npx prettier --write themes/Seasons-color-theme.json package.json
```

**In VS Code / Cursor**

- **Run extension**: `F5` → Extension Development Host; pick **Seasons** via `Preferences: Color Theme` (`Ctrl+K Ctrl+T` / `Cmd+K Cmd+T`).
- **Inspect scopes**: Command Palette → `Developer: Inspect Editor Tokens and Scopes` — use when tuning `tokenColors` scopes.
- **Theme edits**: Changes to `Seasons-color-theme.json` reload automatically in the Development Host window.

**Publish** (human-driven; do not run unless asked)

- Package: `vsce package` (requires `@vscode/vsce` and publisher setup).
- Docs: [Color Theme](https://code.visualstudio.com/api/extension-guides/color-theme), [Publishing](https://code.visualstudio.com/api/working-with-extensions/publishing-extension).

## Code style

- **Theme JSON**: Match existing structure — named `tokenColors` entries with `scope` (string or array), `settings.foreground`, optional `fontStyle`. Keep hex colors consistent (`#RRGGBB`, uppercase or lowercase as in file).
- **UI colors**: Keys under `colors` follow VS Code theme color IDs (see [Theme Color](https://code.visualstudio.com/api/references/theme-color)).
- **Prettier**: `semi: true`, `singleQuote: true`, `tabWidth: 2`, `trailingComma: 'all'` — run Prettier after editing `package.json` or JS config; theme JSON may use tabs today — avoid drive-by reformat of the whole theme unless requested.
- **package.json**: Bump `version` when preparing a release; update `CHANGELOG.md` under `[Unreleased]` / new version section.

## Testing / done criteria

- [ ] Theme loads in Extension Development Host without JSON errors.
- [ ] Sample files (TS, JS, HTML, CSS, Markdown) look correct for comments, strings, keywords, types, functions.
- [ ] `Developer: Inspect Editor Tokens and Scopes` confirms scopes match the rules you added or changed.
- [ ] No edits to `.vscodeignore` unless packaging requires it.

## Git and PRs

- **Commits**: Only when the user explicitly asks; never force-push `main`/`master`.
- **Do not commit**: `.env`, tokens, publisher secrets, or `.vsix` unless the user wants them tracked.
- **PRs**: Summarize visual/theme changes; note before/after or languages checked in the test plan.

## Boundaries

- **Do**: Adjust colors, scopes, theme metadata, README/CHANGELOG, extension manifest fields needed for the theme.
- **Ask first**: Adding dependencies, activation events, commands, or non-theme extension features.
- **Avoid**: Unrelated refactors, renaming the theme label without user request, changing `engines.vscode` without compatibility check.

## References

- In-repo: `vsc-extension-quickstart.md` (F5, scope inspection, publishing pointers).
- External: [TextMate scopes](https://macromates.com/manual/en/language_grammars), VS Code color theme guide (linked above).

# Seasons

A VS Code / Cursor color theme extension with four seasonal variants.

| Theme | Mood |
|-------|------|
| **Seasons: Spring** | Soft cream, blossom pink, fresh green |
| **Seasons: Summer** | Bright sky blue, golden sun |
| **Seasons: Autumn** | Warm parchment, rust and amber |
| **Seasons: Winter** | Cool dark night, frost blue accents |

## Try it locally

1. Open this folder in VS Code or Cursor.
2. Press **F5** to launch the Extension Development Host.
3. **Cmd+K Cmd+T** (or **Ctrl+K Ctrl+T**) → choose **Seasons: Spring** (or Summer / Autumn / Winter).

## Customize

Palettes and UI colors are defined in `scripts/generate-season-themes.mjs`. After editing, run:

```bash
node scripts/generate-season-themes.mjs
```

Use **Developer: Inspect Editor Tokens and Scopes** to tune syntax scopes.

## License

See repository license (if added).

## package

```bash
vsce package  
```
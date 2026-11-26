# Nanquim Theme (VS Code)

A dark theme inspired by **Vira Carbon**: charcoal background `#0A0A0A`, sea-green accent `#80CBC4` and soft
pastel syntax colors. It has a Neovim companion (`nanquim.nvim`) generated from the same palette, so code looks
the same in both editors.

*Nanquim* is Portuguese for India ink.

## Themes

| Theme | Background |
|---|---|
| **Nanquim** | charcoal `#0A0A0A` |
| **Nanquim Black** | pure black `#000000` |

Both share the same syntax colors; only the backgrounds change. They match the Neovim variants `nanquim` and
`nanquim-black`.

## Installation

**From the .vsix (easiest)**

```bash
code --install-extension nanquim-theme-1.2.0.vsix
```

Or in VS Code: `Extensions` → `...` → **Install from VSIX...**

**From the folder**

Copy this folder to `~/.vscode/extensions/nanquim-theme` and restart VS Code.

Then press `Ctrl+K Ctrl+T` (`Cmd+K Cmd+T` on macOS) and pick **Nanquim** or **Nanquim Black**.

## Colors look different than expected?

Something else is probably overriding the theme colors:

1. Open `Ctrl+Shift+P` → **Preferences: Open User Settings (JSON)**.
2. Look for `workbench.colorCustomizations` and `editor.tokenColorCustomizations`.
   Theme extensions such as **Vira** write the accent, borders and line highlight into these blocks, and
   unscoped entries apply to *every* theme. Delete those blocks, or move their content inside
   `"[Vira Carbon]": { ... }`.
3. Also look for `viraTheme.*` settings, and disable or uninstall the Vira extension if you no longer use it.
4. Make sure `editor.semanticHighlighting.enabled` is not `false`.

## Recommended settings

```jsonc
{
  "workbench.colorTheme": "Nanquim",
  "editor.semanticHighlighting.enabled": true,
  "editor.bracketPairColorization.enabled": true,
  "editor.guides.bracketPairs": "active",
  "editor.cursorBlinking": "smooth",
  "window.titleBarStyle": "custom"
}
```

## Palette

See `PALETTE.md`: every color, its contrast, and which color paints each element.

## Rebuilding / customizing

The `source/` folder has the palette (`palette.json`) and the generators. Edit the JSON and run, from this folder:

```sh
python3 source/build_vscode.py .                     # rebuild both themes in themes/
python3 source/build_docs.py PALETTE.md              # rebuild PALETTE.md
python3 source/build_nvim.py path/to/nanquim.nvim    # optional: rebuild the Neovim palette and terminal extras
```

For one-off tweaks without touching the theme, use `workbench.colorCustomizations` and
`editor.tokenColorCustomizations` scoped to the theme, e.g. `"[Nanquim]": { ... }`, in settings.json.

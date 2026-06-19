# termdraw

Minimalist pixel art editor that runs entirely in your terminal.

Built with [Ratatui](https://ratatui.rs) and [Crossterm](https://github.com/crossterm-rs/crossterm).

## Features

- **Drawing tools** — brush, line, rect, circle (outline/filled), spray, flood fill, gradient, eraser, eyedropper
- **Colour management** — 14 palette slots, custom RGB input, harmonic colour generator, colour history, colour picker popup
- **Tabs** — multiple canvases, renameable, closeable
- **Undo/redo** — unlimited history per tab
- **Selection** — rectangular select, copy/cut/paste, nudge with arrows
- **Text overlay** — type directly onto the canvas
- **Game of Life** — seed cells and run cellular automata interactively (~6 gen/s)
- **Posterize** — quantise canvas to N most frequent colours
- **Grid overlay, symmetry mode, rainbow mode**
- **File I/O** — save/load custom `.txt` format, load images (jpg/png/gif/bmp), export PNG
- **Session persistence** — auto-saves every 60s, restore on launch
- **Configurable** — TOML config for themes, palette, keybind overrides
- **Searchable help** — `?` for keybinding reference

## Installation

```sh
cargo install termdraw
```

Requires Rust 1.85+ (edition 2024).

### From source

```sh
git clone https://github.com/ark/termdraw
cd termdraw
cargo run --release
```

## Usage

Run `termdraw` to launch the editor.

### CLI companion tool

```sh
cargo run --bin img2termdraw -- photo.jpg --width 80
```

Converts any image (jpg, png, gif, bmp) into termdraw's `.txt` format, resizing to fit the given width while preserving aspect ratio.

## Keybinds

| Key | Action |
|---|---|
| `q` | Quit (saves session) |
| `?` / `/` | Toggle help |
| `Ctrl+S` / `Ctrl+O` | Save / Load |
| `Ctrl+E` / `Ctrl+P` | Export PNG / Quick export |
| `Ctrl+Z` / `Ctrl+Y` | Undo / Redo |
| `Ctrl+T` / `Ctrl+W` | New / Close tab |
| `Tab` / `BackTab` | Next / Previous tab |
| `F2` | Rename tab |
| `Ctrl+R` | Resize canvas |
| `Ctrl+C/X/V` | Copy / Cut / Paste selection |
| `c` | Clear canvas |
| `Esc` | Dismiss popups / reset tools |
| `1`-`9` | Select palette colour |
| `Space` | Next palette colour |
| `[` / `]` or `-` / `+` | Brush size down/up |
| `l` | Line tool |
| `r` / `R` | Rect / Filled rect |
| `o` / `O` | Circle / Filled circle |
| `e` | Eraser |
| `i` | Eyedropper |
| `f` | Flood fill |
| `s` | Spray paint |
| `g` | Gradient fill |
| `t` | Text mode |
| `L` | Game of Life toggle |
| `P` | Posterize |
| `u` | Generate harmonious colours |
| `0` | Cycle custom colours |

See the in-app help (`?`) for the full reference.

## Configuration

Config file at `~/.config/termdraw/config.toml`. A fully-commented default is generated on first run.

Supports 7 built-in themes (Tokyo Night, Catppuccin, Gruvbox, Nord, Dracula, OneDark, RosePine) with per-field overrides, custom colour palettes, and keybinding remapping.

## Technical notes

- Pixels stored in a sparse `BTreeMap` — only occupied pixels consume memory
- Direct buffer rendering (`█` with foreground colour) — no Ratatui `Canvas` widget
- Canvas is single-layer, no zoom, no layer system — intentionally minimal
- Session format is a custom line-based text format (not serde) for readability and debugging

## License

MIT

# termdraw

Terminal-based pixel art editor

## Features

- **Drawing tools** — brush, line, rect, circle (outline/filled), spray, flood fill, gradient, eraser, eyedropper
- **Colour management** — 14 palette slots, custom RGB input, harmonic colour generator, colour history, colour picker popup
- **Tabs** — multiple canvases, renameable, closeable
- **Undo/redo** — unlimited history per tab
- **Selection** — rectangular select, copy/cut/paste, nudge with arrows
- **Text overlay** — type directly onto the canvas
- **Game of Life** — seed cells and run cellular automata interactively (~6 gen/s)
- **File I/O** — save/load custom `.txt` format, load images (jpg/png/gif), export PNG
- **Session persistence** — auto-saves every 60s, restore on launch
- **Configurable** — TOML config for themes, palette, keybind overrides
- **Searchable help** — `?` for keybinding reference

## Installation

```sh
cargo install termdraw
```

## Usage

Run `termdraw` to launch the editor.

### convert image to txt/png file

```sh
cargo run --bin img2termdraw -- photo.jpg --width 80
```

Converts any image (jpg, png, gif, bmp) into termdraw's `.txt` format, resizing to fit the given width while preserving aspect ratio.

## Keybinds

| Key       | Action               |
| --------- | -------------------- |
| `q`       | Quit (saves session) |
| `?` / `/` | Toggle help          |

See the in-app help (`?`) for the full reference.

## Configuration

Config file at `~/.config/termdraw/config.toml`. A fully-commented default is generated on first run.

## License

MIT

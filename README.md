# Image Autocrop

A zero-dependency, single-file web app that crops PNG and WebP images to their content bounds on all 4 sides — no resolution change, no quality loss.

## How it works

The app uses the browser's Canvas API to scan every pixel and find the outermost non-transparent pixel on each edge (top, bottom, left, right). The image is then sliced to exactly those bounds and exported in the original format.

## Features

- Supports PNG and WebP
- Drag-and-drop or file picker, multiple files at once
- Side-by-side before/after preview with checkerboard transparency background
- Shows original and cropped dimensions plus crop offset
- Optional padding — keep N pixels of breathing room around the content
- Download preserves the original format (`_cropped.png` / `_cropped.webp`)
- Fully client-side — files never leave your device

## Usage

1. Open `index.html` in any modern browser (no server required)
2. Drop one or more `.png` or `.webp` files onto the drop zone, or click to browse
3. Optionally check **Add padding** and enter a pixel value
4. Click **Download** on any result to save the cropped file

## Limitations

- Crops by **transparency** (alpha = 0). Images with a solid opaque background (e.g. white) will not be trimmed since no transparent pixels exist.
- Processing is done on the main thread; very large images may cause a brief pause.
- WebP download relies on browser-level WebP canvas export support (all major browsers support this).

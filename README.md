[![CI](https://github.com/crimpdeq/book/actions/workflows/ci.yml/badge.svg)](https://github.com/crimpdeq/book/actions/workflows/ci.yml)
[![Documentation](https://img.shields.io/badge/Documentation-Book-orange.svg)](https://crimpdeq.github.io/book/)

# Crimpdeq Book

This repository contains the source of the ["Crimpdeq" book](https://crimpdeq.github.io/book/).

## Quickstart

This book is generated using `mdbook`. To install it:

```
cargo install mdbook
```

With `mdbook` installed, you can clone the repository and start a development server by running:
```
git clone https://github.com/crimpdeq/book
cd book/
mdbook serve
```

## Content

- Introduction: What is Crimpdeq?
- Making your own Crimpdeq
- How to calibrate your Crimpdeq
- Charging the Battery
- Firmware Details
- PCB Details

## Contributing
- Fixes and improvements are welcome. Please open an issue or submit a pull request.
- For small text changes, you can edit pages directly via the “Edit this page” link (when available) or by editing files under `src/` and running `mdbook serve` to preview.

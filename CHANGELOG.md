# Changelog

All notable changes to Servicepage are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Date Versioning](https://datevers.ing) since v26.10.23 (`YY.MM.DD`, the UTC release date, with `-1`, `-2`… for later releases the same day); earlier releases used [Semantic Versioning](https://semver.org/).

## v26.10.23-1

### Added

- Discord link previews: every page except the 404 page carries a `discord:component-embed` block in its `<head>`, in the Stux.Design pink (`#E71081`) with the Stux.Design icon. The home page says what this placeholder is and links to Stux.Design and all services; the changelog, the legal hub and the other pages get their own preview. The blocks are pre-built and committed by `python scripts/build-discord-embeds.py` (which `build-sitemap.py` now runs too), page text is escaped so it shows as plain text, a preview over Discord's 3,000-byte limit is left out, and the page title and description stay as the fallback
- A full favicon set generated from the Stux.Design icon: `favicon.ico` (16, 32 and 48px), `apple-touch-icon.png` (on a white background, so iOS doesn't fill it with black) and `site.webmanifest` with 192px, 512px and maskable 512px icons, linked from every page, the 404 page included
- `tests/site.sh`, which checks every Discord preview (valid JSON, under 3,000 bytes, none on the 404 page), the favicon files and sizes, the manifest, and the icon tags in every `<head>`; CI now runs it and `tests/version.sh`

## v26.10.23

### Added

- `tests/version.sh`, which checks that `VERSION.md` is a valid Date Version, a real calendar date not in the future, and the same as the newest entry in this changelog

### Changed

- Switched from Semantic Versioning to [Date Versioning](https://datevers.ing): releases are numbered by their UTC release date as `YY.MM.DD`, with `-1`, `-2`… for later releases the same day. This release follows v1.0.3
- `commit.sh` and `commit.bat` refuse a `VERSION.md` that isn't a valid Date Version or is dated in the future (UTC), and warn when it's dated before today
- `README.md` and `CONTRIBUTING.md` describe Date Versioning and the release steps

## v1.0.3

### Changed

- The favicon follows the browser's light or dark theme: the deep icon (`icon-dark.png`) on light and the bright one (`icon-light.png`) on dark, straight from the brand's media host, so a brand colour change is just a new file there
- The logos and icons in the Markdown docs (README and the like) follow GitHub's light or dark theme, using each brand's `logo-light`/`logo-dark` and `icon-light`/`icon-dark` files

## v1.0.2

### Changed

- The favicon follows the browser's light or dark theme: the deep icon (`icon-dark.png`) on light and the bright one (`icon-light.png`) on dark, straight from the brand's media host, so a brand colour change is just a new file there
- The logos and icons in the Markdown docs (README and the like) follow GitHub's light or dark theme, using each brand's `logo-light`/`logo-dark` and `icon-light`/`icon-dark` files

## v1.0.1

### Added

- The home page's footer has a copyright line ("© 2026 Stux.Design. All rights reserved."), like the legal pages, with the years kept current automatically

### Fixed

- The legal, changelog and sitemap footers name Stux.Design in the copyright line instead of Stux.Group, and no longer say Stux.Design is operated by Stux Group Ltd: that belongs on the Imprint only, which still says it

## v1.0.0

### Added

- The placeholder for a service that hasn't been set up yet for Stux.Design (servicepage.stux.design), built like the other Stux.Group page templates in Stux.Design magenta (`#e71081`), with light and dark themes
- The Stux.Design artboard: the page sits on a faint layout grid with rulers along the top and left edges, the headline's highlighted words get a selection box with handles and a "Blank artboard" tag, and the card has crop marks at its corners
- The Boring Legal Stuff hub with its six pages, a changelog page that renders `CHANGELOG.md`, a sitemap and a 404 page
- `dev-server.sh`/`.bat` that serve the site the way GitHub Pages does with DEV_MODE on (dev banner), and `--no-dev-mode` to see it as production does

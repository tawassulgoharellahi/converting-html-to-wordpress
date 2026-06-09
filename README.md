# HTML to WordPress Automation Tool

This repository contains a lightweight, automated utility that takes a static HTML webpage and converts it into a ready-to-use WordPress theme. It separates the HTML structure, updates asset links dynamically, injects core WordPress hooks, and outputs a convenient `.zip` bundle.

## Features

- **CSS Extraction**: Automatically extracts styles from inline `<style>` tags and bundles them into WordPress's standard `style.css`.
- **WordPress Hook Injection**: Places the mandatory `wp_head()` and `wp_footer()` calls case-insensitively at the appropriate locations in the markup.
- **Dynamic Asset Paths**: Rewrites asset references (e.g. `src` or `href` pointing to `assets/`) to utilize `get_template_directory_uri()`.
- **PHP File Structuring**: Splits the static template into proper WordPress template files:
  - `header.php`
  - `footer.php`
  - `front-page.php`
  - `functions.php`
  - `style.css`
- **Automatic Packaging**: Moves the assets, writes the PHP/CSS files, packages them into a `.zip` archive, and cleans up the working directory.

## Requirements

- Python 3.x

## Usage

Run the Python script with paths to your HTML file, your assets directory, and your desired theme name:

```bash
python html2wp.py --html <path_to_index.html> --assets <path_to_assets> --theme <theme_name>
```

### Arguments

- `--html`: (Required) Path to the input static HTML file (usually `index.html`).
- `--assets`: (Required) Path to the assets folder (containing images, css, scripts, etc.).
- `--theme`: (Optional) Slug/name of the generated theme (default: `custom-theme`).

## License

MIT

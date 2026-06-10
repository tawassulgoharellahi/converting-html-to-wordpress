# HTML to WordPress Automation Tool

This repository contains a lightweight, automated utility that takes static HTML webpages and converts them into a ready-to-use WordPress theme. It separates the HTML structure, updates asset links dynamically, injects core WordPress hooks, and outputs a convenient `.zip` bundle.

## Features

- **Multi-Page Page Templates**: Converts `index.html` into `front-page.php` and other HTML files into custom page templates (`template-[slug].php`) with standard WordPress headers so they can be assigned via the Page Settings sidebar.
- **Conditional Asset Enqueuing**: Scans each page's head and body, extracts page-specific scripts and styles, and registers and enqueues them dynamically inside `functions.php` using conditional tags like `is_page_template()`.
- **Dynamic Asset Paths**: Rewrites asset references (e.g. `src` or `href` pointing to `assets/` or `./assets/`, including `srcset` and inline `url()`) to utilize `get_template_directory_uri()`.
- **Automatic Webpack Chunk Path Patching**: Patches hardcoded paths in Webpack scripts (such as `runtime.bundle.js`) to dynamically map to the theme's active folder path.
- **Automatic Packaging**: Moves the assets, writes the PHP/CSS files, packages them into a `.zip` archive, and cleans up the working directory.

## Requirements

- Python 3.x

## Usage

### Single-Page Conversion Mode
Run the Python script with a path to your HTML file, your assets directory, and your desired theme name:

```bash
python3 html2wp.py --html <path_to_index.html> --assets <path_to_assets> --theme <theme_name>
```

### Multi-Page / Directory Conversion Mode
Run the Python script with a path to the folder containing your HTML files, your assets directory, and your desired theme name:

```bash
python3 html2wp.py --html-dir <path_to_templates_dir> --assets <path_to_assets> --theme <theme_name>
```

### Arguments

- `--html`: Path to the input static HTML file.
- `--html-dir`: Path to the directory containing multiple HTML files to convert.
- `--assets`: (Required) Path to the assets folder (containing images, css, scripts, etc.).
- `--theme`: (Optional) Slug/name of the generated theme (default: `custom-theme`).

## License

MIT

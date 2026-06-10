---
name: html-to-wp-automation
description: Automates the conversion of static HTML files into a WordPress theme ZIP package using a Python script.
---
# Converting HTML to WordPress

## Instructions
When the user asks to convert HTML to WordPress, follow these steps:

1. **Ask for inputs:** If not provided, ask the user for:
   - The path to their `index.html` file OR the path to their HTML templates directory.
   - The path to their `assets` directory.
   - The desired theme name (e.g., `my-theme`).

2. **Execute the Script:** Run the python script located in this skill directory using the user's inputs:

   *   **Single Page Conversion Mode:**
       ```bash
       python3 .agents/skills/converting-html-to-wordpress/html2wp.py --html <path_to_html> --assets <path_to_assets> --theme <theme_name>
       ```

   *   **Multi-Page / Directory Conversion Mode:**
       ```bash
       python3 .agents/skills/converting-html-to-wordpress/html2wp.py --html-dir <path_to_templates_dir> --assets <path_to_assets> --theme <theme_name>
       ```

## Features Handled Automatically
- **Multi-Page Page Templates**: Converts `index.html` to `front-page.php` and other HTML templates into specific WordPress custom page templates (`template-*.php`) automatically.
- **Conditional Styles and Scripts Enqueuing**: Scans `<head>` and `<body>` tags of each page to isolate page-specific styles and scripts, enqueuing them dynamically inside `functions.php` using conditional tags like `is_page_template()`.
- **Dynamic Link Remapping**: Automatically maps internal absolute links of the target domain to dynamic local home URLs using `home_url()`.
- **Webpack Output Patching**: Automatically replaces hardcoded paths in Webpack bundles (like `runtime.bundle.js`) to dynamically map to the theme's active folder path under `/wp-content/themes/`.
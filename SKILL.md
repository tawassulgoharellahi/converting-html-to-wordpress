---
name: html-to-wp-automation
description: Automates the conversion of static HTML files into a WordPress theme ZIP package using a Python script.
---
# Converting HTML to WordPress

## Instructions
When the user asks to convert HTML to WordPress, follow these steps:

1. **Ask for inputs:** If not provided, ask the user for:
   - The path to their `index.html` file.
   - The path to their `assets` directory.
   - The desired theme name (e.g., `my-theme`).
2. **Execute the Script:** Run the python script located in this skill directory using the user's inputs:
   ```bash
   python3 .agents/skills/converting-html-to-wordpress/html2wp.py --html <path_to_html> --assets <path_to_assets> --theme <theme_name>
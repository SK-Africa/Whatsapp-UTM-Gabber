### README for Plugin Build Automation

# SearchKings Africa UTM Grabber

**Plugin Name:** SearchKings Africa UTM Grabber  
**Description:** A plugin that dynamically updates an anchor tag link with UTM parameters from the current URL.  
**Version:** 1.1.1  
**Author:** SearchKings Africa  
**License:** MIT  

## Description

The SearchKings Africa UTM Grabber plugin dynamically updates an anchor tag link with UTM parameters from the current URL, ensuring that the parameters persist as users navigate through the site. This is particularly useful for tracking campaigns and maintaining consistent UTM tracking for analytics.

## Features

- Dynamically appends UTM parameters to a predefined URL.
- Stores UTM parameters in session storage to persist them across page navigations.
- Provides an option to show/hide a WhatsApp call-to-action button.
- Dynamically updates links with a specified class.

## Installation

1. **Upload the Plugin:**
   - Download the plugin ZIP file.
   - Navigate to `Plugins > Add New` in your WordPress admin dashboard.
   - Click `Upload Plugin` and select the downloaded ZIP file.
   - Click `Install Now` and then `Activate`.

2. **Manual Installation:**
   - Unzip the downloaded plugin file.
   - Upload the `sk-utm-grabber-plugin` directory to the `/wp-content/plugins/` directory.
   - Activate the plugin through the `Plugins` menu in WordPress.

## Usage

### Configuring the Plugin

1. **Navigate to Settings:**
   - Go to `Settings > SearchKings Africa UTM Grabber`.

2. **Configure the Base URL, Show Icon Option, and Link Class:**
   - Enter the base URL for the WhatsApp call-to-action link.
   - Check or uncheck the option to show the WhatsApp icon.
   - Enter the class name for links that should be dynamically updated with the UTM parameters. The default class is `sudonim-link`.

### Adding the WhatsApp Call-to-Action Button

1. **If "Show WhatsApp Icon" is enabled:**
   - Insert the shortcode `[ska_utm_grabber_anchor]` in any post, page, or widget where you want the WhatsApp button to appear.

### Example Shortcode Usage

```html
[ska_utm_grabber_anchor]
```

This shortcode will display the WhatsApp icon link with the configured URL and UTM parameters if the icon is enabled.

### Adding Dynamic Link Class

1. **Add the specified class to your links:**
   - Use the class specified in the settings (default: `sudonim-link`) for any links you want to be dynamically updated with the UTM parameters.

### Example Class Usage

```html
<a href="#" class="sudonim-link">Your Link Text</a>
```

All links with the specified class will be dynamically updated with the configured URL and UTM parameters.

## Changelog

### [1.0.1] - 2024-06-13
- Added option to show/hide WhatsApp icon.
- Added option to dynamically update links with a specified class.

### [1.0.0] - 2024-06-12
- Initial release

## Frequently Asked Questions

**Q1: How do I change the base URL for the WhatsApp link?**  
A1: Navigate to `Settings > SearchKings Africa UTM Grabber` and update the base URL in the provided field.

**Q2: How do I make the WhatsApp button appear on every page?**  
A2: Add the shortcode `[ska_utm_grabber_anchor]` to a template file that is included on all pages, such as `footer.php` or `header.php`.

**Q3: How do I dynamically update links with UTM parameters?**  
A3: Add the specified class (default: `sudonim-link`) to any links you want to be dynamically updated.

## License

This plugin is licensed under the MIT License. See the LICENSE file for more details.

## Support

For support and further information, please contact SearchKings Africa.

## Automation for Creating the Distributable ZIP File

To automate the process of creating a distributable ZIP file for your WordPress plugin, you can use the provided `build-plugin.sh` script. This script copies the plugin directory to a temporary location, removes unnecessary files, creates a ZIP file, and then cleans up.

### Steps to Use the Automation Script

1. **Ensure the Script is Executable**:
   Make the script executable by running the following command:
   ```sh
   chmod +x build-plugin.sh
   ```

2. **Run the Script**:
   Execute the script to create the ZIP file:
   ```sh
   ./build-plugin.sh
   ```

### build-plugin.sh Script

```sh
#!/bin/bash

# Variables
PLUGIN_DIR="sk-utm-grabber-plugin"
TEMP_DIR="${PLUGIN_DIR}-temp"
ZIP_FILE="${PLUGIN_DIR}.zip"

Continuing from where it left off:

```sh
# Step 1: Clean up any previous builds
echo "Cleaning up previous builds..."
rm -rf "$TEMP_DIR" "$ZIP_FILE"

# Step 2: Copy the plugin directory to a temporary location
echo "Copying plugin directory to temporary location..."
if [ -d "$PLUGIN_DIR" ]; then
    cp -r "$PLUGIN_DIR" "$TEMP_DIR"
else
    echo "Error: Directory $PLUGIN_DIR does not exist."
    exit 1
fi

# Step 3: Remove the .git folder from the temporary copy
echo "Removing .git folder..."
rm -rf "${TEMP_DIR}/.git"

# Step 4: Create a ZIP file from the temporary copy
echo "Creating ZIP file..."
if [ -d "$TEMP_DIR" ]; then
    zip -r "$ZIP_FILE" "$TEMP_DIR"
else
    echo "Error: Temporary directory $TEMP_DIR does not exist."
    exit 1
fi

# Step 5: Clean up the temporary copy
echo "Cleaning up temporary files..."
rm -rf "$TEMP_DIR"

echo "Build completed successfully. ZIP file created: $ZIP_FILE"
```

### Summary

By using the `build-plugin.sh` script, you can automate the process of creating a distributable ZIP file for your WordPress plugin. This script ensures that the `.git` folder is excluded without permanently deleting it.

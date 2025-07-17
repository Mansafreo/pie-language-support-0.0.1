# PIE Language VS Code Extension

This extension provides syntax highlighting for the PIE programming language.

## Setup Instructions

### Method 1: Development Setup (Recommended)

1. **Create the extension directory structure:**
   ```bash
   mkdir pie-language-support
   cd pie-language-support
   mkdir syntaxes
   mkdir icons
   ```

2. **Copy the files:**
   - Copy `package.json` to the root directory
   - Copy `language-configuration.json` to the root directory
   - Copy `pie.tmLanguage.json` to the `syntaxes/` directory
   - Copy `pie-light.svg` and `pie-dark.svg` to the `icons/` directory

3. **Install the extension locally:**
   ```bash
   # From the pie-language-support directory
   code --install-extension .
   ```

4. **Or use the Developer: Reload Window command:**
   - Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
   - Type "Developer: Reload Window"
   - Your extension should now be active

### Method 2: Manual Installation

1. **Find your VS Code extensions directory:**
   - **Windows:** `%USERPROFILE%\.vscode\extensions`
   - **macOS:** `~/.vscode/extensions`
   - **Linux:** `~/.vscode/extensions`

2. **Create the extension folder:**
   ```bash
   mkdir ~/.vscode/extensions/pie-language-support-0.0.1
   ```

3. **Copy all files to this directory with the correct structure:**
   ```
   pie-language-support-0.0.1/
   ├── package.json
   ├── language-configuration.json
   ├── syntaxes/
   │   └── pie.tmLanguage.json
   └── icons/
       ├── pie-light.svg
       └── pie-dark.svg
   ```

4. **Restart VS Code**

## Testing the Extension

1. Create a new file with the `.pie` extension
2. Copy this sample code:

```pie
string prompt = "Enter a number";
output(prompt, string);
int num;
input(num, int); // store the first number

prompt = "Enter the second number";
output(prompt, string);
int num2;
input(num2, int);

int sum = num + num2;

string msg = "The sum is ";
output(msg, string);
output(sum, int);

if (sum > 10) {
    output("Large sum!", string);
} else {
    output("Small sum", string);
}

for (int i = 0; i < 5; i++) {
    output(i, int);
}
```

You should see:
- **Keywords** (`string`, `int`, `if`, `else`, `for`) highlighted in blue
- **System functions** (`input`, `output`) highlighted in yellow
- **String literals** highlighted in green
- **Numbers** highlighted in light blue
- **Comments** highlighted in gray/green
- **Operators** highlighted appropriately

## Features

- **Syntax Highlighting** for PIE language constructs
- **Auto-closing** brackets, parentheses, and quotes
- **Comment toggling** with `Ctrl+/` (line comments) and `Ctrl+Shift+A` (block comments)
- **Bracket matching** and **indentation** support

## Customization

To modify the highlighting colors, you can:

1. **Use a different color theme** in VS Code
2. **Customize token colors** in your `settings.json`:

```json
{
  "editor.tokenColorCustomizations": {
    "textMateRules": [
      {
        "scope": "storage.type.pie",
        "settings": {
          "foreground": "#FF6B6B"
        }
      },
      {
        "scope": "support.function.builtin.pie",
        "settings": {
          "foreground": "#4ECDC4"
        }
      }
    ]
  }
}
```

## Publishing (Optional)

To publish this extension to the VS Code Marketplace:

1. **Install vsce:**
   ```bash
   npm install -g vsce
   ```

2. **Package the extension:**
   ```bash
   vsce package
   ```

3. **Install the generated .vsix file:**
   ```bash
   code --install-extension pie-language-support-0.0.1.vsix
   ```

## Troubleshooting

- **Extension not loading:** Check that all files are in the correct directories
- **Syntax highlighting not working:** Ensure the file has a `.pie` extension
- **Colors look wrong:** Try a different color theme or customize token colors

## File Structure

```
pie-language-support/
├── package.json                 # Extension manifest
├── language-configuration.json  # Language settings
├── syntaxes/
│   └── pie.tmLanguage.json     # Syntax highlighting rules
├── icons/
│   ├── pie-light.svg           # Light theme icon
│   └── pie-dark.svg            # Dark theme icon
└── README.md                   # This file
```
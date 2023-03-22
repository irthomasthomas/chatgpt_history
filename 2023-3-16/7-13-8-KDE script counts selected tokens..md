## USER
Create a script for KDE's context menu that counts tokens of selected text in any application window.

## ASSISTANT
To create a script for KDE's context menu that counts tokens (words) of selected text in any application window, you can use a Python script and the 'klipper' tool that comes with KDE. Here is a step-by-step guide to create the script and integrate it into the KDE context menu:

1. First, create a new Python script file called `count_tokens.py` with the following content:

```python
#!/usr/bin/env python3

import sys
import pyperclip

def count_tokens(text):
    tokens = text.split()
    return len(tokens)

if __name__ == "__main__":
    selected_text = pyperclip.paste()
    token_count = count_tokens(selected_text)
    pyperclip.copy(str(token_count))
    sys.exit(0)
```

This script uses the `pyperclip` library to interact with the clipboard. If you don't have the `pyperclip` library installed, you can install it with:

```bash
pip install pyperclip
```

2. Make the script executable by running the following command:

```bash
chmod +x count_tokens.py
```

3. Create a new file called `count_tokens.desktop` in the `~/.local/share/kservices5/ServiceMenus/` directory. If the directory does not exist, create it:

```bash
mkdir -p ~/.local/share/kservices5/ServiceMenus/
```

4. Add the following content to the `count_tokens.desktop` file:

```
[Desktop Entry]
Type=Service
ServiceTypes=KonqPopupMenu/Plugin
MimeType=text/plain;
Actions=CountTokens;
X-KDE-Priority=TopLevel
Icon=accessories-text-editor

[Desktop Action CountTokens]
Name=Count Tokens
Icon=accessories-text-editor
Exec=python3 /path/to/your/count_tokens.py
```

Replace `/path/to/your/count_tokens.py` with the actual path to your `count_tokens.py` script.

5. Restart the KDE Plasma shell for the changes to take effect:

```bash
killall plasmashell; kstart5 plasmashell
```

Now, when you right-click on any selected text in a KDE application window, you should see a "Count Tokens" option in the context menu. Clicking on it will count the tokens in the selected text and copy the result to your clipboard.
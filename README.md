# Hungarian Windows Keyboard for macOS

- [1. Summary](#1-summary)
- [2. Files](#2-files)
- [3. Requirements](#3-requirements)
- [4. Installation](#4-installation)
  - [4.1. Keyboard layout](#41-keyboard-layout)
  - [4.2. Karabiner rules](#42-karabiner-rules)
  - [4.3. Function keys (F1–F12)](#43-function-keys-f1f12)
  - [4.4. VS Code settings](#44-vs-code-settings)
- [5. Notes](#5-notes)

## 1. Summary

Use a standard Hungarian Windows (PC) keyboard on a Mac with the familiar Windows layout and shortcuts.

## 2. Files

- `hu-windows.keylayout`: the Hungarian Windows keyboard layout for macOS, including AltGr characters and dead keys.
- `karabiner-rules.json`: Karabiner-Elements rules for the external keyboard.
  - Ctrl acts as Command, so Ctrl+C / Ctrl+V and other shortcuts work as on Windows.
  - Win acts as Control.
  - Home, End and Ctrl+arrow keys work Windows-style.

## 3. Requirements

- [Karabiner-Elements](https://karabiner-elements.pqrs.org/), a free download, needed only for the shortcut rules

## 4. Installation

### 4.1. Keyboard layout

1. Copy `hu-windows.keylayout` to `/Library/Keyboard Layouts/`.
2. Log out and log back in.
3. Open **System Settings → Keyboard → Text Input → Edit… → +** and add **CustomHuWinLayout**.

### 4.2. Karabiner rules

1. Install Karabiner-Elements and grant the permissions it asks for.
2. Copy `karabiner-rules.json` to `~/.config/karabiner/assets/complex_modifications/`.
3. In Karabiner-Elements, go to **Complex Modifications → Add predefined rule** and enable all four rules, rule 1 first.
4. Go to **Settings → Devices** and make sure **Modify events** is turned on for your external keyboard.
   - If several devices are listed, check that you enabled the right one.
   - Wireless receivers (for example Logitech Unifying or Bolt) are often off by default.
   - If this is off, none of the rules will work.
5. In the Karabiner-Elements settings, turn on the **Swap ISO layout-specific keys** option.
   - Without it, `0` and `í` are swapped on the external keyboard once Karabiner is active.

### 4.3. Function keys (F1–F12)

By default, Karabiner treats the external keyboard's F-keys like the MacBook's: F1 changes brightness, and you need fn to get F1. The Fn key on a Windows keyboard is handled inside the keyboard itself and sends nothing to the Mac, so it cannot be used as the Mac fn key. Instead, make the external F-keys work as plain F1–F12, as on Windows:

1. In Karabiner-Elements, open the **Function Keys** tab.
2. Set **Target device** to your external keyboard.
3. Map every key to itself: `f1` → `f1`, `f2` → `f2`, … `f12` → `f12`.

### 4.4. VS Code settings

**Find and replace (ctrl + h):**

*macOS* uses **cmd (ctrl) + h** to hide the app. Go to **System Settings → Keyboard → Keyboard Shortcuts… → App Shortcuts → +** and set:

- **Application:** Visual Studio Code
- **Menu Title:** `Hide Visual Studio Code` (must match exactly)
- **Keyboard Shortcut:** something unused, for example Ctrl+Option+Cmd+H

Open **Preferences: Open Keyboard Shortcuts (JSON)** in VS Code from the Command Palette (Ctrl+Shift+P) and add these entries for Windows-like behavior:

```json
[
  {
    "key": "cmd+h",
    "command": "editor.action.startFindReplaceAction",
    "when": "editorFocus || editorIsOpen"
  }
]
```

## 5. Notes

- If `0` and `í` are swapped on your keyboard, check the **Swap ISO…** option in Karabiner-Elements (step 5 above). While Karabiner is active, the macOS *Change Keyboard Type* setting has no effect on this.
- If you have to hold fn to get F1–F12 on the external keyboard, set up the Function Keys tab for that keyboard (section 4.3).
- The Karabiner rules only affect external keyboards. The built-in MacBook keyboard is not changed.

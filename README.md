# Hungarian Windows Keyboard for macOS

- [1. Summary](#1-summary)
- [2. Files](#2-files)
- [3. Requirements](#3-requirements)
- [4. Installation](#4-installation)
  - [4.1. Keyboard layout](#41-keyboard-layout)
  - [4.2. Karabiner rules](#42-karabiner-rules)
- [5. Notes](#5-notes)

## 1. Summary

Use a standard Hungarian Windows (PC) keyboard on a Mac with the familiar Windows layout and shortcuts.

## 2. Files

- `hu_windows.keylayout`: the Hungarian Windows keyboard layout for macOS, including AltGr characters and dead keys.
- `karabiner-hungarian-windows-keyboard.json`: Karabiner-Elements rules for the external keyboard.
  - Ctrl acts as Command, so Ctrl+C / Ctrl+V and other shortcuts work as on Windows.
  - Win acts as Control.
  - Home, End and Ctrl+arrow keys work Windows-style.

## 3. Requirements

- macOS
- [Karabiner-Elements](https://karabiner-elements.pqrs.org/), a free download, needed only for the shortcut rules

## 4. Installation

### 4.1. Keyboard layout

1. Copy `hu_windows.keylayout` to `/Library/Keyboard Layouts/`.
2. Log out and log back in.
3. Open **System Settings → Keyboard → Text Input → Edit… → +** and add **CustomHuWinLayout**.

### 4.2. Karabiner rules

1. Install Karabiner-Elements and grant the permissions it asks for.
2. Copy `karabiner-hungarian-windows-keyboard.json` to `~/.config/karabiner/assets/complex_modifications/`.
3. In Karabiner-Elements, go to **Complex Modifications → Add predefined rule** and enable all four rules, rule 1 first.
4. Go to **Settings → Devices** and make sure **Modify events** is turned on for your external keyboard.
   - If several devices are listed, check that you enabled the right one.
   - Wireless receivers (for example Logitech Unifying or Bolt) are often off by default.
   - If this is off, none of the rules will work.
5. In the Karabiner-Elements settings, turn on the **Swap IS layout-specific keys** option.

## 5. Notes

- If `0` and `í` are swapped on your keyboard, check the **Swap ISO…** option in Karabiner-Elements (step 5 above). While Karabiner is active, the macOS *Change Keyboard Type* setting has no effect on this.
- The Karabiner rules only affect external keyboards. The built-in MacBook keyboard is not changed.

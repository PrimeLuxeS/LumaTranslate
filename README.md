<div align="center">

<img src="assets/LumaTranslate-logo.png" width="136" alt="LumaTranslate Classic logo">

# LumaTranslate Classic

**Free Windows translator with configurable global shortcuts, text correction, and screen OCR.**

Windows 10/11 x64 · C# · WPF · .NET 10

[Русский](README.ru.md) · [Download the installer](https://github.com/PrimeLuxeS/LumaTranslate/releases/latest)

</div>

## What the application does

LumaTranslate translates text in its own window or directly from another Windows application. It can read a selection, open a popup, replace the selected text with a translation, translate the clipboard, read text aloud, recognize a screen region, and correct text typed in the wrong English/Russian keyboard layout.

Translation providers use internet connections. Keyboard-layout correction, the bundled Rekey models, Russian text preparation, and the built-in Windows OCR do not require a translation-service API key. The optional OCR.space service is different: it requires an API key and uploads the selected image.

## Capabilities

| Area | How it works |
| --- | --- |
| Translation | Input and output fields, source/target language selection, automatic source-language detection, provider switch and reverse translation |
| Selection popup | Translate highlighted text in another program without first opening the main translator window |
| Replace selection | Get the selected text, translate it, and paste the result back into the original editable field |
| Clipboard | Translate text already copied to the clipboard |
| Keyboard layout | EN ↔ RU physical-key conversion and optional intelligent Rekey correction |
| Russian typo correction | Spelling and conservative contextual corrections before translation |
| Mouse mode | Show a translation icon by the selection, translate immediately, or translate and speak |
| Screen OCR | Select a screen region; recognize locally with Windows OCR or use OCR.space |
| Speech | Read original or translated text using speech voices installed in Windows |
| Dictionary | Search English or Russian Wiktionary |
| History and favorites | Store translations, reopen previous results and bookmark useful entries |
| Interface | Light/dark theme, configurable popup appearance, status tray icon and optional desktop shortcut |

### Translation services

**Google, Bing, DeepL, Yandex, PROMT and MyMemory** are selectable in Settings → Services. You can enable only the providers you want, test each connection and allow automatic fallback if the preferred service fails. Translation requests are sent to external providers. Their availability, language coverage, request limits and accuracy can change independently of LumaTranslate.

The regular translation providers are accessed without asking the user to enter a personal provider API key. This is not a guarantee of uninterrupted service. In particular, MyMemory requires an explicitly selected source language in the implemented adapter instead of Auto-Detect.

### Correction before translation

Text preparation combines three separate mechanisms:

1. **Russian spelling and contextual rules.** The application can correct selected Russian misspellings and, when context supports it, confusing real-word typos such as “привит май друк” in a greeting.
2. **Rekey (offline).** Bundled English/Russian language models evaluate words entered in the wrong keyboard layout and attempt high-confidence correction before the translation request. You can also enable correction after typing a space inside the LumaTranslate editor.
3. **Direct EN ↔ RU layout conversion.** The dedicated layout hotkey maps physical keys for one word or a longer selection, including layout-dependent punctuation.

These are separate features; a raw keyboard-layout conversion is not the same as translating English into Russian. Automatic correction is heuristic and may leave ambiguous words untouched.

### Working with text outside LumaTranslate

The global keyboard handler can operate on selections in common Windows editors and some embedded application inputs. Selection retrieval uses Windows automation with a clipboard-copy fallback. When replacing text, the app attempts to return focus to the original field and preserve the clipboard.

Not every external application exposes its selection or accepts synthetic input. Other programs, their privileges and Windows hotkey conflicts may prevent capture or replacement. Add affected programs to Settings → Exclusions when needed; do not assume a shortcut will override every native app shortcut.

### Screen recognition (OCR)

- **Windows OCR:** local processing; depends on the OCR language packs installed in Windows.
- **OCR.space:** cloud recognition with an API key and selectable OCR engine (2 or 3).
- **Auto mode:** try OCR.space, then fall back to Windows OCR on a supported error.

After selecting a screen rectangle, LumaTranslate can insert recognized text into the main window, translate it automatically and optionally show the result in a popup. An OCR.space image is sent over HTTPS and is subject to the service's terms and usage limits. The OCR API key is protected using Windows DPAPI for the current Windows user.

## Default keyboard shortcuts

All shortcuts can be edited or disabled in **Settings → Hotkeys**. Their effective scope matters: *Global* works outside the main window when Windows allows it; *Main window* and *Popup* apply to their respective windows.

| Action | Default | Scope |
| --- | --- | --- |
| Translate selected text in a popup | `Ctrl+Q` | Global |
| Open dictionary for selection | `Ctrl+Shift+Q` | Global |
| Speak selection | `Ctrl+E` | Global |
| Translate clipboard | `Ctrl+Alt+T` | Global |
| Correct EN ↔ RU keyboard layout | `Ctrl+Alt+L` | Global |
| Translate and replace selection | `Ctrl+S` | Global |
| Capture screen region (OCR) | `Ctrl+Shift+O` | Global |
| Translate input | `Ctrl+Enter` | Main window |
| Clear input | `Ctrl+N` | Main window |
| Swap source and target languages | `Ctrl+I` | Main window |
| Open dictionary | `Ctrl+D` | Main window |
| Open history | `Ctrl+H` | Main window |
| Open virtual keyboard | `Ctrl+K` | Main window |
| Open settings | `Ctrl+Alt+S` | Main window |
| Speak source text | `Ctrl+Shift+E` | Main window |
| Speak translation | `Ctrl+Alt+E` | Main window |
| Copy popup translation | `Ctrl+Shift+C` | Popup |
| Speak popup translation | `Ctrl+Shift+E` | Popup |
| Close translation popup | `Escape` | Popup |

An additional option enables **double Ctrl** for translating selected text. The application checks for conflicting bindings. For example, `Ctrl+S` is also the standard Save command in many applications, so edit the binding or configure an exclusion if there is a conflict.

## All Settings sections

| Section | Available controls |
| --- | --- |
| **General** | Windows sign-in startup, interface font and size, typo correction, Rekey, preferred languages and translation history |
| **Hotkeys** | Enable global shortcuts, edit each binding, double Ctrl, and inspect hotkey diagnostics |
| **Internet** | Connection timeout; system, disabled, manual HTTP/HTTPS/SOCKS5, or autodetected proxy; proxy credentials |
| **Services** | Enable individual translation engines, test providers and configure fallback |
| **Languages** | Search the language catalog and choose which languages appear in the main window |
| **View** | Light/dark theme, window appearance, popup size/position, opacity, border, colors and popup action icons |
| **Exclusions** | Configure programs and window classes that should not receive the application's global operations |
| **Advanced** | Mouse selection behavior, tray actions, text formatting, Windows OCR/OCR.space and recognition options |
| **Update and uninstall** | Check the published GitHub version, change update-check preference, or run the Windows uninstaller |

Some advanced legacy-style controls are present in the interface without a fully implemented action (for example, “Translate GUI elements”). Their presence does not imply that the feature works.

## Installing and uninstalling

1. Open [GitHub Releases](https://github.com/PrimeLuxeS/LumaTranslate/releases/latest) and download **LumaTranslate-Setup.exe**.
2. Launch the graphical NSIS installer. Administrator approval may be requested by Windows.
3. Choose whether to create a desktop shortcut. The default installation directory is `C:\Program Files (x86)\LumaTranslate`.
4. Start the application from the Start menu or its shortcut. A tray icon is available while it runs.

The package includes the Windows x64 application and its bundled Rekey runtime/models. A separate .NET runtime installation is not necessary. Remove LumaTranslate through Windows Installed Apps/Programs and Features or the built-in Settings → Update and uninstall page.

Updates are checked against stable GitHub Releases; a downloaded installer is checked using SHA-256 before installation. **The application is currently unsigned**, so Windows SmartScreen may show a warning. Download from this repository's official release page.

## Files, privacy and limitations

- Settings, translation history and favorites are stored in `%LOCALAPPDATA%\LumaTranslate\classic-settings.json`; saved text depends on your preferences.
- The OCR.space API key is stored in protected form, using Windows DPAPI. Manual proxy credentials are included in the local settings file and should be protected as user data.
- Translation text is transmitted to the selected online provider. OCR.space receives the captured region only when its cloud mode is used.
- Windows OCR, layout mapping and local language models run on the PC. Text-to-speech uses installed Windows voices.
- Internet access is necessary for web translation and Wiktionary lookups. Installed languages, Windows permissions, service changes and app-specific input restrictions can affect individual features.

## Technology and distribution

The application is built with **C# / WPF / .NET 10**. It uses Windows hooks and UI Automation for shortcuts and selection handling, a native Rust bridge for offline Rekey correction, Windows OCR or OCR.space for recognition, and an NSIS installer. Installer releases contain an accompanying SHA-256 file.

This **public repository contains the downloadable installer and documentation**, not the development source. LumaTranslate is independent of QTranslate and the translation providers; it does not include original QTranslate binaries. Refer to the third-party notices included with the installed application for third-party licensing. Distributed under the [MIT License](LICENSE).

<div align="center">
<img src="assets/LumaTranslate-logo.png" width="128" alt="LumaTranslate Classic logo">
</div>

# LumaTranslate Classic

**Free desktop translator for Windows 10 and 11 (x64).**

[Русский](README.ru.md) · [Download latest release](https://github.com/PrimeLuxeS/LumaTranslate/releases/latest)

LumaTranslate is a standalone Windows translation application with a graphical installer, configurable global keyboard shortcuts, and on-screen text recognition.

## Features

- Translate selected text, clipboard contents, and text entered into the application.
- Edit global keyboard shortcuts and configure quick translation popups.
- Choose from Google, Bing, DeepL, Yandex, PROMT, and MyMemory translation backends (service availability can vary).
- Recognize text from screenshots using local Windows OCR or optional OCR.space.
- Customize themes, proxy settings, languages, and translation history.
- Check for newer releases and verify downloaded installers against SHA-256.

## Install

1. Open the [Releases page](https://github.com/PrimeLuxeS/LumaTranslate/releases).
2. Download **LumaTranslate-Setup.exe** from the latest stable release.
3. Run the graphical installer and, if desired, enable the desktop shortcut.

The application installs by default to `C:\Program Files (x86)\LumaTranslate`. Administrator confirmation (Windows UAC) is required. To uninstall, use **Windows Settings → Installed apps**, **Control Panel → Programs and Features**, or **Settings → Updates and uninstall → Uninstall application** inside LumaTranslate.

The installer is currently **unsigned**. Windows SmartScreen may show a reputation warning. Download only from the project's official GitHub Releases.

## Privacy

Settings and translation history are stored locally in `%LOCALAPPDATA%\LumaTranslate`. Local Windows OCR performs recognition on your device. Enabling OCR.space sends the selected image to that external service. Online translation requests are sent to the chosen translation provider.

## Downloads and source

This public repository is used for distribution. Release assets include the **Windows installer** and its **SHA-256 checksum**; the development source is maintained separately. No original QTranslate binaries are distributed.

LumaTranslate is an independent project and is not affiliated with QTranslate, Microsoft, or translation providers. Third-party components and trademarks belong to their owners.

Distributed under the [MIT License](LICENSE).

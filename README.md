# Termux-OS

**A menu-driven Termux optimization tool**: set up Zsh, Fish or Bash with custom prompts, install Nerd Fonts, switch color themes, tweak Termux behavior, and lock your shell, all from one script.

![Shell](https://img.shields.io/badge/shell-bash-green)
![Platform](https://img.shields.io/badge/platform-Termux%20(Android)-blue)
![License](https://img.shields.io/badge/license-MIT-yellow)
![Version](https://img.shields.io/badge/version-3.0-orange)

---

## Features

| Menu | What it does |
|------|--------------|
| **Necessary Setup** | Installs required packages, `lolcat`, the custom figlet font, and applies the default Termux config |
| **Zsh Customizer** | Oh My Zsh + `zsh-autosuggestions` + `zsh-syntax-highlighting`, custom theme, switch default shell |
| **Fish Customizer** | Fish config with a custom prompt, switch default shell |
| **Bash Customizer** | [ble.sh](https://github.com/akinomyoga/ble.sh) (Bash Line Editor) + custom prompt, switch default shell |
| **Termux Nerd Fonts** | Fira Code, JetBrains Mono, Hack, Caskaydia Cove, Sauce Code Pro, Ubuntu, Meslo |
| **Termux Color Themes** | Default (Gunmetal), Dracula, Nord, Monokai, Solarized Dark, Gruvbox, Tokyo Night, Catppuccin, Ayu Dark, Cobalt2, One Half Dark |
| **Termux Behavior Settings** | Cursor style and blink, extra keys row, bell, fullscreen, back key |
| **Security & Updates** | Password lock for your shell startup, and one-tap self-update via Git |

The script also checks for updates on launch (when the folder is a Git clone) and asks before pulling anything.

## Requirements

- Android with [Termux](https://github.com/termux/termux-app)
- Internet connection (for packages, plugins, fonts and updates)
- Packages installed automatically if missing: `zsh fish git figlet toilet ruby wget curl bat eza unzip xz-utils ca-certificates`

## Installation

```bash
pkg update -y && pkg install git -y
git clone https://github.com/pxxkashzz/Termux-os.git
cd Termux-os
bash os.sh
```

> Cloning with `git` (instead of downloading the zip) is recommended so the built-in updater works.

## Usage

Run the script and pick an option by number:

```bash
bash os.sh
```

```
[01] Necessary Setup
[02] Zsh Customizer
[03] Fish Customizer
[04] Bash Customizer
[05] Termux Nerd Fonts
[06] Termux Color Themes
[07] Termux Behavior Settings
[08] Security & Updates
[00] Exit Terminal
```

**Suggested first run:** `01` Necessary Setup, then your shell of choice (`02`, `03` or `04`), then a font (`05`) and a color theme (`06`). Restart Termux afterwards.

## Project Structure

```
Termux-os/
├── os.sh                 # Main script (menus + all logic)
└── .object/
    ├── .1bashrc, .1zshrc, .1fishrc, .2zshrc, .2fishrc   # Shell config templates
    ├── .h4Ck3r.zsh-theme                                # Custom Zsh theme
    ├── .termux.properties                               # Default Termux behavior
    ├── .colors.properties, .colors_<theme>.properties   # Color themes
    └── ANSI Shadow.flf                                  # Figlet banner font
```

## Files Modified on Your Device

Use the script knowing it writes to these locations:

- `~/.termux/termux.properties`, `~/.termux/colors.properties`, `~/.termux/font.ttf`
- `~/.bashrc`, `~/.zshrc`, `~/.config/fish/config.fish`
- `~/.oh-my-zsh/`, `~/.local/share/blesh/`
- `$PREFIX/share/figlet/ASCII-Shadow.flf`

Back up your existing shell config files before running the setup options if you want to keep them.

## Security Lock: Please Read

The "Cyber Lock" adds a password prompt to the top of your shell startup files. It is a **convenience lock only**, not real security:

- It only runs when a shell starts and can be bypassed by anyone with access to your files, or by running a different shell.
- The password is stored as an unsalted SHA-256 hash inside your rc files.

Use it to deter casual snooping, not to protect sensitive data. To remove it, use **Security & Updates → Remove Lock**.

## Updating

From the menu: **08 Security & Updates → 03 Update Script**, or manually:

```bash
cd Termux-os && git pull
```

## Contributing

Issues and pull requests are welcome. For larger changes, please open an issue first to discuss what you would like to change.

## Credits

- **Author:** Pxxkashzz (Hacrrr)
- [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh), [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions), [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
- [ble.sh](https://github.com/akinomyoga/ble.sh)
- [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)
- Color schemes are inspired by Dracula, Nord, Monokai, Solarized, Gruvbox, Tokyo Night, Catppuccin, Ayu, Cobalt2 and One Half.
- The bundled `ANSI Shadow.flf` figlet font belongs to its original author(s) and is not covered by this project's license.

## Contact

- GitHub: [github.com/pxxkashzz](https://github.com/pxxkashzz)
- Instagram: [instagram.com/_itz_pxxkashzzz_](https://instagram.com/_itz_pxxkashzzz_)

## License

Released under the [MIT License](LICENSE).

## Disclaimer

This tool modifies your shell configuration and Termux settings. It is provided as is, without warranty. Use it at your own risk.

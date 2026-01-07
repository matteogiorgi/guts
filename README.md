# GUI UNIX Tools System &nbsp;<a href="https://www.debian.org"><img src="https://www.debian.org/logos/officiallogo-nd.svg" style="height: 1em; vertical-align: top;"></a>

This repository contains configuration files and installation scripts for a quick and ready to coding work environment, based on any *Debian* or *Debian-based* distribution.

For a more hardcore all-tui setup, take a look at [PUTS](https://github.com/matteogiorgi/puts/), it may sting a bit but you might like it.




## Install

The only prerequisite you need to cover is a working *Debian* in any version or form. There is just one installer at your disposal (for now 😎): [`guts_code`](https://github.com/matteogiorgi/guts/blob/main/guts_code).

> The installer do not symlink any file, it just copy the configurations in the right place, so they can be easily modified end eventually resetted running the installer again.

To full install GUTS, run the [`install`](https://github.com/matteogiorgi/guts/blob/main/install) script, it will execute the installer for you.




### Code

This script installs all the basic packages you need and resets your *VSCode* configuration, plus few extensions to make it as loose as a goose and ready to roll in no time. Run `./guts_code` any time you want from the root of the repository to clean *VSCode* for good.

> You need to install *VSCode* yourself, check the [official website](https://code.visualstudio.com) for the deb package.




## No-Install

If you don't want to run any installer, you can just copy the main configuration files with the following command and you got yourself just the *VSCode* dotfiles. Copy-pasta this in your terminal and hit enter 😜
```sh
sh -c '
    BASE="https://raw.githubusercontent.com/matteogiorgi/guts/refs/heads/main/code"
    VSCODE_DIR="$HOME/.config/Code/User"
    FILES="settings.json keybindings.json"
    command -v wget >/dev/null 2>&1 || { echo "ERROR: install wget"; exit 1; }
    mkdir -p "$VSCODE_DIR"
    for FILE in $FILES; do
        [ -f "$VSCODE_DIR/$FILE" ] && cp "$VSCODE_DIR/$FILE" "$VSCODE_DIR/$FILE.bak"
        wget -qO "$VSCODE_DIR/$FILE" "$BASE/$FILE" && echo "$FILE copied"
    done
    echo "finish"
'
```

# gdm-ctrl-alt-to-altGr
> a very simple hack to type '{', '[', ']', '}', '\'. '~'. and 'µ' with ctrl+alt instead of altGr

**NOTE:** Using AutoKey & XBinKeys did not work on my newest Gnome desktop using Wayland. But `xremap` works.

I programm with a german keymap (qwertz) and I havent found an easy way to use the combination <kbd>ctrl</kbd>+<kbd>alt</kbd>+<kbd>7</kbd> instead of <kbd>altGr</kbd>+<kbd>7</kbd> to type <kbd>{</kbd>. People told me to just use the altGr -Combo, but this is unusable for everyone who types with all ten fingers...

## xremap
### Requirements
 - Rust / Cargo
 - [xremap](https://github.com/k0kubun/xremap)

### Installation (on Fedora 39)

#### xremap:

Install xremap using cargo: 

```bash
cargo install xremap --features 
```

Setup sudo-less usage:

```bash
# check if uinput is installed
lsmod | grep uinput
```
```bash
# add access permissions for uinput / evdev
sudo gpasswd -a $USER input
echo 'KERNEL=="uinput", GROUP="input", TAG+="uaccess"' | sudo tee /etc/udev/rules.d/input.rules
```

Install [gnome extension](https://extensions.gnome.org/extension/5060/xremap).

Reboot.

#### Add configuration file

Add the configuration yml `$HOME/.config/xremap.yml`:

```yml
keymap:
  - name: Global
    remap:
      C-M-7: Alt_R-7
      C-M-8: Alt_R-8
      C-M-9: Alt_R-9
      C-M-0: Alt_R-0
      C-M-MINUS: Alt_R-MINUS
      C-M-RIGHTBRACE: Alt_R-RIGHTBRACE
      C-M-M: Alt_R-M
```

#### Autostart

Add an desktop entry file to `$HOME/.config/autostart/xremap.desktop`:

```desktop
[Desktop Entry]
Name=xremap
Type=Application
TryExec=<path to xremap>
Exec=<path to xremap> <path to .yml-config>
```



## Autokey
### Requirements
 - **autokey-common**
 - **autokey-gtk**

### Installation
Import the scripts in Autokey and set the corresponding Hotkeys for each file.

for example `C-A-0.py`:
```python
# Enter script code
keyboard.send_keys("<alt_gr>+0")
```
Set the *Hotkey* to `0` and check the modifiers *Alt* and *Ctrl*.

Just do this for all the scripts and set AutoKey to start at login. 

### Issues
I have noticed that this setup crashes Jetbrains IDEs when typing those characters in the editor.
To fix that, you have to disable all Keybinds that normally use <Kbd>Ctrl+Alt+?</Kbd>. (To do this easily,
stop AutoKey and then use the "Key-Search"-Functionality in the Keymap Settings to find all conflicts)

## XBindKeys
So here is my barely working hack-solution (mostly so that I don't forget it again...)

### Requirements
you have to install
 - **xbindkeys**
 - **xdotool**

(previously I used **xvkbd** but it broke somehow?)

### Installation
 - put the `.xbindkeysrc` in `$HOME/.xbindkeysrc`
 - run `xbindkeys` on startup



## Problems with this "Solution"
I have to put a `sleep 0.1` before all the commands, otherwise it won't work. This means that there is a delay whilst typing. Unfortunatly I haven't found a workaround. If you know something, please contact me.


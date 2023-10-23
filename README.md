# gdm-ctrl-alt-to-altGr
> a very simple hack to type '{', '[', ']', '}', '\'. '~'. and 'µ' with ctrl+alt instead of altGr

**NOTE:** I recently found better way than the `xbindkeys`-hack. Using *autokey*, I get a way smoother experience. Do yourself this favour and use it too.

I programm with a german keymap (qwertz) and I havent found an easy way to use the combination <kbd>ctrl</kbd>+<kbd>alt</kbd>+<kbd>7</kbd> instead of <kbd>altGr</kbd>+<kbd>7</kbd> to type <kbd>{</kbd>. People told me to just use the altGr -Combo, but this is unusable for everyone who types with all ten fingers...

## Autokey Hack
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
To fix that, you have to disable all Keybinds that normally use <Kbd>Ctrl+Alt</Kbd>. (To do this easily,
stop AutoKey and then use the "Key-Search"-Functionality in the Keymap Settings to find all conflicts)

## XBindKeys Hack
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


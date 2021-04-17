# gdm-ctrl-alt-to-altGr
> a very simple hack to type '{', '[', ']', '}', '\'. '~'. and 'µ' with ctrl+alt instead of altGr

I programm with a german keymap (qwertz) and I havent found an easy way to use the combination <kbd>ctrl</kbd>+<kbd>alt</kbd>+<kbd>7</kbd> instead of <kbd>altGr</kbd>+<kbd>7</kbd> to type <kbd>{</kbd>. People told me to just use the altGr -Combo, but this is unusable for everyone who types with all ten fingers...

So here is my barely working hack-solution (mostly so that I don't forget it again...)

## Requirements
you have to install
 - **xbindkeys**
 - **xdotool**

(previously I used **xvkbd** but it broke somehow?)

## Installation
 - put the `.xbindkeysrc` in `$HOME/.xbindkeysrc`
 - run `xbindkeys` on startup

###

## Problems with this "Solution"
I have to put a `sleep 0.1` before all the commands, otherwise it won't work. This means that there is a delay whilst typing. Unfortunatly I haven't found a workaround. If you know something, please contact me.


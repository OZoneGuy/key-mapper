# Table of Contents

1.  [Usage](#orgc5ef459)
    1.  [Create Configuration](#org8d51c8d)
2.  [Installation](#org5a76b68)
    1.  [Arch Linux](#org625af2e)
    2.  [Git](#orgf4beb5a)
3.  [Future features](#orgd622066)

A program that runs in the background to provide a different way to execute shortcuts. This program utilises key press sequences, following a master key bind, to execute different shell commands. This is meant for shortcuts and not key binds, such as volume up.


<a id="orgc5ef459"></a>

# Usage


<a id="org8d51c8d"></a>

## Create Configuration

Create the a config file, default location `$XDG_CONFIG_HOME/shortcut-mapper/key-map` or `$HOME/.config/shortcut-mapper/key-map` if `$XDG_CONFIG_HOME` is not set. An example config file is provided in `/usr/share/shortcut-mapper/key-map`, or checkout `template/key-map`. It is copied to the config file location of no file is found.

The file must contain a `Master` key binding. This key binding must be pressed before the program starts listening to key strings. Must be in a separate line. Key modifiers, like <kbd> Ctrl </kbd>, can be used. The list of currently supported key modifiers are as follows:

-   `C`: <kbd> Ctrl </kbd>
-   `M`: <kbd> Alt </kbd>
-   `S`: <kbd> Super </kbd>

The format for the `Master` key bind is as such: \((Mod-)^{*}^{}^{}Key\). Where \(Mod\) is any modifier specified above and key is any single character key. An example would be `C-S-k` which is `Control+Super+k` which is the default in case it failed to recognise a master key bind.

Here you can also create key strings. The format of which is as such: \((key)^{+}^{}\ cmd\) where \(key\) is any single character key and \(cmd\) is the command to be executed. The key string has to be at least one character long and the command is any shell command.

Conflicting key string will be reported in the system log. Only the first conflicting key string will be registered.


<a id="org5a76b68"></a>

# Installation


<a id="org625af2e"></a>

## Arch Linux

Install `shortcut-mapper-git` from AUR


<a id="orgf4beb5a"></a>

## Git

1.  Clone this repo, `git clone ... DIR`
2.  `cd` into the directory
3.  Run `cmake . -B BUILD-DIR`
4.  Run `cmake --build BUILD-DIR`
5.  Run `cmake --install BUILD-DIR` with sudo privileges


<a id="orgd622066"></a>

# Future features

-   [ ] Show a dialogue box when activated

    To show the current shortcut string

-   [ ] Support input masks for shortcut strings

    Masks like <kbd> Ctrl </kbd> or <kbd> Alt </kbd>.

-   [ ] Support using shift

-   [ ] Terminate when loading key map if the `Master` key bind is unavailable

-   [ ] Log to system log and to a file in `/var/log`

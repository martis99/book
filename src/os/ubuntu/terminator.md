# Terminator

To install `Terminator` app run `sudo apt install terminator`

To create custom terminator layout: `Right click in terminal background -> Preferences -> Layouts -> Add`

Or if more control is needed edit `~/.config/terminator/config` file

Example of `config` file
```
[global_config]
  case_sensitive = False
[keybindings]
[profiles]
  [[default]]
    cursor_color = "#aaaaaa"
    foreground_color = "#ffffff"
    show_titlebar = False
    scrollback_infinite = True
[layouts]
  [[default]]
    [[[child0]]]
      type = Window
      parent = ""
      order = 0
      maximised = False
      fullscreen = False
    [[[terminal1]]]
      type = Terminal
      parent = child0
      order = 0
      profile = default
[plugins]
```

To add new layout add new entry in `[layouts]` with name of your layout `[[<name>]]`

Example of 4 windows terminal layout
```
  [[four]]
    [[[child0]]]
      type = Window
      parent = ""
      order = 0
      maximised = True
      fullscreen = False
    [[[child1]]]
      type = HPaned
      parent = child0
      order = 0
      position = 922
    [[[child2]]]
      type = VPaned
      parent = child1
      order = 0
      position = 519
    [[[terminal3]]]
      type = Terminal
      parent = child2
      order = 0
      profile = default
    [[[terminal4]]]
      type = Terminal
      parent = child2
      order = 1
      profile = default
    [[[child5]]]
      type = VPaned
      parent = child1
      order = 1
      position = 521
    [[[terminal6]]]
      type = Terminal
      parent = child5
      order = 0
      profile = default
    [[[terminal7]]]
      type = Terminal
      parent = child5
      order = 1
      profile = default
```

To start terminal with custom layout run `terminator -l <name>`

To add terminator to Favorites with your custom layout add `.desktop` file in `~/.local/share/applications/`

Example of `.desktop` file
```
[Desktop Entry]
Name=Terminator
Comment=Multiple terminals in one window
Exec=terminator -l <name>
Icon=terminator
Type=Application
Categories=GNOME;GTK;Utility;TerminalEmulator;System;
StartupNotify=true
X-Ubuntu-Gettext-Domain=terminator
X-Ayatana-Desktop-Shortcuts=NewWindow;
Keywords=terminal;shell;prompt;command;commandline;
[NewWindow Shortcut Group]
Name=Open a New Window
Exec=terminator
TargetEnvironment=Unity
```

# Add to Favorites

To add App to Favorites create `.desktop` file in `~/.local/share/applications/`.

Example of `.desktop` file
```
[Desktop Entry]
Name=Terminator
Comment=Multiple terminals in one window
Exec=terminator
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

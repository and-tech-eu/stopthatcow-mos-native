# mos-native

Installer script to download, build and install all dependencies needed for [mos tool](https://github.com/mongoose-os/mos) to build Mongoose OS apps for ESP32 without docker. Docker on Mac is painfully slow and builds can take many minutes this approach lets us build naitively on OS X.

## install
```bash
$ git clone https://github.com/stopthatcow/mos-native.git
$ cd mos-native
$ ./install.sh
```
The installer downloads the esp-idf to the current directory and installs the compiler to `~/.espressif/`.
Because the IDF uses its own virtual environment for python that we don't want to keep activated all the time, we generate a helper script to activate this environment before invoking `mos`.
The helper script is generated by the installer and is called `mos_build_local.sh`.

To build your firmware, use the generated shell script `mos_build_local.sh`
```bash
mos_build_local.sh --platform esp32
```

You will likely want to move/symlink this file somewhere on your path or add an alias in your .bashrc/.zshrc file.
e.g.
```bash
alias mos_build_local=</PATH/TO>/mos-native/mos_build_local.sh
```

## uninstall
```bash
$ ./uninstall.sh
```

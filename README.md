# Unikey (Vietnamese Input Method) engine support for Fcitx

Released under GPLv3+

# Dependencies
```
sudo apt install libfcitx5-qt-dev fcitx5-modules-dev extra-cmake-modules fcitx5 fcitx5-frontend-*
```

# Install
```sh
cmake -DCMAKE_INSTALL_PREFIX=/usr/ .
make
sudo make install
```

# Viber fix
Fcitx/Fcitx5 for Viber AppImage
```
./viber.AppImage --appimage-extract
cp /usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libfcitx5platforminputcontextplugin.so squashfs-root/plugins/platforminputcontexts
# Download appimagetool from https://github.com/AppImage/AppImageKit/releases
appimagetool squashfs-root/ viber.AppImage
```

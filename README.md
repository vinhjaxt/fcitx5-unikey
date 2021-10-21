# Fcitx5 Unikey
Vietnamese Input Method engine support for Fcitx5

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
# https://docs.appimage.org/packaging-guide/manual.html

sudo apt install -y patchelf chrpath

./viber.AppImage --appimage-extract
cp /usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libfcitxplatforminputcontextplugin.so ./squashfs-root/plugins/platforminputcontexts

patchelf --set-rpath '$ORIGIN/../../lib' ./squashfs-root/plugins/platforminputcontexts/libfcitxplatforminputcontextplugin.so
# chrpath -r '$ORIGIN/../../lib' ./squashfs-root/plugins/platforminputcontexts/libfcitxplatforminputcontextplugin.so
chmod +x ./squashfs-root/plugins/platforminputcontexts/*

objdump -x ./squashfs-root/plugins/platforminputcontexts/libfcitxplatforminputcontextplugin.so
readelf -d ./squashfs-root/plugins/platforminputcontexts/libfcitxplatforminputcontextplugin.so
# chrpath -l ./squashfs-root/plugins/platforminputcontexts/libfcitxplatforminputcontextplugin.so

# Download appimagetool from https://github.com/AppImage/AppImageKit/releases

appimagetool squashfs-root/ viber.AppImage
```

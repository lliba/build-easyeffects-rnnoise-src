# build-easyeffects-rnnoise-src
Build easyeffects with rnnoise from source on Debian 12.2 Bookworm with the Gnome DE.

There's probably some better packages or a nicer meta-package for this but this is my command history cleaned up while trying to build easyeffects 7.0.1 (highest version that didn't require gtk =>4.10, and librust-gtk4-dev is 4.8) with rnnoise.

# Build rnnoise
```
cd /tmp
git clone https://gitlab.xiph.org/xiph/rnnoise.git
cd rnnoise
sudo apt install build-essential binutils make csh g++ sed gawk autoconf automake autotools-dev libtool
./autogen.sh
./configure
sudo make install
```
# Build easyeffects
```
cd /tmp
git clone https://github.com/wwmm/easyeffects.git
cd easyeffects
git checkout v7.0.1
sudo apt install meson gettext libglib2.0-0 libglib2.0-dev itstool ladspa-sdk libzita-convolver-dev libtbb-dev libpipewire-0.3-dev librust-gtk4-dev libportal-gtk4-dev appstream-util speex libspeex-dev libadwaita-1-dev libsigc++-3.0-dev liblilv-dev libbs2b-dev libsndfile1-dev libebur128-dev libsamplerate0-dev librubberband-dev libspeexdsp-dev nlohmann-json3-dev libfmt-dev libgsl-dev
meson _build --prefix=/usr
sudo ninja -C _build install
```

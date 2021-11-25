# Crux install guide

- Supported Crux version: `3.6`
- Install steps may also work on other Crux versions

## Install/update kernel

Info: https://www.kernel.org/

Tested version: ---

### Dependencies

none

### Installation

```bash
# Switch to root user
sudo su

# Set kernel version
VERSION="5.10.81"

# Move to /usr/src dir
cd /usr/src

# Get kernel source
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-${VERSION}.tar.xz

# Extract kernel source
unxz linux-${VERSION}.tar.xz

# Untar kernel source
tar -xf linux-${VERSION}.tar

# Remove tar file and cd to new kernel source
rm linux-${VERSION}.tar && cd linux-${VERSION}

# Get old kernel config
zcat /proc/config.gz > .config

# If needed, edit kernel config
make menuconfig

# Build kernel
make all

# Build modules
make modules_install

# Copy new kernel and system.map
cp arch/x86/boot/bzImage /boot/vmlinuz-${VERSION}
cp System.map /boot

# Update grub
grub-mkconfig -o /boot/grub/grub.cfg
```

## Thunar

Info: https://docs.xfce.org/xfce/thunar/start

Tested version: `4.17.1`

### Dependencies:

#### intltool

Can be installed from ports `/usr/ports/opt`:

```bash
sudo prt-get depinst intltool
```

#### perl

<TODO>

#### GTK+

<TODO>

#### GLib

<TODO>

#### exo

<TODO>

#### libxfce4util

<TODO>

#### libxfce4ui

<TODO>

#### xfconf

<TODO>

## Polybar

<TODO>

## Urxvt

Info: http://software.schmorp.de/pkg/rxvt-unicode.html

Tested versions: 
- `9.26`
- `9.29`

### Dependencies

<TODO>

#### libptytty

##### Dependencies

```bash
sudo prt-get depinst cmake
```

##### Installation

```bash
wget http://dist.schmorp.de/libptytty/libptytty-2.0.tar.gz
tar -xzf libptytty-2.0.tar.gz && rm libptytty-2.0.tar.gz
cd libptytty-2.0
cmake -DCMAKE_INSTALL_PREFIX=/usr -DBUILD_SHARED_LIBS=ON .
cmake --build .
sudo cmake --install .
```

### Installation

```bash
wget http://dist.schmorp.de/rxvt-unicode/rxvt-unicode-9.29.tar.bz2
tar -xvjf rxvt-unicode-9.29.tar.bz2 && rm rxvt-unicode-9.29.tar.bz2
cd rxvt-unicode-9.29
./configure --prefix=/usr --enable-everything --enable-256-color --enable-text-blink --enable-fading --enable-font-styles --enable-pixbuf --enable-iso14755 --enable-mousewheel --enable-perl --enable-unicode3 --enable-xft
make
sudo make install
```

## obconf

<TODO>

## lxappearance

<TODO>

## Discord

<TODO>

## mtPaint

<TODO>

## MenuMaker

<TODO>

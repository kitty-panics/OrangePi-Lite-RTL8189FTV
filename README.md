# OrangePi-Lite-RTL8189FTV

适用于 Orange Pi Lite 的 Wi-Fi 驱动 (RTL8189FTV)。

## 使用

有两种方法可完成安装与使用。

### 通过包管理器安装

对于一切系统文件，应尽可能使用包管理器进行管理。因此本仓库提供了适用于 Arch Linux ARM
的驱动包 (其它发行版请自行打包)。

1. 下载对应版本的驱动包
    - [5.17.1-1]
    - [5.17.0-1]
    - [5.16.5-1]
2. 安装驱动包
    - `pacman -U 8189fs-git-内核版本号-armv7h.pkg.tar.xz`

[5.17.1-1]: binary/5.17.1-1/8189fs-git-5.17.1-1-armv7h.pkg.tar.xz
[5.17.0-1]: binary/5.17.0-1/8189fs-git-5.17.0-1-armv7h.pkg.tar.xz
[5.16.5-1]: binary/5.16.5-1/8189fs-git-5.16.5-1-armv7h.pkg.tar.xz

**注：**

鉴于每次升级内核后得重新编译一次驱动，为方便管理和识别旧驱动，软件包的版本号将与 linux-armv7
内核包的版本号同步。

### 通过源码编译安装

如果想更细粒度定制驱动，可通过编译进行安装。

1. `git clone --depth=1 --recurse-submodules git@github.com:kitty-panics/OrangePi-Lite-RTL8189FTV.git`
2. `cd OrangePi-Lite-RTL8189FTV/source/rtl8189ES_linux`
3. `git checkout rtl8189fs`
4. 根据自己的需求修改代码
5. `make ARCH=arm KSRC="/usr/lib/modules/$(uname -r)/build/"`
6. `gzip -9 8189fs.ko`

**注：**

编译需安装 **linux-armv7-headers** 软件包。

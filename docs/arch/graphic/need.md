# 安装其他程序

要构成一个好用的桌面系统，除了之前安装的工具外，还需要字体、终端模拟器、系统状态栏等诸多工具

## 字体

可以直接使用 pacman 包管理器安装的英文字体推荐 Source Code Pro Fonts 中文字体推荐文泉驿雅黑字体

```shell
sudo pacman -S adobe-source-code-pro-fonts wqy-microhei
```

同时推荐需要手动安装的符号字体 Nerd 字体，Nerd 中包括了 Font Awesome

手动下载字体依赖 Xorg 中的字体工具，手动下载操作如下

```shell
# 下载字体包
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/SourceCodePro.zip
# 解压字体包到一定路径并复制到系统字体路径
unzip SourceCodePro.zip -d /path/to/font
sudo cp -r /path/to/font /usr/share/fonts
# 刷新字体缓存
fc-cache -vf
```

## 终端模拟器 Alacritty

直接使用 pacman 包管理器安装 Alacritty

```shell
sudo pacman -S alacritty
```

## 软件启动器 dmenu

dmenu 的下载方式有源码编译和 pacman 包管理器两种，为了方便管理此处使用 pacman 进行下载

```shell
sudo pacman -S dmenu
```


## 系统状态栏 Polybar

Polybar 需要使用 AUR 下载，操作如下

```shell
yay -S polybar
```

## 显示合成器 Picom

直接使用 pacman 包管理器下载 Picom

```shell
sudo pacman -S picom
```

## 输入法 Fcitx5 与 RIME

输入法的安装除了本体外还需要安装输入法模块与输入法引擎，因此推荐直接安装 fcitx-im 并加上任一个输入法引擎，其中 fcitx-im 中包含了本体、配置工具与输入法模块

我选择的输入法引擎为 RIME

```shell
sudo pacman -S fcitx5-im fcitx5-rime
```

下载完成后需要设置一定的环境变量才能在程序中正常启用输入法

```conf title="/etc/environment" linenums="1"
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
INPUT_METHOD=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

## 声音管理器 PulseAudio

参考网站 [Arch PulseAudio](https://wiki.archlinux.org/title/PulseAudio_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

Linux 中声音内核模块为 ALSA，PulseAudio 则为内核与应用程序之间的界面，需要安装本体与一定模块

```shell
sudo pacman -S pulseaudio pulseaudio-alsa
```

同时推荐安装图形界面控制程序 pavucontrol

```shell
sudo pacman -S pavucontrol
```

安装完上述程序后，这个系统就可堪一用了，但由于还没有进行详尽的配置，因此这些程序不一定好用，而对程序的配置将在后文展开介绍

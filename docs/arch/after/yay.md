# 安装 AUR 工具 yay

Arch Linux 很为人称道的一点便是 AUR 了，其中包含了很多很多常用软件，甚至包括闭源软件，主要还包含了很多中国大陆常用的软件

但直接使用 AUR 相对麻烦，需要首先克隆源码，然后编译安装，最重要的是管理上相对复杂

yay 工具使 AUR 使用更加方便，像 pacman 包管理器一样可以一条命令安装卸载软件，同时方便管理

参考网站 [yay GitHub](https://github.com/Jguer/yay)

以下为安装 yay 的操作

首先克隆 yay 的源代码

```shell
git clone https://aur.archlinux.org/yay.git
```

然后进入 yay 源码目录并进行编译安装

```shell
cd yay
makepkg -si
```

!!! note "注意"
    
    编译安装的工具包含在 base-devel 软件包中，因此请保证安装了 base-devel

    安装过程中会从 GitHub 上克隆代码，有时会因连接不上而下载失败，因此推荐配置代理之后再进行 yay 的下载

安装完成后可以进行以下操作更新整个系统，同时检查是否安装成功

```shell
yay -Syyu
```

yay 的使用方法与 pacman 几乎一模一样，请尽情享受 AUR 的快乐吧！

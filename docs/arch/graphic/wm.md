# 安装窗口管理器

我的方案中选择的是 i3-wm 窗口管理器，想选择其他窗口管理器或想安装桌面环境请参考网站 [Arch WM](https://wiki.archlinux.org/title/Window_manager_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)) 或 [Arch DE](https://wiki.archlinux.org/title/Window_manager_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

其中 i3-wm 的参考网站为 [Arch i3](https://wiki.archlinux.org/title/I3_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

直接使用 pacman 包管理器下载 i3-wm 即可

```shell
# 下载有窗口间隙特性的分支，推荐
sudo pacman -S i3-gaps
# 也可以下载没有该特性的版本
sudo pacman -S i3-wm
```

i3-wm 的可配置性极强，此处暂不叙述，详细配置说明参见后文

由于我们还要安装显示管理器，因此不需要对启动进行配置，可以直接由显示管理器引导启动

这里我还推荐安装与其搭配的锁屏程序 i3lock

```shell
sudo pacman -S i3lock
```

之后会配置快捷键达到快速锁屏的功能

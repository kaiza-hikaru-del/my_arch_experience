# 安装显示服务程序

除了概述中介绍的 Xorg 之外，目前还出现了新的显示服务程序 Wayland，但由于其对现存图形程序的适配程度依然不太好，因此我们仍然使用 Xorg

参考网站 [Arch Xorg](https://wiki.archlinux.org/title/Xorg_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

直接使用 pacman 包管理器安装即可

```shell
# 只下载 Xorg 服务
sudo pacman -S xorg-server
# 下载 Xorg 实用工具
sudo pacman -S xorg-apps
# 把上述两者一并下载，推荐
sudo pacman -S xorg
```

因为我的方案中包含了显示管理器和窗口管理器，此处就不折腾更多内容


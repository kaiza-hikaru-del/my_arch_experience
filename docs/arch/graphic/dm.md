# 安装显示管理器

我的方案中选择的是 LightDM，想选择其他显示管理器请参考网站 [Arch DM](https://wiki.archlinux.org/title/Display_manager_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

其中 LightDM 的参考网站为 [Arch LightDM](https://wiki.archlinux.org/title/LightDM)

直接使用 pacman 包管理器下载 LightDM 即可，需要下载本体与 Greeter

```shell
sudo pacman -S lightdm lightdm-gtk-greeter
```

其中 Greeter 的选择有多种，请参阅参考网站，此处我选择的是 GTK 风格的

下载完成后需要启动相应服务

```shell
sudo systemctl enable lightdm.service
```

启动完成后在下次进入系统时就可以由 LightDM 引导进入 i3-wm 了

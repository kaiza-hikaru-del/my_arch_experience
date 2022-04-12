# 联网

首次进入 Arch Linux 时是没有网络连接的，需要手动配置网络并打开网络服务

有许多优秀的网络管理器可供选择，我此处选择的是很方便使用的 NetworkManager，下面介绍 NetworkManager 的用法

参考网站 [Arch NetworkManager](https://wiki.archlinux.org/title/NetworkManager_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

首先启动网络服务

```shell
systemctl enable --now NetworkManager.service
```

如果是有线网络的话，启动之后一般就可以连接上网络如果是无线网络的话，还需要手动连接 WiFi

以下为连接无线网络的操作

首先扫描附近的 WiFi 并将结果显示出来

```shell
nmcli device wifi list
```

然后连接到其中一个 WiFi

```shell
nmcli device wifi connect [SSID] password [password]
```

进行完上述操作后就可以连接上网络了

可以使用 `ip addr` 或 `ping` 命令检查联网情况

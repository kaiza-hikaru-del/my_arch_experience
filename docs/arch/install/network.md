# 联网

下载系统与必要工具时需要从互联网获取，因此需要保证安装过程中连接着网络

联网时可能用到的工具有如下几个

- 有线网络：systemd-networkd
- 无线网络：iwd 或 wpa_supplicant

## systemd-networkd 使用方法

参考网站 [Arch systemd-networkd](https://wiki.archlinux.org/title/Systemd-networkd_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

有线网络一般不需要过多配置就可以直接使用，但有可能需要开启网络服务，开启操作如下

```shell
systemctl enable --now systemd-networkd.service
```

## iwd 使用方法

参考网站 [Arch iwd](https://wiki.archlinux.org/title/Iwd_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

首先打开 iwd 服务

```shell
systemctl enable --now iwd.service
```

其次使用 iwctl 进入交互命令行

```shell
iwctl
```

然后在交互命令行中连接无线网络，连接操作如下

```shell
# 列出所有 WiFi 设备
device list
# 扫描附近 WiFi
station [device] scan
# 列出扫描结果
station [device] get-networks
# 连接到其中一个网络
station [device] connect [SSID]
# 然后需要输入 WiFi 口令
```

完成上述操作后便连接上了无线网络

## wpa_supplicant 使用方法

参考网站 [Arch wpa_supplicant](https://wiki.archlinux.org/title/Wpa_supplicant_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

首先创建 wpa_supplicant 配置文件

```conf title="/etc/wpa_supplicant/wpa_supplicant.conf"
ctrl_interface=/run/wpa_supplicant
update_config=1
```

其次运行 wpa_supplicant

```shell
# 查看无线网卡名称
ip addr
# 根据无线网卡名称与配置文件运行 wpa_supplicant
wpa_supplicant -B -i [interface] -c /etc/wpa_supplicant/wpa_supplicant.conf
```

然后进入交互命令行并连接无线网络，操作如下

```shell
# 进入交互命令行
wpa_cli
# 在交互命令行中，扫描 WiFi
scan
# 显示扫描结果
scan_results
# 创建网络
add_network
# 设置该网络的 SSID 与口令
set_network 0 ssid "MYSSID"
set_network 0 psk "passphrase"
# 启用该网络
enable_network 0
# 保存连接配置
save_config
```

完成上述操作后便连接上了无线网络

但我在使用 wpa_supplicant 时出现扫描不出 WiFi 结果的情况，请谨慎使用

## 联网结果检查

联网完成后可以使用以下操作检查是否连接成功

```shell
# 列出网卡详细信息，查看是否分配了 ip 地址
ip addr
# ping 互联网上的主机查看是否能够连接，'-c 6'参数连续表示 ping 6次
ping archlinux.org -c 6
```

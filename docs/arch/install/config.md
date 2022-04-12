# 配置系统

## 创建挂载配置文件

进行以下操作创建挂载配置文件

```shell
genfstab -U /mnt >> /mnt/etc/fstab
```

## 进入新系统并设置时区

进行以下操作进入新系统

```shell
arch-chroot /mnt
```

进行以下操作设置时区

```shell
# 设置时区
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
# 生成 /etc/adjtime 文件
hwclock --systohc
```

!!! note "时间相关概念"
    
    时间相关概念可以参考网站 [Arch System Time](https://wiki.archlinux.org/title/System_time) 的描述，其中最重要的概念是硬件时间与系统时间，以及 UTC 与地方时，Linux 系统一般采用硬件时间为 UTC 时间而系统时间根据时区调整到地方时的方案，但 Windows 系统采用硬件时间与系统时间都为地区时的方案，因此需要统一时间方案，一般推荐修改 Windows 系统方案契合 Linux 系统
    ```powershell title="在 Windows 中以管理员身份运行 powershell 并执行以下命令"
    reg add "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation" /v RealTimeIsUniversal /d 1 /t REG_DWORD /f
    ```

## 在新系统中设置本地化

进行以下操作设置本地化

```shell
# 将 /etc/locale.gen 文件中含 en_US 与 zh_CN 的行注释删除然后执行如下操作
locale-gen
```

创建 locale.conf 文件并指定英语与 UTF-8 编码为系统默认设置

```conf title="/etc/locale.conf" linenums="1"
LANG=en_US.UTF-8
```

## 在新系统中配置网络

创建 hostname 文件并指定计算机名

```conf title="/etc/hostname" linenums="1"
[hostname]
```

修改 hosts 文件解析本机地址

```conf title="/etc/hosts" linenums="1"
127.0.0.1   localhost
::1         localhost
127.0.1.1   [hostname].[localdomain]    [hostname]
```

## 在新系统中进行 Initramfs

进行以下操作

```shell
mkinitcpio -P
```

## 配置新系统 root 用户密码

进行以下操作设置 root 用户密码

```shell
passwd
# 根据提示输入两次密码
```

## 为新系统安装 Grub 引导程序

参考网站 [Arch Grub](https://wiki.archlinux.org/title/GRUB_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

此处只叙述 UEFI 引导模式下的操作，BIOS 引导模式下的操作请浏览参考网站

首先下载 grub 与 efibootmgr 

```shell
pacman -S grub efibootmgr
```

其次使用 grub-install 下载引导文件

```shell
# [esp] 表示 EFI 分区的挂载位置
grub-install --target=x86_64-efi --efi-directory=[esp] --bootloader-id=GRUB
```

!!! note "Grub 探测双系统"
    
    探测其他系统操作首先需要下载 os-prober
    
    ```shell
    pacman -S os-prober
    ```
    
    然后取消 grub 文件最后一行配置的注释
    
    ```conf title="/etc/default/grub" linenums="63"
    GRUB_DISABLE_OS_PROBER=false
    ```

最后生成配置文件并检查

```shell
grub-mkconfig -o /boot/grub/grub.cfg
```

## 为新系统安装处理器微码

安装微码操作如下

```shell
# Intel 处理器微码
pacman -S intel-ucode
# AMD 处理器微码
pacman -S amd-ucode
```

安装微码后需要重新生成 Grub 配置文件

```shell
grub-mkconfig -o /boot/grub/grub.cfg
```

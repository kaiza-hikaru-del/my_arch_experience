# 硬盘分区、格式化与挂载

## 建立硬盘分区

首先查看硬盘信息

```shell
fdisk -l
```

分区方案有多种多样，Arch 推荐的分区方案在 [此处](https://wiki.archlinux.org/title/Partitioning_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#%E5%B8%83%E5%B1%80%E7%A4%BA%E4%BE%8B) 可以看到

我所使用的分区方案如下表所示

| 挂载点 | 分区 | 分区类型 | 参考大小 |
| :----: | :--: | :------: | :------: |
| /boot | /dev/[efi_part] | EFI 系统分区 | 550M |
| [swap] | /dev/[swap_part] | Linux swap 交换分区 | 与内存大小相同 |
| / | /dev/[root_part] | Linux x86-64 根目录 | 32G |
| /home | /dev/[home_part] | Linux /home | 剩余空间 |

!!! note "Windows + Linux 双系统方案注意"
    
    如果想安装 Windows + Linux 双系统的话，则建议现安装 Windows 系统，安装时会自动生成一个 EFI 分区，在安装 Linux 时就不需要再分出 EFI 分区以及格式化

    但在实践双系统过程中发现 Windows 自动生成的 EFI 分区较小，可以利用傲梅或其他工具将 EFI 分区扩大到 550M

    同时推荐双系统方案分出一个共享分区，方便两个系统之间进行文件交换

建立硬盘分区操作如下

```shell
# 使用 fdisk 对硬盘分区
fdisk /dev/sda
# fdisk 简要使用方法
# n-新建分区 t-改变分区类型 w-写入分区信息并退出 q-不保存修改然后退出
```

分区建立完成后可以使用 `fdisk -l` 查看分区信息

## 格式化分区

格式化分区操作如下

```shell
# 对 EFI 分区格式化
mkfs.fat -F 32 /dev/[efi_part]
# 对根目录分区格式化
mkfs.ext4 /dev/[root_part]
# 对交换分区进行格式化
mkswap /dev/[swap_part]
```

!!! note "注意"
    
    如果是已经存在的 EFI 分区，务必不要对 EFI 分区进行格式化，尤其是安装双系统时更需要注意

## 挂载分区

首先挂载根目录

```shell
mount /dev/[root_part] /mnt
```

其次创建其他文件夹并挂载其他分区

```shell
# EFI 分区
mkdir /mnt/boot
mount /dev/[efi_part] /mnt/boot
# /home 分区
mkdir /mnt/home
mount /dev/[home_part] /mnt/home
```

然后启用交换分区

```shell
swapon /dev/[swap_part]
```

对双系统可能有共享分区也请记得挂载

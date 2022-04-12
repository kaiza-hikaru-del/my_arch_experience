# 安装系统与必要工具

首先调整软件源到国内源以加快安装速度

```shell
reflector --country China --latest 10 --protocol http --protocol https --save /etc/pacman.d/mirrorlist
```

在北方则推荐将清华源调整至前面，在南方则推荐将中科大源调整至前面

也可以直接修改配置文件调整软件源

```conf title="/etc/pacman.d/mirrorlist" linenums="1"
# 清华镜像
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
Server = http://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
# 中科大镜像
Server = https://mirrors.ustc.edu.cn/archlinux/$repo/os/$arch
Server = http://mirrors.ustc.edu.cn/archlinux/$repo/os/$arch
```

其次安装操作系统与必要程序

```shell
# 网络管理器NetworkManager 文本编辑器Neovim 程序手册man 基础开发工具base-devel 版本管理工具git 终端下载器wget与curl
pacstrap /mnt base linux linux-firmware networkmanager neovim man base-devel git wget curl
```

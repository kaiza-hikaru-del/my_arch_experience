# 安装显卡驱动

参考网站 [Arch Xorg 驱动安装](https://wiki.archlinux.org/title/Xorg_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#%E9%A9%B1%E5%8A%A8%E5%AE%89%E8%A3%85)

首先查看显卡型号

```shell
lspci | grep -e VGA -e 3D
```

其次可以在 pacman 包管理器中查询所有显卡驱动的名称

```shell
pacman -Ss xf86-video
```

然后根据显卡的型号下载对应的驱动程序，此处展示主流显卡对应的开源驱动程序名称

| 显卡型号 | 开源驱动程序名称 |
| :------: | :--------------: |
| AMD 旧型号 | xf86-video-ati |
| AMD 新型号 | xf86-video-amdgpu |
| Intel      | xf86-video-intel  |
| Nvidia     | xf86-video-noveau |

!!! note "注意"
    
    此处展示的都是开源驱动程序名称，但如果需要使用闭源驱动程序的功能，请自行参阅参考网站下载对应的闭源驱动，但没有特殊需要的话还是更推荐开源驱动

    AMD 此处分类叙述并不准确，还请自行参阅参考网站查看究竟使用哪个驱动程序

??? quote "引用"
    
    So Nvidia, F**K YOU!

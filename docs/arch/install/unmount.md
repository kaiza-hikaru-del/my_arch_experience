# 解挂载并重新启动

从新系统退出到安装环境需要使用快捷键`<Ctrl-D>`或输入命令`exit`

退出到安装环境后需要解挂载所有分区

```shell
umount -R /mnt
```

最后使用`reboot`重启系统

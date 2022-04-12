# 更新系统时间

进行以下操作设置时区并开启时间同步服务

```shell
timedatectl set-timezone Asia/Shanghai
timedatectl set-ntp true
```

设置完成后最好检查以下服务状态

```shell
timedatectl status
```

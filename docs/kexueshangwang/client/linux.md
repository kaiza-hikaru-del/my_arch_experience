# Linux 客户端

这里就以 Arch Linux 为例，都用 Linux 了这种程度的举一反三应该不成问题吧（不会吧不会吧）

直接用 pacman 包管理器下载 v2ray

```shell
sudo pacman -S v2ray
```

v2ray 的配置文件位于 /etc/v2ray/config.json

我们可以使用服务端的 multi-v2ray 自动生成客户端配置文件，服务端生成配置文件方法如下

```shell
# 进入脚本管理程序中
v2ray
# 选择生成配置文件对应的操作序号和要生成端口的序号
# 操作完成后需要手动强制结束管理脚本，<Ctrl-C> 不好使，要用 <Ctrl-/>
```

操作完成后会生成客户端配置文件到 /root/config.json

将这个配置文件复制到 Linux 客户端的 /etc/v2ray/config.json 即可完成配置

然后需要启动客户端 v2ray 服务，操作如下

```shell
sudo systemctl enable --now v2ray.service
```

不过此时还不能科学上网，还得配置需要科学上网的程序，比如浏览器、Shell 程序等等（都用 Linux 了这点程度的事就自己查吧）

配置完成后就尽情享受科学上网吧

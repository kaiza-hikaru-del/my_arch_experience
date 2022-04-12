# 科学上网服务端

首先你需要一台服务器，既可以被自己访问到，也可以访问到外面的世界

我个人推荐 Vultr 的服务器，因为有亚太地区的业务，总比跨越大洋到漂亮国快很多吧

服务器系统选择比较多，不过起码得是 Linux 吧，原则上用哪个发行版都没问题，但我个人还是推荐 Debian 或者 Arch Linux

在我自己的实践中，首尔的服务器 IP 出现了移动网连不上的情况，东京的 IP 目前没有问题，单个案例不能说明共性问题，仅供参考

SSH 登录服务器我就不展开讲了吧

这里推荐一个开源项目 multi-v2ray，可以方便地管理服务端的 v2ray

参考网站 [multi-v2ray GitHub](https://github.com/Jrohy/multi-v2ray)

在服务端进行以下操作下载 multi-v2ray

```shell
source <(curl -sL https://multi.netlify.app/v2ray.sh) --zh
```

等跑完就安装成功了，并且自动配置了一个 v2ray 端口，其中输出的含有 `vmess://...` 的URL可以用于很多客户端导入，这个URL很重要，最好复制一份保存到一个地方

可以执行命令 `v2ray status` 查看运行状态，在 Running 就没问题

成功科学上网之后，很多自定义操作就自己查参考网站来看吧

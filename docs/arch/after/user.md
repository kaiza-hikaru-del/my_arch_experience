# 创建非 root 用户并加入 sudoer

为了系统的安全性，往往使用 Linux 系统时不直接使用 root 用户，而是创建一个普通用户并将其加入 sudoer 以获得 root 权限

在 sudoer 使用 root 权限时需要输入密码确认，因此很大程度避免了危险的误操作

## 创建非 root 用户

进行以下操作创建非 root 用户

```shell
# '-m' 参数表示为用户创建家目录
useradd -m [username]
# 为新用户创建密码
passwd [username]
```

## 将用户加入 sudoer

编辑 sudo 配置文件的命令为 `visudo` ，相比直接编辑配置文件，该命令会检查配置文件的正确性，因此推荐用 `visudo` 进行配置

但 `visudo` 的默认编辑器为 `vi` ，我使用软链接的方式解决没有 `vi` 的问题，操作如下

```shell
ln -s /usr/bin/nvim /usr/bin/vi
```

然后编辑 sudo 配置

```conf title="执行 visudo 命令后进入配置文件并去掉第82行的注释" linenums="82"
%wheel ALL=(ALL) ALL
```

然后将用户加入 wheel 用户组以加入 sudoer

```shell
usermod -aG wheel [username]
```

可以使用以下命令查看用户是否加入 wheel 用户组

```shell
groups [username]
```

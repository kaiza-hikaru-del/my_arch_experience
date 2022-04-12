# Git 配置

参考网站 [廖雪峰 Git 教程](https://www.liaoxuefeng.com/wiki/896043488029600)

Git 使用时主要需要配置用户名与邮箱，以及生成 SSH 密钥与远程仓库链接

## 配置用户名与邮箱

配置用户名与邮箱的操作如下

```shell
git config --global user.name "[Your Name]"
git config --global user.email "[email@example.com]"
```

配置完成后可以在 $HOME/.gitconfig 中看到配置的内容

```conf title="$HOME/.gitconfig" linenums="1"
[user]
	name = [Your Name]
	email = [email@example.com]
```

也可以使用以下命令查看已配置的内容

```shell
git config -l
```

## 生成 SSH 密钥

生成 SSH 密钥的操作如下

```shell
ssh-keygen -t rsa -C "[youremail@example.com]"
# 会有需要输入的选项，直接回车默认就好
```

执行命令并保持默认选项时，会在 $HOME/.ssh 目录生成两个文件，分别是

- $HOME/.ssh/id_rsa 是私钥，需要留在此处但务必不要透露出去
- $HOME/.ssh/id_rsa.pub 是公钥，需要将其中内容复制填写到远程仓库网站（主要是 GitHub 或 Gitee）个人配置中

设置成功后可以使用以下命令检测是否与远程仓库网站建立连接

```shell
ssh -T git@[git-server]
# 通常 git-server 是 GitHub 或 Gitee
ssh -T git@github.com
ssh -T git@gitee.com
```

## 配置别名

Git 通过配置命令别名简化一些操作

这里提供一个显示历史提交记录的命令别名，可以高亮显示 Git 历史记录

```shell
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

配置完成后可以在 $HOME/.gitconfig 中看到配置的内容

```conf title="$HOME/.gitconfig" linenums="1"
...
[alias]
	lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

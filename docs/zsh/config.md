# ZSH 配置

ZSH 可配置性十分高，目前我也没有研究透彻大部分可配置内容，以下为方便我使用的配置内容，仅供参考

ZSH 的配置文件位于 $HOME/.zshrc

```conf title="$HOME/.zshrc" linenums="1"
...
# 配置代理
export http_proxy=http://127.0.0.1:10809
export https_proxy=http://127.0.0.1:10809
export socks5_proxy=socks5://127.0.0.1:10808

# 配置命令别名
alias n="neofetch"
alias reboot="systemctl reboot"   # 在非 root 用户下不用 sudo 进行关机重启需要 polkit 包支持
alias poweroff="systemctl poweroff -i"

# pip下载的工具一般位于 $HOME/.local/bin
export PATH=$PATH:~/.local/bin
```

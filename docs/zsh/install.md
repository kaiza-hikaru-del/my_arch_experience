# 安装 ZSH 与 oh my zsh

ZSH 是一款功能强大的 Shell 软件，个人认为不论是美观上还是补全体验上都比默认的 bash 好很多，因此选用 ZSH 作为默认 Shell 软件

oh my zsh 则是一个方便 ZSH 配置与管理插件的工具，使 ZSH 的使用更方便

首先下载 ZSH 本体与补全命令包

```shell
sudo pacman -S zsh zsh-completions
```

然后从 GitHub 源码下载 oh my zsh 接管 ZSH 的管理，操作如下

```shell
# 克隆源码
git clone https://github.com/ohmyzsh/ohmyzsh.git
# 进入安装脚本目录并执行安装脚本
cd ohmyzsh/tools
bash install.sh
```

!!! note "注意"
    
    直接从 GitHub 上克隆源代码可能出现速度很低的情况，因此推荐配置代理后再进行克隆

当看到不同于 bash 的华丽提示符后则表示安装成功，尽情享受 ZSH 的便捷吧！

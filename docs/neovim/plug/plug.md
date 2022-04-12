# Neovim 插件管理

Neovim 能够十分好用的一大重要原因来自插件众多，可以根据需求进行个性化配置，甚至将 Neovim 打造成集成开发环境

但如果按照官方的方法进行插件安装既麻烦又不便于管理，因此我推荐使用 vim-plug 进行 Neovim 插件的管理

参考网站为 [Vim-plug GitHub](https://github.com/junegunn/vim-plug)

以下为给 Neovim 安装 vim-plug 的过程，与作者推荐的方法略有不同

首先克隆源码到一定目录中

```shell
git clone https://github.com/junegunn/vim-plug.git
```

然后将源码目录中的 plug.vim 文件复制到指定目录中

```shell
# 指定目录可能不存在，先创建它
mkdir -p ~/.local/share/nvim/site/autoload
# 复制文件到该目录
cp /path/to/plug.vim ~/.local/share/nvim/site/autoload/plug.vim
```

最后在配置文件中添加以下内容就可以通过 vim-plug 管理插件了

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
call plug#begin(stdpath('data') . '/plugged')
" 在此处添加插件
call plug#end()
```

常用 vim-plug 命令如下表

| 命令 | 功能 |
| :--: | :--: |
| `:PlugInstall` | 下载列出的插件 |
| `:PlugUpdate`  | 升级下载的插件 |
| `:PlugClean`   | 删除不在列表中的插件 |

!!! note "注意"
    
    将想要下载的插件添加到对应位置或将想要删除的插件去除之后，需要更新配置文件后才能进行插件下载或删除

    更新配置文件的方法有以下两种

    - 保存后退出重新启动 Neovim
    - 保存后使用底线命令 `:source %`

# 标签列表 Tagbar

Tagbar 可以显示当前文件的各种标签，包括变量名、函数名等等

参考网站 [Tagbar Github](https://github.com/preservim/tagbar)

首先需要下载依赖 ctags

```shell
sudo pacman -S ctags
```

将以下内容添加到配置文件进行插件下载

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
Plug 'preservim/tagbar'
```

该插件常用命令如下表

| 命令 | 功能 |
| :--: | :--: |
| `:TagbarToggle` | 打开或关闭标签列表 |

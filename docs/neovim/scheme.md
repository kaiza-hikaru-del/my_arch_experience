# Neovim 主题

Neovim 是可以配置主题的，并且可选择的主题配色方案很多，喜欢深色主题的话我推荐 Dracula

主题安装方式有多种，但我认为用插件的方式安装比较方便，因此我以插件方式安装为例

首先在插件部分添加以下内容

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
Plug 'dracula/vim', { 'as': 'dracula' }
```

然后进行完下载该插件的过程后再往配置文件中添加以下内容

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
colorscheme dracula
```

然后重新加载配置文件后即可应用该主题

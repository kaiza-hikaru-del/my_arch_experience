# Neovim 基础配置

Neovim 是一款十分好用的终端模拟器，其前身是 Vim 和 Vi

其中 Neovim 的配置文件位于 $HOME/.config/nvim/init.vim

Neovim 尚未配置时使用并不方便，但在进行了一系列配置后 Neovim 就可以变得十分好用，甚至可以根据个性化需求定制对应的功能

Neovim 配置教程主要参考以下两个网站

- [Vim Configuration Guide](https://www.freecodecamp.org/news/vimrc-configuration-guide-customize-your-vim-editor/)
- [阮一峰 Vim 配置入门](http://www.ruanyifeng.com/blog/2018/09/vimrc.html)

基础配置主要是令 Neovim 显示更多辅助信息设置一些基本参数，如显示行号与设置缩进字符数

以下为我的基础配置，在注释中标注了配置的主要内容

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
set nocompatible            " 禁用与vi的兼容性
filetype on                 " 探测文件类型
filetype plugin on          " 按照文件类型加载插件
filetype indent on          " 按照文件类型设置缩进
syntax on                   " 打开语法高亮
set number                  " 显示行号
set relativenumber          " 显示相对行号
set cursorline              " 高亮当前行
set cursorcolumn            " 高亮当前列
set shiftwidth=4            " 设置位移宽度为4
set tabstop=4               " 设置缩进宽度为4
set expandtab               " 将缩进替换为空格
set nobackup                " 不生成backup文件
set scrolloff=10            " 设置滚动时始终显示上下10行
set nowrap                  " 禁止折行
set incsearch               " 增量式搜索
set ignorecase              " 搜索时大小写不敏感
set smartcase               " 搜索时对首字母大小写敏感
set showcmd                 " 显示键入的命令前缀
set showmode                " 显示当前模式（插入、可视等）
set showmatch               " 在搜索过程中显示匹配的单词
set hlsearch                " 高亮搜索结果
set history=1000            " 设置命令历史记录为1000
set wildmenu                " 设置tab补全
set wildmode=list:longest   " 使tab补全类似于Bash
set encoding=utf-8          " 设置编码方式为UTF-8
```

如果使用 Fcitx5 输入法，往往不希望在退出插入模式时仍然打开着输入法，因此我们添加以下自动脚本到配置文件里以避免这种情况

此处参考网站 [Arch Fcitx Vim](https://wiki.archlinux.org/title/Fcitx_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#Vim)

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
"##### auto fcitx5  ###########
let g:input_toggle = 1
function! Fcitx52en()
   let s:input_status = system("fcitx5-remote")
   if s:input_status == 2
      let g:input_toggle = 1
      let l:a = system("fcitx5-remote -c")
   endif
endfunction

function! Fcitx52zh()
   let s:input_status = system("fcitx5-remote")
   if s:input_status != 2 && g:input_toggle == 1
      let l:a = system("fcitx5-remote -o")
      let g:input_toggle = 0
   endif
endfunction

set ttimeoutlen=150
"退出插入模式
autocmd InsertLeave * call Fcitx52en()
"进入插入模式
autocmd InsertEnter * call Fcitx52zh()
"##### auto fcitx5 end ######
```

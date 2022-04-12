# 目录树 NERDTree

NERDTree 是一个可以显示目录树的插件，对于工程型代码能够实时看到工程目录十分重要

参考网站 [NERDTree GitHub](https://github.com/preservim/nerdtree)

将以下内容添加到配置文件进行插件下载

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
Plug 'preservim/nerdtree'
```

该插件常用命令如下表

| 命令 | 功能 |
| :--: | :--: |
| `:NERDTree` | 打开目录树 |
| `:NERDTreeToggle` | 打开或关闭目录树 |

根据 GitHub 中的描述，可以在配置文件中添加一些自动化脚本使 NERDTree 更好用

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
" 在指定文件打开 Neovim 时同时打开 NERDTree 并将光标置于文件中
autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * NERDTree | if argc() > 0 || exists("s:std_in") | wincmd p | endif
" 当 NERDTree 是最后一个窗口时关闭整个 tab
autocmd BufEnter * if winnr('$') == 1 && exists('b:NERDTree') && b:NERDTree.isTabTree() | quit | endif
" 对每个 tab 都打开 NERDTree
autocmd BufWinEnter * if getcmdwintype() == '' | silent NERDTreeMirror | endif
" 如果另一个缓冲区试图替换 NERDTree，请将其放在另一个窗口中，然后带回 NERDTree
autocmd BufEnter * if bufname('#') =~ 'NERD_tree_\d\+' && bufname('%') !~ 'NERD_tree_\d\+' && winnr('$') > 1 |
    \ let buf=bufnr() | buffer# | execute "normal! \<C-W>w" | execute 'buffer'.buf | endif
```

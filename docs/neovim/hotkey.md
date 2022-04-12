# Neovim 快捷键

Neovim 可以设置快捷键映射以快速触发一些操作，比如快速保存文件、快速打开某些插件等等

我所设置的快捷键如下表，同时附上源码，仅供参考

| 快捷键 | 功能或等价命令 |
| :----: | :------------: |
| <leader\>="," | 设置 <leader\> 键为英文逗号 |
| <leader\>s    | `:source %` 更新配置文件    |
| <leader\>ww   | `:w` 保存文件               |
| <leader\>qq   | `:q!` 强制退出              |
| <leader\>wq   | `:wq` 保存退出              |
| <leader\>pi   | `:PlugInstall` 下载插件     |
| <leader\>nn   | `:NERDTreeToggle` 目录树    |
| <leader\>tt   | `:TagbarToggle` 标签列表    |

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
" basic map
let mapleader = ','
nnoremap <leader>s :source %<CR>
nnoremap <leader>ww :w<CR>
nnoremap <leader>wq :wq<CR>
nnoremap <leader>qq :q!<CR>
" vim-plug map
nnoremap <leader>pi :PlugInstall<CR>
" NERDTree map
nnoremap <leader>nn :NERDTreeToggle<CR>
" Tagbar man
nnoremap <leader>tt :TagbarToggle<CR>
```

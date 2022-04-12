# 代码补全 coc.nvim

coc.nvim 其实不仅仅只是一个代码补全插件，而是带有一套子插件系统的多功能插件，通过下载一定的子插件实现不同语言的代码补全以及其他功能

参考网站 [coc.nvim Github](https://github.com/neoclide/coc.nvim)

首先需要下载 node.js 依赖

```shell
sudo pacman -S nodejs npm
```

将以下内容添加到配置文件进行插件下载

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
Plug 'neoclide/coc.nvim', {'branch': 'release'}
```

下载完成后即可使用 coc.nvim 提供的命令下载众多子插件

该插件常用命令如下表

| 命令 | 功能 |
| :--: | :--: |
| `CocInstall <sub-plugin>` | 下载子插件 |
| `CocUninstall <sub-plugin>` | 删除子插件 |
| `CocUpdate` | 更新子插件 |
| `CocInfo` | 查看插件状态 |

为了保证某个子插件必然被加载，可以通过设置变量自动检查是否存在，若不存在则自动下载子插件

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
# 设置了两个全局子插件
# coc-marketplace 是子插件市场
# coc-clangd 是基于 clang 的语义型 C 语言补全插件，依赖于 clang
let g:coc_global_extensions = ['coc-marketplace', 'coc-clangd']
```

在下载 coc-marketplace 的情况下可以通过`:CocList marketplace`命令查看子插件市场

该子插件的细节请参考网站 [coc-marketplace Github](https://github.com/fannheyward/coc-marketplace)

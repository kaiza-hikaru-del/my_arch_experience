# 快速注释 NERDCommenter

NERDCommenter 插件用于快速注释，可以单行注释也可以多行注释，提供了很多注释快捷键

参考网站 [NERDCommenter](https://github.com/preservim/nerdcommenter)

将以下内容添加到配置文件进行插件下载

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
Plug 'preservim/nerdcommenter'
```

该插件通过设置变量默认进行了快捷键映射，变量配置如下

```conf title="$HOME/.config/nvim/init.vim" linenums="1"
let g:NERDCreateDefaultMappings = 1     " 创建默认快捷键
let g:NERDSpaceDelims = 1               " 在注释左右添加一个空格
```

默认快捷键映射如下

| 快捷键 | 主要功能 |
| :----: | :------: |
| <leader\>cc | 注释当前行或选中模式中的部分 |
| <leader\>c<space\> | 注释或取消注释 |

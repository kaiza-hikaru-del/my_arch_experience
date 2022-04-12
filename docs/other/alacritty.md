# Alacritty 配置

alacritty 配置文件位于 $HOME/.config/alacritty/alacritty.yml

下载完成后不会自动创建配置文件，需要手动创建

```shell
mkdir ~/.config/alacritty
touch ~/.config/alacritty/alacritty.yml
```

配置文件参考如下，配置内容会以注释方式说明

```yml title="$HOME/.config/alacritty/alacritty.yml" linenums="1"
# 设置字体为 Sauce Code Pro Nerd Font，需要下载该字体
font:
  # Normal (roman) font face
  normal:
    family: Sauce Code Pro Nerd Font
    style: Regular

  bold:
    family: Sauce Code Pro Nerd Font
    style: Bold

  italic:
    family: Sauce Code Pro Nerd Font
    style: Italic

  bold_italic:
    family: Sauce Code Pro Nerd Font
    style: Bold Italic

  # 设置字体大小
  size: 14.0

# 设置配色方案为 Dracula
colors:
  # Default colors
  primary:
    background: '#282a36'
    foreground: '#f8f8f2'

  # Normal colors
  normal:
    black:   '#000000'
    red:     '#ff5555'
    green:   '#50fa7b'
    yellow:  '#f1fa8c'
    blue:    '#caa9fa'
    magenta: '#ff79c6'
    cyan:    '#8be9fd'
    white:   '#bfbfbf'

  # Bright colors
  bright:
    black:   '#575b70'
    red:     '#ff6e67'
    green:   '#5af78e'
    yellow:  '#f4f99d'
    blue:    '#caa9fa'
    magenta: '#ff92d0'
    cyan:    '#9aedfe'
    white:   '#e6e6e6'
```

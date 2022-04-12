# Polybar 配置

参考网站 [Polybar GitHub](https://github.com/polybar/polybar)

Polybar 的配置文件位于 $HOME/.config/polybar/config.ini

我所配置的 Polybar 只有顶部一个状态栏，左侧显示活动窗口与编号，右侧显示音量、电量、网络与日期信息，中间显示活动进程

由于配置文件中使用了 Nerd Fonts 中的符号字2，因此详细配置文件请参考本文档的 GitHub 仓库中的 example/config.ini 文件，此处仅截取部分

```ini title="$HOME/.config/polybar/config.ini" linenums="1"
; 详细配置请参考本文档 GitHub 仓库中的 example/config.ini 文件
[colors]
; Dracula theme
background = #282A36
foreground = #F8F8F2
current-line = #44475A
selection = #44475A
comment = #6272A4
cyan = #8BE9FD
green = #50FA7B
orange = #FFB86C
pink = FF79C6
purple = #BD93F9
red = #FF5555
yellow = #F1FA8C

[bar/mybar]
width = 100%
height = 3%

background = ${colors.background}
foreground = ${colors.foreground}

module-margin = 1
modules-left = xworkspaces 
modules-center= xwindow
modules-right = pulseaudio battery wlan eth date

font-0 = "Sauce Code Pro Nerd Font"
...
```

配置完成后，需要一个启动脚本添加到窗口管理器或桌面系统的自动启动项中

一般将启动脚本放在与配置文件相同的位置，例如 $HOME/.config/polybar/launch.sh

启动脚本示例如下

```sh title="$HOME/.config/polybar/launch.sh" linenums="1"
#!/bin/bash

killall -q polybar

while pgrep -u $UID -x polybar >/dev/null; do sleep 1; done

polybar mybar &

echo "Polybar launched..."
```

!!! note "注意"

    启动脚本本身要具有可执行权限才能被执行，以下为添加可执行权限的操作

    ```shell
    chmod u+x $HOME/.config/polybar/launch.sh
    ```

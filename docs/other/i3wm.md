# i3-wm 配置

参考网站 [Configuring i3](https://thevaluable.dev/i3-config-mouseless/) 与 [Arch i3](https://wiki.archlinux.org/title/I3_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

i3-wm 的配置文件位于 $HOME/.config/i3/config

首次启动时会进行最基础的配置并生成基础配置文件，若不小心错过了初次配置，可以使用`i3-config-wizard`命令进行配置文件创建

初次配置时需要选择 $mod 按键，一般推荐使用 WIN 键而非 ALT 键

以下是对基础配置文件的修改

```conf title="$HOME/.config/i3/config" linenums="1"
...
# 第 47 行左右，换为自己实用的终端，我使用的是 alacritty
# start a terminal
bindsym $mod+Return exec alacritty
...
# 第 53 行左右，注释掉默认的 dmenu 打开快捷键，因为后面会添加带有 dracula 主题的 dmenu 快捷键
# start dmenu (a program launcher)
#bindsym $mod+d exec --no-startup-id dmenu_run
...
# 在第 182 行左右，删除掉所有 i3-bar 的内容，因为会用到 polybar
...
# 以下为添加的配置内容
# 设置边框与间隙
gaps inner 8
new_window pixel 1
new_float pixel 1

# 设置自启动，包括合成器、壁纸、输入法、polybar
exec --no-startup-id picom -b
exec --no-startup-id feh --no-fehbg --bg-scale '/path/to/pic.png' &
exec --no-startup-id fcitx5 -d
exec_always --no-startup-id /home/kaiza/.config/polybar/launch.sh

# 设置为dracula主题，此处包括了该主题的 dmenu
# class                 border  bground text    indicator child_border
client.focused          #6272A4 #6272A4 #F8F8F2 #6272A4   #6272A4
client.focused_inactive #44475A #44475A #F8F8F2 #44475A   #44475A
client.unfocused        #282A36 #282A36 #BFBFBF #282A36   #282A36
client.urgent           #44475A #FF5555 #F8F8F2 #FF5555   #FF5555
client.placeholder      #282A36 #282A36 #F8F8F2 #282A36   #282A36

client.background       #F8F8F2

bindsym $mod+d exec "dmenu_run -nf '#F8F8F2' -nb '#282A36' -sb '#6272A4' -sf '#F8F8F2' -fn 'monospace-10' -p 'dmenu%'"

# 设置快捷键打开浏览器
bindsym $mod+b exec firefox
bindsym $mod+c exec google-chrome-stable --proxy-server="socks5://127.0.0.1:1080"   # 此处设置了 google-chrome 的代理，需要提前配置好科学上网
# 设置快捷键打开网络管理器GUI
bindsym $mod+n exec nm-connection-editor

# 设置熄屏快捷键
bindsym $mod+BackSpace exec xset dpms force off

# 设置关机重启菜单快捷键
set $i3lockwall i3lock -i /path/to/pic.png -t     # 设置锁屏壁纸

bindsym $mod+Control+l exec --no-startup-id $i3lockwall
bindsym $mod+Control+r exec --no-startup-id systemctl reboot
bindsym $mod+Control+s exec --no-startup-id systemctl poweroff -i
```

```sh
journalctl -b 0 | rg asdf > "$HOME/Documents (Shared)/component/asdf.txt"
journalctl -b 0 | rg asdf > "$HOME/Documents (Shared)/component/asdf dc=0.txt"
journalctl --follow
    HDMI-A-2

output-crt
# nesdev server
xrandr --newmode "1440x480i-60" 27 1440 1478 1602 1716 480 489 495 525 interlace
# crt emudriver
xrandr --newmode "1440x240p_60" 27.26 1440 1480 1608 1736 240 244 247 262 -hsync -vsync
xrandr --addmode HDMI-2 "1440x480i-60"
xrandr --addmode HDMI-2 "1440x240p_60"

xrandr --output HDMI-2 --mode "1440x480i-60" --scale-from 1280x960 --pos 3640x0
# xrandr --output HDMI-2 --mode "1440x480i-60" --scale-from 1280x960 --pos 2560x0
#xrandr --output HDMI-2 --mode "1440x480i-60" --scale 1x1 --pos 3640x0
# xrandr --output HDMI-2 --mode "1440x480i-60" --scale 1x1 --pos 2560x0

xrandr --output HDMI-2 --mode "1440x240p_60" --scale-from 1280x960 --pos 3640x0

# then 1 second later, ctrl-c
```

```sh
cd ~/code/bcc
sudo ./examples/tracing/stacksnoop.py ...
```

```sh
pkill -f clangd
cd ~/pkgbuild/linux-zen-local/trunk
makepkg -fsi

reboot
```

# Bug report

https://gitlab.freedesktop.org/drm/amd/-/issues/1636
https://docs.google.com/document/d/1UUXKck_suy_klkz4eFa0bKv18I5SXsp0LbVcgAcrRCE/edit#heading=h.s0x60se6isoi

# does xrandr underscan avoid double-scaling?

```sh
# remove 64,64 pixels from each edge of the screen. cannot trim more than 128 on amdgpu.
xrandr --output DP-1 --set "underscan hborder" 128 --set "underscan vborder" 128
xrandr --output DP-1 --set underscan on

# blurry!
xrandr --output DP-1 --scale-from 2432x1312 #2304x1184
```

xrandr scales framebuffer pixels twice, once to the output resolution, and once to the output underscan resolution.

this is a big problem for vertical scaling, not horizontal.

- Install packages
  ```
  sudo pacman -S \
    sway waybar wofi konsole swaylock-effects swaybg\
    xorg-xwayland xorg-xlsclients qt5-wayland glfw-wayland\
    swayidle
  ```
  
  todo: switch input method?
  todo: konsole hidpi?
  
  Install settings (todo: where to place my `/etc`)
  
  Config `/etc/environment`:
  ```
  GTK_IM_MODULE=fcitx
  QT_IM_MODULE=fcitx
  XMODIFIERS=@im=fcitx
  
  MOZ_ENABLE_WAYLAND=1
  ```
  
  Config vscode to wayland native (link: https://wiki.archlinux.org/title/Visual_Studio_Code#Running_natively_under_Wayland)
  ```
  --enable-features=WaylandWindowDecorations
  --ozone-platform-hint=auto
  ```
  
  Config Chrome:
- open `chrome://flags/`
- search for `Preferred Ozone platform`
- set it to wayland
  
  Font needs for waybar: `ttf-font-awesome`
-
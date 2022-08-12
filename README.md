# macOS Look auf dem XFCE-Desktop
## Basic
```
sudo pacman -Syyu firefox plank zsh ranger tilix refind nautilus geany git ark
sudo pacman -R xfce4-terminal mousepad
sudo nano /etc/nanorc
```
- danach Plank zum Autostart hinzufügen

## Touchpad Tap to Click
```
cp 30-touchpad.conf /etc/X11/xorg.conf.d/
```
- zum aktivieren des Linksklick durch tippn auf dem Touchpad

## rEFInd - Bootmanager
```
refind-install
sudo cp -r refind /boot/efi/EFI
```

## YAY - AUR_Helper
```
cd /opt/
sudo git clone https://aur.archlinux.org/yay
sudo chown -R leon:wheel yay/
cd yay
makepkg -si
sudo rm -r yay/
cd ~
yay -S pamac
```

## Vala Panel
```
yay -S vala-panel-appmenu-common-git vala-panel-appmenu-registrar-git vala-panel-appmenu-xfce-git
sudo pacman -S appmenu-gtk-module
xfconf-query -c xsettings -p /Gtk/ShellShowsMenubar -n -t bool -s true
xfconf-query -c xsettings -p /Gtk/ShellShowsAppmenu -n -t bool -s true
```

## ZSH and Oh My ZSH
```
chsh -s /usr/bin/zsh
sudo chsh -s /usr/bin/zsh
zsh
bash install.sh
cp Plugins/zsh* ~/.oh-my-zsh/custom/plugins
cp .zshrc ~
source ~/.zshrc
```

## Purify Themen
```
mkdir ~/.local/ranger/colorschemes
mkdir ~/.local/tilix/schemes
cp Purify/purify.zsh-theme ~/.oh-my-zsh/custom/themes/	# ZSH
cp Purfiy/default.py ~/.local/ranger/colorschemes/		# Ranger
cp Purify/purify.json ~/.local/tilix/schemes			# Tilix
```

## Themen
```
mkdir ~/.themes && cp -r Themes/* ~/.themes
mkdir ~/.icons && cp -r Icons/* ~/.icons
cp Fonts/* /usr/share/fonts
mkdir /usr/share/backgrounds/macOS && cp Wallpaper/* /usr/share/backgrounds/macOS
cd WhiteSur-firefox-theme && bash install.sh && cd ..
cp gtk.css ~/.config/gtk-3.0/
```

## LY - Displaymanager
```
yay -S ly
sudo systemctl disable lightdm.service
sudo systemctl enable ly.service
```

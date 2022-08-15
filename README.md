# macOS Look auf dem XFCE-Desktop <br />
## Installation von Programmen
Die grundlegend wichtigsten Programme werden installiert. Unwichtige, vorinstallierte Programme werden gelöscht.
```
sudo pacman -Syyu firefox plank zsh ranger tilix refind nautilus geany git engrampa
sudo pacman -R xfce4-terminal mousepad
sudo nano /etc/nanorc
```
> Syntax-Highlighting aktivieren 
<br />

## Touchpad - Tippen um zu Klicken
```
sudo cp 30-touchpad.conf /etc/X11/xorg.conf.d/
```
- zum Aktivieren des Linksklick durch tippn auf dem Touchpad <br />

## rEFInd - Bootmanager
```
refind-install
sudo cp -r refind /boot/efi/EFI
```
Installiert das macOS-Thema für den rEFInd-Bootmanager. <br /> <br />

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
<br /> <br />

## Vala Panel
```
yay -S vala-panel-appmenu-common-git vala-panel-appmenu-registrar-git vala-panel-appmenu-xfce-git
sudo pacman -S appmenu-gtk-module
xfconf-query -c xsettings -p /Gtk/ShellShowsMenubar -n -t bool -s true
xfconf-query -c xsettings -p /Gtk/ShellShowsAppmenu -n -t bool -s true
```
- AppMenü zu Leiste hinzufügen
<br /> <br />
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
<br /> <br />
## Purify Farbschemen
> [Purify](https://github.com/kyoz/purify0) von Kyoz

Farbschemen für ZSH, Ranger und Tilix.

Erstellen der passenden Verzeichnisse für Ranger und Tilix 
```
mkdir ~/.local/ranger/colorschemes
mkdir ~/.local/tilix/schemes
```

Kopieren sie nun die Datein in ihr Verzeichnisse.
```
cp Purify/purify.zsh-theme ~/.oh-my-zsh/custom/themes/	  # ZSH
cp Purfiy/default.py ~/.local/ranger/colorschemes/	  	  # Ranger
cp Purify/purify.json ~/.local/tilix/schemes			        # Tilix
```
<br /> <br />
## Themen
Kopieren sie die Themen, Icon-Pakete und Fonts in die Systemverzeichnisse. Nutzen sie wenn nötig `sudo`.
```
cp Fonts/* /usr/share/fonts
cp -r Themes/* /usr/share/themes
cp -r Icons/* /usr/share/icons
```
> - [macOS Light](https://github.com/zayronxio/Mkosbigsur-gtk)
> - [macOS Dark](https://github.com/B00merang-Project/macOS-Dark)
> - [BigSur-Icons](https://github.com/zayronxio/Mkos-Big-Sur)
> - [Catalina-Icons](https://github.com/zayronxio/Os-Catalina-icons) 
<br />

Erstellen sie einen Ordner für die spezifischen Hintergründe und kopieren sie diese dort hin.
```
mkdir /usr/share/backgrounds/macOS
cp Wallpaper/* /usr/share/backgrounds/macOS
```
<br />

Installieren sie das WhiteSur-Thema für Firefox.
```
cd WhiteSur-firefox-theme && bash install.sh && cd ..
```
> von [VinceLiuice](https://github.com/vinceliuice/WhiteSur-firefox-theme)

Erstellen sie einen Rand von 16p im Terminal.
```
cp gtk.css ~/.config/gtk-3.0/
```
<br />

## LY - Displaymanager
LY ist ein schlichter Displaymanager im Konsolen-Design.
```
yay -S ly
sudo systemctl disable lightdm.service
sudo systemctl enable ly.service
```

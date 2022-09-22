# Optisches Setup für Arch <br />
## Installation von Programmen
Die grundlegend wichtigsten Programme werden installiert. Unwichtige, vorinstallierte Programme werden gelöscht.
```
sudo pacman -Syyu firefox plank zsh ranger tilix refind nautilus geany git engrampa
sudo pacman -R xfce4-terminal mousepad
sudo nano /etc/nanorc
```
> Syntax-Highlighting aktivieren 

<br />

## YAY - AUR-Helper
```
cd /opt/
sudo git clone https://aur.archlinux.org/yay
sudo chown -R leon:wheel yay/
cd yay
makepkg -si
cd ~
sudo rm -r yay/
``` 
<br />

## ZSH and Oh My ZSH
```
chsh -s /usr/bin/zsh
sudo chsh -s /usr/bin/zsh
zsh
bash install.sh
cp -r Plugins/* ~/.oh-my-zsh/custom/plugins
cp .zshrc ~
source ~/.zshrc
```
<br />

## Vala Panel
```
sudo pacman -S gobject-introspection
yay -S vala-panel-appmenu-common-git vala-panel-appmenu-registrar-git 
yay -S vala-panel-appmenu-xfce-git
yay -S appmenu-gtk-module-git
xfconf-query -c xsettings -p /Gtk/ShellShowsMenubar -n -t bool -s true
xfconf-query -c xsettings -p /Gtk/ShellShowsAppmenu -n -t bool -s true
```
- AppMenü zu Leiste hinzufügen
<br />
 
## Themen
Kopieren sie die Themen, Icon-Pakete und Fonts in die Systemverzeichnisse. Nutzen sie wenn nötig `sudo`.
```
mkdir ~/.themes
mkdir ~/.icons
cp -r Themen/* ~/.themes
cp -r Icons/* ~/.icons
sudo cp Fonts/* /usr/share/fonts
cd Icons/Borealis-cursors
sudo bash install.sh
cd -
```
> - XFCE: [macOS Light](https://github.com/zayronxio/Mkosbigsur-gtk), [macOS Dark](https://github.com/B00merang-Project/macOS-Dark), [BigSur-Icons](https://github.com/zayronxio/Mkos-Big-Sur), [Catalina-Icons](https://github.com/zayronxio/Os-Catalina-icons), [Borealis-Cursors](https://github.com/alvatip/Borealis-cursors)
<br />

Kopieren sie die Hintergünde in den `backgrounds`-Ordner.
```
sudo cp -r Wallpaper/* /usr/share/backgrounds/
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

## Purify Farbschemen
> [Purify](https://github.com/kyoz/purify0) von Kyoz

<a href="https://imgbox.com/FVl9f8Ce" target="_blank"><img src="https://thumbs2.imgbox.com/4e/06/FVl9f8Ce_t.png" alt="image host"/></a>
Farbschemen für ZSH, Ranger und Tilix.

Erstellen der passenden Verzeichnisse für Ranger und Tilix 
```
mkdir ~/.config/ranger/colorschemes
mkdir ~/.config/tilix/schemes
```

Kopieren sie nun die Datein in ihr Verzeichnisse.
```
cp Purify/purify.zsh-theme ~/.oh-my-zsh/custom/themes/	  # ZSH
cp Purfiy/default.py ~/.config/ranger/colorschemes/	  	  # Ranger
cp Purify/purify.json ~/.config/tilix/schemes			  # Tilix
```
<br />

## Touchpad - Tippen um zu Klicken
```
sudo cp 30-touchpad.conf /etc/X11/xorg.conf.d/
```
- zum Aktivieren des Linksklick durch tippn auf dem Touchpad 
<br />

## rEFInd - Bootmanager
Installiert das macOS-Thema für den rEFInd-Bootmanager.

<a href="http://imgbox.com/V9FDFr5B" target="_blank"><img src="https://thumbs2.imgbox.com/4b/f5/V9FDFr5B_t.png" alt="imgbox"/></a>
```
refind-install
sudo cp -r refind /boot/efi/EFI
```
<br />

## LY - Displaymanager
LY ist ein schlichter Displaymanager im Konsolen-Design.

<a href="http://imgbox.com/ahK81Qtk" target="_blank"><img src="https://thumbs2.imgbox.com/33/8e/ahK81Qtk_t.png" alt="imgbox"/></a>
```
yay -S ly
sudo systemctl disable lightdm.service
sudo systemctl enable ly.service
```

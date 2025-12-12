https://www.raspberrypi.com/news/heating-and-cooling-raspberry-pi-5/

watch -n 2 vcgencmd measure_temp

https://www.raspberrypi.com/documentation/computers/configuration.html#secure-your-raspberry-pi

https://forums.raspberrypi.com/viewtopic.php?t=133691

sudo apt install mate-desktop-environment
sudo nano /etc/lightdm/lightdm.conf
* #greeter-session=pi-greeter-labwc
* greeter-session=lightdm-gtk-greeter

sudo update-alternatives --config x-session-manager

esp flash
* venv
* download image
* activate venv
* (venv) python -m pip install esptools
* flash device

python3 -u -m esptool --port /dev/ttyUSB0 --chip esp32 --baud 115200 write-flash --flash-mode keep --flash-size keep --erase-all 0x1000 ~/Downloads/ESP32_GENERIC-20251209-v1.27.0.bin


https://forums.raspberrypi.com/viewtopic.php?t=373028

sudo apt update && sudo apt install --ignore-missing -y \
  gnome-core \
  yaru-theme-{gnome-shell,gtk,icon,sound,unity} \
  fonts-ubuntu fonts-ubuntu-{title,console} ttf-mscorefonts-installer \
  rpi-chromium-mods chromium chromium-common chromium-driver chromium-l10n gnome-browser-connector \
  rhythmbox rhythmbox-plugins rhythmbox-plugin-alternative-toolbar \
  gstreamer1.0-plugins-{base,good,bad,ugly} gstreamer1.0-{libav,tools,alsa,pulseaudio,x,gl,vaapi,pipewire} libwidevinecdm0 \
  libreoffice-{writer,calc,impress,gtk3,gnome} \
  gnome-text-editor simple-scan hplip file-roller \
  network-manager-openvpn-gnome \
  gnome-tweaks gnome-calendar gnome-weather \
  plymouth plymouth-themes gnome-shell-extension-dashtodock gnome-shell-extension-desktop-icons-ng gnome-shell-extensions \
  dbus-x11 || true && \
sudo systemctl set-default graphical.target && \
sudo reboot 

# RPi Stuff

https://www.raspberrypi.com/news/heating-and-cooling-raspberry-pi-5/

watch -n 2 vcgencmd measure_temp

watch cat /sys/devices/platform/cooling_fan/hwmon/hwmon2/fan1_input

https://www.raspberrypi.com/documentation/computers/configuration.html#secure-your-raspberry-pi

https://forums.raspberrypi.com/viewtopic.php?t=133691

sudo apt install mate-desktop-environment
sudo nano /etc/lightdm/lightdm.conf
* #greeter-session=pi-greeter-labwc
* greeter-session=lightdm-gtk-greeter

sudo update-alternatives --config x-session-manager

sudo apt install rp-bookshelf 

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

sudo apt install lm-sensors gnome-shell-extension-freon


# Micropython esp32xx standard build flash

esp flash
* venv
* download image
* activate venv
* (venv) python -m pip install esptools
* flash device

python3 -u -m esptool --port /dev/ttyUSB0 --chip esp32 --baud 115200 write-flash --flash-mode keep --flash-size keep --erase-all 0x1000 ~/Downloads/ESP32_GENERIC-20251209-v1.27.0.bin


# LVGL custom Micropython BUILD for CYD 

* https://github.com/lvgl-micropython/lvgl_micropython/tree/main

1. build

cd ~/workspace/lvgl_micropython

python3 make.py esp32 BOARD=ESP32_GENERIC DISPLAY=ILI9341 INDEV=XPT2046 clean

2. flash

cd ~/workspace/lvgl_micropython/build

cd python3 -u -m esptool --port /dev/ttyUSB0 --chip esp32 --baud 115200 write-flash --flash-mode keep --flash-size keep --erase-all 0x0 ./lvgl_micropy_ESP32_GENERIC-4.bin


# ulab custom Micropython build

0. For the most part follow build instructions in: https://github.com/micropython/micropython/blob/master/ports/esp32/README.md 
1. But then before final build, see: https://github.com/orgs/micropython/discussions/17225
2. Use: ```MICROPY_ROM_TEXT_COMPRESSION OFF``` in  ```esp32_common.cmake```
3. In micropython esp32 dir: ```make submodules``` followed by ```make USER_C_MODULES=${BUILD_DIR}/micropython-ulab/code/micropython.cmake```
4. Should build. Then flash and test.


# Interesting Projects/Ideas/Examples

GitHub - lspr98/bike-computer-32: Simple open source bike computer based on an ESP32-C3. Supports OSM-offline maps, GPX-track rendering and Multi-Constellation GNSS positioning. 
* https://share.google/EsLgX9GNUgv25chDK

ECUMaster Black + ESP32 Bluetooth Display: 
* https://github.com/danuecumaster/ECUMaster-Black-ESP32-Bluetooth-Display

Temp and Humidity:
* https://github.com/fabse-hack/temp_humidity_micropython_lvgl/tree/main#

Using the CYD: All Clones are Not Created Equal! 
* https://youtu.be/agfuTNZGGl4
* https://resinchemtech.blogspot.com/2025/08/cyd.html

Detailed CYD tutorial:
* https://docs.freenove.com/projects/fnk0103/en/latest/fnk0103/codes/tutorial.html
* https://github.com/Freenove/Freenove_ESP32_Display
* https://github.com/Freenove/Freenove_ESP32_Display/blob/main/Main_Tutorial.pdf
* Cheap Black Display (esp32-S3): https://www.amazon.com.au/Freenove-Supporting-XiaoZhiAI-Dual-core-Microcontroller/dp/B0FSQF6FKN/ref=sr_1_45?sr=8-45

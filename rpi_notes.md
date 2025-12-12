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

esp flash
* venv
* download image
* activate venv
* (venv) python -m pip install esptools
* flash device

python3 -u -m esptool --port /dev/ttyUSB0 --chip esp32 --baud 115200 write-flash --flash-mode keep --flash-size keep --erase-all 0x1000 ~/Downloads/ESP32_GENERIC-20251209-v1.27.0.bin

sudo apt install rp-bookshelf 


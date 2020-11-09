# microbit-arduino-howto

How to get micro:bit working in the Arduino IDE on Fedora. Based heavilly on this guide:

https://learn.adafruit.com/use-micro-bit-with-arduino/install-board-and-blink


1. Add new board manager URL (Preferences):
    * https://sandeepmistry.github.io/arduino-nRF5/package_nRF5_boards_index.json
2. Install nrf boards support (Tools -> Board -> Boards manager
    *. search for nrf5, install "Nordic Semiconductor nRF5 Boards"
3. Install systemd-libs.i686 to provide libudev1:i386
    *. dnf install systemd-libs.i686
4. Create an udev rule to allow user to access the microbit
    1. create "/etc/udev/rules.d/99-microbit.rules":
         1. ATTRS{idVendor}=="0d28", ATTRS{idProduct}=="0204", MODE="666"
    2. udevadm control --reload-rules
5. Plug in the microbit
6. Set port in arduino IDE as usual
7. Use microbit-blink.ino from this repo
8. Compile & upload

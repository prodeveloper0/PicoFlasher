## Build PicoFlasher on Ubuntu

Some Raspberry Pi Pico with prebuilt binary from `X360/PicoFlasher` are recognized not a serial port but unknown device (Device Descriptor Request Failed) in device manager.

I think it is USB compatibility issue of TinyUSB of old version. so building own PicoFlasher with latest version of TinyUSB may solve (or solved) the problem.

## Install `picotool`
Download and install dependencies
```bash
sudo apt install build-essential pkg-config libusb-1.0-0-dev git cmake gcc-arm-none-eabi libnewlib-arm-none-eabi
wget https://raw.githubusercontent.com/raspberrypi/pico-setup/master/pico_setup.sh
chmod +x pico_setup.sh
SKIP_VSCODE=1 SKIP_UART=1 bash ./pico_setup.sh
```

Build and install `picotool`
```bash
cd ~/pico/picotool
git submodule update --init
cmake .
make
sudo make install
```

## Build `PicoFlasher`
```bash
cd $PICOFLASHER_PATH
cmake
make
```
After building `PicoFlasher`, flashing compiled `PicoFlasher.uf2` file on project root path.

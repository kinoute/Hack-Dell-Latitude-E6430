# Dell Latitude E6430 Hackintosh

![System Specs](https://raw.githubusercontent.com/kinoute/Hack-Dell-Latitude-E6430/master/Pictures/system.png)

I have already a [Hackintosh](https://github.com/kinoute/Hack-Z370-HD3P-i5-8400) at home running smoothly. I was given an old laptop at work, a Dell Latitude E6430, and couldn't resist to try to install macOS on it despite its age. It worked!

## Laptop Specs

* macOS Mojave 10.4.4
* Intel Core i5-3320M 2.6Ghz Turbo 3.3Ghz (2 cores, 4 threads)
* Crucial Ballistix Sport 16GB DDR3-RAM @ 1600 Mhz (BLS8G3N169ES4.16FE)
* Intel HD Graphics 4000 1536 Mb
* Crucial MX200 250 GB SSD (Crucial_CT250MX200SSD1)
* 14" HD 1366x768 Screen
* MATSHITA DVD+/-RW UJ8B2

**Note:** My model doesn't have a Nvidia Card. If you have one, my install might not work for you.


### What works:
* Sound (in and out)
* Trackpad with gestures
* USB Ports
* DVD Player
* Webcam (tested with Photobooth)
* LAN/Ethernet
* Fn keys to change volume or brightness
* Sleep/Wake-up
* Battery percentage/status

### Doesn't work natively / Not tested
* Wifi (need to change internal card) ; I use a [TP-Link-TL-WN725N](https://www.tp-link.com/us/home-networking/usb-adapter/tl-wn725n/) USB Dongle since I don't own the laptop
* Bluetooth
* SD Card Reader (not tested)
* HDMI/VGA out (not tested yet)

## BIOS

### Flashing your BIOS

First thing you need to do is to flash your BIOS if you're running an old one like A02/A03. I flashed mine to the A12 version which seems to work fine. If you already have a recent version superior to mine, I can't guarantee that my install will work for you. Some had to downgrade first to A02/A03 then flash to A12 in order to install.

You can find the A12 BIOS here: https://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=TW3TN&osCode=w732&productCode=latitude-e6430&lwp=rt

Read carefully the installation instructions. It's pretty straight-forward though: download their `.exe` file and you can start the flashing directly from Windows. It will reboot your machine and finish the work.

### BIOS Settings

Once you have the correct BIOS version, go to the BIOS by using the `F12` key at boot. Click on "Load defaults" then set SATA Operations to `AHCI`, set Boot List Option to `UEFI` and Disable Secure Boot.

### Creating the USB Installer

You will need a 16+ GB USB, a Mac and an internet connection to download the Mojave Installer.
Open the AppStore, search for "macOS Mojave", download the app.

While it's downloading, use Disk Utility to format your USB Drive as Mac OS X Extended (Journaled) and rename your USB stick to "USB" (just to be easier). Once the download is done, open the Terminal and write:

`sudo "/Applications/Install macOS Mojave.app/Contents/Resources/createinstallmedia" --volume /Volumes/USB`

It will copy the installer to your USB Stick and make it bootable. It can take some time.

### Install Clover on the USB Installer

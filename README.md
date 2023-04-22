# pi-hole
Documentation and scripts for pi-hole

## Environment 

Raspberry Pi 4 Model B 2 GB
- [Specifications](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/specifications/)
- [Raspberry Pi 4 Model B product brief](https://datasheets.raspberrypi.com/rpi4/raspberry-pi-4-product-brief.pdf)
- [Raspberry Pi 4 Model B schematic diagrams](https://datasheets.raspberrypi.com/rpi4/raspberry-pi-4-reduced-schematics.pdf)
- [Raspberry Pi 4 Model B mechanical drawing](https://datasheets.raspberrypi.com/rpi4/raspberry-pi-4-mechanical-drawing.pdf)
- [Documentation including hardware and configuration](https://datasheets.raspberrypi.com/rpi4/raspberry-pi-4-mechanical-drawing.pdf)

## Setup the PI

The following sections cover the setup that I did for the Pi and Pi-hole

### Setting up the PI OS

1. Need to install the PI OS and flash the SD card do this with the Raspberry Pi Imager
   - Download and install the Raspberry Pi Imager [here](https://www.raspberrypi.com/software/)

2. Run Raspberry Pi Imager
![](assets/raspberry-pi-imager.png)
3. Select the OS
   -  I am running "Raspberry PI (64 bit)" or the "Lite" version depending on if I don't want a desktop and will be 
      running it headless.
   - These are based on Debian
![](assets/raspberry-pi-imager-os-selection.png)
4. Select the storage device to write to. (SD card)
5. Click the gear icon and make sure seeting are how you want them to be.
   - Enable SSH
   - Setup user and password
   - Enable/disable wireless
6. Click write
   - took between 10-20 minutes
   - eject the card and put it into the Pi
7. Connect to either NET
8. Power on the Pi

### Install pi-hole
- [Pi-hole](https://pi-hole.net/)
- [Pi-hole documentation](https://docs.pi-hole.net/)
- [Install steps](https://github.com/pi-hole/pi-hole/#one-step-automated-install)

1. SSH into Pi
 ```bash
  ssh admin@192.168.68.116
 ```
  - Note: I have setup reservation for the IP for the MAC address of the Pi.

2. Run install script
 ```bash
  curl -sSL https://install.pi-hole.net | bash
 ```

3. Update the Raspberry Pi
 ```bash
  # answer any prompts
  sudo apt update
  sudo apt full-upgrade
  sudo reboot
 ```

If you run into issues with above that the file is locked run the following.
 ```bash
   sudo touch /forcefsck
   subo reboot
 ```

4. setup the default resolver for DNS on the Pi
   - Want to do this so the Pi can resolve addresses if needed.
 ```bash
  sudo nano /etc/resolv.conf
 ```
Set the following in the file.
 ```bash
   nameserver 2001:558:feed::1
   nameserver 2001:558:feed::2
 ```

### Configuring Pi to auto update
cron job anyone

### Configuring devices

### Setting up router

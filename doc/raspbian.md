# Raspbian

## Base  Iso

There are many images that you can start iwth. I'm attempting to start off with the most light wight version and only add.  I do plan at some point soon in the future switching over to a Kubernetes cluster.

## Headless

### Default to Bash/SSH

To set any Raspberry Pi in headless mode, you'll only need your Pi with pre-loaded Raspbian OS (latest is Stretch) and your Wi-Fi network.
Make sure you know your Wi-Fi SSID and Password in order to perform headless setup.

Once you've burned/etched the Raspbian image onto the microSD card, connect the card to your working PC and you'll see the card being mounted as "boot". Inside this "boot" directory, you need to make 2 new files. You can create the files using Atom code editor.

Step 1: Create an empty file. You can use Notepad on Windows or TextEdit to do so by creating a new file. Just name the file ssh. Save that empty file and dump it into boot partition (microSD).

Step 2: Create another file name wpa_supplicant.conf . This time you need to write a few lines of text for this file. For this file, you need to use the FULL VERSION of wpa_supplicant.conf. Meaning you must have the 3 lines of data namely country, ctrl_interface and update_config

```bash

country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="your_real_wifi_ssid"
    scan_ssid=1
    psk="your_real_password"
    key_mgmt=WPA-PSK
}

```

### Change Keyboard Configuration

To change the Raspbian keyboard you need to modify the keyboard config file.

```bash

sudo nano /etc/default/keyboard

```

Keyboard - look for the uk and change it to your type (us will do us, aus, can, nz etc). Then save and exit.

## Basic

### Network Management

Wicd is a network connection manager that can manage wireless and wired interfaces, similar and an alternative to NetworkManager.

### Get IP address

```bash

ip addr show

```

### Install dotnet Core

## Runtime Setup

Install .NET Core on Raspbain

https://www.microsoft.com/net/download/linux

Please note that you cannot do any development on the Raspberry Pi as the .NET Core SDK does not support ARM processesors.  From my reading it doesn't sound like this will be changing any time soon.

https://github.com/debian-pi/raspbian-ua-netinst
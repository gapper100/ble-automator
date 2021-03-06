ble-automator
======================================
Automate interactions with a BLE device.

Some of the scripts have hardcoded addresses.


## How to use:

The file bleAutomator.py contains handy function to write and read data to a BLE device.
An example usage is currentRecord.py which uses it to sample current usage of the crownstone.

Use the scripts like:

    ./turnoff.py -i hci0 -a E5:C8:68:8A:BB:9C


### How to use the Powermate

To run the script that connects with the PowerMate button, you will first need to add it:

    sudo hcitool lewladd 00:12:92:08:05:16

If you set a random address for yourself, with for example `-t random` as argument you will need to do this again. Or else you will encounter this error:

    [   ][00:12:92:08:05:16][LE]> connect
    Connecting... connect error: Transport endpoint is not connected (107)

During the connection attempt you will have to press the button!

## Prerequisite:

Prior to running, install:

* bluez
* python 2.7
* [bluepy](https://github.com/IanHarvey/bluepy) - Currently you have to get an older version:
  * `sudo apt-get install git build-essential libglib2.0-dev libdbus-1-dev python-dev`
  * `git clone https://github.com/IanHarvey/bluepy.git`
  * `cd bluepy`
  * `git checkout v/0.9.11`
  * `python setup.py build`
  * `sudo python setup.py install`
* intelhex

```
sudo apt-get install bluez python-pip
sudo pip install pexpect
sudo pip install intelhex --allow-unverified intelhex
sudo pip install pycrypto
```

======================================

## Create .zip file for Nordic app

The following will create a .zip file with a .bin binary, a Manifest file and a .dat file.

	python dfGenPkg.py -a crownstone.hex

This used to create a .zip file with a .hex file, but that doesn't play well with DFU version 0.8.

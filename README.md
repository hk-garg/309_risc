NVIDIA Jetson Xavier NX Setup Guide
This guide outlines the steps to set up the NVIDIA Jetson Xavier NX Developer Kit on a laptop running Windows, macOS, or Linux.
Prerequisites

NVIDIA Jetson Xavier NX Developer Kit
MicroSD card (16GB or larger, UHS-I speed class recommended)
Laptop with internet connection and SD card reader
Micro USB cable
HDMI monitor, USB keyboard, and mouse
Power supply (12V, 2A or higher, barrel connector)
NVIDIA Developer account

Steps

Download JetPack SD Card Image

Visit NVIDIA Developer Downloads.
Select Jetson > Jetson Xavier NX Developer Kit under SD Card Image Method.
Log in or register for a free NVIDIA Developer account.
Download the latest Jetson Xavier NX SD Card Image (JetPack).


Flash MicroSD Card

Insert the microSD card into your laptop.
Format the card using SD Memory Card Formatter.
Use Balena Etcher:
Select the downloaded JetPack image (.zip file).
Choose the microSD card as the target.
Click Flash to write the image.


Alternatively, use command line (Linux/macOS example):unzip ~/Downloads/jetson-nx-developer-kit-sd-card-image.zip | sudo dd of=/dev/sdx bs=1M status=progress

Replace /dev/sdx with your microSD card’s device name.


Set Up Jetson Xavier NX

Insert the flashed microSD card into the slot on the underside of the Jetson Xavier NX module (label facing up, until it clicks).
Connect the Jetson to:
HDMI monitor via HDMI port.
USB keyboard and mouse via USB ports.
Power supply via barrel connector (9-16V, not the 19V supply included).


Connect the micro USB cable to your laptop for data transfer (not power).


Boot and Initial Configuration

Power on the Jetson (green LED near micro USB port lights up).
Follow on-screen prompts to:
Accept the EULA.
Select language, keyboard, and time zone.
Set a username and password (e.g., username: nvidia, password: nvidia for simplicity).


The Jetson boots to the Ubuntu desktop (18.04 or 20.04, depending on JetPack version).


Install JetPack Components

On your laptop, download and install NVIDIA SDK Manager.
Run SDK Manager:sudo dpkg -i sdkmanager_<version>_amd64.deb


Log in with your NVIDIA account.
Select Jetson Xavier NX as target hardware and the matching JetPack version.
Keep the micro USB cable connected for virtual Ethernet (IP: 192.168.55.1 for Jetson, 192.168.55.100 for laptop).
Follow prompts to install libraries and drivers (ensure username/password match Jetson setup).
After installation, reboot the Jetson.


Verify Setup

Log in to the Ubuntu desktop.
Open a terminal and check system status:nvcc --version

This confirms CUDA installation.
Optionally, configure WiFi:nmcli r wifi on
nmcli d wifi list
nmcli d wifi connect <SSID> password <PASSWORD>





Notes

Ensure the power supply is 12V 2A (or higher, up to 16V). The included 19V supply may not be compatible with some setups.
For NVMe SSD booting, follow this guide after initial setup.
Refer to NVIDIA Jetson Xavier NX Getting Started for detailed documentation.

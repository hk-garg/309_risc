# NVIDIA Jetson Xavier NX Setup Guide

This guide outlines the steps to set up the NVIDIA Jetson Xavier NX Developer Kit on a laptop running Windows, macOS, or Linux.

## Prerequisites
- NVIDIA Jetson Xavier NX Developer Kit
- MicroSD card (16GB or larger, UHS-I speed class recommended)
- Laptop with internet connection and SD card reader
- Micro USB cable
- HDMI monitor, USB keyboard, and mouse
- Power supply (12V, 2A or higher, barrel connector)
- NVIDIA Developer account

## Steps

1. **Download JetPack SD Card Image**
   - Visit [NVIDIA Developer Downloads](https://developer.nvidia.com/downloads).
   - Select *Jetson* > *Jetson Xavier NX Developer Kit* under SD Card Image Method.
   - Log in or register for a free NVIDIA Developer account.
   - Download the latest Jetson Xavier NX SD Card Image (JetPack).

2. **Flash MicroSD Card**
   - Insert the microSD card into your laptop.
   - Format the card using [SD Memory Card Formatter](https://www.sdcard.org/downloads/formatter/).
   - Use [Balena Etcher](https://www.balena.io/etcher/):
     - Select the downloaded JetPack image (.zip file).
     - Choose the microSD card as the target.
     - Click *Flash* to write the image.
   - Alternatively, use command line (Linux/macOS example):
     ```bash
     unzip ~/Downloads/jetson-nx-developer-kit-sd-card-image.zip | sudo dd of=/dev/sdx bs=1M status=progress
     ```
     Replace `/dev/sdx` with your microSD card’s device name.

3. **Set Up Jetson Xavier NX**
   - Insert the flashed microSD card into the slot on the underside of the Jetson Xavier NX module (label facing up, until it clicks).
   - Connect the Jetson to:
     - HDMI monitor via HDMI port.
     - USB keyboard and mouse via USB ports.
     - Power supply via barrel connector (9-16V, not the 19V supply included).
   - Connect the micro USB cable to your laptop for data transfer (not power).

4. **Boot and Initial Configuration**
   - Power on the Jetson (green LED near micro USB port lights up).
   - Follow on-screen prompts to:
     - Accept the EULA.
     - Select language, keyboard, and time zone.
     - Set a username and password (e.g., username: `nvidia`, password: `nvidia` for simplicity).
   - The Jetson boots to the Ubuntu desktop (18.04 or 20.04, depending on JetPack version).

5. **Install JetPack Components**
   - On your laptop, download and install [NVIDIA SDK Manager](https://developer.nvidia.com/nvidia-sdk-manager).
   - Run SDK Manager:
     ```bash
     sudo dpkg -i sdkmanager_<version>_amd64.deb
     ```
   - Log in with your NVIDIA account.
   - Select *Jetson Xavier NX* as target hardware and the matching JetPack version.
   - Keep the micro USB cable connected for virtual Ethernet (IP: 192.168.55.1 for Jetson, 192.168.55.100 for laptop).
   - Follow prompts to install libraries and drivers (ensure username/password match Jetson setup).
   - After installation, reboot the Jetson.

6. **Verify Setup**
   - Log in to the Ubuntu desktop.
   - Open a terminal and check system status:
     ```bash
     nvcc --version
     ```
     This confirms CUDA installation.
   - Optionally, configure WiFi:
     ```bash
     nmcli r wifi on
     nmcli d wifi list
     nmcli d wifi connect <SSID> password <PASSWORD>
     ```

## Notes
- Ensure the power supply is 12V 2A (or higher, up to 16V). The included 19V supply may not be compatible with some setups.[](https://f1tenth.readthedocs.io/en/stable/getting_started/software_setup/optional_software_nx.html)[](https://f1tenth.readthedocs.io/en/foxy_test/getting_started/software_setup/optional_software_nx.html)
- For NVMe SSD booting, follow [this guide](https://developer.ridgerun.com/wiki/index.php?title=How_to_flash_and_boot_a_Jetson_from_NVMe_SSD) after initial setup.[](https://github.com/jetsonhacks/bootFromExternalStorage)
- Refer to [NVIDIA Jetson Xavier NX Getting Started](https://developer.nvidia.com/embedded/learn/get-started-jetson-xavier-nx-devkit) for detailed documentation.[](https://developer.ridgerun.com/wiki/index.php/Jetson_Xavier_NX/Introduction/Getting_Started)

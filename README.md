# Jackal-Jetson-Xavier-NX-SDK

## Overview

The **Jackal-Jetson-Xavier-NX-SDK** repository provides a comprehensive software development kit (SDK) for integrating the Jackal robot with the NVIDIA Jetson Xavier NX hardware. This SDK allows users to leverage the Jetson Xavier NX's computational power to enhance the Jackal platform for advanced robotics applications.

This SDK contains the following preinstalled software:
- Ubuntu 20.04
- Nvidia Drivers
- ROS2 Humble
- Jackal Packages
- Self Developed On-Boot TeleOp Control

Simply Get the image into an SD card following the steps below and connect your Jetson Xavier NX onto your Jackal Robot.

We are assuming you are running Micro-ROS on the Jackal Motors Drivers PCB, if you have not done this step, please visit the section **Updating Firmware** in this website [Micro-ROS-Jackal](https://www.clearpathrobotics.com/assets/guides/foxy/jackal/JackalInstallRobotSoftware.html).

## Getting Started

### Prerequisites

Before getting started, make sure you have the following:

- **NVIDIA Jetson Xavier NX**: Ensure you have the Jetson Xavier NX development board.
- **Jackal Robot with Micro-ROS**: Access to the Jackal robot is required.
- **32GB+ SD Card**: A microSD card with at least 32GB of space.
- **Linux Machine**: A Linux-based system (Ubuntu recommended) for building the image.
- **Required Tools**: 
  - `sgdisk` and `dd` utilities (for partitioning and flashing)
  - `unzip` (for extracting files)

To install these utilities on Ubuntu, you can run:
```bash
sudo apt-get install gdisk unzip
```

### Installation

1. **Clone the Repository**

   ```bash
   git clone git@github.com:PaoloReyes/Jackal-Jetson-Xavier-NX-SDK.git
   cd Jackal-Jetson-Xavier-SDK
   ```

2. **Generate Partitions Zip File**

   ```bash
   cat image_parts/zippart_* > image.zip
   ```

3. **Unzip the Partitions Binaries**

   ```bash
   unzip image.zip
   ```

4. **Prepare the Target Device** 

   Replace /dev/sdb with the correct device path (use lsblk to find your device):

   Warning: Double-check your target device to avoid overwriting important data.

   ```bash
   sudo sgdisk -l=partitions_table.gpt /dev/sdb
   ```

5. **Flash the Partitions**

   Important: Adjust the device names (/dev/sdb1, /dev/sdb2, etc.) according to your system.

   ```bash
   sudo dd if=sdb1.img of=/dev/sdb1 bs=4M status=progress
   sudo dd if=sdb2.img of=/dev/sdb2 bs=4M status=progress
   sudo dd if=sdb3.img of=/dev/sdb3 bs=4M status=progress
   ...
   sudo dd if=sdb22.img of=/dev/sdb22 bs=4M status=progress
   ```

6. **Connect and Boot your Jetson Xavier NX with the SD**

## Usage

- Default User: tomatoxplorers

- Password: Riku254

### TeleOperation

By default your Jetson will execute a service on boot called launch_teleop_jackal.service that automatically will wait for a serial connection with the robot on the port ```/dev/ttyACM0``` and launch our ROS2 node for listening a PS4 controller and move the robot in slow and fast mode (More details on teleop controls later).

If you need to change the robot port or the user executing the Micro-ROS connection, please edit the On-Boot .sh file in ```~/.scripts/launch_teleop_jackal```

### Setting up PS4 controller

The process of pairing the PS4 controller with the Jackal's computer is the following:
* Ensure the PS4 controller is fully charged before starting
* Start the bluetoothctl utility with `sudo bluetoothctl`
* Run `agent on`
* Put the PS4 controller into pairing mode by holding down the "share" and "PS" buttons until the light flashes rapidly. Once the light is flashing rapidly, the following steps must be done before the flashing stops.
* Run `scan on`
* Wait until a device called "wireless controller" appears in the list of detected devices. Then run `scan off`.
* Copy the MAC address of the wireless controller. It should be something like "70:20:84:5E:88:B5".
* Run `trust 70:20:84:5E:88:B5`, but put in the MAC address of your controller
* Run `connect 70:20:84:5E:88:B5`, but put in the MAC address of your controller
* At this point, the LED on the controller should have turned solid blue
* Close bluetoothctl with `exit`

From now your controller should auto pair each time you press the "PS" button.

### Default Controller Buttons

## Contact

For questions or support, please open an issue on the [GitHub repository](https://github.com/PaoloReyes/Jackal-Jetson-Xavier-NX-SDK/issues) or contact the project maintainer at [paolo.alfonso.reyes@gmail.com](mailto:paolo.alfonso.reyes@gmail.com).

---

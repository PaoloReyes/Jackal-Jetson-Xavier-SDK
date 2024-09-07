
---

# Jackal-Jetson-Xavier-SDK

## Overview

The Jackal-Jetson-Xavier-SDK repository provides a comprehensive software development kit (SDK) for integrating the Jackal robot with NVIDIA Jetson Xavier NX hardware. This SDK enables users to leverage the computational power of Jetson Xavier NX for advanced robotics applications using the Jackal platform.

## Getting Started

### Prerequisites

- **NVIDIA Jetson Xavier NX**: Ensure you have a Jetson Xavier development board.
- **Jackal Robot**: You should have access to a Jackal robot.
- **+32Gb SD Card**: You should haven SD card of at least 32Gb.
- **Linux Machine**: You need a linux machine to build the image.

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

4. **Create Empty Partitions on your target device** *(If your device is sdb, PLEASE CHANGE ACCORDINGLY TO YOUT DEVICE)*

   ```bash
   sudo sgdisk -l=backup_table.gpt /dev/sdb
   ```

5. **Flash the Partitions**

   ```bash
   sudo dd if=sdb1.img of=/dev/sdb1 bs=4M status=progress
   sudo dd if=sdb2.img of=/dev/sdb2 bs=4M status=progress
   sudo dd if=sdb3.img of=/dev/sdb3 bs=4M status=progress
   ...
   sudo dd if=sdb22.img of=/dev/sdb22 bs=4M status=progress
   ```

## Contact

For questions or support, please open an issue on the [GitHub repository](https://github.com/PaoloReyes/Jackal-Jetson-Xavier-NX-SDK/issues) or contact the project maintainer at [paolo.alfonso.reyes@gmail.com](mailto:paolo.alfonso.reyes@gmail.com).

---

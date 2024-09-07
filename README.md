# Jackal-Jetson-Xavier-NX-SDK

## Overview

The **Jackal-Jetson-Xavier-NX-SDK** repository provides a comprehensive software development kit (SDK) for integrating the Jackal robot with the NVIDIA Jetson Xavier NX hardware. This SDK allows users to leverage the Jetson Xavier NX's computational power to enhance the Jackal platform for advanced robotics applications.

## Getting Started

### Prerequisites

Before getting started, make sure you have the following:

- **NVIDIA Jetson Xavier NX**: Ensure you have the Jetson Xavier NX development board.
- **Jackal Robot**: Access to the Jackal robot is required.
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

## Contact

For questions or support, please open an issue on the [GitHub repository](https://github.com/PaoloReyes/Jackal-Jetson-Xavier-NX-SDK/issues) or contact the project maintainer at [paolo.alfonso.reyes@gmail.com](mailto:paolo.alfonso.reyes@gmail.com).

---

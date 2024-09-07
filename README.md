
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

2. **Install Git LFS dependency**

   - *On Debian Based Distros (e.g., Ubuntu, Debian)*:

      ```bash
      sudo apt update
      sudo apt install git-lfs
      ```


   - *On RPM-based Linux (e.g., Fedora, CentOS)*

      ```bash
      sudo yum install git-lfs
      ```
      or
      ```bash
      sudo dnf install git-lfs
      ```

   - *On Arch Based Distros*

      ```bash
      sudo pacman -S git-lfs
      ```

3. **Pull the LFS files**

   ```bash
   git lfs pull
   ```

4. **Source the Workspace**

   ```bash
   source devel/setup.bash
   ```

## Usage

### Running Examples

To test the SDK, run the provided example scripts. For instance, to start a basic navigation example, use:

```bash
roslaunch jackal_xavier_sdk navigation_example.launch
```

### Customizing

You can customize the SDK according to your needs. Modify the configuration files located in the `config` directory and update the example scripts to fit your specific use case.

## Documentation

Detailed documentation for the SDK, including API references and configuration options, can be found in the [docs](docs) directory.

## Contributing

Contributions are welcome! Please follow the [contributing guidelines](CONTRIBUTING.md) to submit your changes or improvements.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

For questions or support, please open an issue on the [GitHub repository](https://github.com/PaoloReyes/Jackal-Jetson-Xavier-SDK/issues) or contact the project maintainer at [email@example.com](mailto:email@example.com).

---

Feel free to adjust any sections to better fit the specifics of the repository or the preferences of the project maintainers!
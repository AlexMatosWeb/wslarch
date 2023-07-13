# WSLArch

![WSLArch](https://github.com/AlexMatosWeb/wslarch/blob/main/wslarch-logo.png)

## Prerequisites

Before getting started, make sure the following software is installed on your system:

- Windows 10 (version 2004 or higher)
- Windows Subsystem for Linux (WSL) enabled
- A WSL distribution installed (e.g., Ubuntu, Debian, etc.)

## Installation

Follow the steps below to install and configure Arch Linux on WSL:

1. Clone this repository to your local system:


2. Navigate to the repository directory:


3. Run the installation script:


This script will download the Arch Linux image, create an Arch Linux root file, configure your environment, and install necessary tools.

4. Follow the instructions displayed during the installation to set up your Arch Linux root password.

5. Once the installation is complete, you can launch Arch Linux in WSL using the command:


This will open a new terminal window with Arch Linux running.

## Usage

After launching Arch Linux in WSL, you can use the system as you would in a native Arch Linux installation. Some important points to note:

- You can install Arch Linux packages using the `pacman` package manager. Refer to the official Arch Linux documentation for more information on using `pacman`.
- Windows files and directories will be available within WSL at `/mnt/c`, `/mnt/d`, etc.
- WSL supports running GUI applications, allowing you to run Linux graphical applications within WSL using an X server such as Xming or VcXsrv.

## Contributing

If you wish to contribute to the project, follow these steps:

1. Fork this repository.

2. Create a new branch with your contribution:
   
3. Make desired changes and add them to the commit:


4. Commit your changes:


5. Push your changes to the remote repository:


6. Open a pull request for your changes to be reviewed and merged into the main repository.

## Issues

If you encounter any issues or have any questions about WSLArch, please open a new issue in the repository, and we'll be happy to help.

## License

This project is licensed under the [MIT License](https://github.com/AlexMatosWeb/wslarch/blob/main/LICENSE).



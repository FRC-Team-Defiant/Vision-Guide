# Software Installation

This part of guide demonstrates how PhotonVision softwares should be installed on the coprocessors. For the sake of brevity and rigor, this tutorial will be using Orange Pi 5B with 8GB RAM as a demonstration.

## Preparations

- Coprocessor of choice
- SD/TF card with ^8GB of space
- Screens and keyboards (as needed)
- Internet connectivity for the coprocessor

## Installation

### PhotonVision Prebuilt Image

If the model of the coprocessor is listed among the [releases page](https://github.com/PhotonVision/photonvision/releases), one may safely download the corresponding image for the coprocessor and load it into Balena Etcher for etching onto the TF card.

After etching is complete, plug the TF card into the coprocessor for booting. The first boot up for the coprocessor may take a few minutes, and it is vital that one acknowledges it and does not interfere with its initialization.

### Custom Image & Installation

If the model of the coprocessor is not listed among the [releases page](https://github.com/PhotonVision/photonvision/releases), it is advised not to use the prebuilt images as there may be unknown consequences. For example, the coprocessor Orange Pi 5B should not be running the Orange Pi 5 image even though 5B only features minor improvements over 5.

The solution to the installing PhotonVision should instead be using the installation script provided by official releases [1]. First, download a Debian-based linux ARM image and etch it onto the SD card and either connect the coprocessor with a screen and keyboard or SSH. Then, prepare the installation script by this command.

```shell
wget https://git.io/JJrEP -O install.sh
```

If you are in China Mainland or anywhere else that <git.io> is inaccessible, you can save the `install.sh` script in `scripts/install.sh` to your coprocessor.

Then, upon completion, run these commands.

```shell
sudo chmod +x install.sh
sudo ./install.sh
sudo reboot now
```

### Testing

After startup, use <http://photonvision.local:5800> or YourCoprocessorIP:5800 to access the coprocessor that is in the same LAN/WLAN network with the computer in use. One is not required to log in to use the vision server even when prompted.

[1]: <https://docs.photonvision.org/en/latest/docs/installation/sw_install/other-coprocessors.html>

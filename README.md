# Vision Guide

This is Team Defiant's (6399/9975) guide for implementing Vision subsystem for FRC games. A proven feasible combination of hardwares would be Orange Pi 5B 8GB RAM with USB camera mounted on OV4689, with expected performance at around 60 fps in recognizing AprilTags after proper calibration and adjustments.

This guide is a tested and simplified tutorial for incorporating computer vision on coprocessors into FRC robots via PhotonVision, a third-party, open-source, and free-to-use library. The main sources of this guide are [WPILib's Documentation for FRC](https://docs.wpilib.org/en/stable/index.html) and [PhotonVision's Official Documentation](https://docs.photonvision.org/en/latest/docs/description.html)

This guide is based on the success incorporation of PhotonVision over Orange Pi 5B and thus is guaranteed to work on identical hardwares. Despite that this guide is written with intention of maximizing compatibility over a variety of hardwares, it is recommended, however, that you look into the original documentation to ensure the support for the particular hardware combination.

## Requirements/Prerequisites

- A FRC supported coprocessor: Orange Pi, Raspberry Pi, Limelight .etc (RAM of ^8GB is recommended)
- A USB camera that supports at least 60fps of 720p video or up.
- A TF/SD card with 8GB or more storage space
- Latest image/installer from PhotonVision, which can be found in their [release](https://github.com/PhotonVision/photonvision/releases)
- Balena Etcher with version ^1.18.11, which can also be found in their [website](https://etcher.balena.io)

## Contents

- [Software Installation](docs/Installation.md)
- [Basic Configuration](docs/Configuration.md)

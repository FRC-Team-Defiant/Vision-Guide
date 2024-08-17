# Troubleshooting and Best Practices

This section of the guide is more as a reference than a how-to guide. You can look up some troubleshooting tips and known issues here. Feel free to contribute to this page.

## Troubleshooting

This part is dedicated for troubleshooting and quick reference. Follow the listed steps for a general debugging session of PhotonVision. It is recommended to follow strictly in case something is suddenly wrong, whether during competition or practicing.

### General Troubleshooting Guide

If PhotonVision was running properly but then appear to be disconnected from the robot, follow these steps. You can also use this as a pre-match checklist for checking vision system status.

1. **Check coprocessor status lights.** Your coprocessor should be up and running. Check coprocessor's user manual for a detailed status light interpretation. Continue to the next step if the coprocessor is checked to be running. Otherwise, turn on the coprocessor. If the coprocessor is unable to boot, first check if the SD card with PhotonVision image is correctly inserted, if so, troubleshoot wiring first.

2. **Check if the coprocessor correctly booted to the PhotonVision-imaged system.** If the correct OS is loaded, you should be seeing a Ubuntu or Debian system. You can use a HDMI-connected screen to check the status of the system. Some models of coprocessors feature a pre-etched OS on the board that boots up if no additional system image is provided. If not, shut down the current OS, insert/reinsert the SD card with correct image and boot again.

3. **Check networking hardware status.** Under normal connection, the LAN port on the coprocessor should be flashing green/yellow lights to indicate there are incoming/outgoing transmissions. If there are no lights, check the connection, powering, and hardware status of the network switch and robot's radio.

4. **Visit PhotonVision's web dashboard.** Connect to robot's controlling WiFI and visit <photonvision.local:5800> or <http://10.TE.AM.11:5800> in your browser to access PhotonVision's web dashboard.

    - If the browser cannot find the IP address/cannot connect, try scanning the IP addresses with tools such as `Angry IP Scanner` mentioned in the [configuration section](./Configuration.md). Target IP address should range from 10.TE.AM.0 to 10.TE.AM.255.
    - If you can find a host named `photonvision`, then you can visit that address in the browser instead. See the `Networking` section in [configuration section](./Configuration.md) for more details.
    - If the problem does not appear to be fixed, go through the previous steps for a thorough hardware check.

5. **Check configurations in PhotonVision's web dashboard.** There are a number of things that you should take note of.
    - **Camera Name**: check in main dashboard if the camera name is the same as used in code
    - **Camera Pipeline**: check if the pipeline is correctly set to `AprilTags`
    - **Team Number**: check in settings tab if the team number is correctly set.

Typically, if you encounter any problem on the field, the listed steps should be able to help you locate it. Try for a second time and pay attention to any detail if the first time cannot help you locate the problem. If you still cannot find the problem, reach out for [support](https://docs.photonvision.org/en/latest/index.html#contact-us) from PhotonVision's developers.

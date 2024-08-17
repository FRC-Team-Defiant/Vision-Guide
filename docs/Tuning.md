# Software Tuning

This section of the guide explains and goes through the process of tuning a camera and adjust necessary parameters for the video to be processed with performance and quality.

**IMPORTANT**: **DO NOT GO THROUGH STEPS IN THIS SECTION UNLESS ALL PREVIOUS STEPS ARE COMPLETED AND VERIFIED**

## Choosing a Strategy

It is vital to have a vision strategy in mind as well as tactics. A strategy would mean that vision is only used for positioning, only for targeting or both, while on the other hand a tactic would mean to use 3D vision distance measurement, Photon Pose Estimator or triangulating pose via 2D posing. It is suggested to have both strategies and tactics in mind because your later tuning process and code implementation is dependant on them.

## General Tuning

Since this guide is made for FRC, for the sake of brevity and concision, only tuning for AprilTags will be covered.

First, either note the camera name or rename the camera in PhotonVision. The name of the camera can be found on the upper right corner of the dashboard. **Take note of the camera name carefully as it will be later used in your code.**

Second, selected the correct vision pipeline from the top right of the dashboard. The name of the pipeline is of no importance, but the pipeline type should be set to `AprilTags`.

Third, lower brightness and exposure. Keep the exposure as low as possible since it takes up computational resources.

### Tuning for AprilTags

After completing initial setup, go to `AprilTag` tab in the center. You should be adjusting the following parameters.

- Tag Family: in FRC 2024 Crescendo, AprilTag family `36h11` will be used. For detailed information on how AprilTags will be used, see [FRC's official guide for AprilTags](https://firstfrc.blob.core.windows.net/frc2024/FieldAssets/Apriltag_Images_and_User_Guide.pdf)
- Decimate: trading off detection rate with detection distance. For Team 6399's reference, we have found a relatively optimal settings of 3.
- Threads: if you have a coprocessor vent shielding/case that helps cool down the CPU, then you can change it to the maximum value (different across different coprocessors). Otherwise, adjust the value down a little to avoid heat throttling.
- Refine Edges: recommended, or experiment it with different settings of `Decimate`.
- Pose Iterations: recommended to keep the value within 0~100. For Team 6399's reference, keep it at 50.
- Decision Margin Cutoff: recommended to keep it around 30. For Team 6399's reference, set to 25.

After the adjustment above, your camera should be ready to track AprilTags in 2D mode, detecting its yaw, pitch, roll, .etc. You will need further math transformations and conversions to estimate robot pose.

For a detailed explanation on the meaning of each parameter and how to adjust them with precision, see [PhotonVision's official guide](https://docs.photonvision.org/en/latest/docs/apriltag-pipelines/2D-tracking-tuning.html#tracking-apriltags) on 2D AprilTag tracking & tuning.

## 3D Tuning

3D tracking features a number of benefits such as distance measuring, 3D target data, robot pose estimation and more, but at the same time it requires a handsome amount of practice and experiments to implement.

### Calibrating Camera

To enable 3D tracking, you need to first calibrate your camera for both lens distortion and distance recognition. As quoted from [PhotonVision's guide for camera calibration](https://docs.photonvision.org/en/latest/docs/calibration/calibration.html):

```text
While any resolution can be calibrated, resolutions lower than 960x720 are often too low to provide accurate results. Additionally, high resolutions may be too performance intensive for a coprocessor like a Raspberry Pi to handle (solutions to this are being looked into). Thus, we recommend 960x720 when using 3D mode.
```

To start calibrating your camera, navigate to the `Camera` tab and begin the following setup.

- Download and print the 8\*8 chessboard calibration target. Ensure that the printer prints the target in its original size. For a 8\*8 chessboard, each black/white cell should be 1\*1 inch in height/width.
- Select resolution target: recommend to 720p and above.
- Ensure good lighting: recommend to have direct light towards calibration targets.
- Ensure enough whitespace around the printed targets
- Ensure the calibration target is completely flat and does not bend or fold in any way.
- Ensure the camera is fixed during the calibration process
- Avoid having targets that are parallel to the lens of the camera.

After the checklist above is completed, click `Start Calibrating` button and begin.

- Take calibration image only if the camera shows dots and lines that indicate capture of calibration targets.
- Take images from **various angles and distance**.
- Distance/Angle difference across images should be **as large as possible**.
- Tilt **no more than 45 degree** about each axis.
- Try to take **at least one image** in **every region of the camera**.
- Take **at least one image** that covers the total image area
- Ensure that you get **even coverage** of the lens with your image set.
- Take no less than 12 images.

After this process, your camera should be successfully calibrated. Check if your selected resolution target has calibration data, and head back to pipelines to check if 3D tag recognition is stable.

It is generally recommended that you save the calibration data and export your settings in the `Settings` tab in case the configuration files are accidentally lost.

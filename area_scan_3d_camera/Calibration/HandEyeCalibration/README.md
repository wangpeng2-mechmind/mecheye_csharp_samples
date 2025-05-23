# HandEyeCalibration Sample

With this sample, you can perform hand-eye calibration and obtain the extrinsic parameters.

This document contains instructions for building the sample and using the sample to complete hand-eye calibration.

> Note:
>
> * Currently, the samples only support hand-eye calibration of 6-axis robots.
> * For UHP series, to perform the hand-eye calibration, the **Capture Mode** parameter must be set to **Camera1**.

If you have any questions or have anything to share, feel free to post on the [Mech-Mind Online Community](https://community.mech-mind.com/). The community also contains a [specific category for development with Mech-Eye SDK](https://community.mech-mind.com/c/mech-eye-sdk-development/19).

## Prerequisites for Performing Hand-Eye Calibration

Before performing the hand-eye calibration, the following prerequisites must be met.

* The accuracy of the robot is good enough.
* The calibration board that came with the camera is correctly placed/attached.

  * For EIH mode: the calibration board should be placed inside the camera FOV.
  * For ETH mode: the calibration board should be attached to the robot flange.

* The 2D image is not overexposed or underexposed (circles on the calibration board are clearly visible).
* No parts of the calibration board are missing from the depth map.
* The camera intrinsic parameters are accurate (you can check the camera intrinsic parameters with Mech-Eye Viewer).

## Perform Hand-Eye Calibration

During Hand-Eye Calibration, you need to collect the images of the calibration board in **at least 15 different robot poses**.

The images should satisfy the following requirements:

* The entire calibration board is visible.
* The pose of the calibration board should vary enough among the images:

  * The images should capture the calibration board at different heights.
  * The images should capture the calibration board tilted in different directions.
  * The images should capture the calibration board at different tilting angles.

1. Enter the index of the camera to which you want to connect, and press the Enter key.

2. Set the model of the calibration board: enter the number that corresponds to the model labeled on the calibration board.

3. Set camera mounting mode: enter `1` if the camera is mounted in EIH mode; enter `2` if the camera is mounted in ETH mode.

4. Set the Euler angle convention: enter the number that corresponds to the Euler angle convention of your robot.

5. Move the robot to a candidate calibration pose.

6. Capture 2D image: enter `P` to capture the 2D image of the calibration board. Check if the entire calibration board is visible and if the 2D image is overexposed/underexposed.

   * If the calibration board is not entirely visible, and/or if the 2D image is overexposed/underexposed, close the image window, move your robot, and capture the 2D image again.
   * If the entire calibration board is visible, and the exposure of the 2D image is good, close the image window and proceed to the next step.

7. Recognize feature points: enter `T` to obtain the 2D image with feature point recognition results.

   * If the recognition fails, repeat steps 5 to 7 until the returned image contains recognition results.
   * If the returned image contains recognition results, the recognition succeeded. Close the image window and proceed to the next step.

8. Enter robot pose: enter `A` to input the current robot pose. Five Euler angle conventions are currently supported. Please refer to the table at the end of this file.

9. The entered pose (XYZ + Euler angle) and converted pose (XYZ + quaternions) will be displayed.

   * If the displayed poses are incorrect, press any key to re-enter the current robot pose.
   * If the displayed poses are correct, enter `y` to proceed.

10. Repeat steps 5 to 9 until you have collected images at 15 different robot poses or more.

11. Calculate extrinsic parameters: enter `C` to calculate the extrinsic parameters. The result will be displayed in the command prompt window and saved to a TXT file named `ExtrinsicParameters`.

### Supported Euler Angle Conventions

The conversion from the following Euler angle conventions to quaternions is already supported in the sample.

  | Angle input order | Euler angle convention | Robot brand               |
  | :----             | :----                  | :----                     |
  | Z-Y'-Z''          | rzyz                   | Kawasaki                  |
  | Z-Y'-X''          | rzyx                   | ABB, KUKA                 |
  | X-Y-Z             | sxyz                   | FANUC, YASKAWA, ROKAE, UR |
  | X-Y'-Z''          | rxyz                   | --                        |
  | Z-X'-Z''          | rzxz                   | --                        |

> Note:
>
>* Even using the same Euler angle convention, different robot brands might display the Euler angles in different orders. Please input the Euler angles in the order specified in the above table.
>* If the Euler angle convention used by your robot is not listed in the above table, you need to add the conversion from this Euler angle convention to quaternions in the header file.

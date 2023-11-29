# C# Samples for Mech-Eye 3D Laser Profiler

This documentation provides descriptions of Mech-Eye API C# samples for Mech-Eye 3D Laser Profiler and instructions for building the samples on Windows.

If you have any questions or have anything to share, feel free to post on the [Mech-Mind Online Community](https://community.mech-mind.com/). The community also contains a [specific category for development with Mech-Eye SDK](https://community.mech-mind.com/c/mech-eye-sdk-development/19).

## Sample List

Currently, the following samples are provided.

The samples marked with `(EmguCV)` require [Emgu.CV.runtime.windows](https://www.nuget.org/packages/Emgu.CV.runtime.windows/) to be installed via NuGet.

* [AcquireProfileData](https://github.com/MechMindRobotics/mecheye_csharp_samples/tree/master/profiler/AcquireProfileData) `(EmguCV)`  
  Acquire the profile data, generate the intensity image and depth map, and save the images.
* [AcquireProfileDataUsingCallback](https://github.com/MechMindRobotics/mecheye_csharp_samples/tree/master/profiler/AcquireProfileData)  `(EmguCV)`  
  Acquire the profile data using a callback function, generate the intensity image and depth map, and save the images.
* [AcquirePointCloud](https://github.com/MechMindRobotics/mecheye_csharp_samples/tree/master/profiler/AcquireProfileData)  
  Acquire the profile data, generate the point cloud, and save the point cloud in the CSV and PLY formats.
* [ManageUserSets](https://github.com/MechMindRobotics/mecheye_csharp_samples/tree/master/profiler/AcquireProfileData)  
  Manage user sets, such as obtaining the names of all user sets, adding a user set, switching the user set, and saving parameter settings to the user set.
* [RegisterProfilerEvent](https://github.com/MechMindRobotics/mecheye_csharp_samples/tree/master/profiler/RegisterProfilerEvent)  
Define and register the callback function for monitoring the laser profiler connection status.

## Build the Samples

### Install Required Software

Please download and install the required software listed below.

* [Mech-Eye SDK (latest version)](https://downloads.mech-mind.com/?tab=tab-sdk)
* [Visual Studio (version 2017 or above)](https://visualstudio.microsoft.com/vs/community/)

  > Note: When installing, select the following workloads and individual component.
  >
  >* Workloads in the **Desktop & Mobile** category:
  >
  >   * **.NET desktop development**
  >   * **Desktop development with C++**
  >   * **Universal Windows Platform development**
  >
  >* Individual component: **.NET Framework 4.8 targeting pack**
  > Caution: C# Mech-Eye API is developed based on .NET Framework 4.8. If .NET Framework 4.8 is not installed, the samples cannot be built.

* Emgu CV: The **AcquireProfileData** sample and the **AcquireProfileDataUsingCallback** sample contain functions that depend on the EmguCV software libraries. Therefore, Emgu CV (the .NET wrapper for EmguCV) must be installed through NuGet Package Manager in Visual Studio. For detailed instructions, refer to [the guide provided by Microsoft](https://learn.microsoft.com/en-us/nuget/consume-packages/install-use-packages-visual-studio).

### Instructions

1. Double-click **MechEyeCSharpSamples.sln** in the `profiler` folder.
2. In Visual Studio toolbar, change the solution configuration from **Debug** to **Release**.
3. In the menu bar, select **Build** > **Build Solution**. An EXE format executable file is generated for each sample. The executable files are saved to the `Build` folder, located in the `source` folder.
4. In the **Solution Explorer** panel, right-click a sample, and select **Set as Startup Project**.
5. Click the **Local Windows Debugger** button in the toolbar to run the sample.
6. Enter the index of the profiler to which you want to connect, and press the Enter key. The obtained files are saved to the `Build` folder.
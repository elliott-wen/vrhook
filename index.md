---
layout: default
---

<img style="float: right;" src="assets/ahlab.png" alt="drawing" width="200"/>


# VRHook


## Introduction

Despite the increasing popularity of VR games, one factor hindering the industry's rapid growth is motion sickness experienced by the users. Symptoms such as fatigue and nausea severely hamper the user experience.
Machine Learning methods could be used to automatically detect motion sickness in VR experiences, but generating the extensive labeled dataset needed is a challenging task. It needs either very time consuming manual labeling by human experts or modification of proprietary VR application source codes for label capturing. 
To overcome these challenges, we developed a novel data collection tool, VRhook, which can collect data from any VR game without needing access to its source code. This is achieved by dynamic hooking, where we can inject custom code into a game's run-time memory to record each video frame and its associated transformation matrices. Using this, we can automatically extract various useful labels such as rotation, speed, and acceleration. In addition, VRhook can blend a customized screen overlay on top of game contents to collect self-reported comfort scores. In this web page, we provide a real-world VR game dataset gathered using VRHook. 

## Dataset Format

For each game frame, our dataset provides the following types of data.

1. RGB Image 
![RGB](assets/rgb.jpg)

2. Motion Flow Image
![Motion Flow](assets/motion.jpg)

3. Depth Image
![Motion Flow](assets/depth3.jpg)

4. Pose Information for VR Headset and Controllers
```
struct TrackedDevicePose_t
{
	// position in tracker space
	HmdMatrix34_t mDeviceToAbsoluteTracking; 
	// velocity in tracker space in m/s
	HmdVector3_t vVelocity;		
	// angular velocity in radians/s
	HmdVector3_t vAngularVelocity;	
};
```

5. Controller Button/Trackpad Events
```
/** Holds all the state of a controller at one moment in time. */
struct VRControllerState
{
	// bit flags for each of the buttons. 
	uint64_t ulButtonPressed;
	uint64_t ulButtonTouched;
	// Axis data for the controller's analog inputs
	VRControllerAxis_t rAxis[ k_unControllerStateAxisCount ];
};
```

6. Scene Object Data
```
struct ObjectData
{
	// Object Name
    public char[] name;
    // Object Boundary
    public float[6] bounds;
    // Model Matrix
    public float[4][4] localToWorldMatrix; 
}
``` 

7. Camera Data
```
struct CameraData
{
	// Camera Name
    public char[] name;
    // Camera Boundary
    public float[4][4] view;
    // Projection Matrix
    public float[4][4] projection; 
}
``` 

8. Light Source Data
```
struct LightData
{
	// Light Name
    public char[] name;
    // Light Materials (e.g., shadow & color)
    public float[13] Material;
    // Light Position Matrix
    public float[4][4] localToWorldMatrix; 
}
```


## Access to Dataset and Tools

To acquire the dataset, please send an email to info@ahlab.org.

## License & Copyright

To be Added.

## Publication
1. E. Wen, Nanayakkara, S., Yao, R., and Lim, J. VRhook: A Data Collection Tool for VR Motion Sickness Research. The ACM Symposium on User Interface Software and Technology 2022.
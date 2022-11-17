---
layout: default
---

<img style="float: left;" src="assets/logo.png" alt="drawing" width="60"/>
<img style="float: right;" src="assets/ahlab.png" alt="drawing" width="200"/>


# VRHook


## Introduction

<p style="text-align: justify;">
Despite the increasing popularity of VR games, one factor hindering the industry's rapid growth is motion sickness experienced by the users. Symptoms such as fatigue and nausea severely hamper the user experience.
Machine Learning methods could be used to automatically detect motion sickness in VR experiences, but generating the extensive labeled dataset needed is a challenging task. It needs either very time consuming manual labeling by human experts or modification of proprietary VR application source codes for label capturing. 
To overcome these challenges, we developed a novel data collection tool, VRhook, which can collect data from any VR game without needing access to its source code. This is achieved by dynamic hooking, where we can inject custom code into a game's run-time memory to record each video frame and its associated transformation matrices. Using this, we can automatically extract various useful labels such as rotation, speed, and acceleration. In addition, VRhook can blend a customized screen overlay on top of game contents to collect self-reported comfort scores. In this web page, we provide a real-world VR game dataset gathered using VRHook. 
</p>

## Demo Video
<p align="center">
  <iframe
      width="640"
      height="480"
      src="https://www.youtube.com/embed/p83i0GB2z2Q"
      frameborder="0"
      allow="autoplay; encrypted-media"
  >
  </iframe>
</p>

## Dataset Format

For each game frame, our dataset provides the following types of data.

1. RGB Image for both eyes (JPG format, Same resolution to your VR Goggle)
![RGB](assets/rgb.jpg)

2. Motion Flow Image (JPG format. Its resolution has same width to your VR Goggle, but double the height since every motion vector is 2-dimensional).
![Motion Flow](assets/motion.jpg)

3. Depth Image from the Main Camera (JPG format. Same resolution to your VR Goggle)
![Depth Image](assets/depth3.jpg)

4. Pose Information for VR Headset and Controllers
```java
class TrackedDevicePose
{
	// position in tracker space
	float[4][4]  mDeviceToAbsoluteTracking; 
	// velocity in tracker space in m/s
	float[3]  vVelocity;		
	// angular velocity in radians/s
	float[3] vAngularVelocity;	
};
```

5. Controller Button/Trackpad Events
```java
class VRControllerState
{
	// bit flags for each of the buttons. 
	uint64_t ulButtonPressed;
	uint64_t ulButtonTouched;
	// Axis data for the controller's analog inputs
	VRControllerAxis_t rAxis[ k_unControllerStateAxisCount ];
};
```

6. Scene Object Data
```java
class ObjectData
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
```java
class CameraData
{
	// Camera Name
    public char[] name;
    // View Matrix
    public float[4][4] view;
    // Projection Matrix
    public float[4][4] projection; 
}
``` 

8. Light Source Data
```java
class LightData
{
	// Light Name
    public char[] name;
    // Light Materials (e.g., shadow & color)
    public float[13] Material;
    // Light Position Matrix
    public float[4][4] localToWorldMatrix; 
}
```

9. User Self Report From Microsoft Dial.
![report](assets/self.png)

## Game List (43 in total):
You can see the full list of games in our dataset [here](https://docs.google.com/spreadsheets/d/12zwxyRahxCtOeitROCGRJhvpuehsNMrOOzNdVHfva84/edit?usp=sharing).

## License & Copyright

VRHook does not own the copyright of the games in our datasets. For researchers and educators who wish to use the dataset for non-commercial research and/or educational purposes, we can provide access through our site under this [conditions and terms](https://docs.google.com/document/d/1uMAg4voER3MdSsZKBAkP6PPS6xhcm5kbustfjwEMXXE/edit?usp=sharing). 

## Request Access To Dataset and Tools

<form action="https://getform.io/f/6d47b2fe-1839-4f5e-a07a-73c68d0d53a1" method="POST" enctype="multipart/form-data">
   
  <label for="name">Your name:</label><br>
  <input type="text" name="name" value="" required> <br>
  <label for="email">Your email:</label><br>
  <input type="text" name="email" value="" required> <br>
  <label for="email">Your institution:</label><br>
  <input type="text" name="institution" value="" required> <br>
  <label for="description">Short research description:</label><br>
  <textarea cols="60" rows="5" type="text" name="description" value="" required></textarea><br>
  <label for="name">Please sign this <a href="https://docs.google.com/document/d/1uMAg4voER3MdSsZKBAkP6PPS6xhcm5kbustfjwEMXXE/edit?usp=sharing">form</a> and upload it here:</label>
  <input type="file" accept=".doc,.docx,.pdf" name="file" required><br>
  <input type="hidden" name="_gotcha" style="display:none !important"><br>
  <button type="submit">Submit</button>
</form>

## Citation:
The recommend citation for this system is 
```
Wen, E., Kaluarachchi, T. I., Siriwardhana, S., Tang, V., Billinghurst, M., Lindeman, R. W., ... & Nanayakkara, S. (2022, October). VRhook: A Data Collection Tool for VR Motion Sickness Research. In Proceedings of the 35th Annual ACM Symposium on User Interface Software and Technology (pp. 1-9) DOI: https://dl.acm.org/doi/abs/10.1145/3526113.3545656.
```


```bibtex
@inproceedings{wen2022vrhook,
  title={VRhook: A Data Collection Tool for VR Motion Sickness Research},
  author={Wen, Elliott and Kaluarachchi, Tharindu Indrajith and Siriwardhana, Shamane and Tang, Vanessa and Billinghurst, Mark and Lindeman, Robert W and Yao, Richard and Lin, James and Nanayakkara, Suranga},
  booktitle={Proceedings of the 35th Annual ACM Symposium on User Interface Software and Technology},
  pages={1--9},
  year={2022}
}
```

<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-82644344-1"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-82644344-1');
</script>

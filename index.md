---
layout: default
---

<img style="float: left;" src="assets/logo.png" alt="drawing" width="60"/>
<img style="float: right;" src="assets/ahlab.png" alt="drawing" width="200"/>


# VRHook


## Introduction

<p style="text-align: justify;">
Despite the increasing popularity of VR games, one factor hindering the industry's rapid growth is motion sickness experienced by the users. Symptoms such as fatigue and nausea severely hamper the user experience. Machine Learning methods could be used to automatically detect motion sickness in VR experiences, but generating the extensive labeled dataset needed is a challenging task. It needs either very time consuming manual labeling by human experts or modification of proprietary VR application source codes for label capturing. To overcome these challenges, we developed a novel data collection tool, VRhook, which can collect data from any VR game without needing access to its source code. This is achieved by dynamic hooking, where we can inject custom code into a game's run-time memory to record each video frame and its associated transformation matrices. Using this, we can automatically extract various useful labels such as rotation, speed, and acceleration. In addition, VRhook can blend a customized screen overlay on top of game contents to collect self-reported comfort scores. In this paper, we describe the technical development of VRhook, demonstrate its utility with an example, and describe directions for future research.
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

## Tool Access
We provide beta access to our tool upon email request (elliott@ahlab.org). The current tool works for VR games built atop Unity and Unreal Engines running in Windows and Oculus. 
Please send an authentic copy of the VR game to us. We will bundle and setup the VRHook tool for you. 
We are also working on a web portal system to automate this process.

We have used our tool to collect a dataset named [VR.net](https://vrnet.ahlab.org). It currently contains 12 hours videos from 10 games in 10 genres. 

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

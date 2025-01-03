# Jetson-SLAM


**The frontend of Jetson-SLAM will be released as a separate repository as-well.**

**Authors:** Ashish Kumar

![Jetson-SLAM Design](/assets/img/jetson-slam.png "Jetson-SLAM")

This repository contains Jetson-SLAM with [FULL-BA back-end](https://128.84.21.199/pdf/1610.06475.pdf)
Jetson-SLAM is a GPU-thrusted real-time SLAM library for **Monocular**, **Stereo** and **RGB-D** cameras. It can run very high speeds beyond **500FPS** on RTX-2070 and Beyond **90FPS** on Jetson-NX **@320x240** resolution. Please see the [Jetson-SLAM Paper](https://drive.google.com/file/d/1KagYH0YVSDOeBwv4oHyKrmndOF7Sc_TV/view?usp=drive_link) for rigorous results over different resolutions, GPUs and comparison with existing VO/VIO/SLAM pipelines.

**Jetson-SLAM can run alongside Deep Neural Networks. It is fully behchmarked with VGG**

# Video
<p align="center">
<a href="https://drive.google.com/file/d/16FN0FKy76R6MBdu44WzHyH3KstruOeJT/view?usp=drive_link" target="_blank" ><img align="center" src="/assets/img/video_thumbnail.png" 
alt="Jetson-SLAM" width="70%" height="70%" border="0" /></a>
</p>

<div>
<p align="center">
<img align="center" src="/assets/gif/kaistvio_circle.gif" 
alt="Jetson-SLAM" width="50%" height="50%" border="0" />
</p>


# Main Highlight

<p align="center">
<img align="center" src="/assets/img/fig1.png" 
alt="Jetson-SLAM" width="70%" height="70%" border="0" />

# 1. Main Results

### Datasets 
1. [KITTI-Benchmark](https://github.com/zinuok/VINS-MONO)

2. [EuRoC Benchmark](https://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets)

3. [KAIST-VIO Benchmark](https://github.com/url-kaist/kaistviodataset)


#### Results on KITTI Benchmark
![Results on KITTI Benchmark](/assets/img/kitti_plot.png)

![KITTI Trajectories](/assets/img/kitti_traj.png)


#### Results on EuRoC Benchmark
![Results on EuRoC Benchmark](/assets/img/euroc_plot.png)

![Results on EuRoC Benchmark](/assets/img/euroc_table.png)

![EuRoC Trajectories](/assets/img/euroc_traj.png)


#### Results on KAIST-VIO Benchmark
![Results on KAIST-VIO Benchmark](/assets/img/kaistvio_table.png)

![KAIST-VIO Trajectories](/assets/img/kaistvio_traj.png)

#### Performance with scaled versions of VGG-16 Co-existing on Jetson-NX
![Co-exating VGG performance](/assets/img/vgg.png)


### Build Instructions

	**Step-1**
	 Install the dependencies given below:

	1. OpenCV 4 (Currently tested with 4.10.0)
	2. Eigen3
	3. CUDA
	4. Pangolin
	5. cmake 3.31


	**Step-2**
	 Run build.sh

### Run Instructions

	Go to execs and run Jetson-SLAM on following choices:
	1. Run stereo_kitti for KITTI-Benchmark
	2. Run stereo_euroc for EuRoC Benchmark
	3. Run stereo_kaistvio for KAIST-VIO Benchmark
	4. Run stereo_live for live images from a Stereo-Rig. Please customize the "stereo_live_config.yaml" file for your stereo rig.
	
### Image Masks
Jetson-SLAM expects one mask for monocular/RGBD while two masks for stereo configuration. There are two mask path for each left and right image in the yaml file. Only non-zero regions in the mask shall be used to detect and extract keypoints. These masks are helpful when the camera is mounted on a structure and some part of the structure is always present in the camera field of view. Manytimes, this leads to static keypoints on the structure visible in the camera which degrades SLAM's accuracy because these points never moves w.r.t. camera.

If such requirement is not needed, one can simply create a white image of size equal to the RGB/grayscale image size that would be supplied into Jetson-SLAM.

e.g. If your RGB/grayscale image size is 240x240, simply create a mask of size 240x240 and supply the path to the yaml file. IF you need to hide some regions of the image, you can choose linux tool such as "GIMP" or any software of your choice.

### License

Jetson-SLAM is released under a [GPLv3 license].

### Bibtex citation:

     @article{kumar2023high,
	  title={High-speed stereo visual SLAM for low-powered computing devices},
	  author={Kumar, Ashish and Park, Jaesik and Behera, Laxmidhar},
	  journal={IEEE Robotics and Automation Letters},
	  year={2023},
	  publisher={IEEE}
      }



# Pedestrian Detection with IR, RGB, and LiDAR fusion
![image](https://github.com/user-attachments/assets/18f2be33-9a8a-49cd-ab7f-f6108f226d5f) 
![image](https://github.com/user-attachments/assets/692ffafb-e9bd-400f-a4fc-224509a45140) 


## Project Overview

This project demonstrates the use of multiple sensors to detect pedestrians, estimate their pose, and determine their distance from the vehicle. The sensors used include IR cameras, RGB cameras, and LiDAR units mounted on a 2016 Lincoln MKZ, equipped with:

- 2 Velodyne LiDARs
- 1 Ouster LiDAR
- 4 IR cameras
- 5 RGB cameras
- IMU
- GPS

The goal was to combine data from these sensors to accurately detect pedestrians and analyze their pose in a 3D space.

## Hardware Used

- Velodyne Lidar
- Ouster Lidar
- IR Camera
- RGB Camera

## Software Used

- **Python**: Initial implementation with YOLOv5 for object detection.
- **MATLAB**: Transitioned to MATLAB for its robust support for image, LiDAR, and ROS functions.

### Required Packages/Toolboxes

#### For MATLAB:
- Computer Vision Toolbox
- Sensor Fusion and Tracking Toolbox
- ROS Toolbox
- Mapping Toolbox

#### For Python:
- OS Module
- YOLOv5 dependencies (listed in `requirements.txt`)

## Main Code

### ROS Launch and Processing Scripts

- **export.launch**: ROS launch file to extract messages.
- **extract_lidar_camera.m**: Extracts LiDAR, RGB, and IR camera data from the bag and outputs time-synced point clouds and images for YOLO processing.
- **lidar_camera_fusion.m**: Fuses LiDAR and camera data to generate 3D bounding boxes on images and point clouds representing pedestrian pose.
- **looping.m**: Iteratively processes a series of images to generate 3D bounding boxes on images and point clouds.
- **ir_rgb_imfuse.m**: Creates and applies a transformation matrix between RGB and IR images for fusion.

#### Execution Sequence

- To process a series of images:
  1. `extract_lidar_camera.m`
  2. `looping.m`
  
- To process a single image:
  1. `extract_lidar_camera.m`
  2. `lidar_camera_fusion.m`

## YOLO Code

- **yolov5 folder**: Contains YOLOv5 implementation and detections ([YOLOv5 GitHub](https://github.com/ultralytics/yolov5)).
- **detect.py**: YOLO detection algorithm ([YOLOv5 GitHub](https://github.com/ultralytics/yolov5)).

## Additional Code

- **runYolov5OnEachImage.py**: Iteratively runs YOLO on images and sets up the detection folder for generating GIFs. Ensure that all ‘exp#’ files in the `yolov5/runs/detect` folder are deleted before running.
- **part1.m**: Extracts and synchronizes LiDAR and camera data from the bag, generates RGB and IR images for YOLO.
- **part2.py**: Executes YOLO on folders of IR and RGB images.
- **part3.m**: Calculates and displays 3D bounding boxes and poses on IR or RGB images.
- **videoProcessingCode/entireImageAndVideoProcess.m**: Initial video processing code for testing YOLO on images (outdated).
- **combineCodeForGifs.m**: Combines YOLO detection images into GIFs. Ensure correct specification of ‘exp#’ files.

#### Execution Sequence for GIFs
1. `part1.m`
2. `runYolov5OnEachImage.py`
3. `combineCodeForGifs.m`

#### Execution Sequence for 3D Bounding Boxes
1. `part1.m`
2. `part2.py`
3. `part3.m`

## Additional Files

- **finalProjectFinalPresentation.pdf**: Presentation slides for the project.

## Collaborators
1. Arvinder Singh
2. Luke Davidson
3. Uday Raghuvanshi
4. Lucas Eby



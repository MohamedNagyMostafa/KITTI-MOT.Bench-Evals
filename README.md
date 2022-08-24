# KITTI-MOT.Bench-Evals
*KITTI evaluation results for multi-object tracking using detectors with different performances.*:heavy_check_mark:

## Introduction
The purpose of this repo supports further works in multi-object tracking (MOT) to compare their work with recent benchmark models by sharing tracking results for individual ***KITTI training+evaluation*** streams. The comparison will provide an initial insight into the stability of the tracking performance of a framework. The repo includes tracking results of [(EagerMOT, 2021)](https://github.com/aleksandrkim61/EagerMOT) and [(DeepFusionMOT, 2022)](https://github.com/wangxiyang2022/DeepFusionMOT), including our framework [(DFR-FastMOT, 2023)](https://github.com/MohamedNagyMostafa/DFR-FastMOT), and *we appreciate your contribution by providing results of your/other frameworks*. It also supports different detection performances *(Poor/Moderate/High)*, so other researchers can measure the dependency of their tracking solution on the detection accuracy. 

**Note: This evaluation considers Cars only.**


## Description
### Frameworks:
We provide output results of two recent MOT frameworks ([(**EagerMOT**, 2021)](https://arxiv.org/abs/2104.14682) and [(**DeepFusionMOT**, 2022)](https://arxiv.org/abs/2202.12100), **(DFR-FastMOT, 2023)**), and we highly recommend that further researchers share their results by following the instructions mentioned in the *Submission Section*.
The frameworks are shared in the repo as follows:
- `~/[DETECTOR_PERFORMANCE]/deep/data`: refers to [(DeepFusionMOT, 2022)](https://github.com/wangxiyang2022/DeepFusionMOT) framework.
- `~/[DETECTOR_PERFORMANCE]/eager/data`: refers to [(EagerMOT, 2021)](https://github.com/aleksandrkim61/EagerMOT) framework.
- `~/[DETECTOR_PERFORMANCE]/our/data`: refers to [(DFR-FastMOT, 2023)](https://github.com/MohamedNagyMostafa/DFR-FastMOT) framework.

The folders contain all KITTI streams, 21 streams, except stream 0017 since it does not involve any Car object. 

### Evaluation tool:
We evaluate frameworks' performance using [**KITTI-Evaluation**](https://github.com/JonathonLuiten/TrackEval) tools and update the results on the table below accordingly.  
![Screenshot from 2022-08-24 14-15-42](https://user-images.githubusercontent.com/20774864/186395095-1e00c891-a000-4852-add4-d9f685a1a795.png)
**Note: Red color :red_circle: indicates the highest score per metric overall in the table, and bold styles :black_circle: indicate the highest score per metric in a block (For particular detectors)**


### Detection Models:
We classify the performance of the detector into three categories:
1. ***Poor detector***`[~/poor-detectors/..]`: 2D detector with low performance and 3D detection is obtained by projecting Pointcloud into a 2D camera frame.  
  - **2D Detection**: [**YOLOv3**](https://arxiv.org/abs/1804.02767)
  - **3D Detection**: NONE. (Pointcloud Projection) 
2. ***Moderate detector***`[~/moderate-detectors/..]`: we utilize a more sophisticated 2d detector with 3D Pointcloud projection.
  - **2D Detection**: [**RCC**](https://ieeexplore.ieee.org/document/8099570)
  - **3D Detection**: NONE. (Pointcloud Projection) 
3. ***sophisticated-detectors***`[~/sophisticated-detectors/..]`: we employ multi-detection for 2D camera frame and 3D LiDAR Pointcloud.
  - `[~/sophisticated-detectors/both_2d_rrc_3d_pointgnn]`
    - **2D Detection**: [**RCC**](https://ieeexplore.ieee.org/document/8099570)
    - **3D Detection**: [**PointGNN**](https://openaccess.thecvf.com/content_CVPR_2020/papers/Shi_Point-GNN_Graph_Neural_Network_for_3D_Object_Detection_in_a_CVPR_2020_paper.pdf)
  - `[~/sophisticated-detectors/both_2d_rrc_3d_pointrcnn]`
    - **2D Detection**: [**RCC**](https://ieeexplore.ieee.org/document/8099570)
    - **3D Detection**: [**PointRCNN**](https://arxiv.org/abs/1812.04244)
  - `[~/sophisticated-detectors/both_2d_trackrcnn_3d_pointgnn]`
    - **2D Detection**: [**TrackR-CNN**](https://github.com/VisualComputingInstitute/TrackR-CNN)
    - **3D Detection**: [**PointGNN**](https://openaccess.thecvf.com/content_CVPR_2020/papers/Shi_Point-GNN_Graph_Neural_Network_for_3D_Object_Detection_in_a_CVPR_2020_paper.pdf)
  - `[~/sophisticated-detectors/both_2d_trackrcnn_3d_pointrcnn]`
    - **2D Detection**: [**TrackR-CNN**](https://github.com/VisualComputingInstitute/TrackR-CNN)
    - **3D Detection**: [**PointRCNN**](https://arxiv.org/abs/1812.04244)    
    
## Submission :heavy_check_mark:
We encourage contributors to push their framework results to the repo to facilitate further research in this area.  Make sure that you consider the following instructions before pushing a merge request. 
### Location
You should indicate the correct location for your results based on the type of detectors utilized in the framework. You may consider the following scheme:

1 If the framework employs a mono-detector (Either 2D or 3D), then the results location should be in:
  - `[~\poor-detectors\..]`: In case you use a 2D detector that performs as sufficiently as *YOLOv3* or less.
  - `[~\moderate-detectors\..]`: In case you use an advanced 2D detector such as RCC or 3D detector with good performance. 
2. If the framework employs a multi-detector (2D and 3D), then the results should be inside the `[~\sophisticated-detectors\..]` folder.

The pushed folder should be named based on the utilized detectors, ex: `both_2d_rcc_3d_pointgnn`, which means the framework utilizes the *RCC* detector for 2D and *PointGNN* for 3D. In case of poor and moderate detectors, you may create a new folder named with detector/s that you have used.

**Note: You may push your results directly into a folder if it exists, and your full submission should be located as follow: `[DETECTOR_PERFORMANCE]/[DETECTOR_NAME]/[2d_xxx_3d_xxx]/data/`. We expect to have all KITTI training+evaluation streams seperately as shown [HERE](https://github.com/MohamedNagyMostafa/KITTI-MOT.Bench-Evals/tree/master/sophisticated-detectors/both_2d_rrc_3d_pointgnn/deep/data), except stream `0017`.** 

### Format
The data format should follow KITTI label format shown in this [Link](https://github.com/bostondiditeam/kitti/blob/master/resources/devkit_object/readme.txt) with an additiona column at the beginning for the frame id, check out below table for more illustration. 

|frame|type|truncated|occluded|alpha|2d_bbox|3d_dimensions|3d_location|rotation_y|score|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|0|Car|0|0|-1|(255,182,0,23)|(1.24,2,3,0.9)|(2.3,5.9,1.2)|-35|0

### Steps
1. Use the following command load the repo locally.
```
git clone https://github.com/MohamedNagyMostafa/KITTI-MOT.Bench-Evals
```
2. Add your framework's results as illusterated above.
3. Push your work to the repo using the following command.
```
git add .
git commit -m "[WRITE_YOUR_MSG]"
git push origin master
```

We are going to review your submission and evaluate the performance using [**KITTI-Evaluation**](https://github.com/JonathonLuiten/TrackEval) tools. If your submission has no issue, we will accept your merge request.
  
# Citation
**TBA**

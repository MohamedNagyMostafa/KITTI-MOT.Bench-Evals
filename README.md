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


## References


# Citation

**TBA**

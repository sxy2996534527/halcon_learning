# halcon_learning

## open source
### youtube channel: https://www.youtube.com/user/mvtecsoftware
1. 3D shape detection with halcon: step1: click on the "Open New Imgae Acquisition", set image acquisition interface and connection parameters; step2: open the main script, which is designed for interfacing the stereo vision system with halcon: connect and open camera, get image; step3: choose a 3D pose for viewing the 3D point cloud: ```create_pose```, then cameras are looking down approximately vertically onto the table and then we can apply a simple threshold operation to the observed depth values. step4, use function ```segment_object_model_3d``` to segments a set of 3D points given by a 3D object model with the handle ```object_model_3d``` into several sub-sets of neighbored 3D points with similar characteristics like the same normal orientation or curvature.
2. Stereo calibration with MVTec HALCON, https://www.youtube.com/watch?v=Iizs61Qg4H0, https://www.mvtec.com/services-support/videos-tutorials/single-video/stereo-calibration-with-mvtec-halcon, https://www.youtube.com/watch?v=iEjH244KRbw
3. matching: component-based, correlation-based, deformable, descriptor-based, shape-based
4. remove the background of a 3D Scene:
(1). 2D, threshold
(2). 3D, ```select_points_object_model_3d```, select only points near the camera, without the background
(3). 2D, ```sub_image```; 3D, ```distance_object_model_3d```, ```select_points_object_model_3d```
![Screenshot from 2021-09-10 14-46-41](https://user-images.githubusercontent.com/27469356/132811816-a8c079c4-1346-4806-9496-6c54cf92c945.png)
5. edge-supported surface-based 3D-matching with MVTec Halcon: a. XYZ-Mappings, ordered point clouds when the 3D coordinates are written as gray values in XYZ images; b. 3D edge extraction, 2 main adjustable parameters: MinAmplitudeRel & MaxGap; c. edge direction inspection, the viewpoint should be located roughly where the 3D scene was acquired; d. adjust the parameters in step b & c to optimize the visualization results and set them to ```find_surface_model```; e. extend the edge-supported surface-based matching with 2D images
![Screenshot from 2021-09-13 10-25-50](https://user-images.githubusercontent.com/27469356/133014911-4a704923-521f-4e91-9e2e-2b642f3cafcc.png)
![Screenshot from 2021-09-13 10-58-15](https://user-images.githubusercontent.com/27469356/133017395-74a5bfd5-f464-45da-b5bb-065f8503cb6a.png)
6. Integrate HDevelop code into a C++ application using the Library Project Export: https://www.youtube.com/watch?v=BAZGskDPDlY
7. MVTec HALCON's anomaly detection based on deep learning, [youtube](https://www.youtube.com/watch?v=uHIAs0xYzhs)

step1: preparation

step2: training

step3: evaluation

step4: inference, 训练和测试的采图光照条件要相同

![Screenshot from 2021-09-17 11-02-53](https://user-images.githubusercontent.com/27469356/133717622-c150f0f1-0e1b-4d2f-bf60-b985c4ca0a38.png)
![Screenshot from 2021-09-17 14-14-25](https://user-images.githubusercontent.com/27469356/133733616-dae2a4e3-505b-4f0a-ade5-6545dd636514.png)


## operators
### 3D object model
#### creation
1. ```clear_object_model_3d```: 释放存储资源
2. ```copy_object_model_3d```: 拷贝模型
3. ```deserialize_object_model_3d```: 与```serialize_object_model_3d```配合使用，serialize将3D模型序列化到传输流中传输，deserialize将接收的序列化3d数据反序列化为文件

## application
### 1. 金属管缺陷检测
1. 数据采集问题：一方面光照不均匀，另一方面金属表面存在凹坑、污渍、滑痕等多种干扰基于正常数据集训练的halcon缺陷检测算法
2. 人为的对于好坏采集图像的分类也存在主观性
3. 拟实施的解决方案：贴近金属管表面以获得光照均匀、正常区域表面变化很小的图像; 小区域裁减（可通过先识别定位可能的区域），进行是否存在缺陷以及缺陷种类的判断。

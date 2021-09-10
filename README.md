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
![Uploading Screenshot from 2021-09-10 14-46-41.png…]()

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

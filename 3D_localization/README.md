# 3D localization learning

## Optimize your 3D Data for Surface-based 3D-Matching with MVTec HALCON, [link](https://www.youtube.com/watch?v=Dfw7VuiSF4Y)
1. 创建模板：软件输入模型参数创建‵‵`gen_box_object_model_3d``` or 采集模板三维数据
2. check your object for unnecessary surfaces
3. 预处理——为了加速匹配模型，可以定义一些模型中的对称元素；此外可以限制旋转角度来加速匹配——check the doc of function ```set_surface_model_param```; filter out the invalid pixels by using a threshold for example; 如果三维数据存在噪点，可以在z-image上使用中值滤波
4. 匹配——解决误匹配，提高匹配精度：利用边缘信息；剔除数据背景

## Edge-supported Surface-based 3D-Matching with MVTec HALCON, [link](https://www.youtube.com/watch?v=geQa1xpu3No)
a. XYZ-Mappings, ordered point clouds when the 3D coordinates are written as gray values in XYZ images; 

b. 3D edge extraction, 2 main adjustable parameters: MinAmplitudeRel & MaxGap; 

c. edge direction inspection, the viewpoint should be located roughly where the 3D scene was acquired; 

d. adjust the parameters in step b & c to optimize the visualization results and set them to ```find_surface_model```; 

e. extend the edge-supported surface-based matching with 2D images.

更多细节，参考```find_surface_model_with_edges.hdev```说明
![Screenshot from 2021-09-13 10-25-50](https://user-images.githubusercontent.com/27469356/133014911-4a704923-521f-4e91-9e2e-2b642f3cafcc.png)
![Screenshot from 2021-09-13 10-58-15](https://user-images.githubusercontent.com/27469356/133017395-74a5bfd5-f464-45da-b5bb-065f8503cb6a.png)

## find_surface_model_with_edges.hdev
### 1. Yaw, Pitch, Roll, Omega, Phi, Kappa, [link](https://support.pix4d.com/hc/en-us/articles/202558969-Yaw-Pitch-Roll-and-Omega-Phi-Kappa-angles#How%20to%20convert%20Yaw,%20Pitch,%20Roll%20to%20Omega,%20Phi,%20Kappa)
1. Yaw, Pitch, Roll angles define the relation between the navigation coordinate system and the body coordinate system.
2. The omega, phi, kappa angles are defined as the angles used in order to rotate a (X, Y, Z) geodetic coordinate system and align it with the image coordinate system. The rotations are applied in the following order:

Kappa (κ), the rotation around the Z axis.

Phi (φ), the rotation around the Y axis.

Omega (ω), the rotation around the Χ axis


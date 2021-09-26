# 3D localization learning

## Optimize your 3D Data for Surface-based 3D-Matching with MVTec HALCON, [link](https://www.youtube.com/watch?v=Dfw7VuiSF4Y)
1. 创建模板：软件输入模型参数创建‵‵`gen_box_object_model_3d``` or 采集模板三维数据
2. check your object for unnecessary surfaces
3. 预处理——为了加速匹配模型，可以定义一些模型中的对称元素；此外可以限制旋转角度来加速匹配——check the doc of function ```set_surface_model_param```; filter out the invalid pixels by using a threshold for example; 如果三维数据存在噪点，可以在z-image上使用中值滤波
4. 匹配——解决误匹配，提高匹配精度：利用边缘信息；剔除数据背景

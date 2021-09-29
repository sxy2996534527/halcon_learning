# Applications trial

## edge extraction
1. 使用halcon算子```edges_object_model_3d```尝试对点云ply文件进行边缘提取
2. 但是```The operator supports edge extraction only from 3D object models that contain a XYZ mapping, such as models that were created with xyz_to_object_model_3d or that were obtained with a sensor that delivers the mapping.```，算子仅支持带XYZ_MAPPINGS的三维数据
3. 学习XYZ_MAPPINGS的概念、优势和生成方法，[官方说明](https://www.mvtec.com/services-support/developers-corner/article/introduction-to-xyz-mappings)

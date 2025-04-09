Cesium 官网： https://cesium.com/
# Cesium是什么
Cesium是一个跨平台、跨浏览器的展示三维地球和地图的**javascript库**

Cesium使用WebGL来进行硬件加速图形，使用时不需要任何插件支持，但是浏览器必须支持WebGL

Cesium是基于Apache2.0许可的开源程序，它可以免费的用于商业和非商业用途。

# 支持的数据格式
**影像数据：
- 影像数据：Bing、天地图、ArcGIS、OSM、WMTS、WMS等
- 地形数据：ArcGIS、谷歌、STK等
- 矢量数据：KML、KMZ、GeoJSON、TopoJSON、CZML
- 三维模型：GLTF、GLB（二进制glTF文件）
- 三维瓦片：3D Tiles（倾斜摄影、人工模型、 三维建筑物、CAD、BIM，点云数据等）
## 用途
- 支持2D,2.5D,3D 形式的地理（地图）数据展示
- 可以绘制各种几何图形、高亮区域，支持导入图片，甚至三维模型等多种数据可视化展示
- 可用于动态数据可视化并提供良好的触摸支持，支持绝大多数的浏览器和移动端浏览器
- 支持基于时间轴的动态流式数据展示

## Cesium知识体系

Cesium 是一个跨界的SDK，涉及三个知识领域 : Web前端、计算机图形学、地理信息系统（GIS）。所以想要学好Cesium，并能够利用Cesium进行二次开发，必须对Web前端、计算机图形学、GIS相关的基础知识有所掌握，当然阅读Cesum源码也是非常有必要的。计算机图形学方面建议学习《WebGL编程指南》书籍。

## Cesium学习路线

Cesium API学习由浅入深的学习路线如下图所示：

![](https://pic4.zhimg.com/80/v2-7a32e7833314deff496ff31b5f48809f_1440w.webp)


## 进阶使用

- **Web前端方向：**Cesium与webpack（裁剪以及压缩），Cesium 与vue（框架设计， 嵌入复杂业务系统），Cesium的UI（UI 设计，定制可复用的Cesium交互界面）
- **计算机图形学方向：**WebGL深入，基于Cesium 的可视化定制（视阈、水淹、水面、热力图，流场图、飞线图、扫描图）
- **数据预处理方向：**投影变换，空间索引，LOD ，3dtile 生成，数据存储，数据分发服务，解决超大空间数据如何在 Cesium上流畅可视化的问题。



对地理信信息平台进行介绍的
https://www.zhihu.com/people/ls870061011
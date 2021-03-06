# coordtransform 坐标转换
****
一个提供了百度坐标（BD09）、国测局坐标（火星坐标，GCJ02）、和WGS84坐标系之间的转换的工具模块。

## 为什么写这个模块

随着移动互联网的兴起，几乎每一个app都会去收集用户位置，如果恰好你在处理与地理定位相关的代码，并且不了解地理坐标系的话，肯定要被我大天朝各种坐标系搞晕。写这个模块的目的也是因为项目中app获取的坐标是百度sdk获取的，在做webgis可视化的时候各种偏，各种坐标不对，叠加错位。

## 当前互联网地图的坐标系现状
### 地球坐标 (WGS84)
- 国际标准，从 GPS 设备中取出的数据的坐标系
- 国际地图提供商使用的坐标系

### 火星坐标 (GCJ-02)也叫国测局坐标系
- 中国标准，从国行移动设备中定位获取的坐标数据使用这个坐标系
- 国家规定： 国内出版的各种地图系统（包括电子形式），必须至少采用GCJ-02对地理位置进行首次加密。

### 百度坐标 (BD-09)
- 百度标准，百度 SDK，百度地图，Geocoding 使用
- (本来就乱了，百度又在火星坐标上来个二次加密)

## 开发过程需要注意的事
- 从设备获取经纬度（GPS）坐标
    		如果使用的是百度sdk那么可以获得百度坐标（bd09）或者火星坐标（GCJ02),默认是bd09
    		如果使用的是ios的原生定位库，那么获得的坐标是WGS84
    		如果使用的是高德sdk,那么获取的坐标是GCJ02
- 互联网在线地图使用的坐标系
		火星坐标系：
    			iOS 地图（其实是高德）
    			Google国内地图（.cn域名下）
    			搜搜、阿里云、高德地图、腾讯
		百度坐标系：
    			当然只有百度地图
		WGS84坐标系：
    			国际标准，谷歌国外地图、osm地图等国外的地图一般都是这个
# 举个例子
app使用的是百度的sdk,需要对定位坐标做web可视化效果，百度地图提供的js api满足不了需求，选用leaflet来做可视化，这里要说到百度地图了，它使用的坐标系和切图的原点都不一致，并且其加偏还是非线性的，因此无法利用常用的加载方法去加载，放弃使用它的底图，选用了符合标准的高德底图，高德底图使用的是国测局坐标也就是GCJ02坐标系，如果简单的将app获取的经纬度叠加上去，就有可能你本来在百度大厦的位置就显示在西二旗地铁站了甚至更远，因此需要将bd09转成gcj02坐标系，这个时候这个库就有了用武之地，对点批量转换再加载到底图上，就可以让点显示在本应该出现的位置。

	另外如果你拿到了一些WGS84的坐标，想加载到各种底图上就可以根据这个库在底图坐标系和你的数据坐标系之间进行转换。希望对大家有用吧。
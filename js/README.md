****

### 示例用法（Example&Usage）
1 NodeJs用法

```
//国测局坐标(火星坐标,比如高德地图在用),百度坐标,wgs84坐标(谷歌国外以及绝大部分国外在线地图使用的坐标)
var coordtransform=require('coordtransform');
//百度经纬度坐标转国测局坐标
var bd09togcj02=coordtransform.bd09togcj02(116.404, 39.915);
//国测局坐标转百度经纬度坐标
var gcj02tobd09=coordtransform.gcj02tobd09(116.404, 39.915);
//wgs84转国测局坐标
var wgs84togcj02=coordtransform.wgs84togcj02(116.404, 39.915);
//国测局坐标转wgs84坐标
var gcj02towgs84=coordtransform.gcj02towgs84(116.404, 39.915);
console.log(bd09togcj02);
console.log(gcj02tobd09);
console.log(wgs84togcj02);
console.log(gcj02towgs84);
//result
//bd09togcj02:   [ 116.39762729119315, 39.90865673957631 ]
//gcj02tobd09:   [ 116.41036949371029, 39.92133699351021 ]
//wgs84togcj02:  [ 116.41024449916938, 39.91640428150164 ]
//gcj02towgs84:  [ 116.39775550083061, 39.91359571849836 ]
```
2 浏览器用法
直接引用目录内的index.js，会有一个coordtransform的全局对象暴露出来，也支持用AMD加载器加载

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>coordTransform</title>
</head>
<body>
<h1>请按F12打开控制台查看结果</h1>
<script src="index.js"></script>
<script>
    //国测局坐标(火星坐标,比如高德地图在用),百度坐标,wgs84坐标(谷歌国外以及绝大部分国外在线地图使用的坐标)
    //百度经纬度坐标转国测局坐标
    var bd09togcj02 = coordtransform.bd09togcj02(116.404, 39.915);
    //国测局坐标转百度经纬度坐标
    var gcj02tobd09 = coordtransform.gcj02tobd09(116.404, 39.915);
    //wgs84转国测局坐标
    var wgs84togcj02 = coordtransform.wgs84togcj02(116.404, 39.915);
    //国测局坐标转wgs84坐标
    var gcj02towgs84 = coordtransform.gcj02towgs84(116.404, 39.915);
    console.log(bd09togcj02);
    console.log(gcj02tobd09);
    console.log(wgs84togcj02);
    console.log(gcj02towgs84);
    //result
    //bd09togcj02:   [ 116.39762729119315, 39.90865673957631 ]
    //gcj02tobd09:   [ 116.41036949371029, 39.92133699351021 ]
    //wgs84togcj02:  [ 116.41024449916938, 39.91640428150164 ]
    //gcj02towgs84:  [ 116.39775550083061, 39.91359571849836 ]
</script>
</body>
</html>
```
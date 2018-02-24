![](http://upload-images.jianshu.io/upload_images/3888312-946c2d3d5ffd16f2.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

<br>
安卓同事分享了一款Lottie的动画库，效果挺好，查了一下发现这款动画库可以支持H5。

#### Lottie开源动画库
 

Airbnb开源了一个[Lottie动画库](https://github.com/airbnb/lottie-web),它能够同时支持iOS、Android、ReactNative和H5
的开发。

Lottie动画库和Bodymovin的AE插件结合，把在AE上做好的动画导出为json文件，然后以Android/iOS原生动画的形式在移动设备上渲染播放。

#### H5的应用
![效果](http://upload-images.jianshu.io/upload_images/3888312-79d8c566161e719c.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
###### 1. 资源准备：
1、AE导出的json文件；
2、lottie.js
demo下载：https://github.com/MiuMiu-S/Lottie-bodymovin-H5

###### 2. 代码：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Bodymovin Demo</title>
    <script src="lottie.js"></script>
    <style>
        #animation{width: 300px;height: 300px;}
    </style>
</head>
<body>
<div id="animation"></div>
<script>
    bodymovin.loadAnimation({
        path:'servishero_loading.json',   //json文件路径
        loop:true,
        autoplay:true,
        renderer:'canvas',  //渲染方式，有"html"、"canvas"和"svg"三种
        container:document.getElementById('animation')
    });
    bodymovin.setSpeed(2);
    bodymovin.setDirection(-2);
</script>
</body>
</html>
```
###### 3. 属性
animationData: 包含导出的动画数据的对象。
path: 动画数据文件的相对路径。 (animationData 和 path 参数是互斥的)
loop: 循环设置，值为true / false / number（循环/不循环/循环n次（n为输入值））
autoplay: 自动播放设置。true为准备就绪后自动播放，false为不自动播放。
name: 动画名，用于后续引用。
renderer: 选择渲染器，值为'svg' / 'canvas' / 'html' 。
container: 需要渲染动画的dom元素。

###### 4. 相关方法:
bodymovin.play() -- 播放指定动画，1个参数动画名。
bodymovin.stop() -- 停止播放指定动画，1个参数动画名。
bodymovin.setSpeed() -- 第一个参数设置动画速度 (1为正常速度），第二个参数动画名可选。
bodymovin.setDirection() -- f播放方向，正数和0为正常播放，负数为倒放，第二个参数动画名可选。
bodymovin.searchAnimations() -- 检测class值为"bodymovin"的元素。
bodymovin.loadAnimation() -- 前面已有介绍， 返回一个可单独控制的动画实例。
bodymovin.destroy() --销毁和释放资源。 DOM 元素将会被清空。
bodymovin.registerAnimation() -- 你可以直接用registerAnimation来注册一个自定义元素，它必须包含"data-animation-path"属性并指向data.json的地址。
bodymovin.setQuality() -- 画质设置，调整动画播放器性能。默认为高画质(high), 可选值为'high'、'medium'、'low', 或者大于1的数字。对于有的动画这些设置差别不大。


参考
https://www.cnblogs.com/zamhown/p/6688369.html<br>
https://github.com/bigxixi/bodymovin
---
  layout: h5
  title: webGL
---

# Three.js

Three.js实现了webGL的大多数功能，使用它可以很方便的绘制三维场景。

## 全景和VR


+ [使用立方体创建三维全景demo](threejs.html)

这个demo创建的场景使用了在立方体上渲染六个面图片的原理。这样把摄像机放到立方体里往外看就能有全景效果。

缺点：1.渲染的图片是反的，因为是在图片的背面看。2.手机控制还没写完善(没必要，因为有googleVR的polyfill)

+ [使用three.js官方创建webVR](vr.html)

这个是threeJS和webVR的标准VR写法。但是这样必须在webvr的网站上下载专用浏览器才能查看vr效果。现在的浏览器很少支持webvr。

+ [使用three.js+googleVR创建webVR](vr-polyfill.html)

这个利用了googleVR的polyfill，使得即使不具备webvr的浏览器也可以有类似的效果。利用了加速度传感器来不断计算camera的lookAt实现。




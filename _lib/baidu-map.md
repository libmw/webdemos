---
  layout: lib
  title: 百度地图
---

# 百度地图

## 让图标的底部中心指向地图点：

marker.setOffset(new BMap.Size(0, -55 / 2));

## 转换gps坐标为百度地图的坐标

<pre><code data-language="javascript">function getBaiduPointsByGps(pointsArr, callback){
    //pointsArr的格式为 ['109.25417849429,28.970671972375996','109.25426387200001,28.167058867105997']
    var xPoints = [];
    var yPoints = [];

    for(var i = 0; i < pointsArr.length; i++){
        var point = pointsArr[i].split(',');
        xPoints.push(point[0]);
        yPoints.push(point[1]);

    }

    $.ajax({
        url: 'http://api.map.baidu.com/ag/coord/convert?from=0&to=4&mode=1&x='+ xPoints.join(',') +'&y='+ yPoints.join(','),
        dataType: 'jsonp',
        success: function(xyResults){
            var xyResult = null;
            var finallyResults = [];
            for(var i = 0; i < xyResults.length; i++){
                xyResult = xyResults[i];
                if(xyResult.error != 0){
                    callback(null);
                    return;
                }
                finallyResults.push(xyResult);
            }
            callback(finallyResults);
        },
        error: function(){
            callback(null);
        }
    });
}
</code></pre>

## 转换百度坐标为gps坐标

<pre><code data-language="javascript">function getGpsPointsByBaidu(pointsArr, callback){
    var xPoints = [];
    var yPoints = [];
    for(var i in pointsArr){
        xPoints.push(pointsArr[i].lng);
        yPoints.push(pointsArr[i].lat);
    }
    $.ajax({
        url: 'http://api.map.baidu.com/ag/coord/convert?from=0&to=4&mode=1&x='+ xPoints.join(',') +'&y='+ yPoints.join(','),
        dataType: 'jsonp',
        success: function(xyResults){
            var xyResult = null;
            var point = null;
            var xGps;
            var yGps;
            var finallyResults = [];
            for(var i = 0; i < xyResults.length; i++){
                xyResult = xyResults[i];
                if(xyResult.error != 0){
                    callback(null);
                    return;
                }
                point = new BMap.Point(xyResult.x, xyResult.y);
                //gps坐标转换公式xPoints是以前的百度坐标，point是把以前的百度坐标当成gps坐标转换成的百度坐标
                xGps = 2 * xPoints[i] - point.lng;
                yGps = 2 * yPoints[i] - point.lat;
                finallyResults.push({
                    lng: xGps,
                    lat: yGps
                });
            }
            callback(finallyResults);
        },
        error: function(){
            callback(null);
        }
    });
}
/**
* 调用方法： getGpsPointsByBaidu([{lng:116,lat:10},{lng:116,lat:11}], function(res){console.log(res)});
* 返回res内容： [
    {
        lat: 9.9960186477,
        lng: 115.98953313041
    },
    {
        lat: 10.995784233462,
        lng: 115.98952577073
    }
]
*/
</code></pre>
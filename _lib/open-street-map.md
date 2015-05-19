---
  layout: lib
  title: OpenStreetMap
  exthead: <link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.css" /><link rel="stylesheet" href="leaflet.draw.css" />
---
<style type="text/css">
    #map {
        height: 500px;
        width: 900px;
    }
</style>

# OpenStreetMap

## OpenStreetMap是一个免费的地图数据库，提供瓦片数据等。

## JS

一般通过[leaflet](http://leafletjs.com/)来管理瓦片

## 瓦片

tile.openstreetmap.org：官方的瓦片服务商是，是否免费无限使用未知。

[MapQuest](http://www.mapquest.com/)：是有一定限制的，如果要超出限制，需要发邮件说明（目前没遇到超限的情况）。

## 插件扩展

丰富的[plugins](http://leafletjs.com/plugins.html)为OpenStreetMap带来了极强的扩展性。本页面就是用了Leaflet.draw插件绘制出了一个可以编辑的矩形区域。

<div id="map"></div>

<script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>
<script src="leaflet.draw.js"></script>
<script>

    var osmUrl = 'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
    osmAttrib = '&copy; <a href="http://openstreetmap.org/copyright">OpenStreetMap</a> contributors',
    osm = L.tileLayer(osmUrl, {maxZoom: 18, attribution: osmAttrib});
    map = new L.Map('map', {layers: [osm], center: new L.LatLng(51.505, -0.04), zoom: 13});
    var rectangle = L.rectangle([[51.49, -0.1], [51.48, -0.06]]);
    var southWest = L.latLng(51.49, -0.1),
    northEast = L.latLng(51.48, -0.06),
    bounds = L.latLngBounds(southWest, northEast);
    map.fitBounds(bounds);
    //alse useful as:
    //map.fitBounds([[51.49, -0.1], [51.48, -0.06]]);
    rectangle.editing.enable();
    map.addLayer(rectangle);
    //获取bounds：rectangle.getBounds()

    /* 使用MapQuest

    var map = L.map('map', {drawControl: true}).setView([51.505, -0.09], 13);
    var	cloudmadeUrl = 'http://{s}.mqcdn.com/tiles/1.0.0/osm/{z}/{x}/{y}.png';
    var	subDomains = ['otile1','otile2','otile3','otile4'];
    var	cloudmadeAttrib = 'Data, imagery and map information provided by <a href="http://open.mapquest.co.uk" target="_blank">MapQuest</a>, <a href="http://www.openstreetmap.org/" target="_blank">OpenStreetMap</a> and contributors, <a href="http://creativecommons.org/licenses/by-sa/2.0/" target="_blank">CC-BY-SA</a>';
    //var cloudmade = new L.tileLayer(cloudmadeUrl, {maxZoom: 18, attribution: cloudmadeAttrib, subdomains: subDomains});
    L.tileLayer(cloudmadeUrl, {maxZoom: 18, attribution: cloudmadeAttrib, subdomains: subDomains}).addTo(map);
    */
</script>




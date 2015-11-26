# react-d3-map

react-d3 interactive map, just like Leaflet!!! But BYE BYE layers!!!! We use SVG components to replace layers!!!

## LIVE DEMO

#### Multipolygon and Polygon

- http://map.reactd3.org/test-multipolygon.html
- http://map.reactd3.org/test-polygon.html

#### Markers and Points

- http://map.reactd3.org/test-point.html

#### LineString and MultiLineString

- http://map.reactd3.org/test-line.html

## Examples

#### Polygon and MultiPolygon

```js

var Map = require('react-d3-map').Map;

var PolygonPopupGroup = require('react-d3-map').PolygonPopupGroup;

(function() {
  var width = 1000;
  var height = 800;
  var scale = 1 << 12;
  var scaleExtent = [1 << 10, 1 << 14]
  var center = [-100.95, 40.7];
  var data = require('json!../data/states.json');
  var onPolygonMouseOut= function(dom , d, i) {
    console.log('out')
  }
  var onPolygonMouseOver= function(dom, d, i) {
    console.log('over')
  }
  var onPolygonClick= function(dom, d, i) {
    console.log('click')
  }
  var onPolygonCloseClick= function(id) {
    console.log('close click')
    console.log(id)
  }
  var popupContent = function(d) { return 'hi, i am polygon'; }

  // data= {data}
  // onPolygonMouseOut= {onPolygonMouseOut}
  // onPolygonMouseOver= {onPolygonMouseOver}
  // onPolygonClick= {onPolygonClick}
  // onPolygonCloseClick= {onPolygonCloseClick}


  ReactDOM.render(
    <Map
      width= {width}
      height= {height}
      scale= {scale}
      scaleExtent= {scaleExtent}
      center= {center}
    >
      <PolygonPopupGroup
        key= {"polygon-test"}
        data= {data}
        popupContent= {popupContent}
        onClick= {onPolygonClick}
        onCloseClick= {onPolygonCloseClick}
        onMouseOver= {onPolygonMouseOver}
        onMouseOut= {onPolygonMouseOut}
        polygonClass= {"your-polygon-css-class"}
      />
    </Map>
  , document.getElementById('blank-multipolygon')
  )

})()

```

![polygon](./example/img/polygon.png)


#### LineString and MultiLineString

```js

var Map = require('react-d3-map').Map;

var LinePopupGroup = require('react-d3-map').LinePopupGroup;


(function() {
  var width = 1000;
  var height = 800;
  var scale = 1 << 22;
  var scaleExtent = [1 << 20, 1 << 24]
  var center = [-122.486052, 37.830348];
  var popupContent = function(d) { return d.properties.text; }

  var data = {
          "type": "Feature",
          "properties": {},
          "geometry": {
              "type": "LineString",
              "coordinates": [
                  [-122.48369693756104, 37.83381888486939],
                  [-122.48348236083984, 37.83317489144141],
                  [-122.48339653015138, 37.83270036637107],
                  [-122.48356819152832, 37.832056363179625],
                  [-122.48404026031496, 37.83114119107971],
                  [-122.48404026031496, 37.83049717427869],
                  [-122.48348236083984, 37.829920943955045],
                  [-122.48356819152832, 37.82954808664175],
                  [-122.48507022857666, 37.82944639795659],
                  [-122.48610019683838, 37.82880236636284],
                  [-122.48695850372314, 37.82931081282506],
                  [-122.48700141906738, 37.83080223556934],
                  [-122.48751640319824, 37.83168351665737],
                  [-122.48803138732912, 37.832158048267786],
                  [-122.48888969421387, 37.83297152392784],
                  [-122.48987674713133, 37.83263257682617],
                  [-122.49043464660643, 37.832937629287755],
                  [-122.49125003814696, 37.832429207817725],
                  [-122.49163627624512, 37.832564787218985],
                  [-122.49223709106445, 37.83337825839438],
                  [-122.49378204345702, 37.83368330777276]
              ]
          }
      }

  var onLineMouseOut= function(dom , d, i) {
    console.log('out')
  }
  var onLineMouseOver= function(dom, d, i) {
    console.log('over')
  }
  var onLineClick= function(dom, d, i) {
    console.log('click')
  }
  var onLineCloseClick= function(id) {
    console.log('close click')
  }


  ReactDOM.render(
    <Map
      width= {width}
      height= {height}
      scale= {scale}
      scaleExtent= {scaleExtent}
      center= {center}
    >
      <LinePopupGroup
        key= {"line-test"}
        data= {data}
        popupContent= {popupContent}
        onClick= {onLineClick}
        onCloseClick= {onLineCloseClick}
        onMouseOver= {onLineMouseOver}
        onMouseOut= {onLineMouseOut}
        meshClass= {"your-line-css-class"}
      />
    </Map>
  , document.getElementById('blank-line')
  )

})()
```

![line](./example/img/line.png)


#### Points and Markers

```js

var Map = require('react-d3-map').Map;
var MarkerPopupGroup = require('react-d3-map').MarkerPopupGroup;


// Example
(function() {
  var width = 1000;
  var height = 800;
  var scale = 1200 * 5;
  var scaleExtent = [1 << 12, 1 << 13]
  var center = [-5, 55.4];
  var uk = require('json!../data/uk.json');
  var data = topojson.feature(uk, uk.objects.places);
  var popupContent = function(d) { return d.properties.name; }
  var onMarkerMouseOut= function(dom , d, i) {
    console.log('out')
  }
  var onMarkerMouseOver= function(dom, d, i) {
    console.log('over')
  }
  var onMarkerClick= function(dom, d, i) {
    console.log('click')
  }
  var onMarkerCloseClick= function(id) {
    console.log('close click')
  }


  ReactDOM.render(
    <Map
      width= {width}
      height= {height}
      scale= {scale}
      scaleExtent= {scaleExtent}
      center= {center}
    >
      <MarkerPopupGroup
        key= {"polygon-test"}
        data= {data}
        popupContent= {popupContent}
        onClick= {onMarkerClick}
        onCloseClick= {onMarkerCloseClick}
        onMouseOver= {onMarkerMouseOver}
        onMouseOut= {onMarkerMouseOut}
        markerClass= {"your-marker-css-class"}
      />
    </Map>
  , document.getElementById('blank-point')
  )

})()
```

![point](./example/img/point.png)

## Install

```
npm install react-d3-map
```


## License

Apache 2.0

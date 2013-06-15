# EsriRest Layer Leaflet plugin
This plugin provides the ability to display and query ESRI REST services using
the _export_ feature and the _identify_ feature. This treats the REST service
as if it were a WMS service, as opposed to a normal tiled service.

The _identify_ feature return a URL to a json file where a developer can use
JSONP to extract information from an ArcGIS server.

### L.TileLayer.EsriRest
- Description: Allows a developer to include an ESRI server in Leaflet using
  the ESRI REST API _export_ function. It will also produce a URL based on a
  point that links to a JSON object returning information from the _identify_
  function.

#### Export Feature
- Usage: L.TileLayer.EsriRest(_PATH_TO_SERVICE_);
```javascript
var wildfires = new L.TileLayer.EsriRest("http://wildfire.cr.usgs.gov/ArcGIS/rest/services/geomac_dyn/MapServer", {
    layers: '1,18',
    transparent: true
}).addTo(map);
```

#### Identify Feature
- Usage: tileLayer.getIdentifyUrl(<L.Point>, {ESRI REST Identify Parameters});
```javascript
var wildfireUrl = wildfires.getIdentifyUrl(clickedPoint, {showLayers: 'all'});
```

- Note: The _showLayers_ parameter was added to allow the developer to select they type of query. The _layers_ parameter was also modified to only accept layer numbers. (ex. layers: 0,1,2)
For more information on the ESRI REST _identify_ feature [NOAA has a great page](http://gis.srh.noaa.gov/arcgis/SDK/REST/identify.html) about it.

### Example
See ./examples/wildfires.html to see usage

### See Also
- There is a similar project on github that provides ESRI tiled services as well as Bing and GeoJSON WFS.  The project can be found at this link [https://github.com/azgs/azgs-leaflet](https://github.com/azgs/azgs-leaflet)

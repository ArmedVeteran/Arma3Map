# Arma3Map
Tool to display [Arma 3](https://arma3.com/) maps in a web browser using [Leaflet](https://leafletjs.com/).

# Supported maps

| [Tanoa](tanoa.html)  | [X-CAM Taunus](taunus.html) | [Kujari](kujari.html) |
| -------------------- | --------------------------- | --------------------- |
| <a href="tanoa.html"><img src="maps/tanoa/0/0/0.png" width="200" height="200" /></a> | <a href="taunus.html"><img src="maps/taunus/0/0/0.png" width="200" height="200" /></a> | <a href="kujari.html"><img src="maps/kujari/0/0/0.png" width="200" height="200" /></a> |

| [Altis](altis.html)  | [Malden](malden.html)  | [Island Panthera](panthera3.html)  | 
| -------------------- | -------------------- | -------------------- | 
| <a href="altis.html"><img src="maps/altis/0/0/0.png" width="200" height="200" /></a> | <a href="malden.html"><img src="maps/malden/0/0/0.png" width="200" height="200" /></a> | <a href="panthera3.html"><img src="maps/panthera3/0/0/0.png" width="200" height="200" /></a> |

| [Livonia](enoch.html) (enoch) | [Lythium](lythium.html) | [Virolahti - Valtatie 7](vt7.html) | 
| -------------------- | -------------------- | -------------------- | 
| <a href="enoch.html"><img src="maps/enoch/0/0/0.png" width="200" height="200" /></a> | <a href="lythium.html"><img src="maps/lythium/0/0/0.png" width="200" height="200" /></a> |  <a href="vt7.html"><img src="maps/vt7/0/0/0.png" width="200" height="200" /></a> |

| [Stratis](stratis.html) | [Uzbin Valley](uzbin.html) | 
| -------------------- | -------------------- | 
| <a href="stratis.html"><img src="maps/stratis/0/0/0.png" width="200" height="200" /></a> | <a href="uzbin.html"><img src="maps/uzbin/0/0/0.png" width="200" height="200" /></a> | 

Content under 
- [Arma Public Licence](https://www.bohemia.net/community/licenses/arma-public-license). &copy; Bohemia Interactive.
- Taunus: [Arma Public Licence](https://www.bohemia.net/community/licenses/arma-public-license). &copy; X-CAM Taunus Dev Team.
- Kujari: [Arma Public Licence-Share Alike](https://www.bohemia.net/community/licenses/arma-public-license-share-alike). &copy; Temppa.
- Lythium : Unspecified Licence. &copy; GreenBeret &amp; FFAA MOD Team
- Virolahti - Valtatie 7: [Arma Public Licence-Share Alike](https://www.bohemia.net/community/licenses/arma-public-license-share-alike). &copy; furean.
- Uzbin Valley : Unspecified Licence. &copy; Dark, Max.

# How to use

## Base map

Each map have a js file that provides informations to configure Leaflet:
`https://jetelain.github.io/Arma3Map/maps/[mapname].js`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Tanoa</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.6.0/dist/leaflet.css" />
    <link rel="stylesheet" href="https://jetelain.github.io/Arma3Map/css/mapUtils.css" />
</head>
<body style=" margin:0;padding:0;border:0;">
    <div class="map" id="map" style="width:100%; height:100vh; margin:0;padding:0;border:0;">
    </div>
    <script src="https://unpkg.com/leaflet@1.6.0/dist/leaflet.js">
    </script>
	<script src="https://unpkg.com/jquery@3.5.1/dist/jquery.min.js">
    </script>
    <script src="https://jetelain.github.io/Arma3Map/js/mapUtils.js">
    </script>
    <script src="https://jetelain.github.io/Arma3Map/maps/tanoa.js">
    </script>
    <script>
    $(function () {
        var mapInfos = Arma3Map.Maps.tanoa;

        // Create map control
        var map = L.map('map', { 
            minZoom: mapInfos.minZoom, 
            maxZoom: mapInfos.maxZoom, 
            crs: mapInfos.CRS 
        });

        // Define tile layer
        L.tileLayer('https://jetelain.github.io/Arma3Map' + mapInfos.tilePattern, { 
            attribution: mapInfos.attribution, 
            tileSize: mapInfos.tileSize
        }).addTo(map);

        // Center map, and sets default zoom
        map.setView(mapInfos.center, mapInfos.defaultZoom);

        // (optional) Add grid sliders
        L.latlngGraticule().addTo(map);

        // (optional) Add a scale control
        L.control.scale({ maxWidth: 200, imperial: false }).addTo(map);

        // (optional) Add mouse grid position
        L.control.gridMousePosition().addTo(map);
    });
    </script>
</body>
</html>

```

## Leaflet

Once you have the base map, you can use all Leaflet features and plugins.

In Leaflet APIs, the latitude will be the northing in meters, and the longitude the easting in meters (x=lon, y=lat).

# How to help

- [Export map for Arma3Map](HowToExport.md)

# See also

My projects powered by Arma3Map :
- https://maps.plan-ops.fr/ : Prepare tactical maps, share them in real time, and import them into Arma 3 (you can host your own server using https://github.com/jetelain/Arma3TacMap)
- https://ctab.plan-ops.fr/ : Commander tablet in real time on your mobile device. Extension of the cTab mod (https://github.com/jetelain/cTab)

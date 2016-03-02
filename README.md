# OSM2VectorTiles GL Styles

OSM2VectorTiles compatible GL styles for use in Mapbox GL JS or the Mapbox Mobile SDKs - derived from official MapBox GL Styles.
(C) MapBox may be required on derivative designs (license not provided in the MapBox repo in the moment of fork).

This repo contains also cleanly compiled resources for using the GL styles locally or from custom hosting. Bellow are described the steps.

Use it with vector tiles which you can host by your own on your server. See documentation at: http://osm2vectortiles.org/.

How to compile MapBox GL JS and fonts and styles for offline use:

## Compile MapBox GL JS from source code

    npm install -g browserify
    npm install -g minifyify
    sudo apt-get install imagemagick
    sudo apt-get install libglew-dev
    # unpack mapbox-gl-js source code release from https://github.com/mapbox/mapbox-gl-js/releases
    npm install
    browserify js/mapbox-gl.js --debug --transform unassertify --plugin [minifyify --map mapbox-gl.js.map --output dist/mapbox-gl.js.map] --standalone mapboxgl > dist/mapbox-gl.js
    echo -e "\nmapboxgl.accessToken = 'NOT-REQUIRED-WITH-YOUR-VECTOR-TILES-DATA';" >> dist/mapbox-gl.js

## Create font glyphs

    npm install -g fontnik
    # unpack font release from https://github.com/mapbox/mapbox-studio-default-fonts/releases
    mkdir -p "glyphs/Open Sans Regular"
    build-glyphs open-sans/OpenSans-Regular.ttf "glyphs/Open Sans Regular"

## Create sprites for JSON styles

    npm install -g spritezero-cli
    # unpack style release from https://github.com/mapbox/mapbox-gl-styles/releases
    cd sprites
    spritezero bright-v8 bright-v8/_svg/
    spritezero --retina bright-v8@2x bright-v8/_svg/

## Customise the JSON style for OSM2VectorTiles

Modify the JSON styles to link locally stored assets and your own vector tiles - check relevant commit:
https://github.com/klokantech/osm2vectortiles-gl-styles/commit/9b9d3ff0dd50e5a1d5647dbb33bb3a8bde183031

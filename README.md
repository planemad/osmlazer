# osmlazer
osmium based OpenStreetMap data filter. Input is an OSM PBF, output is a stream of line delimited GeoJSON FeatureCollection.

## Setup

### Dependencies
#### Linux

```
apt-get install -y build-essential zlib1g-dev unzip python-dev \
  git libtool g++ autotools-dev automake cmake make xutils-dev realpath ragel
```

#### osx

```
brew install autoconf automake libtool makedepend
```

* [Install osmium dependencies](https://github.com/osmcode/node-osmium#depends)
* git clone https://github.com/geohacker/osmlazer.git
* `npm install`

## Usage

Download a OSM pbf file from [Geofabrik](http://download.geofabrik.de) or [Mapzen](https://mapzen.com/data/metro-extracts/)

`node index.js --file /path/to/pbf --filter /path/to/filter`

**Write to a single GeoJSON FeatureCollection**

Use [geojson-stream-merge](https://github.com/geohacker/geojson-stream-merge) to convert the line delimited GeoJSON FeatureCollection to a single object.

```
node index.js --file /path/to/pbf --filter /path/to/filter > features.output
geojson-stream-merge --input features.output --output output.json
```



## Filters

Filters are Mapbox GL filters. See `filters/` for examples.

# MapProxy examle with OpenStreetMap

First, create volume:

```sh
docker volume create --name=openstreetmap-data
```

Secondly, install Estonia map tiles:

```sh
wget https://download.geofabrik.de/europe/estonia-latest.osm.pbf
```

```sh
docker run -v estonia-latest.osm.pbf:/data.osm.pbf -v openstreetmap-data:/var/lib/postgresql/12/main overv/openstreetmap-tile-server:v1.6.0 import
```

Finally, you can run following command:

```sh
docker-compose up
```

Enjoy!

## Links

Local OSM URL: http://localhost:8081/
MapProxy URL: http://localhost:8080/demo/

### OSM Tiles

http://localhost:8080/demo/?tms_layer=osm&format=png&srs=EPSG%3A900913

Example tile: http://localhost:8080/tms/1.0.0/osm/EPSG900913/4/14/16.png

### Maa-amet Tiles

http://localhost:8080/demo/?tms_layer=maaamet_orto&format=png&srs=EPSG%3A3857

Example tile: http://localhost:8080/tms/1.0.0/maaamet_orto/webmercator/7/144/180.png

### Local OSM Tiles

http://localhost:8080/demo/?tms_layer=osm_local&format=png&srs=EPSG%3A900913

Example tile: http://localhost:8080/tms/1.0.0/osm_local/GLOBAL_MERCATOR/6/72/90.png

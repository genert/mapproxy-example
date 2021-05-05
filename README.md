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

OSM: http://localhost:8080/demo/?tms_layer=osm&format=png&srs=EPSG%3A900913
OSM example tile: http://localhost:8080/tms/1.0.0/osm/EPSG900913/4/14/16.png

Maa-amet: http://localhost:8080/demo/?tms_layer=maaamet_orto&format=png&srs=EPSG%3A3857
Maa-amet example tile: http://localhost:8080/tms/1.0.0/maaamet_orto/webmercator/7/144/180.png

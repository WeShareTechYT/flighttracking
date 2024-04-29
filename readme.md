# GETTING STARTED

## First install Docker
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```
## Obtaining Coordinates
You can obtain your latitude, longitude and altitude from https://www.mapcoordinates.net

## Configure .env 
```bash
LAT=
LONG=
ALT=
EMAIL=
TIMEZONE=
```
## Generate Keys for .env

### Create Flightradar24 Key
```bash
docker run \
  --rm \
  -it \
  -e FEEDER_LAT="YOUR_FEEDER_LAT" \
  -e FEEDER_LONG="YOUR_FEEDER_LONG" \
  -e FEEDER_ALT_FT="YOUR_FEEDER_ALT_FT" \
  -e FR24_EMAIL="YOUR@EMAIL.ADDRESS" \
  --entrypoint /scripts/signup.sh \
  mikenye/fr24feed
```
### Create Flightaware Key
```bash
docker run --rm ghcr.io/sdr-enthusiasts/docker-piaware:latest | grep "my feeder ID"
```
### Create Planefinder Key
```bash
docker run \
    --rm \
    -it \
    --name pfclient_temp \
    --entrypoint /firstrun \
    -p 30053:30053 \
    ghcr.io/sdr-enthusiasts/docker-planefinder:latest
```
### Create Radarbox Key
```bash
 docker run \
    --rm \
    -it \
    -e BEASTHOST=readsb \
    -e LAT=YOURLATITUDE \
    -e LONG=YOURLONGITUDE \
    -e ALT=YOURALTITUDE \
    ghcr.io/sdr-enthusiasts/docker-radarbox:latest
```    
## In the last Step run
```bash
docker-compose up -d 
```





# aad-vue
Vuejs version of Adopt a Drain

# Prerequistes
* postgres
* nodejs
* vuejs

# Installation 

# Setup Environment Variables
* data.world
* google maps
* postres 

# Setup Docker-Compose

```
# Override database settings as the docker host:
echo DB_HOST=db > .env
echo DB_USER=postgres >> .env

# Enable google maps with your dev or prod google map api key
echo GOOGLE_MAPS_JAVASCRIPT_API_KEY=<get-google-map-api-key> >> .env

# Provide an owner id for the drain data.
echo DW_USER=citizenlabs

# Enable data.world data with your "read/write" api token
echo DW_AUTH_TOKEN=<get-data.world-api-token> >> .env

# URL for drain data
echo OPEN_SOURCE=https://api.data.world/v0/sql/citizenlabs/grb-storm-drains >> .env

# Setup your docker based postgres database:
docker-compose run --rm web bundle exec rake db:setup

# Load data:
docker-compose run --rm web bundle exec rake data:load_things
# OR: don't load all that data, and load the seed data:
# docker-compose run --rm web bundle exec rake db:seed

# Start the web server:
docker-compose up

# Visit your website http://localhost:3000 (or the IP of your docker-machine)
```

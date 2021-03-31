# zigbee2mqtt2ha

A quick and easy setup for HomeAssistant with MQTT and Zigbee2MQTT in Docker.

clone the repo and cd in, then:

docker-compose up -d 
docker exec -it mqtt /bin/sh
{for the first mqtt user}
mosquitto_passwd -c /mosquitto/config/password_file <username>
{for additional users}
mosquitto_passwd /mosquitto/config/password_file <username>
exit
fill the password you just created into mosquitto/configuration.yaml
docker-compose restart
and fill in your mqtt user/pass in the home assistant integration when you set it up.
  

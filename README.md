# zigbee2mqtt2ha

A quick and easy setup for HomeAssistant with MQTT and Zigbee2MQTT in Docker.

clone the repo and cd in, then:

  1. docker-compose up -d 
  2. docker exec -it mqtt /bin/sh
  {for the first mqtt user}
  3. mosquitto_passwd -c /mosquitto/config/password_file <username>
  {for additional users}
  4. mosquitto_passwd /mosquitto/config/password_file <username>
  5. exit
  6. fill the password you just created into mosquitto/configuration.yaml
  7. docker-compose restart
  and 
 8. fill in your mqtt user/pass in the home assistant integration when you set it up.
  

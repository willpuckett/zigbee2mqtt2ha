# zigbee2mqtt2ha

A quick and easy setup for HomeAssistant with MQTT and Zigbee2MQTT in Docker.

clone the repo and cd in, then:

  1. docker-compose up -d 
  2. docker exec -it mqtt /bin/sh
  3. {for the first mqtt user}: mosquitto_passwd -c /mosquitto/config/password_file insert-username-here
  4. {for additional users}: mosquitto_passwd /mosquitto/config/password_file insert-username-here
  5. exit
  6. fill the password you just created into mosquitto/configuration.yaml
  7. docker-compose restart
  8. And!... fill in your mqtt user/pass in the home assistant integration when it starts up.
  
  

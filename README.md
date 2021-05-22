# zigbee2mqtt2ha

A quick and easy setup for HomeAssistant with MQTT and Zigbee2MQTT in Docker.

clone the repo and cd in, then:

  1. `docker-compose up -d`
  2. `docker exec -it mqtt /bin/sh`
  4. Run `mosquitto_passwd /mosquitto/config/password_file insert-username-here`to create as many username/password combos as you need (I use seperate ones for zigbee2mqtt, ha, and various types of devices around the house, although if you only create one and reuse it everywhere, 🤷🏻‍♂️, but *do* jot them down as you create them, just sayin'...).
  5. `exit`
  6. fill the password you just created into zigbee2mqtt/configuration.yaml (`nano zigbee2mqtt/configuration.yaml`)
  7. `docker-compose restart`
  8. And!... fill in your mqtt user/pass in the home assistant integration when it starts up.
  
  

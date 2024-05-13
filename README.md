# mosquitto-mqtt-docker

## MQTT Broker - mosquitto
> Mosquitto is an open source message broker which implements MQTT version 5, 3.1.1 and 3.1

[eclipse-mosquitto image](https://hub.docker.com/_/eclipse-mosquitto)

```
$ docker run  
    -it 
    --name mos1 
    -p 1883:1883   # MQTT port 1883
    -p 9001:9001  # Websocket
    -v ./conf/mosquitto.conf:/mosquitto/config/mosquitto.conf  
    -v ./conf/passwd:/mosquitto/passwd
    -v ./data:/mosquitto/data 
    -v ./log:/mosquitto/log 
    eclipse-mosquitto:2 # (2.0.18 is the latest version)

$ docker exec -it -u 1883 mos1 sh
```

### Set up authentication

```
$ docker exec -it -u 1883 mos1 sh
    mosquitto_passwd -c /mosquitto/passwd user_name # create and add user to /mosquitto/passwd
    
    mosquitto_passwd -b /mosquitto/passwd user_name password # add more users to the password file.

    mosquitto_passwd -D /mosquitto/passwd user_name # remove a user
```

* install mosquitto_passwd
```
$ sudo apt install mosquitto-clients
```

## 参考资料
[How to Configure Mosquitto MQTT Broker in Docker](https://cedalo.com/blog/mosquitto-docker-configuration-ultimate-guide/)

## FAQ
1. Conflicting UIDs and GIDs inside and outside of the container
```

```

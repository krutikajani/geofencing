
# What is IoTOpen 
IoTOpen is a generic platform for IoT applications. It is in use in several industries with multiple use cases. From monitoring homes to whole cities as well as boats and many other appliances.
IoTOpen has an easy-to-use API and is really fast and scalable. Even though it is very easy to use, it is very flexible. It is very easy to build applications around it.
IoTOpen also has built-in functionality for edge intelligence. It is possible to connect edge clients to the platform and write applications targeted to run on the clients. This open up for great possibilities to build scalable distributed applications running on different locations in the solution.

# How is it used in GeoFencing project
GeoFencing project uses sensors fixed on various vehicles to send data about **time** and **vehicle co-ordinates**. All the sensors are configured to send data to IoT Open platform, where data is being filtered, stored and made available through various API end points. This makes it easier to process this data and generate meaning ful information out of it without worrying about storing them securely and other compliance requirements.

# What is IoTOpen API
IoTOpen collects the data sent by various sensors (IoT Devices) and stores them for to make them available for further processing. These data is made available through various API endpoints. You can query those API endpoints and fetch the data related to specif device at that point of time. These API endpoints require API key for authentication purpose to access the data.

# What is Lynx
In 2018 the company IoT Open One was formed in order to make use of the full potential of the IoT platform. The platform was then named IoT Open Lynx and was part of a family of products around the platform. In 2020 TH1NG bought the remaining part in IoT Open, and it became a full owned daughter company to TH1NG. The platform was then renamed from IoT Open Lynx to just IoT Open. The name remains in many components still, and now you know why.

# Accessing IoT Open
You will need an account with IoT Open in order to access the data collected on IoTOpen platform. If you are Administrator and creating first account then you will need to register your organization and create the account. Once you have received the credentials you will be able to login to [IoTOpen](https://iot.skekraft.se/). 

## Username and password
You can access IoT Open in two ways. The most common is username and password. When you log in with username and password you will get a session key that is used during the time you are logged in. Even though this token can be valid for a long time it is not lasting forever and therefore this is not a good way to authorize integrations and other tools.

## API Key
One other alternative is using an API Key. It is almost the same thing as an access token, but it lasts until you remove it. When the API key is used, it always gets the same rights as the user it belongs to. Actually it IS the user that it is connected to.

Here's how to create an API Key

- Log in to the standard user interface.
- Navigate to your profile by clicking the account image in the top right corner.
- Click on Security.
- Click Create new API Key at the bottom.
- Enter a name to identify the key.
- Click Create.
- The key should now be visible on screen. For security-reasons this key can not be shown again. If a key is needed again please remove the key and create a new one.
Go ahead and create one and remove it if you haven't done so already.

You will need to create more later on, when using Grafana, Node-RED and the Bash scripts.

# Objects in IoTOpen
There are various objects associated with IoTOpen platform and they are very important in the way we access data. Here is the heirarchy of these objects.

## Organization
Organization is the object under which IoTOpen data will be accessible for the specific company and it will security boundry for various companies data.

## User
A user is the actual user of the platform for that specific organization. A user will authenticate and query various API endpoints to fetch data.

Alongwith Organization and User there are three more interesting central objects that actually builds up the logic for IoT. 

## Device
A device typically represents some hardware. E.g. a motion sensor, a wall plug, a switch, a thermometer, a GPS-tracker or any other sensor or actuator.

## Function
A function is something you can measure or control. For instance a temperature is something you can measure. Humidity is also something you can measure. A switch is something you can control. Typically, a device has one or more functions. E.g. a motion sensor might have both a motion function and a light function. It might also be equipped with a temperature function.

A function can belong to a device but doesn't have to. You can have functions not belonging to a device if you wish. However, both functions and devices must belong to an installation.

## Installation
An installation is a logical object. It represents a collection of devices and functions grouped together in some way. An example might be a house, a ship, a floor in a building, a part of a city, an IoT application or something else.

# API endpoints and fetching data
API endpoints can be queried and data can be fetched from those endpoints via curl, postman or they can be fetched from Node-red nodes and passed on to other flows.

## Sample requests using curl

### Get a list of installations

```
 curl -H  "X-API-Key: (Enter your API key)" https://iot.skekraft.se/api/v2/installation | jq
[
  {
    "id": 64,
    "name": "Kultur och Fritid GIOTIS",
    "client_id": 64,
    "created": 1666958735,
    "organization_id": 22,
    "notes": "",
    "users": [
      31,
      91,
      112,
      115,
      130,
      133,
      151,
      187,
      220,
      223
    ],
    "meta": {},
    "protected_meta": {}
  }
]
```

### Find devices

```
curl -H  "X-API-Key: (Enter your API key)" https://iot.skekraft.se/api/v2/devicex/64 | jq
[
  {
    "id": 250,
    "installation_id": 64,
    "type": "lora",
    "created": 1666952239,
    "updated": 1708517728,
    "meta": {
      "eui": "70b3d5705001378d",
      "lora_manager.decoder_name": "digital_matter.oyster",
      "manufacturer": "Digital Matter",
      "name": "Digital Matter - 70b3d5705001378d - Ismaskin"
    },
    "protected_meta": {}
  },
  {
    "id": 709,
    "installation_id": 64,
    "type": "lora",
    "created": 1674028148,
    "updated": 1674556631,
    "meta": {
      "eui": "70b3d57050013b83",
      "lora_manager.decoder_name": "digital_matter.oyster",
      "manufacturer": "Digital Matter",
      "name": "Digital Matter - 70b3d57050013b83 - Skotersläp"
    },
    "protected_meta": {}
  },
  {
    "id": 712,
    "installation_id": 64,
    "type": "lora",
    "created": 1674035973,
    "updated": 1705333575,
    "meta": {
      "eui": "70b3d5705001390d",
      "lora_manager.decoder_name": "digital_matter.oyster",
      "manufacturer": "Digital Matter",
      "name": "Digital Matter - 70b3d5705001390d - Stora Pistmaskinen"
    },
    "protected_meta": {}
  },
  {
    "id": 1060,
    "installation_id": 64,
    "type": "lora",
    "created": 1704280864,
    "updated": 1704281711,
    "meta": {
      "eui": "24e124136d211967",
      "lora_manager.decoder_name": "milesight",
      "manufacturer": "Milesight",
      "name": "Milesight - 24e124136d211967 - Tempsensor"
    },
    "protected_meta": {}
  }
]
```

### Get data from devices and functions

The data is separated from the devices and functions and can be retrieved in some different ways.

Via the status of an installation you get all the current (i.e. last known) status of all functions.
`
curl -H  "X-API-Key: (enter your API key)" https://iot.skekraft.se/api/v2/status/64
`
Note that the key between the function and the data is the topic that you can find via the function. Normally it is topic_read.
```
curl -H  "X-API-Key: (Enter your API key)" https://iot.skekraft.se/api/v2/status/64\?topics\=obj/lora/70b3d5705001378d/latitude | jq
[
  {
    "client_id": 64,
    "installation_id": 64,
    "timestamp": 1709466290,
    "value": 64.7564984,
    "topic": "obj/lora/70b3d5705001378d/latitude",
    "msg": "u7wbmk89gnhr"
  }
]
```



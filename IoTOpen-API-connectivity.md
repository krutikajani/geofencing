
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

### Objects in IoTOpen
There are various objects associated with IoTOpen platform and they are very important in the way we access data. Here is the heirarchy of these objects.


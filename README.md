# 1-to-1 Video Calling Application with Face AI: Building with JavaScript and EnableX Toolkit for Web

This is a sample one to one video calling client application written in JavaScript that allows developers to implement video calling capabilities empowered with Face AI in their websites. The application runs on the web browsers (referred as client end point) and utilizes EnableX Web SDK to conduct an RTC session with its peers through EnableX Video Services.The client application performs the following tasks to facilitate an RTC session:

Get token from the application server
Connect to the room using the token
Publish audio/video streams in the room
Subscribe to remote audio/video streams in the room
Listen to any session related events
This sample client application also demonstrates the following features:

Mute/Unmute video
Mute/Unmute audio
Session Recording
Chat
face AI
Screen share
Disconnect

## 1. Important!

When developing a Client Application with EnxRtc.js ( present in client/js ), make sure to replace the old EnxRtc.js with updated EnxRtc.js polyfills from https://developer.enablex.io/docs/references/sdks/video-sdk/web-sdk/index/ for RTCPeerConnection and getUserMedia. Otherwise your application will not work in web browsers.

## 2. Trial

Sign up for a free trial https://www.enablex.io/free-trial/ or try our multiparty video chat https://try.enablex.io/

## 3. Installation

### 3.1 Pre-Requisites

#### 3.1.1 App Id and App Key 

* Create a free account on EnableX [https://www.enablex.io/free-trial/]
* Create your Project
* Get the App ID and App Key generated against the Project
* Clone this Repository `git clone https://github.com/EnableX/Video-Conferencing-Open-Source-Web-Application-Sample.git --recursive` & follow the steps further 

#### 3.1.2 SSL Certificates

The Application needs to run on https. So, you need to use a valid SSL Certificate for your Domain and point your application to use them. 

However you may use self-signed Certificate to run this application locally. There are many Web Sites to get a Self-Signed Certificate generated for you, Google it. Few among them are:

* https://letsencrypt.org/
* https://www.sslchecker.com/csr/self_signed
* https://www.akadia.com/services/ssh_test_certificate.html  

The following below can also be used to create a self-signed certificate.

 Linux/Mac
```javascript
  cd Video-Conferencing-Open-Source-Web-Application-Sample
  cd server
  mkdir certs
  sudo openssl req -x509 -newkey rsa:4096 -keyout ./certs/example.key -out ./certs/example.crt -days 10000 -nodes
  sudo chmod 755 ./certs/example.*
  cd ..
```
Windows(Use Git Bash)
```javascript
  cd Video-Conferencing-Open-Source-Web-Application-Sample
  cd server
  mkdir certs
  openssl req -x509 -newkey rsa:4096 -keyout ./certs/example.key -out ./certs/example.crt -days 10000 -nodes
  chmod 755 ./certs/example.*
  cd ..
```
#### 3.1.3 Configure

Before you can run this application, configure the service. Copy the `server/example.env` as `server/.env` and update the values. Or you can set following system environment variables instead:

```javascript
  SERVICE_PORT - Node port on which your application will run. Default port set is 3000
  ENABLEX_APP_ID - Your EnableX `App ID` - It's your username for EnableX API and can be found at Dashboard > Projects https://portal.enablex.io/dashboard/
  ENABLEX_APP_KEY - Your EnableX `App Key` - - It's your password for EnableX API and can be found at Dashboard > Projects https://portal.enablex.io/dashboard/
```

For Mac and Linux, open a terminal window and type the following commands. Note - Replace all the characters after the `=` with values from your EnableX account:
```javascript
  export SERVICE_PORT=XXXX
  export ENABLEX_APP_ID=XXXXXXXXXX
  export ENABLEX_APP_KEY=XXXXXXXXX
```

On Windows, open a powershell / command window and type the following commands. Note that there is no `=`, just the key and value separated by a space:
```javascript
  setx SERVICE_PORT 'XXXX'
  setx ENABLEX_APP_ID 'XXXXXXXXX'
  setx ENABLEX_APP_KEY 'XXXXXXXXX'
```

### 3.2 Build

Run `npm install --save` to build the project and the build artifacts will be stored in the `./node_modules` directory.

#### 3.2.1 Run Server

Run `node server.js` inside `server` folder for starting your Server. 

```javascript
  cd server
  node server.js
```

#### 3.2.2 Test 

* Open a browser and go to [https://localhost:3000/](https://localhost:3000/). The browser should load the App. 
* Allow access to Camera and Mic as and when prompted to start your first RTC Call through EnableX
* You need to Room ID to join. We have added a "Create Room" link below the login form. Click it to get a Room-Id prefilled in the form. 
* You can share the Room-ID with anyone to join your Conference.


## 4. Server API

EnableX Server API is a Rest API service meant to be called from Partners' Application Server to provision video enabled
meeting rooms. API Access is given to each Application through the assigned App ID and App Key. So, the App ID and App Key
are to be used as Username and Password respectively to pass as HTTP Basic Authentication header to access Server API.

For this application, the following Server API calls are used:
* https://developer.enablex.io/docs/references/apis/video-api/content/api-routes/#create-a-room - To create a room
* https://developer.enablex.io/docs/references/apis/video-api/content/api-routes/#get-a-list-of-rooms - To get list of Rooms
* https://developer.enablex.io/docs/references/apis/video-api/content/api-routes/#get-room-information - To get information of the given Room
* https://developer.enablex.io/docs/references/apis/video-api/content/api-routes/#create-a-token - To create Token for the given Room


To know more about Server API, go to:
https://developer.enablex.io/docs/references/apis/video-api/index/


## 5. Client API

Client End Point Application uses Web Toolkit EnxRtc.js to communicate with EnableX Servers to initiate and manage RTC Communications.

To know more about Client API, go to:
https://developer.enablex.io/docs/references/sdks/video-sdk/web-sdk/index/

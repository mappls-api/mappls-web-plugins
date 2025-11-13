[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api)


# Intouch Device Tracking Widget 

**Easy To Integrate Routing APIs & Map SDKs For Web Applications**

Powered with India's most comprehensive and robust mapping functionalities. 

## Document Version History

| Version | Last Updated | Team | Author |Remarks |
| ---- | ---- | ---- | ---- | ---- |
| 1.0 | 07 Aug 2025 | SDK Product Team | Prabhjot Kaur ([PK](https://github.com/prabhjot729)) | OAuth 2 |

## Introduction 
The mappls.intouchTracking is part of the Mappls SDK (formerly MapmyIndia) and is designed to provide real-time tracking and display of routes and activities on a map. This method supports device tracking functionality to visualize movement and journey progress on a map.
This document provides an overview of how to use the mappls.intouchTracking function, including configuration options and code examples.

## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://auth.mappls.com/console), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://auth.mappls.com/console) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
   
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Tracking Plugin. [Javascript Code Example - WIP]() & [Working NPM Code - WIP]()

# Table of Contents

- [Intouch Device Tracking Widget](#intouch-device-tracking-widget)
  - [Document Version History](#document-version-history)
  - [Introduction](#introduction)
  - [Getting Access](#getting-access)
- [Table of Contents](#table-of-contents)
- [Implementation](#implementation)
    - [Step 1: Initialize plugins Map SDK and add (\& libraries=intouchTracking) in the url](#step-1-initialize-plugins-map-sdk-and-add--librariesintouchtracking-in-the-url)
    - [Step 2 : Add map under div container in your project](#step-2--add-map-under-div-container-in-your-project)
    - [Step 3 : Initialize Map \& declare variables](#step-3--initialize-map--declare-variables)
    - [Step 4 : Add tracking options in mappls.intouchTracking() method](#step-4--add-tracking-options-in-mapplsintouchtracking-method)
    - [Step 5: Method call for Initialising the Tracking Plugin with options](#step-5-method-call-for-initialising-the-tracking-plugin-with-options)
    - [Step 6: Starting the Device Tracking Widget](#step-6-starting-the-device-tracking-widget)
    - [Step 7: Ending the Device Tracking Session](#step-7-ending-the-device-tracking-session)
  - [Mandatory Parameters of intouchTracking() Options](#mandatory-parameters-of-intouchtracking-options)
  - [Optional Parameters of intouchTracking() Options](#optional-parameters-of-intouchtracking-options)
    - [Important Entities](#important-entities)
    - [Other Optional Configuration of intouchTracking() Options](#other-optional-configuration-of-intouchtracking-options)
  - [Callback Function of intouchTracking() method](#callback-function-of-intouchtracking-method)
  - [Callback Function of deviceTrackStart() method](#callback-function-of-devicetrackstart-method)
  - [Optional Parameters in deviceTrackStart() options](#optional-parameters-in-devicetrackstart-options)
  - [Other Tracking methods available after deviceTrackStart()](#other-tracking-methods-available-after-devicetrackstart)
      - [Recommendation: When you wish to switch between curved line and route line between source \& destination](#recommendation-when-you-wish-to-switch-between-curved-line-and-route-line-between-source--destination)
        - [Before rider picks up:](#before-rider-picks-up)
        - [After rider picks up:](#after-rider-picks-up)
      - [Re-centering the Map Based Current Tracking Data](#re-centering-the-map-based-current-tracking-data)
    - [Error Handling](#error-handling)


# Implementation

### Step 1: Initialize plugins Map SDK and add (& libraries=intouchTracking) in the url
```js
<script src="https://sdk.mappls.com/map/sdk/web?v=3.0&access_token=<Static key>&layer=vector&callback=initMap1"></script>
<script src="https://apis.mappls.com/advancedmaps/api/<Token>/map_sdk_plugins?v=3.0&libraries=intouchTracking"></script> 
```

### Step 2 : Add map under div container in your project

 ```js
   <div id="map"></div>
 ```

### Step 3 : Initialize Map & declare variables

```js
var map,trackingCallBackData,curvePolyline,strt;
map = new mappls.Map('map', {
    center: [28.62988695137534, 77.4224575062193],
    zoom: 12
});
```


### Step 4 : Add tracking options in mappls.intouchTracking() method

```js

    var trackingOptions = {
        map: map,
        deviceId:'10647019', // required
        type:'deviceTracking', // required
        strt:{ geoposition: "28.63124010064198,77.46734619140625" }, // start location
        start: strt, // required
        profile: 'biking',  // Tracking profile (biking)
        end: {geoposition: "29.5506228,77.2688807"}, //end location
        fitBounds: true,  // Auto-fit map bounds to route
        fitboundsOptions: { padding: 100 },  // Padding for bounds fitting
        strokeWidth: 4,  // Route line width
        routeColor: 'blue',  // Route color
        connector: true,  // Show connector line
        connectorRouteColor: 'gray',  // Connector color
        connectorRouteDash: [2, 2],  // Dash pattern for connector line
        start_icon: false,  // Don't show start icon
        connectorWidth: 2,  // Connector line width
        end_icon: true  // Show end icon
        curveLine:true,  /* default false */
        curveLineColor:"#333", /* default "#333" */
        curveLineOpacity:1, /* default 1 */
        curveDasharray:[2,2], /* default [2,2] for straight line use false */
        curveLineStrokeWeight:2, /* default 4 */
        curveLineFitbounds:true /* default false */
    };
```

### Step 5: Method call for Initialising the Tracking Plugin with options

```js
tracking_plugin = mappls.intouchTracking(tracking_option, function (data) {
                    console.log(data);
                    trackingCallBackData=data;
                });
```

### Step 6: Starting the Device Tracking Widget

```js
     function startCall(){
            trackingCallBackData.deviceTrackStart({
                refreshTime:5000,
                heading:true, // default true
                buffer:50, // default 50
                delay:2000,
                fitBounds:true, // default true
                latentViz:'fly' // default false
            }, function(data){
                console.log(data);
            });
        }
```
###  Step 7: Ending the Device Tracking Session
   
```js   
    function endCall(){
            trackingCallBackData.deviceTrackEnd();
        }
```


## Mandatory Parameters of intouchTracking() Options

- `map`(object): vector map or raster map object from respective Mappls Map SDKs.  This is the map on which the tracking will be displayed. It must be a valid instance of the map object.
- `start` (string) : route start location. 
    
    Example:
    ```js
    { 
        geoposition: "28.63124010064198,77.46734619140625"
    }
    ```
- `type` (String) : Defines the type of tracking. Possible values are:
  - `deviceTracking`: For device-specific tracking.
- `deviceId` (String or Number) : The unique identifier for the device being tracked. 

  Example: `12345`

## Optional Parameters of intouchTracking() Options

### Important Entities

- **trackingOptions (Object)**: This request object contains various configuration settings that define how the tracking plugin initialises &  behaves on the map. It allows developers to customize the tracking experience.
- **callback (Function)**: A callback function that is invoked when tracking data is updated or received. The of intouchTracking() provides a callback that will transmit object containing the important tracking data.


### Other Optional Configuration of intouchTracking() Options 
The trackingOptions object provides various properties for customizing the tracking behavior. Below is a description of each property:

- `resource` :"route_eta", To set the route resource. Default to "`route_eta`". Other valid option is `route_adv`
- `profile` (String): Defines the mode of transportation. Common values include:
    - `biking`: For tracking biking activities.
    - `driving`: For tracking driving activities.
    - `walking`: For tracking walking activities.
- `fitBounds` (Boolean): If true, the map will automatically adjust its view to fit the route. If false, the map will not adjust its bounds automatically.
- `fitboundsOptions` (Object): This option allows you to specify additional parameters when adjusting the map’s bounds. Common parameter is padding, which defines the padding (in pixels) to be applied to the map's edges when fitting bounds. 
  Example: 
  ```js
    fitboundsOptions: {
         padding: 80,
       }
  ```
- `strokeWidth` (Number): Specifies the width (in pixels) of the route line displayed on the map.
- `strokeOpacity` (integer): //signifies opacity of the route polyline. //optional; default is 1. Opacity values from 0 to 1.
- `routeColor` (String): Defines the color of the route line. You can provide a CSS color value (e.g., 'blue', '#FF5733').
- `connector` (Boolean): If true, a connector line will be displayed between points on the route.
- `connectorRouteColor` (String): Specifies the color of the connector route.
- `connectorRouteDash` (Array): An array defining the dash pattern for the connector route. For example, [2, 2] would create a dashed line pattern.
- `connectorWidth` (Number): Defines the width (in pixels) of the connector route line.
- `connectorOpacity` (integer): //signifies opacity of the connector polyline. //optional; default is 1. Opacity values from 0 to 1.
- `connectorVisible`(boolean): To show/hide connector; this is only applicable when curveLine is being used. //default is `true`.
- `ccpIcon` (string):'location.png',  Allows to set URL of current rider position icon; Supports PNG format as of now.
- `ccpIconWidth` (integer): 70; signifies CCP icon's width, // optional
- `ccpOffset` (x,y): [0,20]; //signifies icon's offset in x,y pixels in a div.
- `cPopup` :”`<h1>current popup</h1>”`. To set html in current icon popup (_parameter available only for current location Icon_)
- `sPopup` :”start text”, // optional (for start icon popup)
- `dPopup` :"end text", available for end icon popup
- `buffer` (integer):50,  The distance defined for call reroute for the provided current location.
- `start_icon` : Supports PNG format as of now.
    ```js
    {   url: 'location.png',
        width: 40, 
        height: 40,
        popupOptions:
            {
                offset: {'bottom': [0, -20]}, 
                openPopup:false 
            },
        offset:[0, -18] 
    }, 
    ```
  - `start_icon`: `false` // if set as false then marker will not be visible
- `end_icon` : Supports PNG format as of now.
    ```js
    {   url: 'location.png',
        width: 40, 
        height: 40 
        popupOptions:
        {
            offset: {'bottom': [0, -20]}, 
            openPopup:false 
        },
        /* offset:[0, -18] */
    },
    ```
  - `end_icon`: `false` // if set as false then marker will not be visible
- `curveLine` (boolean): `true`
- `curveLineColor` (string): "gray", signifies curve line's color. // can take in hex codes as well; optional 
- `curveLineOpacity` (integer): //signifies opacity of the curve polyline. //optional; default is 1. Opacity values from 0 to 1.
- `curveDasharray` : [2,2], // default: none and optional; used to display route polyline as dashed polyline.
- `curveLineStrokeWeight` (integer): 7, // signifies width of the curve polyline on the map; optional
- `curveLineFitbounds` (boolean): Whether to include curve line in map fit bound or not, default is `true`,  // optional
- 

## Callback Function of intouchTracking() method
The callback function is triggered when tracking plugin is initialised. This means the first values within this callback indicate the original duration and distance estimates for this tracking device. This function receives a data object containing the initial route information.
The callback function signature is as follows:
- `function callback(data);`

The data object may contain the following properties:
- `dur` (String): The duration of the journey, formatted as "hh:mm:ss".
- `dis` (String): The total distance to be traveled in the journey, usually in kilometers or miles. Default is kms.

## Callback Function of deviceTrackStart() method
The callback function is triggered when tracking is started and data is updated or received. This function receives a data object containing the latest tracking information.
The callback function signature is as follows:
- `function callback(data);`

The data object may contain the following properties:
- `duration` (String): The remaining duration of the journey, formatted as "hh:mm:ss".
- `distance` (String): The remaining distance to be traveled, usually in kilometers or miles. Default is kms.
- `lastdriverLocation` (Object): Contains the last known location of the driver, with properties like latitude and longitude.
- `coveredDistance` (String): The total distance traveled so far, usually in kilometers or miles. Default is kms.


## Optional Parameters in deviceTrackStart() options

- `reRoute` (boolean): To refresh the route as per the current location. This means the route will change as per the current location. If kept false the same route will be displayed. Default is `true`.
- `heading` (boolean): To control the rotation of the marker as per the route direction.For example if you are using a car icon, it would rotate as per the route direction otherwise it would move straight. Default is `true`.
- `buffer` (integer):50,  The distance defined for call reroute for the provided current location. 
- `fitBounds` (boolean): Allowing this would fit the map in the view bound. Default is `true`.
- `fitBoundsOptions`: add padding to the fitBounds, if fitBounds is set as `true`.
    ```
    fitBoundsOptions: 
    {
        padding:80
    }, // optional
    ```
- `fitCoverDistance` (boolean): includes the last movement within the fitBounds call. //default is `true`
- `polylineRefresh` (boolean): removes the covered route as the rider progresses. // default `true`
- `latentViz` (boolean): Smooth visualization when rider suddenly jumps off-route. Default is `false`. Valid options are: 
  - `false`: Disapparate from old location and apparate at the new location if new location not within buffer distance of route.
  - `fly`: Perform a crow-fly animation from old location to new location if new location not within buffer distance of route.
  - `route`: Perform a legal but hidden route based animation from old location to new location if new location not within buffer distance of route.
- `delay` (integer): Animation delay in miliseconds indicating within how much time each subsequent location movement animation is to be completed. Default is `5000` ms.
- `refreshTime` (integer): This is the time at which the location is fetched from Intouch Platform for visualization. Default is `15000` ms.


## Other Tracking methods available after deviceTrackStart()

- `trackingCallbackData.settrackfit(true/false);`  (default is `true`, fitbounds the track)
- `trackingCallbackData.setccpContent(“content”);` (set popup on start)
- `trackingCallbackData.removeCurveLine();` // to remove curved polylines.
- `trackingCallbackData.setLineVisible(true);` // to show/hide polyline on map.
- `trackingCallbackData.getEta(function(data){console.log(data);})` //to fetch eta & distance from the plugin


#### Recommendation: When you wish to switch between curved line and route line between source & destination

##### Before rider picks up: 
1. Show the Curved line.
    - `curveLine:true`
2. Hide the Route line.
    - `strokeOpacity:0` and if `connector:true`, set `connectorVisible:false`

##### After rider picks up: 
1. Call `trackingCallBackData.removeCurveLine();` to remove the curved line.
2. Call `trackingCallBackData.setLineVisible(true);` to set the route line to visible.

####  Re-centering the Map Based Current Tracking Data

```js    
    if (trackingCallBackData) {
        trackingCallBackData.settrackfit(true);  // Auto-fit map to the route
        document.getElementById('recenter').style.display = "none";  // Hide recenter button
    }
```
> You may do a periodic fitbound few seconds after the last user interaction with the map.

### Error Handling
It is important to handle errors effectively when using mappls.intouchTracking:
- `Map not loading`: Ensure the map object is initialized and correctly passed to the tracking function.
- `Invalid device ID`: Ensure the deviceId is valid and corresponds to an active device.
- `Tracking data is unavailable`: Always check the data object in the callback to ensure it contains the expected information (e.g., data.dur, data.dis).



<br>

For any queries and support, please contact: 

[<img src="https://about.mappls.com/images/mappls-logo.svg" height="40"/> </p>](https://about.mappls.com/api/)
Email us at [apisupport@mappls.com](mailto:apisupport@mappls.com)


![](https://about.mappls.com/api/img/icons/support.png)
[Support](https://about.mappls.com/contact/)
Need support? contact us!

<br></br>
<br></br>

[<p align="center"> <img src="https://about.mappls.com/api/img/icons/stack-overflow.png"/> ](https://stackoverflow.com/questions/tagged/mappls-api)[![](https://about.mappls.com/api/img/icons/blog.png)](https://about.mappls.com/blog/)[![](https://about.mappls.com/api/img/icons/gethub.png)](https://github.com/Mappls-api)[<img src="https://mmi-api-team.s3.ap-south-1.amazonaws.com/API-Team/npm-logo.one-third%5B1%5D.png" height="40"/> </p>](https://www.npmjs.com/org/mapmyindia) 



[<p align="center"> <img src="https://about.mappls.com/june-newsletter/icon4.png"/> ](https://www.facebook.com/Mapplsofficial)[![](https://about.mappls.com/june-newsletter/icon2.png)](https://twitter.com/mappls)[![](https://about.mappls.com/newsletter/2017/aug/llinkedin.png)](https://www.linkedin.com/company/mappls/)[![](https://about.mappls.com/june-newsletter/icon3.png)](https://www.youtube.com/channel/UCAWvWsh-dZLLeUU7_J9HiOA)




<div align="center">&copy  Copyright 2023 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>



















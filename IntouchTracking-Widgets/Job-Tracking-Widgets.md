[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api)


# Intouch Tracking Widget 

## Document Version History

| Version | Remarks | Author |
| ---- | ---- | ---- |
| 1.0 | Document Update |SDK Product Team ([PK](https://github.com/prabhjot729/))|

# Table of Contents

- [Intouch Tracking Widget](#intouch-tracking-widget)
  - [Document Version History](#document-version-history)
- [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Mandatory Parameters](#mandatory-parameters)
  - [Important Parameters](#important-parameters)
  - [Configuration Options (trackingOptions)](#configuration-options-trackingoptions)
  - [Callback Function](#callback-function)
  - [Tracking callbacks](#tracking-callbacks)
      - [Recommendation: When you wish to switch between curved line and route line between source \& destination](#recommendation-when-you-wish-to-switch-between-curved-line-and-route-line-between-source--destination)
        - [Before rider picks up:](#before-rider-picks-up)
        - [After rider picks up:](#after-rider-picks-up)
  - [Usage Examples](#usage-examples)
    - [Load SDK](#load-sdk)
    - [Initializing Tracking on Map Load](#initializing-tracking-on-map-load)
    - [Starting the Tracking Session](#starting-the-tracking-session)
    - [Ending the Tracking Session](#ending-the-tracking-session)
    - [Re-centering the Map Based Current Tracking Data](#re-centering-the-map-based-current-tracking-data)
    - [Error Handling](#error-handling)

## Introduction 
The mappls.intouchTracking is part of the Mappls SDK (formerly MapmyIndia) and is designed to provide real-time tracking and display of routes and activities on a map. This method supports job tracking functionality to visualize movement and journey progress on a map.
This document provides an overview of how to use the mappls.intouchTracking function, including configuration options and code examples.

## Mandatory Parameters

  - `map(object)`: vector map or raster map object from respective Mappls Map SDKs.
  - `start (Date or String)` : route start location . For eg -  { geoposition: "28.63124010064198,77.46734619140625" }
  - `type (String)` : jobTracking
  - `jobId (String or Number)` : 12345


## Important Parameters

- **trackingOptions (Object)**: This object contains various configuration settings that define how the tracking plugin behaves on the map. It allows developers to customize the tracking experience.
- **callback (Function)**: A callback function that is invoked when tracking data is updated or received. The callback will receive an object containing the tracking data.



## Configuration Options (trackingOptions)
The trackingOptions object provides various properties for customizing the tracking behavior. Below is a description of each property:
- **map (Map Object)**: This is the map on which the tracking will be displayed. It must be a valid instance of the map object.
- **jobId (String or Number)**: The unique identifier for the job or task being tracked. This is required.
- **type (String)**: Defines the type of tracking. Possible values are:
  - **jobTracking**: For job-specific tracking.
- **profile (String)**: Defines the mode of transportation. Common values include:
    - **biking**: For tracking biking activities.
    - **driving**: For tracking driving activities.
    - **walking**: For tracking walking activities.
- **start (Date or String)**: The start time of the tracking. This value should be a valid timestamp to define the starting point of the journey.
- **fitBounds (Boolean)**: If true, the map will automatically adjust its view to fit the route. If false, the map will not adjust its bounds automatically.
- **fitboundsOptions (Object)**: This option allows you to specify additional parameters when adjusting the map’s bounds. Common parameter is padding, which defines the padding (in pixels) to be applied to the map's edges when fitting bounds.
- **strokeWidth (Number)**: Specifies the width (in pixels) of the route line displayed on the map.
- **strokeOpacity (integer)**: //signifies opacity of the route polyline. //optional; default is 1. Opacity values from 0 to 1.
- **routeColor (String)**: Defines the color of the route line. You can provide a CSS color value (e.g., 'blue', '#FF5733').
- **connector (Boolean)**: If true, a connector line will be displayed between points on the route.
- **connectorRouteColor (String)**: Specifies the color of the connector route.
- **connectorRouteDash (Array)**: An array defining the dash pattern for the connector route. For example, [2, 2] would create a dashed line pattern.
- **start_icon (Boolean)**: If true, the start location will be marked with an icon. If false, no start icon will be shown.
- **connectorWidth (Number)**: Defines the width (in pixels) of the connector route line.
- **connectorOpacity (integer)**: //signifies opacity of the connector polyline. //optional; default is 1. Opacity values from 0 to 1.
- **end_icon (Boolean)**: If true, the end location will be marked with an icon.
- **resource** :"route_eta", To set the route resource. Default to "`route_eta`". 
- **ccpIcon (string)**:'location.png',  Allows to set URL of current rider position icon; Supports PNG format as of now.
- **ccpIconWidth (integer)**: 70; signifies CCP icon's width, // optional
- **ccpOffset (x,y)**: [0,20]; //signifies icon's offset in x,y pixels in a div.
- **sPopup** :”start text”, // optional (for start icon popup)
- **cPopup** :”`<h1>current popup</h1>”`. To set html in current icon popup (_parameter available only for current location Icon_)
- **dPopup** :"end text", available for end icon popup
- **buffer (integer)**:50,  The distance defined for call reroute for the provided current location.
- **start_icon** : Supports PNG format as of now.
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
- **end_icon** : Supports PNG format as of now.
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
- **end_icon**: `false` // if set as false then marker will not be visible
- **curveLine (boolean)**: `true`
- **curveLineColor (string)**: "gray", signifies curve line's color. // can take in hex codes as well; optional 
- **curveLineOpacity (integer)**: //signifies opacity of the curve polyline. //optional; default is 1. Opacity values from 0 to 1.
- **curveDasharray** : [2,2], // default: none and optional; used to display route polyline as dashed polyline.
- **curveLineStrokeWeight (integer)**: 7, // signifies width of the curve polyline on the map; optional
- **curveLineFitbounds (boolean)**: Whether to include curve line in map fit bound or not, default is `true`,  // optional

## Callback Function
The callback function is triggered when tracking data is updated or received. This function receives a data object containing the latest tracking information.
The callback function signature is as follows:
- **function callback(data);**

The data object may contain the following properties:
- **dur (String)**: The duration of the journey, formatted as "hh:mm:ss".
- **dis (String)**: The total distance traveled, usually in kilometers or miles.
- **duration (String)**: Another representation of the journey's duration, used when tracking has started.
- **distance (String)**: Another representation of the distance traveled during the journey.
- **lastdriverLocation (Object)**: Contains the last known location of the driver, with properties like latitude and longitude.

## Tracking callbacks

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






## Usage Examples

### Load SDK
```js
<script src="https://apis.mappls.com/advancedmaps/api/cddd0e53-1ae4-43b8-a1ba-04a534140ae8/map_sdk_plugins?v=3.0&libraries=intouchTracking"></script>
```

### Initializing Tracking on Map Load

```js
map.addListener('load', function () {
    var trackingOptions = {
        map: map,
        jobId: 12345,  // Unique job ID
        type: 'jobTracking',  // Tracking type
        profile: 'biking',  // Tracking profile (biking)
        start:  start: { geoposition: "28.63124010064198,77.46734619140625" },
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

    mappls.intouchTracking(trackingOptions, function (data) {
        console.log(data);  // Log tracking data
        if (data && data.dur && data.dis) {
            document.getElementById('dur_dis').innerHTML = `Distance: ${data.dis} | Duration: ${data.dur}`;
        }
    });
});
```

###  Starting the Tracking Session

```js
    if (trackingCallBackData) {
        trackingCallBackData.jobTrackStart({
            refreshTime: 3000,  // Refresh data every 3 seconds
            fitBounds: true,  // Fit map bounds
            }, function (data) {
            console.log(data);  // Log tracking data
            if (data && data.duration && data.distance) {
                document.getElementById('dur_dis').innerHTML = `Duration: ${data.duration} | Distance: ${data.distance}`;
            }
            if (data && data.lastdriverLocation) {
                localStorage.setItem("lastdriverLocation", JSON.stringify(data.lastdriverLocation));
            }
        });
    }
```
###  Ending the Tracking Session
   
```js   
    if (trackingCallBackData) {
        trackingCallBackData.jobTrackEnd();  // Ends the tracking session
    }
```

###  Re-centering the Map Based Current Tracking Data

```js    
    if (trackingCallBackData) {
        trackingCallBackData.settrackfit(true);  // Auto-fit map to the route
        document.getElementById('recenter').style.display = "none";  // Hide recenter button
    }
```
### Error Handling
It is important to handle errors effectively when using mappls.intouchTracking:
- **Map not loading**: Ensure the map object is initialized and correctly passed to the tracking function.
- **Invalid job ID**: Ensure the jobId is valid and corresponds to an active job.
- **Tracking data is unavailable**: Always check the data object in the callback to ensure it contains the expected information (e.g., data.dur, data.dis).



<br>

For any queries and support, please contact: 

[<img src="https://about.mappls.com/images/mappls-logo.svg" height="40"/> </p>](https://about.mappls.com/api/)
Email us at [apisupport@mappls.com](mailto:apisupport@mappls.com)


![](https://www.mapmyindia.com/api/img/icons/support.png)
[Support](https://about.mappls.com/contact/)
Need support? contact us!

<br></br>
<br></br>

[<p align="center"> <img src="https://www.mapmyindia.com/api/img/icons/stack-overflow.png"/> ](https://stackoverflow.com/questions/tagged/mappls-api)[![](https://www.mapmyindia.com/api/img/icons/blog.png)](https://about.mappls.com/blog/)[![](https://www.mapmyindia.com/api/img/icons/gethub.png)](https://github.com/Mappls-api)[<img src="https://mmi-api-team.s3.ap-south-1.amazonaws.com/API-Team/npm-logo.one-third%5B1%5D.png" height="40"/> </p>](https://www.npmjs.com/org/mapmyindia) 



[<p align="center"> <img src="https://www.mapmyindia.com/june-newsletter/icon4.png"/> ](https://www.facebook.com/Mapplsofficial)[![](https://www.mapmyindia.com/june-newsletter/icon2.png)](https://twitter.com/mappls)[![](https://www.mapmyindia.com/newsletter/2017/aug/llinkedin.png)](https://www.linkedin.com/company/mappls/)[![](https://www.mapmyindia.com/june-newsletter/icon3.png)](https://www.youtube.com/channel/UCAWvWsh-dZLLeUU7_J9HiOA)




<div align="center">&copy  Copyright 2023 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>



















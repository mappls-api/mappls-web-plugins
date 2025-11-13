[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api)


# Intouch Historical Trail Widget 

**Easy To Integrate Routing APIs & Map SDKs For Web Applications**

Powered with India's most comprehensive and robust mapping functionalities. 

## Document Version History

| Version | Last Updated | Team | Author |Remarks |
| ---- | ---- | ---- | ---- | ---- |
| 1.0 | 07 Aug 2025 | SDK Product Team | Prabhjot Kaur ([PK](https://github.com/prabhjot729)) | OAuth 2 |


## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://auth.mappls.com/console), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://auth.mappls.com/console) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using [Mappls Portal](https://auth.mappls.com/console)

## Introduction 
The mappls.intouchTracking is part of the Mappls SDK (formerly MapmyIndia) and is designed to provide real-time tracking and display of routes and activities on a map. This method supports job tracking functionality to visualize movement and journey progress on a map.
This document provides an overview of how to use the mappls.intouchTracking function, including configuration options and code examples.

## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://auth.mappls.com/console), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://auth.mappls.com/console) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using [Mappls Portal](https://auth.mappls.com/console)
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Tracking Plugin. [Javascript Code Example - WIP]() & [Working NPM Code - WIP]()

# Table of Contents

- [Intouch Historical Trail Widget](#intouch-historical-trail-widget)
  - [Document Version History](#document-version-history)
  - [Getting Access](#getting-access)
  - [Introduction](#introduction)
  - [Getting Access](#getting-access-1)
- [Table of Contents](#table-of-contents)
- [Implementation](#implementation)
    - [Step 1: Initialize plugins Map SDK and add (\& libraries=intouchTracking) in the url](#step-1-initialize-plugins-map-sdk-and-add--librariesintouchtracking-in-the-url)
    - [Step 2 : Add map under div container in your project](#step-2--add-map-under-div-container-in-your-project)
    - [Step 3 : Initialize Map \& declare variables](#step-3--initialize-map--declare-variables)
    - [Step 4 : Add tracking options in mappls.intouchTracking() method](#step-4--add-tracking-options-in-mapplsintouchtracking-method)
    - [Step 5: Method call for Initialising the Tracking Plugin with options](#step-5-method-call-for-initialising-the-tracking-plugin-with-options)
  - [Mandatory Parameters of intouchTracking() Options](#mandatory-parameters-of-intouchtracking-options)
  - [Optional Parameters of intouchTracking() Options](#optional-parameters-of-intouchtracking-options)
    - [Important Entities](#important-entities)
    - [Other Optional Configuration of intouchTracking() Options](#other-optional-configuration-of-intouchtracking-options)
  - [Callback Function of intouchTracking() method](#callback-function-of-intouchtracking-method)
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
var map;
function initMap1() {
    map = new mappls.Map('map', {
    center: [28.58089892895083, 77.25187057891208],
    zoom: 12
    });
```


### Step 4 : Add tracking options in mappls.intouchTracking() method

```js

    map.addListener('load', function () { 
                var tracking_option = {
                    map: map, // required
                    deviceId:'10647019', // required
                    type:'Trail', // required
                    startTime:'1737963660', // required
                    endTime: '1737991197', // required
                    /* skipPeriod: 1, */
                    fitBounds:true, 
                    strokeWidth: 4,
                    routeColor: "blue",
                    pointType:'arrow' // default 'circle' / arrow'
                }
    });
```

### Step 5: Method call for Initialising the Tracking Plugin with options

```js
tracking_plugin = mappls.intouchTracking(tracking_option, function (data) {
    console.log(data); 
    });
```

## Mandatory Parameters of intouchTracking() Options

- `map`(object): vector map or raster map object from respective Mappls Map SDKs.  This is the map on which the tracking will be displayed. It must be a valid instance of the map object.
- `type` (String) : Defines the type of tracking. Possible values are:
  - `Trail`: For Historical Trail visualization.
- `deviceId` (String or Number) : The unique identifier for the historical trail visualization. 

  Example: `12345`

## Optional Parameters of intouchTracking() Options

### Important Entities

- **trackingOptions (Object)**: This request object contains various configuration settings that define how the tracking plugin initialises &  behaves on the map. It allows developers to customize the tracking experience.
- **callback (Function)**: A callback function that is invoked when tracking data is updated or received. The of intouchTracking() provides a callback that will transmit object containing the important tracking data.


### Other Optional Configuration of intouchTracking() Options 
The trackingOptions object provides various properties for customizing the tracking behavior. Below is a description of each property:

- `startTime` : Starting time of the trail visualization
- `endTime` : End time of the trail visualization
- `fitBounds` (Boolean): If true, the map will automatically adjust its view to fit the route. If false, the map will not adjust its bounds automatically.
- `fitboundsOptions` (Object): This option allows you to specify additional parameters when adjusting the map’s bounds. Common parameter is padding, which defines the padding (in pixels) to be applied to the map's edges when fitting bounds. 
  Example: 
  ```js
    fitboundsOptions: {
         padding: 80,
       }
  ```
- `strokeWidth` (Number): Specifies the width (in pixels) of the route line displayed on the map.
- `pointType`: type of visualization preffered as historical trail. // default 'circle'/'arrow'
- `strokeOpacity` (integer): //signifies opacity of the route polyline. //optional; default is 1. Opacity values from 0 to 1.
- `routeColor` (String): Defines the color of the route line. You can provide a CSS color value (e.g., 'blue', '#FF5733').

## Callback Function of intouchTracking() method
The callback function is triggered when tracking plugin is initialised. This means the first values within this callback indicate the original duration and distance estimates for this tracking trail. This function receives a data object containing the initial route information.
The callback function signature is as follows:
- `function callback(data);`

The data object may contain the following properties:
- `dur` (String): The duration of the journey, formatted as "hh:mm:ss".
- `dis` (String): The total distance to be traveled in the journey, usually in kilometers or miles. Default is kms.



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
- `Invalid device ID`: Ensure the deviceId is valid and corresponds to an historical trail.
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



















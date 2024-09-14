[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://www.mapmyindia.com/api)


# Mappls Tracking Advanced Plugin 

**Easy To Integrate Routing APIs & Map SDKs For Web Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (http://www.mapmyindia.com/api/dashboard) in the sample code for interactive map development.
2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs.

## Document Version History

| Version | Last Updated  | Author                                                        |Remarks
| ------- | ------------- | ------------------------------------------------------------- |-------------- |
| 1.0  | 15 Dec 2022 | MapmyIndia API Team ([MS](https://github.com/mamtasharma117)) | Initial Commit
| 1.1  | 10 Sep 2024 | MapmyIndia API Team ([PK](https://github.com/prabhjot729)) | Document Update

## Introduction

This advanced tracking plugin, offered by Mappls plugins for Web, allows one to track the path traveled with **smooth animation** along the route. The smooth animation by plugin directly depend upon the frequency of the provided information on the current location, time, and speed of the vehicle being tracked to the plugin. _More the Merrier!_


## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://apis.mappls.com/console/), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://apis.mappls.com/console/) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using Token Generation API.
    - To know more on how to create your access tokens, please use our authorization API URL. More details available [here](https://about.mappls.com/api/advanced-maps/doc/authentication-api.php)
    - The `access token` is a valid by default for 24 hours from the time of generation. This can be configured by you in the API console.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Tracking Plugin. [Javascript Code Example](https://about.mappls.com/api/web-sdk/vector-plugin-example/Tracking/mappls-tracking-plugin) & [Working NPM Code](https://codesandbox.io/p/sandbox/z5qmtq)

## Implementation


### Initialize the Plugin

 #### Step 1: Initialize plugin SDK and add (& libraries=tracking) in the url

```js 
<script src="https://api.mappls.com/advancedmaps/api/<token>/map_sdk_plugins?v=3.0&libraries=tracking"></script> 
```

 #### Step 2 : Add map under div container in your project

 ```js
   <div id="map"></div>
 ```

#### Step 3 : Initialize Map 

```js
map = new mappls.Map('map', {
    center: [28.62988695137534, 77.4224575062193],
                zoom: 12
         })

```

#### Step 4 : Add tracking option in mappls.tracking() method

```js
var tracking_option = {
    map: map, // Required mapObject
    start: [{ geoposition: "28.63124010064198,77.46734619140625" }, // Required
    via:[{geoposition:"28.63124010064198,77.5541"},
           {geoposition:"28.631541442089226,77.4541"}], // optional
    end: { geoposition: "28.631541442089226,77.37808227539064" }, // Required
    resource:"route_eta", // optional
profile: "driving", // optional
    fitBounds: true,  // optional
    connector:true, // default false /* to connect the path to end position */,
connectorRouteColor:"gray",   /* connected path route color for end position */
connectorRouteDash:[2, 2],   /* connected path route in dash array for end position */
    ccpIcon:'location.png',  // optional
    ccpIconWidth:70, // optional
    strokeWidth:7, // optional
    routeColor:"blue", // optional 
dasharray:[2,2], // default None and optional 
sPopup:"start text", // optional (for start icon popup)
cPopup:"<h1>current popup</h1>" // optional you can also set html in current icon popup but only in current Icon not start and end
dPopup:"end text", // optional (for end icon popup)
start_icon: {  // optional
        url: 'location.png',
        width: 40, 
        height: 40,
        popupOptions:{offset: {'bottom': [0, -20]}, openPopup:false },
        offset:[0, -18]
    },
    end_icon: {  // optional
        url: 'location.png',
        width: 40, 
        height: 40,
        popupOptions:{offset: {'bottom': [0, -20]}, openPopup:false },
        offset:[0, -18]
    }
}
```
### Mandatory Parameters

  - `map(object)`: vector map or raster map object from respective Mappls Map SDKs.
  - `start` : route start location . For eg -  { geoposition: "28.63124010064198,77.46734619140625" }
  - `end` : route end location . For eg -   { geoposition: "28.631541442089226,77.37808227539064" }

### Optional Parameters

- `Via` : via locations between the route
For eg - [{geoposition:"28.63124010064198,77.5541"},{geoposition:"28.631541442089226,77.4541"}],
- `resource` :"route_eta", To set the route resource. Default to "_route_eta_". 
-	`profile`: “driving”, To set the profile for the route. Default to "_driving_".
- `fitBounds` : true,  // optional
- `ccpIcon` :'location.png',  Supports PNG format as of now.
- `ccpIconWidth` : 70, // optional
- `strokeWidth` : 7, // optional
- `routeColor` : "blue", // optional 
- `dasharray`:[2,2], // default None and optional 
- `sPopup` :”start text”, // optional (for start icon popup)
- `cPopup` :”`<h1>current popup</h1>”`. To set html in current icon popup (_parameter available only for current location Icon_)
- `dPopup` :"end text", available for end icon popup
- `start_icon` : {   url: 'location.png',
                        width: 40, 
                        height: 40,
                        popupOptions:{offset: {'bottom': [0, -20]}, openPopup:false },
                        offset:[0, -18] 
                    }, //Supports PNG format as of now.
- `end_icon` : { url: 'location.png',
                 width: 40, 
                 height: 40 
                popupOptions:{offset: {'bottom': [0, -20]}, openPopup:false },
                /* offset:[0, -18] */
                    },Supports PNG format as of now.
- start_icon:false // if set as false then marker will not be visible
- end_icon: false // if set as false then marker will not be visible



#### Step 5: Method call  for Tracking Plugin

```js
// With tracking option as a variable

mappls.tracking(tracking_option, function(data) {
                        console.log(data);
                        data1 = data;
});

```
```js
// Or Without tracking option as a variable
mappls.tracking({
    map: map,
    start: {
        geoposition: "28.63124010064198,77.46734619140625"
    },
    end: {
        geoposition: "28.631541442089226,77.37808227539064"
    },
    fitBounds: true,
    ccpIconWidth: 70,
    strokeWidth: 7,
    routeColor: "blue",
    /*
     cPopup:'<h3>Current Popup</h3>',
     */
}
tracking_plugin = mappls.tracking(tracking_option, function(data) {
    console.log(data);
    trackingCallbackData = data;
});
}
, function(data) {
    console.log(data);
    trackingCallbackData = data;
});
```
##### Tracking callbacks

- `trackingCallbackData.settrackfit(true/false);`  (default is true, fitbounds the track)
- `trackingCallbackData.setccpContent(“content”);` (set popup on start)
- `trackingCallbackData.setLineHide(true/false);`  (to make path invisible)

### Methods

`mappls.tracking()`


#### Step 6: Method to inject User data

```js
     trackingCallbackData.trackingCall({
       location: user, // Required
       reRoute: true, // default true or optional
       heading: true, // default true
       mapCenter: false, // default false
       polylineRefresh: true /* it refreshes the covered route */,
       buffer: 50, // default 25
       etaRefresh: true /* to get distance and duration in callback */,
       latentViz: false /* when clicked on map, icon first goes to clicked path with following route  */,
       delay: 3000, // default 5000
       fitCoverDistance:true, // default is false 
       fitBounds: true, // default true
       fitboundsOptions: {
         padding: 80,
       },
       callback: function (datap) {
         console.log(datap);
       },
     });
```


## Properties

### Mandatory Parameters

- `map(object)`: vector map or raster map object from respective Mappls Map SDKs.
- `start` : route start location . For eg -  { geoposition: "28.63124010064198,77.46734619140625" }
- `end` : route end location . For eg -   { geoposition: "28.631541442089226,77.37808227539064" }

### Optional Parameters

- `reRoute` : To refresh the route as per the current location. This means the route will change as per the current location. If kept false the same route will be displayed. Default is true.
- `heading` : To control the rotation of the marker as per the route direction.For example if you are using a car icon, it would rotate as per the route direction otherwise it would move straight . Default is true.
- `Buffer` :50,  The distance defined for call reroute for the ptovided current location. 
- `fitbounds` : Allowing this would fit the map in the view bound.Default is true.
- `mapCenter` :true, keeps the current on the center of the map.
- `fitboundsOptions`:{padding:80}, // optional
- `Connector` : true, from the last navigable point on road to actual input destination corordinate // default false
- `ConnectorRouteColor` : "gray",
- `ConnectorRouteDash` : [2, 2], //[Length, Space of the route dash]
- `polylineRefresh: true, // default true`
- `latentViz:true, // default false`
- `etaRefresh:false, // default false`


## Implementation Example

 ```js

  <html>
  <head>
    <title>Tracking</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Tracking">

        <script src="https://apis.mappls.com/advancedmaps/api/<Token>/map_sdk?layer=vector&v=3.0&callback=initMap1"></script>
          <script src="https://apis.mappls.com/advancedmaps/api/<token>/map_sdk_plugins?v=3.0"></script>
          <style>
        body {
            margin: 0;
        }

        #map {
            width: 100%;
            height: 100vh;
            margin: 0;
            padding: 0;
        }
    </style>
    </head>

    <body>
        <div id="map"></div>
                <script>
            /*Map Initialization*/
            var map;

            function initMap1() {
                map = new mappls.Map('map', {
                    center: [28.62988695137534, 77.4224575062193],
                    zoom: 12
                });
                map.addListener('load', function() {
                    /*tracking plugin initialization*/
                    var tracking_option = {
                        map: map,
                        start: {
                            geoposition: "28.63124010064198,77.46734619140625"
                        },
                        end: {
                            geoposition: "28.631541442089226,77.37808227539064"
                        },
                        fitBounds: true,
                        ccpIconWidth: 70,
                        strokeWidth: 7,
                        routeColor: "blue",
                        /* 
                        cPopup:'<h3>Current Popup</h3>',
                         */
                    }
                    tracking_plugin = mappls.tracking(tracking_option, function(data) {
                        console.log(data);
                        data1 = data;
                    });
                });

                map.on('click', function(e) {
                    var user = [e.lngLat.lng, e.lngLat.lat];
                    data1.trackingCall({
                        location: user,
                        reRoute: true,
                        heading: true,
                        mapCenter: false,
                        buffer: 50,
                        delay: 3000,
                        fitBounds: false,
                        fitboundsOptions: {
                            padding: 80
                        },
                        callback: function(data) {
                            console.log(data)
                        }
                    });
                });
            }
        </script>
        </body>
  </html>

 ```


<br>
That's All !

For any queries and support, please contact:


[<img src="https://about.mappls.com/images/mappls-logo.svg" height="40"/> </p>](https://about.mappls.com/api/)
Email us at [apisupport@mappls.com](mailto:apisupport@mappls.com)

![](https://www.mapmyindia.com/api/img/icons/support.png)
[Support](https://www.mapmyindia.com/api/index.php#f_cont)
Need support? contact us!

<br></br>

[<p align="center"> <img src="https://www.mapmyindia.com/api/img/icons/stack-overflow.png"/> ](https://stackoverflow.com/questions/tagged/mapmyindia-api)[![](https://www.mapmyindia.com/api/img/icons/blog.png)](http://www.mapmyindia.com/blog/)[![](https://www.mapmyindia.com/api/img/icons/gethub.png)](https://github.com/MapmyIndia)[<img src="https://mmi-api-team.s3.ap-south-1.amazonaws.com/API-Team/npm-logo.one-third%5B1%5D.png" height="40"/> </p>](https://www.npmjs.com/org/mapmyindia)

[<p align="center"> <img src="https://www.mapmyindia.com/june-newsletter/icon4.png"/> ](https://www.facebook.com/MapmyIndia)[![](https://www.mapmyindia.com/june-newsletter/icon2.png)](https://twitter.com/MapmyIndia)[![](https://www.mapmyindia.com/newsletter/2017/aug/llinkedin.png)](https://www.linkedin.com/company/mapmyindia)[![](https://www.mapmyindia.com/june-newsletter/icon3.png)](https://www.youtube.com/user/MapmyIndia/)

<div align="center">@ Copyright 2020 CE Info Systems Pvt. Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://www.mapmyindia.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://www.mapmyindia.com/about/privacy-policy">Privacy Policy</a> | <a href="https://www.mapmyindia.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://www.mapmyindia.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://www.mapmyindia.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

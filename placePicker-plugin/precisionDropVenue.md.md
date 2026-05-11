---
title: precisionDropVenue.md

---

[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api)

# Precision Drop Venue Plugin for Mappls Web Maps

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for [200+ nations and territories](https://github.com/MapmyIndia/mapmyindia-rest-api/blob/master/docs/countryISO.md) accross the world.

## Getting Access

Before using the API in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://auth.mappls.com/console/), within your app - be it for Mobile OR Web or Cloud integration.

1. Copy and paste the key from your `credentials` section from your API [keys](https://auth.mappls.com/console/) into the `access_token` query parameter.
    - Your static key can be secured by whitelisting its usage for particular IPs (in case of cloud app usage) OR a set of domains (in case of a web app)
    - Your static key obtained from your Console is to be passed as a query parameter: `access_token`.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Precision Drop Venue Plugin. [See Sample Codes here](https://about.mappls.com/api/web-sdk/vector-plugin-example/Placepicker/mappls-placepicker-plugin) 

## Authentication Object - `access_token` mandatory query parameter.

-  `access_token`: "hklmgbwzrxncdyavtsuojqpiefrbhqplnm".

## Document Version History

| Version | Last Updated | Team | Author 

| 1.0 | 07 Aug 2025 | SDK Product Team | Prabhjot Kaur ([PK](https://github.com/prabhjot729)) 
| 1.0 | 29 Apr 2026 | SDK Product Team | Prabhjot Kaur ([PK](https://github.com/prabhjot729)) 


## Introduction

A simple plugin / widget to pick places from the map. This SDK also has integrated  Precision Drop Venue Plugin as optional component that enables one to narrow down to picked place by searching for it first and then changing the position of the resulting point on map to fine-tune the results.

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web app implementation. Thus it enables developers to include Mappls Places JS in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to pick or search places directly with or without Mappls Maps visual interface.
2. A mappls.placePicker() method to initiate the plugin and pick places from Mappls Maps.
3. Ability to get information from Mappls  Precision Drop Venue plugin through a callback.
4. Include the  Precision Drop Venue Plugin with or without an interactive Map component.
5. Place/building and Venue boundary highlight.


## Sample Implementation


Visit the [samples](https://about.mappls.com/api/web-sdk/vector-plugin-example/Placepicker/mappls-venue-placePicker) for assistance to create a sample implementation with your own keys. 

For detailed understanding of the plugin, Let’s get started!



## Plugin's Configurations

Adding the Nearby Search plugin in the script
```js
<script src="https://about.mappls.com/api/web-sdk/vector-plugin-example/Placepicker/mappls-venue-placePicker"></script>
```

#### Venue Precision Drop extends the precision drop plugin with:

- Entry point snapping
- Building Boundary highlighting
- Higher accuracy placement
- Venue Boundary Highlighting

### 1. Initializing the  Precision Drop Venue plugin

#### Method

`mappls.placePicker()`

```js
 /* Precision Drop - Venue plugin initialization*/
var options = {
  map: map,
  header: true,
  closeBtn: true,
  pinImage: "https://apis.mappls.com/map_v3/1.png",
  snapToEntry: true, // default false
  snappingRadius: 50, // default 50 --> (snappingRadius > 10 and snappingRadius < 200)
  entryMarkerStyle: {
    size: 10, // default 10
    color: "blue", // default '#ff0000'
    strokeWidth: 4, // default 2
    strokeColor: "", // default '#ffffff'
    /* fillColor: '00000',
                     fillopacity: 1,
                     lineColor: 'FFFFFF',
                     linewidth: 5,
                     lineopacity: 1, */
  
  },
};
mappls.advancePlacePicker(options, callback);
function callback(data) {
  picker = data;
  console.log(picker);
  setTimeout(() => {
    if (picker.data) {
      /*  alert(picker.data.formatted_address); */
    }
  }, 700);
}
```

### Venue Visulaization Workflow : 
- If isVenue is false or absent but isRooftop is true, then it shows building footprint using place geom and its entryCoordinate if it is present.

- If both are true, it shows building footprint using its styling options and venue boundary using its separate styling options.

- If isVenue is true, but isRooftop is false or absent, it shows only venue boundary.


## Styling Options: 

- `Building boundary`: 
buildingFootprintsEnabled - boolean - exists
buildingAppearanceFillColor - string - exists
buildingAppearanceFillOpacity - string - exists
buildingAppearanceStrokeOpacity - double - exists
buildingAppearanceFillOpacity - double - exists
buildingAppearanceStrokeWidth - int - exists
buildingAppearanceStrokeColor - string - exists

- `Building Entry`: as much customizable as possible - even upto a custom marker(symbolLayer driven only); with default being a circular symbolLayer driven icon.
color
image
info (popup) on the side of the icon.

- `Venue Entry points`: similar to above but able to styled independently of above.

- `Navigable venue entry point`: This is a special entry point within the venue entry array and should have its own styling options.

- `venue boundary`: same set of styling options as for building.
venueFootprintsEnabled - boolean
venueAppearanceFillColor - string
venueAppearanceFillOpacity - string
venueAppearanceStrokeOpacity - double
venueAppearanceStrokeWidth - int
venueAppearanceStrokeColor - string

    - for inner - fill [#7782E3 - 60%] & border [#7782E3 - 100%],
    - for outer - fill [#7782E3 - 35%] & border [#7782E3 - 50%]. 
    - border thickness is 2px
    - color for circle is #21469C

- blue (building Entry Coordinates)- fill #3463CE, border #21469C 2px border
- amber (Venue Entry Coordinates) - fill #FFB84D, border #DE9424 2px border


if venue entry end building entry are both together then prefer venue visualization.

#### Other Styling Properties : 

1. `entryMarkerStyle` (Optional) :
Controls entry / gate marker
To Change Default Styles
```js
entryMarkerStyle: {
 `size`: 8,                // default: 8
 `color`: "#3463CE",       // default: "#3463CE"
 `strokeWidth`: 2,         // default: 2
 `strokeColor`: "#21469C", // default: "#21469C"
 `icon`: "marker.png"      // optional (URL/path)
} 
```
Remove marker style
```js 
entryMarkerStyle: false
```

2. `venueMarkerStyle `(Optional) : 
Controls markers inside venue (POIs)
To Change Default Styles
```js
venueMarkerStyle: {
 size: 8,                // default: 8
 color: "#FFB84D",       // default: "#FFB84D"
 strokeWidth: 2,         // default: 2
 strokeColor: "#DE9424", // default: "#DE9424"
 icon: "venue_marker.png"
}
```
Used for shops, nodes, internal POIs
Remove venue marker style 
```js
venueMarkerStyle: false
```

3. `venueStyle` (Optional): 
To Change Default Styles
Controls venue polygon (area boundary)
Enable (object)
```js
venueStyle: {
 lineColor: "#7782E3",   // default: "#7782E3"
 linewidth: 2,           // default: 2
 lineOpacity: 0.5,       // default: 0.5
 fillColor: "#7782E3",   // default: "#7782E3"
 fillOpacity: 0.35       // default: 0.35
}
```
Remove venue style
```js
venueStyle: false
```


### Mandatory Parameters
1. `Place Options`: any object containing any of the two following mandatory configurations values.
    - `map`: object > vector map or raster map object from respective Mappls Map JS
    ##### OR
    - `location`: (lat,lng) object // to get data without map.
2. `callback`: (method): to get data after location selection . If no callback method is specified, UI `GET` button will be hidden. In this case, the consuming app can get data by calling method `getData()`.

#### Optional Parameters
1. `Place Options`: any object containing optional configurations for modifying the search request.
    - `location`: location coordinates which will be used as radial bias (not restriction; only BIAS). e.g. `location:[28.61, 77.23]`
    - `geolocation`: boolean value used to enable or disable current location selection . Default is true.
    - `closeBtn`: (boolean): to give the option to close  Precision Drop Venue  (including hiding the top bar that has search & lower bar area that has the 'Done' button and related sub-text). Default is `true`.
    - `closeBtn_callback`: A callback method that is called when user clicks on the close button at the top left. To provide a call to action upon user closing the  Precision Drop Venue plugin and thus providing the ability to continue towards further action by the consuming app.
    - `search`: (boolean): To enable / disable the integrated Place Search plugin. Default is `true`.
    - `topText`: The banner text to show at the top as title of the  Precision Drop Venue plugin. Default is `Precision Drop Venue`.
    - `pinImage`: (URL) The PIN icon on the map. 
    - `pinHeight`: (number). To adjust the placement of the PIN icon on the map.
    - `searchChars` : number of characters required to start search. e.g searchChars:2
    - `region` : To specify the region for various api response.e.g region : "USA"
    - `snapToEntry` : To snap to the entry point of the location. default value is false
    - `snappingRadius` : To specify the snapping radius.
    - ` entryMarkerStyle` : To modify the entry marker style.
      -  `size`: 10, // default 10
      -  `color`: "blue", // default '#ff0000'
      -  `strokeWidth`: 4, // default 2
      -  `strokeColor`: "", // default '#ffffff'
      -  `fillColor`: '00000', 
      -  `fillopacity`: 1,
      -  `lineColor`: 'FFFFFF',
      -  `linewidth`: 5,
      -  `lineopacity`: 1,
<br>

### 2. Calling Mappls Precision Drop Venue for programmatically fixed text

Following is an example of calling Mappls.placePicker() method programmatically for a fixed pair of coordinates rather than depending on a UI driven approach: 

```js
/*CALL for coordinates - LIKE THIS*/
mappls.placePicker({location:{lat:28.9898,lng:77.9898}},callback);
```

### 3. Method for removing Precision Drop Venue plugin with callback from map
#### Method
`remove()`

```js
obj.remove();
```

### 4. Method for programmatically setting location within callback on map.
#### Method
`setLocation()`

```js
obj.setLocation({lat:28.42424,lng:77.232323});
```

### 5. Method for getting location data from  Precision Drop Venue plugin.

#### Description
This method is especially useful if no callback is given in options.
As per the current status of the  Precision Drop Venue plugin's UI (map view and placement of PIN on map), the location data is returned.

#### Method
`getLocation()`

```js
obj.getLocation();
```


### Response Structure of Precision Drop Venue Data

```js
{	
   {
            "houseNumber": "",
            "houseName": "Tower 2",
            "poi": "CRC Sublimis Apartment Out Gate No 2",
            "poi_dist": "13",
            "street": "Street Number 2",
            "street_dist": "279",
            "subSubLocality": "",
            "subLocality": "CRC Sublimis",
            "locality": "Sector 1",
            "village": "Bisrakh Jalalpur",
            "vlgCenCd": "120139",
            "vlgLgdCd": "120139",
            "district": "Gautambuddha Nagar District",
            "dstCenCd": "141",
            "dstLgdCd": "144",
            "subDistrict": "Dadri",
            "sdbCenCd": "00742",
            "sdbLgdCd": "742",
            "city": "Greater Noida",
            "state": "Uttar Pradesh",
            "sttCenCd": "09",
            "sttLgdCd": "9",
            "pincode": "201318",
            "lat": "28.576491000000033",
            "lng": "77.43115900000004",
            "area": "India",
            "areaCode": "IN",
            "eLoc": "1FVG49",
            "twnName": "",
            "twnCenCd": "",
            "twnLgdCd": "",
            "isRooftop": false,
            "isVenue": true,
            "venueDetails": {
                "venueEloc": "00XPJK",
                "venueName": "CRC Sublimis",
                "venueAddress": "Sector 1, Greater Noida, Uttar Pradesh, 201318",
                "venueEntries": [
                    {
                        "elat": "28.576397000000043",
                        "elng": "77.43121700000006",
                        "eName": "CRC Sublimis Apartment Out Gate No 2",
                        "eType": "Gate",
                        "eTag": {
                            "type": "Exit"
                        }
                    },
                    {
                        "elat": "28.576873000000035",
                        "elng": "77.43207700000005",
                        "eName": "CRC Sublimis Apartment In Gate No 1",
                        "eType": "Gate",
                        "eTag": {
                            "type": "Entry"
                        }
                    },
                    {
                        "elat": "28.576491000000033",
                        "elng": "77.43115900000004",
                        "eName": "CRC Sublimis",
                        "eType": "Navigable",
                        "eTag": {
                            "type": ""
                        }
                    }
                ]
            },
            "formatted_address": "Tower 2, Street Number 2, CRC Sublimis, Sector 1, Greater Noida, Uttar Pradesh. 13 m from CRC Sublimis Apartment Out Gate No 2, Pin-201318 (India)"
        }




```




That's All ! Visit the [samples](https://about.mappls.com/api/web-sdk/vector-plugin-example/Placepicker/mappls-venue-placePicker) for assistance to create a sample implementation with your own keys. 


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




<div align="center">@ Copyright 2022 CE Info Systems Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

## Introduction

Venue Place Picker enables venue boundaries, building footprints, and entry points.

---


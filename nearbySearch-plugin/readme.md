[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api)


# Nearby Search Plugin for Mappls Web Maps

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for [200+ nations and territories](https://github.com/MapmyIndia/mapmyindia-rest-api/blob/master/docs/countryISO.md) accross the world.

## Getting Access

Before using the API in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://auth.mappls.com/console/), within your app - be it for Mobile OR Web or Cloud integration.

1. Copy and paste the key from your `credentials` section from your API [keys](https://auth.mappls.com/console/) into the `access_token` query parameter.
    - Your static key can be secured by whitelisting its usage for particular IPs (in case of cloud app usage) OR a set of domains (in case of a web app)
    - Your static key obtained from your Console is to be passed as a query parameter: `access_token`.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Nearby Search Plugin. [See Sample Codes here](https://about.mappls.com/api/web-sdk/vector-plugin-example/Nearbysearch/mappls-nearbysearch-plugin)

## Authentication Object - `access_token` mandatory query parameter.

-  `access_token`: "hklmgbwzrxncdyavtsuojqpiefrbhqplnm".

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

A simple plugin / widget to search for nearby places powered by the best online maps from Mappls. The Nearby Search plugin for Mappls Web Map JS library is provided as a means to enable radially searching for Nearby Places on Mappls Maps. 

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web app implementation. Thus it enables developers to include Mappls web JS in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to search for nearby places directly with or without Mappls Maps visual interface.
2. A Mappls.nearby() method to initiate nearby search across all categories of places available on Mappls.
3. Ability to get information from Mappls Place Search plugin through a callback
4. Include the Nearby Search Plugin with or without an interactive Map component.


## Sample Implementation


Visit the [samples](https://about.mappls.com/api/web-sdk/vector-plugin-example/Nearbysearch/mappls-nearbysearch-plugin) for assistance to create a sample implementation with your own keys. 

For detailed understanding of the plugin, Let’s get started!



## Plugin's Configurations

Adding the Nearby Search plugin in the script

```js
<script src="https://sdk.mappls.com/map/sdk/plugins?access_token=<Static Key>&v=3.0&libraries=nearby"></script>
```

### 1. Initializing the Nearby Search plugin

#### Method

`mappls.nearby()`

```js
/*Nearby plugin initialization*/
var options = {
  divId: 'nearby_search',
  map: map,
  keywords: 'atm',
  refLocation: [28.632735, 77.219696],
  fitbounds: true,
  geolocation: true,
  click_callback: function(d) {
    alert(d);
  }
}

mappls.nearby(options, callback);
```

#### Mandatory Parameters
1. `keywords`: The string or JSON object which will be passed as input query to the search engine. Examples
    - **As a string**: `keywords:"atm"`. This parameter supports input in Hindi Language `keywords:"चाय"`. To get the feature contact apisupport@mapmyindia.com.
    - **As a JSON object**: `keywords:{'FINATM':'ATMS','FODCOF':'Restaurants'}`. This parameter supports input in Hindi Language `keywords:{'एचडीएफसी ':'एटीएम'}`. To get the feature contact apisupport@mapmyindia.com.
    <br>This mechanism is used to display a selection of POI categories on a UI.
    <br>If `keywords` parameter is used, then `refLocation` input also becomes mandatory.
2.  `callback`: (method): results will be returned in this method if specified.

OR

1. `hyperLink`: This is the URL received from Mappls Place Search plugin for bridged Nearby Search. i.e. A Nearby Search trigerred directly from the Place Search Plugin.

#### Optional Parameters
1. `refLocation`: location coordinates which will be used as centroid of the radial search reference . e.g. `refLocation:[28.61, 77.23]` OR `refLocation:[28.61, 77.23]`
2. `map`: A map object from our Maps SDK. Markers can also be passed here that will be displayed on map. Custom icons also can be passed here.
3. `divId`: The HTML where developer wishes results to be displayed.
    <br>Example: `divId:document.getElementbyId('Nrdiv');`
4. `divHeight`: (in pixels) for customizing or improving results display UI.
5. `icon`: (object) To set the icons of the resulting categories of results.
    - *Single Category*: Example: 
        ```js
        icon: {
            url: '2.png'
        }
        ```
        OR 
         ```js
         icon: {
            html: " < div > < img src = 'pin.png' > < /div>",
            width: 30,
            height: 40
        }
        ```
    - *Multiple Category*: Example: 
        ```js
        icon: {
            'FINATM': {
                url: 'atm.png',
                height: 40,
                width: 30
            },
            'FODCOF': {
                url: 'food.png',
                height: 40,
                width: 32
            }
        }
        ```
        Optional parameters for icon configuration are as follows:
        - `offset`: Example: `offset:[20,40]`
        - `popupAnchor`: Example: `popupAnchor:[-10,20]`
6. `popup`: (boolean) Default is true if map is used. Used to bind popup to markers.
7. `popupOptions`: (object) Used to define pop up optional configuration. <br>Example: `popupOptions: {maxWidth:250}`
8. `fitbounds`: (boolean) Default is true. Used to fit all markers to in map view bound.
9. `geolocation`: boolean value used to enable or disable current location selection . Default is true.
10. `radius`: (number): Defines the radius of nearby search.
11. `bounds`: (geographic bounds): Used to define the rectangular bounds within which nearby search will work.
12. `sortBy`: (string)Used to sort the nearby search results.
13. `page`: (number): to request another page of results if available.
14. `pod`: (string): to filter to a certain type of results.
15. `searchChars` : number of characters required to start search. e.g searchChars:2
16. `region` : To specify the region for various api response.e.g region : "USA"
17. `callback_click`: (method): a method that will be called when user clicks on any listing. The action returns the eLoc of the selected place.

<br>

### Types of Nearby Search Implementations

#### 1. Get data from category & coordinates

Following is an example of calling mappls.nearby() method to get data from category and coordinates: 

```js
var res=mappls.nearby({keywords:"atm",refLocation:"123ZRR"});
```

#### 2. Get data from Mappls Search category url

```js
var res=mappls.nearby({hyperLink:'https://atlas.mappls.com/api/places/nearby/json?explain&richData&&refLocation=28.61,77.23&keywords=FINATM'});
```

#### 3. Get data from category & location selection UI

```js
var res=mappls.nearby({divId:'nearby_divId',keywords:{'FINATM':'ATMs', 'FODCOF':'Restaurants'}});
```
This will place a selection of keywords and a location selection UI inside `divId`.

### Remove Nearby Markers within callback from Map

Use remove() method to remove markers from map.

```js
var markers=res.markers();
markers.remove();
```

### Add Event to Markers

Use addListener() method to associate events to markers.

```js
markers.addListener('click',function(data){ console.log(data);});
```


That's All !  Visit the [samples](https://about.mappls.com/api/web-sdk/vector-plugin-example/Nearbysearch/mappls-nearbysearch-plugin) for assistance to create a sample implementation with your own keys. 


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

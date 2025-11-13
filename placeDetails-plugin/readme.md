[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api)


# Place Details Plugin for Mappls Web Maps

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for [200+ nations and territories](https://github.com/MapmyIndia/mapmyindia-rest-api/blob/master/docs/countryISO.md) accross the world.


## Document Version History

| Version | Last Updated | Team | Author |Remarks |
| ---- | ---- | ---- | ---- | ---- |
| 1.0 | 07 Aug 2025 | SDK Product Team | Prabhjot Kaur ([PK](https://github.com/prabhjot729)) | OAuth 2 |


## Getting Access

Before using the API in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://auth.mappls.com/console/), within your app - be it for Mobile OR Web or Cloud integration.

1. Copy and paste the key from your `credentials` section from your API [keys](https://auth.mappls.com/console/) into the `access_token` query parameter.
    - Your static key can be secured by whitelisting its usage for particular IPs (in case of cloud app usage) OR a set of domains (in case of a web app)
    - Your static key obtained from your Console is to be passed as a query parameter: `access_token`.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls PIN (eLoc) Plugin. [See Sample Codes here](https://github.com/mappls-api/mappls-web-plugins/tree/main/eLoc-plugin) 


## Authentication Object - `access_token` mandatory query parameter.

-  `access_token`: "hklmgbwzrxncdyavtsuojqpiefrbhqplnm".


## Introduction

A simple plugin / widget to render details of a particular place. The Place Details plugin for MapmyIndia Web Map JS library is provided as a means to enable rendering of MapmyIndia Places on MapmyIndia Maps. 

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web map implementation. Thus it enables developers to include MapmyIndia Places SDK in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to render places directly on map with reference to the provided eLoc(s).
2. A getPinDetails() method to fetch the details of a place.
3. Customizable markers
4. Remove markers from map.

## Sample Implementation


Visit the [samples](https://github.com/mappls-api/mappls-web-plugins/tree/main/eLoc-plugin) for assistance to create a sample implementation with your own keys. 

For detailed understanding, Let’s get started!

## Plugin's configurations

Adding the Place Details plugin in the script

#### 1. Script URL

```js
<script src="https://sdk.mappls.com/map/sdk/plugins?access_token=<Static Key>&v=3.0&libraries=getPinDetails"></script>
```

### 2. Initializing the Place Details plugin
#### Method

`Mappls.getPinDetails()`

```js
Mappls.getPinDetails({ map: map, pin: '3F45CB'}, callback);
```

#### Mandatory Parameters
1. `getPinDetails`: The pin (Mappls Pin/Eloc) whose details are required.
2. `callback`: to return data to a specified callback method.


#### Optional Parameters
1. `map`: Map Object
2. `icon`: custom icon url.
3. `divId`: The div to put the result in.
4. `markerPopup` (boolean): to show pop-ups on marker click. Default is true.(example: `markerPopup:true`)
5. `popupHtml`: to show html pop up on marker click. User should define values to be shown while using this parameter.(example: `obj.setPopup({content:"<h1>Hello MapmyIndia</h1>"})`)
6. `fitbounds` (boolean): To show all rendered eLoc(s) in a single view bound. (example: `fitbounds:true`)
7. `fitboundOptions` : padding in fitbounds, if any. (Example: `{ padding:50,maxZoom:18}`)
8. `infoDiv` (boolean): To render html div on map or not. Default is true. (example: `infoDiv:true`)
9. `click_callback`: method to call on click of callback. 

### 3. Method to remove the markers with callback populated by Place Details Plugin

```js
pinObj.remove();
```

### 4. Method to set up the div content for populating details from getEloc() plugin

```js
pinObj.setDivContent(“Div html);
```
### 5. Method to set up the pop up content on marker as html.
For Eg:

```js
pinObj.setPopup({content:"<h1>Hello Mappls</h1>"});
```


That's All ! Visit the [samples](https://github.com/mappls-api/mappls-web-plugins/tree/main/eLoc-plugin) for assistance to create a sample implementation with your own keys.



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

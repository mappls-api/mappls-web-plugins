![MapmyIndia APIs](https://www.mapmyindia.com/api/img/mapmyindia-api.png)

# Mappls Route Events Summary Plugin 

**Easy To Integrate Routing APIs & Map SDKs For Web Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (http://www.mapmyindia.com/api/dashboard) in the sample code for interactive map development.
2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs.

## Document Version History

| Version | Last Updated  | Author                                                        |Remarks
| ------- | ------------- | ------------------------------------------------------------- |-------------- |
| 3.0  | 27 Oct 2022 | MapmyIndia API Team ([MS](https://github.com/mamtasharma117)) | Initial Commit

## Introduction

This plugin, offered by Mappls plugins for Web, with the help Mappls Rest API response dependency, provide the route events for the selected route.

This feature is also available inbuilt with Mappls Direction Plugin. For details, please contact apisupport@mapmyindia.com.

## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://apis.mappls.com/console/), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://apis.mappls.com/console/) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using Token Generation API.
    - To know more on how to create your access tokens, please use our authorization API URL. More details available [here](https://about.mappls.com/api/advanced-maps/doc/authentication-api.php)
    - The `access token` is a valid by default for 24 hours from the time of generation. This can be configured by you in the API console.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Direction Plugin. [See Sample Codes here](https://about.mappls.com/api/web-sdk/vector-plugin-example/Direction/mappls-event-alongtheroute-direction-plugin)

## Implementation


### Script URL

```js
<script src="https://apis.mapmyindia.com/advancedmaps/api/{access_token}/map_sdk_plugins?v=3.0&libraries=routesummary"></script>
```

## Method

`mappls.routeSummary()`

## Properties

### Mandatory Parameters

  - map(object): vector map or raster map object from respective Mappls Map SDKs.
  - routeId (String) : routeId, Provide routeId if users needs to get all routes reports summary.

### Optional Parameters


 - Index (String) : routeIdx, Provide routeIdx if user needs routes reports for a selected route only Otherwise returns events for all suggested routes.

 - nodeId (String) : nodeId, nodeId of the Route.

 - categories (String) : Optional, categories (comma(,) separated String).

 - isGroup (Integer) : sGroup, Set to 1, if user needs parentCategory wise grouped data.


## Example


 ```js
mappls.routeSummary({
            map:map,
            routeId:routeId,
            index:0 , 
            categories:"",
            nodeId:"",
            isGroup:0
        },
        function(data){
            console.log(data);
        });
 ```

## Sample Implementation

```html
<html>
   <head>
      <title>Mappls Plugin - Route Events Summary</title>
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta name="desciption" content="Mappls Route Report Summary Plugin">
      <script src="https://apis.mapmyindia.com/advancedmaps/api/{access_token}/map_sdk_plugins?v=3.0&libraries=routesummary"></script>
      <style>
         body{margin: 0}
         #map{
         width: 100%; height: 100vh;margin:0;padding: 0;
         }
      </style>
   </head>
   <body>
      <div id="map"></div>
      <script>
         /*Map Initialization*/
          var map = new mappls.Map('map', {center: [28.62, 77.09], zoom: 15, search: false});
          
          /* RouteReport plugin initialization*/
           mappls.routeSummary({
                map:map,
                routeId:routeId,
                index:0 
        },
        function(data){
            console.log(data);
        });

      </script>
   </body>
</html>
```



<br>
That's All !

For any queries and support, please contact:

[<img src="https://www.mapmyindia.com/images/logo.png" height="40"/> </p>](https://www.mapmyindia.com/api)
Email us at [apisupport@mapmyindia.com](mailto:apisupport@mapmyindia.com)

![](https://www.mapmyindia.com/api/img/icons/support.png)
[Support](https://www.mapmyindia.com/api/index.php#f_cont)
Need support? contact us!

<br></br>

[<p align="center"> <img src="https://www.mapmyindia.com/api/img/icons/stack-overflow.png"/> ](https://stackoverflow.com/questions/tagged/mapmyindia-api)[![](https://www.mapmyindia.com/api/img/icons/blog.png)](http://www.mapmyindia.com/blog/)[![](https://www.mapmyindia.com/api/img/icons/gethub.png)](https://github.com/MapmyIndia)[<img src="https://mmi-api-team.s3.ap-south-1.amazonaws.com/API-Team/npm-logo.one-third%5B1%5D.png" height="40"/> </p>](https://www.npmjs.com/org/mapmyindia)

[<p align="center"> <img src="https://www.mapmyindia.com/june-newsletter/icon4.png"/> ](https://www.facebook.com/MapmyIndia)[![](https://www.mapmyindia.com/june-newsletter/icon2.png)](https://twitter.com/MapmyIndia)[![](https://www.mapmyindia.com/newsletter/2017/aug/llinkedin.png)](https://www.linkedin.com/company/mapmyindia)[![](https://www.mapmyindia.com/june-newsletter/icon3.png)](https://www.youtube.com/user/MapmyIndia/)

<div align="center">@ Copyright 2020 CE Info Systems Pvt. Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://www.mapmyindia.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://www.mapmyindia.com/about/privacy-policy">Privacy Policy</a> | <a href="https://www.mapmyindia.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://www.mapmyindia.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://www.mapmyindia.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

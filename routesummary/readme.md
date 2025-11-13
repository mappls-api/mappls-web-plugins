[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api)



# Mappls Route Events Summary Plugin 

**Easy To Integrate Routing APIs & Map SDKs For Web Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (http://auth.mappls.com/console) in the sample code for interactive map development.
2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs.

## Document Version History

| Version | Last Updated | Team | Author |Remarks |
| ---- | ---- | ---- | ---- | ---- |
| 1.0 | 07 Aug 2025 | SDK Product Team | Prabhjot Kaur ([PK](https://github.com/prabhjot729)) | OAuth 2 |

## Introduction

This plugin, offered by Mappls plugins for Web, with the help Mappls Rest API response dependency, provide the route events for the selected route.

This feature is also available inbuilt with Mappls Direction Plugin. For details, please contact apisupport@mapmyindia.com.

## Getting Access

Before using the API in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://auth.mappls.com/console/), within your app - be it for Mobile OR Web or Cloud integration.

1. Copy and paste the key from your `credentials` section from your API [keys](https://auth.mappls.com/console/) into the `access_token` query parameter.
    - Your static key can be secured by whitelisting its usage for particular IPs (in case of cloud app usage) OR a set of domains (in case of a web app)
    - Your static key obtained from your Console is to be passed as a query parameter: `access_token`.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Direction Plugin. [See Sample Codes here](https://about.mappls.com/api/web-sdk/vector-plugin-example/Direction/mappls-event-alongtheroute-direction-plugin)

## Authentication Object - `access_token` mandatory query parameter.

-  `access_token`: "hklmgbwzrxncdyavtsuojqpiefrbhqplnm".


## Implementation


### Script URL

```js
<script src="https://sdk.mappls.com/map/sdk/plugins?access_token=<Static Key>&v=3.0&libraries=routesummary"></script>
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
      <script src="https://sdk.mappls.com/map/sdk/plugins?access_token=<Static Key>&v=3.0&libraries=routesummary"></script>
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

[<img src="https://about.mappls.com/images/mappls-logo.svg" height="40"/> </p>](https://about.mappls.com/api/)
Email us at [apisupport@mappls.com](mailto:apisupport@mappls.com)


![](https://about.mappls.com/api/img/icons/support.png)
[Support](https://about.mappls.com/api/index.php#f_cont)
Need support? contact us!

<br></br>

[<p align="center"> <img src="https://about.mappls.com/api/img/icons/stack-overflow.png"/> ](https://stackoverflow.com/questions/tagged/mapmyindia-api)[![](https://about.mappls.com/api/img/icons/blog.png)](http://about.mappls.com/blog/)[![](https://about.mappls.com/api/img/icons/gethub.png)](https://github.com/MapmyIndia)[<img src="https://mmi-api-team.s3.ap-south-1.amazonaws.com/API-Team/npm-logo.one-third%5B1%5D.png" height="40"/> </p>](https://www.npmjs.com/org/mapmyindia)

[<p align="center"> <img src="https://about.mappls.com/june-newsletter/icon4.png"/> ](https://www.facebook.com/MapmyIndia)[![](https://about.mappls.com/june-newsletter/icon2.png)](https://twitter.com/MapmyIndia)[![](https://about.mappls.com/newsletter/2017/aug/llinkedin.png)](https://www.linkedin.com/company/mapmyindia)[![](https://about.mappls.com/june-newsletter/icon3.png)](https://www.youtube.com/user/MapmyIndia/)

<div align="center">@ Copyright 2020 CE Info Systems Pvt. Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://about.mappls.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://about.mappls.com/about/privacy-policy">Privacy Policy</a> | <a href="https://about.mappls.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://about.mappls.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://about.mappls.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>

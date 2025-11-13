[<img src="https://about.mappls.com/images/mappls-b-logo.svg" height="60"/> </p>](https://about.mappls.com/api)


# Mappls Tracking Plugin 

**Easy To Integrate Routing APIs & Map SDKs For Web Applications**

## Getting Access

Before using the API in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://auth.mappls.com/console/), within your app - be it for Mobile OR Web or Cloud integration.

1. Copy and paste the key from your `credentials` section from your API [keys](https://auth.mappls.com/console/) into the `access_token` query parameter.
    - Your static key can be secured by whitelisting its usage for particular IPs (in case of cloud app usage) OR a set of domains (in case of a web app)
    - Your static key obtained from your Console is to be passed as a query parameter: `access_token`.
2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs.

## Authentication Object - `access_token` mandatory query parameter.

-  `access_token`: "hklmgbwzrxncdyavtsuojqpiefrbhqplnm".

## Document Version History

| Version | Last Updated | Team | Author |Remarks |
| ---- | ---- | ---- | ---- | ---- |
| 1.0 | 07 Aug 2025 | SDK Product Team | Prabhjot Kaur ([PK](https://github.com/prabhjot729)) | OAuth 2 |

## Introduction

This plugin, offered by Mappls plugins for Web, allows one to track the path traveled.

Features:

 1. Uses Mappls map 
 2. Search for the destination place using Mappls API 
 3. Route from source (current position) to destination. 
 4. Custom Map controls and animation 
 5. Live tracking user position and traveled coordinates


This feature is also available inbuilt with Mappls Direction Plugin. For details, please contact apisupport@mapmyindia.com.

## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://auth.mappls.com/console), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://auth.mappls.com/console) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using [Mappls Portal](https://auth.mappls.com/console)
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Direction Plugin. [See Sample Codes here](https://about.mappls.com/api/web-sdk/vector-plugin-auth2/Tracking/mappls-tracking-plugin)

## Implementation


### Script URL

```js
<script src="https://sdk.mappls.com/map/sdk/plugins?access_token=<Static Key>&v=3.0&libraries=direction"></script>
```

## Method

`direction_obj.tracking()`

## Properties

### Mandatory Parameters

  - `map(object)`: vector map or raster map object from respective Mappls Map SDKs.
- `location` : current location . For eg -  28.63124010064198,77.46734619140625

### Optional Parameters

- `label` : to label the current position.
- `icon` : to show a custom marker. Supports PNG format as of now.
- `heading` : To control the rotation of the marker as per the route direction.For example if you are using a car icon, it would rotate as per the route direction otherwise it would move straight . Default is true.
- `reRoute` : To refresh the route as per the current location. This means the route will change as per the current location. If kept false the same route will be displayed. Default is true.
- `fitbounds` : Allowing this would fit the map in the view bound.Default is true.
- `animationSpeed` : Minimum breakage between the two received locations. For example `animationSpeed` : 5 means if the location received is 100 meters apart the animation would appear at every 5 meters. This parameter would decide the smoothness of the animation appearing on the screen.


 
## Example


 ```js
mappls.direction({
            direction.tracking({
                            location: 28.63124010064198,77.46734619140625,
                            label:'current location',
                            icon:"../img/mkr_start.png",
                            heading: false,
                            reRoute: true, 
                            fitBounds:false,
                            animationSpeed:5,
                            
        },
        function(data){
            console.log(data);
        });
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

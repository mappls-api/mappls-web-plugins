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

## Introduction

This advanced tracking plugin, offered by Mappls plugins for Web, allows one to track the path traveled with **smooth animation** along the route. The smooth animation by plugin directly depend upon the frequency of the provided information on the current location, time, and speed of the vehicle being tracked to the plugin. _More the Merrier!_


## Getting Access

Before using the Plugin in the your solution, please ensure that the related access is enabled in the [Mappls Console](https://apis.mappls.com/console/), in the same project you set up for the Maps SDK.

1. Copy and paste the generated `access token` from your API [keys](https://apis.mappls.com/console/) available in the dashboard in the sample code for interactive map development.
    - This APIs follow OAuth2 based security.
    - `Access Token` can be generated using Token Generation API.
    - To know more on how to create your access tokens, please use our authorization API URL. More details available [here](https://about.mappls.com/api/advanced-maps/doc/authentication-api.php)
    - The `access token` is a valid by default for 24 hours from the time of generation. This can be configured by you in the API console.
2. The sample codes are provided on our domain to help you understand the very basic functionality of Mappls Direction Plugin. [See Sample Codes here](https://about.mappls.com/api/web-sdk/vector-plugin-example/Direction/mappls-tracking-direction-plugin)

## Implementation


### Script URL

```js
<script src="https://apis.mapmyindia.com/advancedmaps/api/{access_token}/map_sdk_plugins?v=3.0&libraries=tracking"></script>
```

## Method

`mappls.tracking()`

## Properties

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
                        height: 40 
                    }, Supports PNG format as of now.
- `end_icon` : { url: 'location.png',
                 width: 40, 
                 height: 40 
                    },Supports PNG format as of now.
- `reRoute` : To refresh the route as per the current location. This means the route will change as per the current location. If kept false the same route will be displayed. Default is true.
- `heading` : To control the rotation of the marker as per the route direction.For example if you are using a car icon, it would rotate as per the route direction otherwise it would move straight . Default is true.
- `Buffer` :50,  The distance defined for call reroute for the ptovided current location. 
- `fitbounds` : Allowing this would fit the map in the view bound.Default is true.
- `mapCenter` :true, keeps the current on the center of the map.
- `fitboundsOptions`:{padding:80}, // optional


 
## Example


 ```js
mappls.tracking(tracking_option, function (data) { 
            data.trackingCall({ // when user location change then reCall ( trackingCall() )
            location: user,
            Heading:true, 
            Buffer:50,
            fitBounds:true,
            mapCenter:true, 
            fitboundsOptions:{padding:80}
            
}

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

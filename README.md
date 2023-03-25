# Google Analytics for AMP
AMP Analytics Config for Tracking AMP Pages using Google Analytics 4. This repository let you add a configuration file to your AMP setup in order to track your visits and users' interactions on Google Analytics 4.

## DISCLAIMER
This isn't sponsored or supported in any way by Google, at the same time I don't know or there's any news about Google or AMP team to start giving official support to GA4 ( that's the reason for this project )

## SERVICE STATUS
Because of the last outage of the CDN on Match 23-24th. We are currently monitoring the availability from NA, AU, EU and ASIA. 

[![Better Uptime Badge](https://betteruptime.com/status-badges/v1/monitor/nz4k.svg)](https://betteruptime.com/?utm_source=status_badge)

Status Page: https://status.analytics-debugger.com

## BLOG POST 

Full configuration and information on:
https://www.thyngster.com/how-to-track-amp-pages-with-google-analytics-4

## SUPPORT / DONATIONS

I'm hosting a copy of the configuration file on my own CDN for those who are not easily able to host it themselves, which actually gets (as of 25th Mar 2023)

- 1.68B hits
- 4.79TB Transfer BW
- 548.92M Unique Visitors

per month.

 
I'd love to go into a higher tier on the CDN to improve the setup and have a more reliable service. So if my work helped you in fixing that tracking gap for GA4 and you would like to help on supporting the CDN costs show some appreciation by buying me some coffees I can keep working on this project and giving a free CDN service.
    
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/Q5Q225ZVD)

  
## Setup
Just add the following code to your AMP Pages:


```javascript
<amp-analytics  type="googleanalytics"  config="https://amp.analytics-debugger.com/ga4.json"  data-credentials="include">
<script  type="application/json">
{
  "vars": {
    "GA4_MEASUREMENT_ID": "G-THYNGSTER",
    "GA4_ENDPOINT_HOSTNAME": "www.google-analytics.com",
    "GOOGLE_CONSENT_ENABLED": false,
    "WEBVITALS_TRACKING": false,
    "PERFORMANCE_TIMING_TRACKING": false,
    "DEFAULT_PAGEVIEW_ENABLED": true,
    "SEND_DOUBLECLICK_BEACON": false,
    "ENABLE_REGIONAL_DATA_COLLECTION": true
  }
}
</script>
</amp-analytics>

```
 

|Feature Name|Description|
|--|--|
|GA4_MEASUREMENT_ID|Your `Measurement ID`, _**G-XXXXXXXX**_|
|GA4_ENDPOINT_HOSTNAME|Override the default endpoint domain. In case you want to send the hits to your own server or a `Server Side GTM` Instance.|
|GOOGLE_CONSENT_ENABLED|a &gcs parameter will be added to the payloads with the current Consent Status|
|WEBVITALS_TRACKING|If you enable this a `webvitals` event will fire 5 seconds after the page is visible|
|PERFORMANCE_TIMING_TRACKING|Whatever you want to push a `performance_timing` event including the current page load performance timings|
|DEFAULT_PAGEVIEW_ENABLED|If enabled a `page_view` event will fire on the page load|
|SEND_DOUBLECLICK_BEACON|Send a DC Hit|
|DISABLE_REGIONAL_DATA_COLLECTION|By default the data will be sent to the regional endpoint if the current user timezone name contains `Europe`)|  

## Suported Features

-  **Page Views**
-  **Event Tracking**
-  **User Properties**  _(number and string)_
-  **Event Parameters**  _(number and string)_
-  **Sessions Tracking**
-  **Session Engagements** (`&seg`)
-  **Sessions Count** (`&sct`)
-  **First Visits Tracking** (`&_fv`)
-  **Session Starts Tracking** (`&_ss`)
-  **AMP Cross-Domain**
-  **Engagement Time Tracking** (`&_et`)
-  **Screen Resolution**
-  **User's Browser Language**
-  **Document Title**
-  **Document URL**
-  **Document Referrer**
-  **Unique Pageview Id** (**`&_p`**)
-  **Debug Mode Switch** (**`&_dbg=1`**)
-  **Regional Data Collection* (**`region1.analytics-debugger.com`**)  

## In-Build Events

-  **Web Vitals**
-  **Performance Timing** 

## Enable Debug Mode
Add a ?_dbg=1 parameter to the current url to allow hits to show on GA4's DebugView

## How to add Event Parameters
Check Post Link on Top

## How to add User Properties
Check Post Link on Top  

## How to track Custom Events
Check Post Link on Top 

## How to track video Interactions
Check Post Link on Top 

## How to track Scrolling
Check Post Link on Top  

## How to track elements visibility
Check Post Link on Top  

## How to track events using timers
Check Post Link on Top

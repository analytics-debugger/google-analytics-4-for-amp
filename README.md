
# Google Analytics for AMP

AMP Analytics Config for Tracking AMP Pages using Google Analytics 4. This repository let you add a configuration file to your AMP setup in order to trackl 

Full configuration and information on:
https://www.thyngster.com/how-to-track-amp-pages-with-google-analytics-4

If this has been useful for your business or work, show some appreciation :) 
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/Q5Q225ZVD)

## Setup
Just add the following code to your AMP Pages:

<amp-analytics type="googleanalytics" config="https://amp.analytics-debugger.com/ga4.json" data-credentials="include">
<script type="application/json">
{
    "vars": {
                "GA4_MEASUREMENT_ID": "G-THYNGSTER",
                "GA4_ENDPOINT_HOSTNAME": "www.google-analytics.com",
                "DEFAULT_PAGEVIEW_ENABLED": true,    
                "GOOGLE_CONSENT_ENABLED": false,
                "WEBVITALS_TRACKING": false,
                "PERFORMANCE_TIMING_TRACKING": false
    }
}
</script>
</amp-analytics>

|Feature Name|Description|
|--|--|
|GA4_MEASUREMENT_ID|Your `Measurement ID`, _**G-XXXXXXXX**_|
|GA4_ENDPOINT_HOSTNAME|Override the default endpoint domain. In case you want to send the hits to your own server or a `Server Side GTM` Instance.|
|GOOGLE_CONSENT_ENABLED|a &gcs parameter will be added to the payloads with the current Consent Status|
|WEBVITALS_TRACKING|If you enable this a `webvitals` event will fire 5 seconds after the page is visible|
|PERFORMANCE_TIMING_TRACKING|Whatever you want to push a `performance_timing` event including the current page load performance timings|
|DEFAULT_PAGEVIEW_ENABLED|If enabled a `page_view` event will fire on the page load|
|SEND_DOUBLECLICK_BEACON|Send a DC Hit|



## Suported Features
-   **Page Views**
-   **Event Tracking**
 -  **User Properties** _(number and string)_
-   **Event Parameters** _(number and string)_
-   **Sessions Tracking**
-   **Session Engagements** (`&seg`)
-   **Sessions Count** (`&sct`)
-   **First Visits Tracking** (`&_fv`)
-   **Session Starts Tracking** (`&_ss`)
-   **AMP Cross-Domain**
-   **Engagement Time Tracking** (`&_et`)
-   **Screen Resolution**
-   **User's Browser Language**
-   **Document Title**
-   **Document URL**
-   **Document Referrer**
-   **Unique Pageview Id** (**`&_p`**)


## In-Build Events
-   **Web Vitals**
-   **Performance Timing**


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

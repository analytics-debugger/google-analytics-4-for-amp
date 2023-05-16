## SUPPORT / DONATIONS

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/Q5Q225ZVD) or Sponsor me here at GIthub > [SPONSOR ME AT GITHUB](https://github.com/sponsors/thyngster "Thank YOU!")

It's being a time consuming task to keep investigating this while Google decides to offer some proper official support,
more even when I don't even run any AMP sites myself.

I'm also hosting a copy of the configuration file on my own CDN for those who are not easily able to host it themselves, which actually gets (as of 02th Mayr 2023)

- 2.23B hits
- 6.81 TB Transfer BW
- 712.09M Unique Visitors per month.
- 30K DNS Queries/min
- 251.3K Security Threats

I'd love to go into a higher tier on the CDN to improve the setup and have a more reliable service.

Since I'me giving my time for free would be great getting back some support from people/companies using this solution to being able to track their AMP sites.

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

## Setup

Just add the following code to your AMP Pages: ( check the table below for a full list of optional parameters and their functionality )

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
    "DISABLE_REGIONAL_DATA_COLLECTION": false,
    "ENHANCED_MEASUREMENT_SCROLL": false,
  }
}
</script>
</amp-analytics>

```

| Feature Name                     | Description                                                                                                                   |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| GA4_MEASUREMENT_ID               | Your `Measurement ID`, _**G-XXXXXXXX**_                                                                             |
| GA4_ENDPOINT_HOSTNAME            | Override the default endpoint domain. In case you want to send the hits to your own server or a `Server Side GTM` Instance. |
| GOOGLE_CONSENT_ENABLED           | a &gcs parameter will be added to the payloads with the current Consent Status                                                |
| WEBVITALS_TRACKING               | If you enable this a `webvitals` event will fire 5 seconds after the page is visible                                        |
| PERFORMANCE_TIMING_TRACKING      | Whatever you want to push a `performance_timing` event including the current page load performance timings                  |
| DEFAULT_PAGEVIEW_ENABLED         | If enabled a `page_view` event will fire on the page load                                                                   |
| SEND_DOUBLECLICK_BEACON          | Send a DC Hit                                                                                                                 |
| DISABLE_REGIONAL_DATA_COLLECTION | By default the data will be sent to the regional endpoint if the current user timezone name contains `Europe`)              |
| OVERRIDE_PAGE_LOCATION           | Will override the default page url passed by AMP                                                                              |
| OVERRIDE_PAGE_TITLE              | Will override the default page title passed by AMP                                                                            |
| USER_ID                          | If set the &uid will be passed back to hits.                                                                                  |
| ENHANCED_MEASUREMENT_SCROLL      | Will send an event to GA4, at 90%, same way as GTAG Enhanced Measurment does.                                                 |

## Suported Features

- **Page Views**
- **Event Tracking**
- **User Properties**  _(number and string)_
- **Event Parameters**  _(number and string)_
- **Sessions Tracking**
- **Session Engagements** (`&seg`)
- **Sessions Count** (`&sct`)
- **First Visits Tracking** (`&_fv`)
- **Session Starts Tracking** (`&_ss`)
- **AMP Cross-Domain**
- **Engagement Time Tracking** (`&_et`)
- **Screen Resolution**
- **User's Browser Language**
- **Document Title**
- **Document URL**
- **Document Referrer**
- **Unique Pageview Id** (**`&_p`**)
- **Debug Mode Switch** (**`&_dbg=1`**)
- ****Regional Data Collection* **(`region1.google-analytics-com`**)
- **Document Referrer**
- **Cross Domain Tracking**
- **User Agent Client Hints**
- **Page Title, Page URL override**
- **User ID**
- **Conversions**
- **Override Attribution Data, including: Source, Medium, Campaign, Term, Content, Id parameters.**
- **Ignore Referral Support**
- **Content Grouping**

## In-Build Events

- **Web Vitals**
- **Performance Timing**
- **Scroll Tracking**

## Cross-Domain Tracking

To utilize the newly implemented core file session cross-linking feature, you can simply add a linker section to your `<script>`
and specify the domains list along with your measurement IDs. Just after the vars: {} key.

However, please note that AMP does not permit the definition of dynamic keys. Therefore, you must manually add the measurement ID and include multiple "ids"
lines for each unique measurement ID you have.

```javascript
"linkers": {
    "enabled": true,
    "destinationDomains": ["*.externaldomain.io"],
    "_gl": {
        "ids": {
            "_ga_THYNGSTER": "${ga4SessionCookie}"
        },
        "proxyOnly": false
    }
}
```

It is important to note that if your measurement ID is "G-THYNGSTER", the "ids" key should be structured as "_ga_THYNGSTER".
After including these lines of code, when a user clicks on a crosslinked domain, the corresponding details will be transmitted to the destination domain.

| Data Key                     | Description                                                       |
| ---------------------------- | ----------------------------------------------------------------- |
| **Client ID**          | Current Client Id from _ga cookie                                 |
| **Session ID**         | Current Session ID to keep the session alive                      |
| **Session Count**      | Current Session Count so it get written on the destination cookie |
| **Session Engagement** | If session is currently engaged                                   |

This ensures that the current user and session remain unchanged when the users navigate from your AMP to NON-AMP pages.

## Custom Page URL, Page TItle

Some times you have want to send a custom URL or Page Title you may use the following variables to override the default values.

| Variable Name                    | Example Value                     |
| -------------------------------- | --------------------------------- |
| **OVERRIDE_PAGE_LOCATION** | https://www.domain.com/custom-url |
| **OVERRIDE_PAGE_LOCATION** | My Custom Title                   |

## Overriding Campaign Data

If you want to override the current campaign data with any of your events , just use the following parameters within the events:

```
"extraUrlParams": {
     "campaign_source": "google", // Matches as having an utm_source querystring parameter
     "campaign_medium": "cpc", // Matches as having an utm_medium querystring parameter
     "campaign_name": "mycampaign", // Matches as having an utm_name querystring parameter
     "campaign_content": "my content", // Matches as having an utm_content querystring parameter
     "campaign_term": "campaign term" // Matches as having an utm_term querystring parameter
     "campaign_id": "23" // Matches as having an utm_id querystring parameter
}
```

## Set a Conversion

You can not set your events as conversions, just add the `"is_conversion": "1"` extraUrl Parameter to the current event you want to be counted as a conversion as follows:

```
"extraUrlParams": {
    "is_conversion": "1"
}
```

## Ignore Referral 

You may want Google Analytics 4 to ignore some referral. You may build the logic yourself and the set this variable to make GA4 ignore the referral info at processing time.

```
"extraUrlParams": {
    "ignore_referral": "1"
}
```

## Content Grouping

You can set your content grouping for your hits in an easy way, just add the following extra parameter to your events definition:

```
"extraUrlParams": {
    "content_group": "men"
}
```

## Enable Debug Mode

Add a ?_dbg=1 parameter to the current url to allow hits to show on GA4's DebugView

## AMP Hostname Reporting

At some point you may want to have the current real AMP hostname to be recorded. To filter out the traffic from the AMP CDN and your domain. An event paratemer named "***amp_hostname***" is now passed back to the hits, so you can use on your reports. Remember you'll need to register this parameter as a dimensio within GA4 admin.

## Setting the User ID

The userId for the current user can bet using the following var:

| Variable Name     | Example Value                       |
| ----------------- | ----------------------------------- |
| **USER_ID** | 123e4567-e89b-12d3-a456-42661417400 |

## Self-Hosting the JSON

When using a third-party integration or not utilizing the provided CDN, it is important to note that the tracking feature may not be updated. Therefore, it is essential to update the core file.

In the event that you choose to host the file yourself, it is necessary to take into account the CORS headers. While accessing the version from your own domain should not pose an issue, it is important to keep in mind that most users will load at least the first page from Google/AMP CDN domains. Failure to set the headers appropriately may result in the file being blocked.

I'm provinding some example about how to do this in some platforms/languages

### PHP

```php
header("Access-Control-Allow-Origin: $_SERVER['HTTP_ORIGIN']");
header("Access-Control-Allow-Credentials: true");
```

### NGINX

```nginx
location = /ga4.json {
    add_header Access-Control-Allow-Origin $http_origin;
    add_header Access-Control-Allow-Credentials true;
#    proxy_pass or try_files or whatever might need to go here
}
```

via @**[fanatixgithub](https://github.com/fanatixgithub)**

### Apache / .htaccess

```apache
  Header set Access-Control-Allow-Origin "https://cdn.ampproject.org"
  Header set Access-Control-Allow-Origin "true"
```

* *Not sure how to grab the Http Origin from Apache*

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

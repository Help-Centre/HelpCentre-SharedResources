# See Snowplow Tracker Setup documentation

- https://docs.snowplowanalytics.com/docs/collecting-data/collecting-from-own-applications/javascript-trackers/browser-tracker/browser-tracker-v3-reference/tracker-setup/

# Install package @snowplow/browser-tracker with preferred package manager

- https://docs.snowplowanalytics.com/docs/collecting-data/collecting-from-own-applications/javascript-trackers/browser-tracker/browser-tracker-v3-reference/tracker-setup/installing-the-tracker-from-npm/

# Initialize Snowplow tracker with imports from @snowplow/browser-tracker

```typescript
import {
    enableActivityTracking,
    newTracker,
} from "@snowplow/browser-tracker";

...
const spBrowserTracker = newTracker(
        "{{trackerNameHere}}",
        {{collector_url}},
        {
            appId: "{{appIdHere}}",
            plugins: [{{usedPluginsWillBeAddedHere}}],
        }
    );
spBrowserTracker.setUserId({{userIdHere}});
enableActivityTracking({
    minimumVisitLength: 30,
    heartbeatDelay: 20,
});
trackPageView({
    title: "{{titleHere}}",
    context: [{
        {{desiredContextSchema}}
    }],
});
...
```

# How to track custom struct events

```typescript
import {
    trackStructEvent,
    trackSelfDescribingEvent
} from "@snowplow/browser-tracker";
...
trackStructEvent({
  ...eventData,
  context: [
    {
      schema: "iglu:com.visma-helpcentre/context_helpcentre/jsonschema/1-0-0",
      data: context_helpcentre,
    },
  ],
});
...
trackSelfDescribingEvent({{eventHere}})
```

# Using Plugins

- https://docs.snowplowanalytics.com/docs/collecting-data/collecting-from-own-applications/javascript-trackers/browser-tracker/browser-tracker-v3-reference/tracker-setup/installing-the-tracker-from-npm/#using-plugins
- https://github.com/snowplow/snowplow-javascript-tracker/tree/master/plugins

# Plugins used in Snowplow.js script (https://drive.google.com/file/d/1H62rgXSkBisYekG6thfSJ7gKz42012Fy/view)

- browser-plugin-geolocation
- browser-plugin-performance-timing
- browser-plugin-link-click-tracking
- browser-plugin-form-tracking

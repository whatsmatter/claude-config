# GA4 Standard Metrics and Dimensions Reference

Commonly used metrics and dimensions in Google Analytics 4 (GA4).

## Standard Dimensions

### Traffic & Acquisition
- `sessionSourceMedium` (e.g., `google / cpc`, `direct / (none)`)
- `sessionSource`
- `sessionMedium`
- `sessionDefaultChannelGroup` (e.g., `Organic Search`, `Direct`, `Paid Search`)
- `sessionCampaignName`
- `pagePath` / `pageLocation` / `pageTitle`
- `landingPagePlusQueryString`

### User Demographics & Geo
- `country`
- `city`
- `deviceCategory` (`desktop`, `mobile`, `tablet`)
- `operatingSystem`
- `browser`

### Event & Behavior
- `eventName` (e.g., `page_view`, `session_start`, `click`, `purchase`)
- `date` (format: YYYYMMDD)
- `yearWeek`
- `yearMonth`

## Standard Metrics

### Users & Sessions
- `activeUsers` — Number of distinct users who had an engaged session or logged an event.
- `totalUsers` — Total number of unique users.
- `newUsers` — Number of users who interacted with your site/app for the first time.
- `sessions` — Total number of sessions.
- `engagedSessions` — Number of sessions that lasted 10+ seconds, had 2+ page views, or 1+ conversion events.
- `engagementRate` — Percentage of engaged sessions (`engagedSessions / sessions`).
- `bounceRate` — Percentage of non-engaged sessions (`1 - engagementRate`).
- `averageSessionDuration` — Average length of a session in seconds.

### Views & Activity
- `views` — Total number of app screens or web pages viewed.
- `screenPageViewsPerSession` — Average views per session.
- `eventCount` — Total number of events triggered.

### Conversions & E-commerce
- `keyEvents` (formerly `conversions`) — Count of key events/conversions.
- `sessionKeyEventRate` — Key event rate per session.
- `ecommercePurchases` — Total number of purchase events.
- `totalRevenue` — Total revenue from purchases, in-app purchases, and subscriptions.
- `purchaseRevenue` — Total revenue from purchase events only.

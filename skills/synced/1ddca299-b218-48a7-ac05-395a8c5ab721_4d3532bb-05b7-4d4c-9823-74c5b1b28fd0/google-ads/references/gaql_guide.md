# Google Ads Query Language (GAQL) Guide

Use `gads_run_gaql_query` when you need custom resource queries or settings not exposed in `gads_get_report`.

## General Rules
1. **Field Naming in Output**: Dots in GAQL field names are converted to underscores in output. E.g., `campaign.name` -> `campaign_name`, `metrics.cost_micros` -> `metrics_cost_micros`.
2. **Micros Conversion**: Any monetary metric ending in `_micros` or representing CPC/CPM is returned in micro-units (1/1,000,000).
   - Example: `50,000,000` micros = `$50.00`.
   - Always divide by 1,000,000 when presenting to users or passing values to write operations like `gads_update_campaign_budget`.
3. **Date Filters**: Use standard YYYY-MM-DD or GAQL relative date keywords (`LAST_30_DAYS`, `DURING LAST_7_DAYS`).

## Common Queries

### Campaign Performance
```sql
SELECT
  campaign.id,
  campaign.name,
  campaign.status,
  campaign_budget.amount_micros,
  metrics.impressions,
  metrics.clicks,
  metrics.cost_micros,
  metrics.conversions,
  metrics.conversions_value
FROM campaign
WHERE segments.date DURING LAST_30_DAYS
  AND campaign.status != 'REMOVED'
ORDER BY metrics.cost_micros DESC
```

### Search Terms Query
```sql
SELECT
  search_term_view.search_term,
  campaign.name,
  ad_group.name,
  metrics.clicks,
  metrics.impressions,
  metrics.cost_micros,
  metrics.conversions
FROM search_term_view
WHERE segments.date DURING LAST_30_DAYS
ORDER BY metrics.clicks DESC
```

### Bidding Strategy & Budget Inspection
```sql
SELECT
  campaign.id,
  campaign.name,
  campaign.bidding_strategy_type,
  campaign.target_cpa.target_cpa_micros,
  campaign.target_roas.target_roas,
  campaign_budget.amount_micros
FROM campaign
WHERE campaign.status = 'ENABLED'
```

### Disapproved Ads Inspection
```sql
SELECT
  ad_group_ad.ad.id,
  ad_group_ad.ad.name,
  campaign.name,
  ad_group_ad.policy_summary.approval_status,
  ad_group_ad.policy_summary.policy_topic_entries
FROM ad_group_ad
WHERE ad_group_ad.policy_summary.approval_status = 'DISAPPROVED'
```

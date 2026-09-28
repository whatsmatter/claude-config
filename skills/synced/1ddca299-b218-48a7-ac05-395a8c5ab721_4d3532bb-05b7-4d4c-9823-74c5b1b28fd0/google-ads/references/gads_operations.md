# Google Ads Operations Reference

This document outlines key Google Ads operations in Markifact, grouped by task domain.

## 1. Prerequisites & Account Discovery
- **`gads_select_accounts`**: Look up and select Google Ads accounts (`selection_mode`: 'all' or 'filter').
- **`gads_list_report_fields`**: Search metrics and dimensions before querying `gads_get_report`.

## 2. Reporting & Analytics
- **`gads_get_report`**: Query campaign, ad group, keyword, or ad level performance data.
  - Common metrics: `clicks`, `impressions`, `cost`, `conversions`, `conversionsValue`, `cpc`, `cpm`, `conversionRate`, `roas`.
  - Common dimensions: `date`, `month`, `campaignName`, `adGroupName`, `adName`, `keywordText`.
- **`gads_run_gaql_query`**: Execute raw Google Ads Query Language (GAQL) queries for custom resources, settings, or unmapped reporting metrics.
  - *Note on Micros:* Cost and monetary fields in GAQL output (e.g., `cost_micros`) are in micro-units (1/1,000,000). Divide by 1,000,000 for standard currency values.
- **`gads_search_gaql_resources`**: Discovery helper for valid GAQL fields, resources, and segments.
- **`gads_ads_transparency`**: Retrieve ad history from Google Ads Transparency Center by domain or advertiser ID.
- **`gads_get_account_history`**: Retrieve historical activity/changes in Google Ads accounts.

## 3. Campaign & Ad Group Setup
- **`gads_create_campaign`**: Create empty Search, Display, Performance Max, Demand Gen, or Shopping campaigns.
- **`gads_create_ad_group`**: Create ad groups inside an existing campaign.
- **`gads_update_campaign_status`**: Enable, pause, or remove campaigns (supports bulk actions).
- **`gads_update_ad_group_status`**: Enable, pause, or remove ad groups.
- **`gads_rename_campaign`**: Rename existing campaigns.
- **`gads_rename_ad_group`**: Rename existing ad groups.

## 4. Budgets & Bidding Strategy
- **`gads_update_campaign_budget`**: Update daily budget amount.
  - *Crucial Rule:* Always pass `campaign_budget` as actual dollar value in account currency (e.g., 50 for $50/day). NEVER pass micros.
- **`gads_update_campaign_bidding_strategy`**: Set campaign strategy (Manual CPC, Maximize Conversions, Maximize Conversion Value, Target CPA, Target ROAS, etc.).
- **`gads_update_ad_group_bid`**: Update CPC bid, Target CPA, or Target ROAS at the ad group level.
- **`gads_manage_portfolio_bidding_strategy`**: Create or update shared portfolio bidding strategies with bid floors/ceilings.
- **`gads_assign_portfolio_bidding_strategy`**: Link portfolio bidding strategies to campaigns.

## 5. Targeting & Scheduling
- **`gads_update_campaign_location_language`**: Update positive/negative geo locations, language targeting, and geo target types.
- **`gads_search_geo_targets`**: Search geographic location IDs by name (cities, regions, countries).
- **`gads_update_campaign_ad_schedule`**: Configure day and hour targeting along with bid modifiers.

## 6. Ad Creation & Editing
- **`gads_create_responsive_search_ad`**: Create Responsive Search Ads (RSA) with headlines, descriptions, final URL, and paths.
- **`gads_edit_responsive_search_ad`**: Edit headlines, descriptions, or URLs on existing RSAs.
- **`gads_create_responsive_display_ad`**: Create Responsive Display Ads (RDA) with image URLs, text assets, and call to action.
- **`gads_create_pmax_asset_group`**: Build PMax asset groups with headlines, descriptions, images, logos, and videos.
- **`gads_create_demand_gen_single_image_ad`**: Single image Demand Gen ads.
- **`gads_create_demand_gen_video_ad`**: Video Demand Gen ads.
- **`gads_create_demand_gen_carousel_ad`**: Multi-card carousel Demand Gen ads.
- **`gads_create_app_ad`**: App install/engagement ads.
- **`gads_update_ad_status`**: Enable, pause, or remove individual ads.

## 7. Keywords, Negative Lists & Asset Extensions
- **`gads_add_keyword_to_ad_group`**: Add keywords with match types (`EXACT`, `PHRASE`, `BROAD`).
- **`gads_update_keyword_status`**: Enable, pause, or remove keywords.
- **`gads_keyword_planner`**: Get keyword ideas and historical search volumes.
- **`gads_create_negative_keyword_list`**: Create negative keyword lists.
- **`gads_add_keywords_to_negative_list`**: Add keywords to existing negative lists.
- **`gads_attach_negative_list_to_campaigns`**: Apply negative lists to campaigns.
- **`gads_create_placement_exclusion_list`**: Create placement exclusion lists.
- **`gads_add_placements_to_exclusion_list`**: Add placements to exclusion lists.
- **`gads_create_sitelinks`**, **`gads_create_callouts`**, **`gads_create_structured_snippets`**, **`gads_create_promotion_asset`**, **`gads_create_image_asset`**, **`gads_create_headline_asset`**, **`gads_create_description_asset`**: Extensions and asset management.
- **`gads_update_asset_status`**: Enable, pause, or remove asset links.
- **`gads_manage_ip_exclusions`**: Exclude IP addresses at account level.
- **`gads_create_label`**, **`gads_manage_label_assignment`**: Account/campaign tagging with labels.

## 8. Fallback Mutations
- **`gads_mutate`**: Send custom Google Ads API mutations when no dedicated tool exists.

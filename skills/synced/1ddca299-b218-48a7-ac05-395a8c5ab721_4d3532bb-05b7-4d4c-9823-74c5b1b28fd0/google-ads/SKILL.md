---
name: google-ads
description: "Comprehensive guide and workflow for managing Google Ads accounts. Covers campaign setup (Search, Display, Performance Max, Demand Gen, Shopping), ad creation (RSA, RDA), keyword research & management, bid/budget updates, negative keyword lists, ad extensions/assets, and performance reporting via gads_get_report and GAQL. Use for any Google Ads task: campaign setup, optimization, budget adjustments, or performance analytics."
---

# Google Ads Skill Guide

This skill provides systematic instructions for managing Google Ads campaigns, ads, keywords, budgets, asset extensions, and performance reporting within Markifact.

---

## Core Execution Pattern

When performing any Google Ads task, follow Markifact's standard operation pattern:
1. **Discover**: Locate required tools via `find_operations` if not already indexed.
2. **Inspect**: Always check input schemas using `get_operation_inputs` before invoking an operation for the first time.
3. **Execute**: Run operations via `run_operation`. Handle human approval if requested by the platform.

---

## 1. Prerequisites & Setup

Before running Google Ads reports or updates:
1. **Select Accounts**: Use `gads_select_accounts` to obtain account IDs/names.
2. **Field Discovery**: When constructing reporting queries, run `gads_list_report_fields` to verify metric and dimension names rather than guessing.

---

## 2. Reporting & Analytics Workflow

### Standard Reporting (`gads_get_report`)
- **Common Metrics**: `clicks`, `impressions`, `cost`, `conversions`, `conversionsValue`, `cpc`, `cpm`, `conversionRate`, `roas`.
- **Common Dimensions**: `date`, `month`, `campaignName`, `adGroupName`, `adName`, `keywordText`.
- **Date Ranges**: Use preset values (`LAST_7_DAYS`, `LAST_30_DAYS`, `LAST_MONTH`, `THIS_MONTH_TO_DATE`) or `FIXED` with start/end dates (`YYYY-MM-DD`).
- **Date Range Comparison**: Use `compare` in `date_range` for period-over-period analysis (e.g. `preset: 'previous_period'`).

### Advanced Queries & GAQL (`gads_run_gaql_query`)
- Use `gads_run_gaql_query` for fields, settings, or search terms not supported by `gads_get_report`.
- **Micros Conversion**: GAQL returns monetary metrics in micro-units (1/1,000,000 of currency unit). Divide micro amounts by 1,000,000 before displaying to users or using in write requests.
- Refer to `references/gaql_guide.md` for pre-built GAQL queries.

### Visualizing Performance & Generating Charts
- Export reporting data to CSV in `/workspace/files/file-<descriptor>.csv`.
- Use Python (`matplotlib` / `pandas`) in `shell` to create charts and save to `/workspace/files/file-chart.png`.
- Obtain safe file URLs with `get_file_url("file-chart.png")` and embed using Markdown `![chart](URL)`.

---

## 3. Campaign & Ad Group Management

### Creating Campaigns & Ad Groups
1. **Create Campaign**: Use `gads_create_campaign` specifying `campaign_type` (`SEARCH`, `DISPLAY`, `PERFORMANCE_MAX`, `DEMAND_GEN`, `SHOPPING`), initial daily budget, and targeting settings.
2. **Create Ad Group**: Use `gads_create_ad_group` attached to the campaign ID.
3. **PMax Asset Groups**: For Performance Max campaigns, add asset groups using `gads_create_pmax_asset_group`.

### Status & Naming Updates
- Enable/pause/remove campaigns: `gads_update_campaign_status`.
- Enable/pause/remove ad groups: `gads_update_ad_group_status`.
- Rename entities: `gads_rename_campaign`, `gads_rename_ad_group`.

---

## 4. Budgets & Bidding Optimization

### Budget Confirmation & Rules
- **CRITICAL**: Always confirm budget and bid adjustments with the user before executing.
- **Currency Format**: Express amounts as standard actual currency values (e.g., "$50/day" -> `50`). **NEVER** pass micros to `gads_update_campaign_budget`.
- **Batching**: Support bulk updates by passing arrays of campaign IDs and budgets when updating multiple campaigns.

### Bidding Strategy Updates
- Update campaign bidding strategies with `gads_update_campaign_bidding_strategy` (`MANUAL_CPC`, `MAXIMIZE_CONVERSIONS`, `MAXIMIZE_CONVERSION_VALUE`, `TARGET_CPA`, `TARGET_ROAS`).
- Set ad group level bids or targets with `gads_update_ad_group_bid`.
- For shared strategies across multiple campaigns, use `gads_manage_portfolio_bidding_strategy` and `gads_assign_portfolio_bidding_strategy`.

---

## 5. Ad Creation & Asset Management

### Responsive Search Ads (RSA)
- Use `gads_create_responsive_search_ad` with:
  - 3 to 15 headlines (`headlines` array).
  - 2 to 4 descriptions (`descriptions` array).
  - `final_url`, optional `path_1` and `path_2`.
- Edit existing RSAs with `gads_edit_responsive_search_ad`.

### Responsive Display & Demand Gen
- Use `gads_create_responsive_display_ad` for Display campaigns.
- Use `gads_create_demand_gen_single_image_ad`, `gads_create_demand_gen_video_ad`, or `gads_create_demand_gen_carousel_ad` for Demand Gen campaigns.

### Ad Extensions & Assets
- Sitelinks: `gads_create_sitelinks`.
- Callouts: `gads_create_callouts`.
- Structured Snippets: `gads_create_structured_snippets`.
- Promotions: `gads_create_promotion_asset`.
- Image & Text Assets: `gads_create_image_asset`, `gads_create_headline_asset`, `gads_create_description_asset`.

---

## 6. Keywords, Targeting & Exclusions

### Keyword Management
- Add keywords: `gads_add_keyword_to_ad_group` specifying match type (`EXACT`, `PHRASE`, `BROAD`).
- Research keywords: `gads_keyword_planner`.
- Update keyword status: `gads_update_keyword_status`.

### Negative Keyword & Placement Exclusions
- Create negative keyword lists: `gads_create_negative_keyword_list` -> add keywords via `gads_add_keywords_to_negative_list` -> attach to campaigns via `gads_attach_negative_list_to_campaigns`.
- Create placement exclusions: `gads_create_placement_exclusion_list` -> add placements via `gads_add_placements_to_exclusion_list`.

### Geo & Location Targeting
- Search geo targets by name with `gads_search_geo_targets`.
- Update location targeting and negative location exclusions with `gads_update_campaign_location_language`.

---

## 7. Safety & Human Approval Flow

1. If `run_operation` returns an indication that human approval is required:
2. Gather all pending write operations into a list.
3. Call `request_human_approval` with the full list of operations.
4. Upon receiving approval, re-run `run_operation` for each approved action.

---

## 8. Detailed Reference Index

For full operation lists and GAQL query examples, consult:
- Operations Guide: `references/gads_operations.md`
- GAQL Guide: `references/gaql_guide.md`

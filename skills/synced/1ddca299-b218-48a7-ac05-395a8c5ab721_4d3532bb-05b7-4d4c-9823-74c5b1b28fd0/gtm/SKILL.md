---
name: gtm
description: "Comprehensive guide and workflow for Google Tag Manager (GTM) management. Covers searching/lookup of GTM accounts and containers, linking GA4 measurement IDs and destination tags, inspecting tags and triggers, updating tag configurations, creating containers, and publishing container versions. Use for any GTM task: container lookup, tag management, GA4 tag linking, or tag auditing."
---

# Google Tag Manager (GTM) Skill Guide

This skill provides systematic instructions for auditing, managing, and updating Google Tag Manager (GTM) accounts, containers, tags, and Google tag destinations within Markifact.

---

## Core Execution Pattern

When performing any GTM task, follow Markifact's standard operation pattern:
1. **Discover**: Confirm required operations via `find_operations` if not already indexed.
2. **Inspect**: Always check input schemas using `get_operation_inputs` before invoking an operation for the first time.
3. **Execute**: Run operations via `run_operation` (`gtm_list_accounts`, `gtm_list_containers`, `gtm_list_tags`, `gtm_create_tag`, etc.).

---

## 1. Container & Account Discovery Workflow

### Finding Accounts and Containers
1. **List Accounts**: Call `gtm_list_accounts` to obtain account IDs.
2. **List Containers**: Call `gtm_list_containers` with the `account` ID to retrieve containers and public IDs (`GTM-XXXXXX`).
3. **Lookup by Tag or Measurement ID**: If you only have a public tag ID (`GTM-XXXXXX`) or GA4 measurement ID (`G-XXXXXXXXXX`), use `gtm_lookup_container` with `tag_id` or `destination_id` to locate the owning container without needing the account ID first.

---

## 2. Linking Google Tag Destinations (GA4 & Google Ads)

### Linking Measurement IDs
- Use `gtm_list_destinations` to view existing linked Google tags.
- Use `gtm_link_destination` to attach a GA4 Measurement ID (`G-XXXXXXXXXX`) or Google Ads Conversion ID (`AW-XXXXXXXXX`) to a GTM container.

---

## 3. Tag & Workspace Operations

### Managing Tags
1. **List Tags**: Call `gtm_list_tags` specifying `account`, `container`, and `workspace` (default workspace is typically required).
2. **Inspect Tag Configuration**: Use `gtm_get_tag` to fetch full payload parameters, firing triggers, and blocking triggers.
3. **Create Tag**: Use `gtm_create_tag` with valid `tag_payload`.
4. **Update Tag**: Follow the get-edit-update flow: `gtm_get_tag` -> modify payload -> `gtm_update_tag`.
5. **Delete Tag**: Use `gtm_delete_tag`. Note that tag deletions take effect once a container version is created and published.

### Managing Google Tag Configurations (`gtag.js`)
- View `gtag.js` settings: `gtm_list_gtag_configs`.
- Manage settings payloads: `gtm_get_gtag_config`, `gtm_create_gtag_config`, `gtm_update_gtag_config`.

---

## 4. Operational Checklist & Reference

For a complete breakdown of GTM operation names and parameters, consult `references/gtm_operations.md`.

# Google Tag Manager (GTM) Operations Reference

List of operations available for Google Tag Manager management in Markifact.

## Accounts & Containers
- `gtm_list_accounts`: List GTM accounts accessible to the connected user.
- `gtm_get_account`: Fetch details of a single GTM account.
- `gtm_update_account`: Update account name or data sharing settings.
- `gtm_list_containers`: List containers in an account with public IDs (GTM-XXXXXX), usage context (`web`, `server`, `amp`, `ios`, `android`), and notes.
- `gtm_get_container`: Fetch a container's details and settings.
- `gtm_create_container`: Create a new container in an account.
- `gtm_update_container`: Update container name or notes.
- `gtm_lookup_container`: Find a container by public tag ID (`GTM-XXXXXX`) or linked destination ID (e.g. GA4 measurement ID `G-XXXXXXXXXX`).

## Destinations & Tags Link
- `gtm_list_destinations`: List linked Google tag destinations (e.g. GA4 measurement IDs).
- `gtm_link_destination`: Link a Google tag destination to a container.
- `gtm_move_tag_id`: Move a public tag ID out of a container into a newly created container.

## Tags & Tag Configurations
- `gtm_list_tags`: List tags in a workspace with type, parameters, firing/blocking triggers, and paused state.
- `gtm_get_tag`: Fetch full configuration of a single tag.
- `gtm_create_tag`: Create a new tag from payload.
- `gtm_update_tag`: Replace tag configuration payload.
- `gtm_delete_tag`: Delete a tag from a workspace.
- `gtm_revert_tag`: Revert tag workspace changes back to latest container version state.

## Google Tag Configurations (`gtag.js`)
- `gtm_list_gtag_configs`: List Google tag configs holding `gtag.js` settings.
- `gtm_get_gtag_config`: Fetch a single Google tag config.
- `gtm_create_gtag_config`: Create a Google tag config.
- `gtm_update_gtag_config`: Replace Google tag config payload.
- `gtm_delete_gtag_config`: Delete Google tag config.

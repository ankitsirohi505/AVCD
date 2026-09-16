# AVCD — Aerolink Cargo Directory

Public, read-only trade-account directory synced one-way from the Aerolink CDM (Salesforce).

Live: <https://ankitsirohi505.github.io/AVCD/>

## What it does
- Lists every trade account flagged public in the CDM
- Click a row to see the full record (all fields read-only)
- Polls every 60s (list) / 30s (detail) so field edits in Salesforce reflect here automatically

## How it works
- Static `index.html` on GitHub Pages
- Fetches JSON from a Salesforce Site public REST endpoint:
  - List: `GET /services/apexrest/accounts`
  - Detail: `GET /services/apexrest/accounts/{id}`
- Apex class `AccountLookupService` filters by `Is_Public_Offering__c = true`
- Guest User FLS and CORS for `https://ankitsirohi505.github.io` are pre-configured

## Sync demo
1. Open the directory in the browser
2. Edit any listed account in Salesforce (e.g. change tagline or description)
3. Within ~30s the site reflects the change and the "Last synced" chip updates

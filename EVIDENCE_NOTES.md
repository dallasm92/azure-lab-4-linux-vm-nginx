# Evidence Notes

The source material for this lab lives in `/home/dallas/SyncLab/Azure Lab 4/` and currently consists of raw screenshots from the Azure portal, SSH session, and browser validation flow.

## Why The Raw Screenshots Are Not In This Repo Yet

- Azure account banner details are visible in the portal screenshots.
- Public IP information is visible in parts of the evidence set.
- Some screenshots show intermediate experiments that would benefit from pruning before public release.

## Current Public-Safe Approach

- This repo uses text-first documentation derived from the private evidence set.
- The workflow, resource relationships, and validated outcome are documented without publishing the raw screenshots directly.

## Recommended Follow-Up

- Redact the Azure account banner consistently across all selected screenshots.
- Remove or blur public IP values.
- Keep only the minimum screenshot set needed to prove:
  - VM deployment
  - NSG HTTP rule creation
  - Nginx install or service state
  - successful browser validation

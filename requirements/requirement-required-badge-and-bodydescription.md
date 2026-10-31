# `required` badge and `bodyDescription` shape: UI/API/MCP contract mismatch

Reported from collection `-Jey39dCAAyx`, endpoint `zPXGO2aLVvVP` (Get all vouchers).

## Problem
1. Query/header params with `required: false` showed red "Required" in public docs.
2. Body field descriptions written to `bodyDescription` showed "—".

## Causes
1. `hitman-ui/src/utils/docsEndpointUtils.js` only treated `optional === true` or `checked === 'false'` as optional. `hitman-api/services/seoUtils.ts` (`requiredKeysOf`) uses `required`. Two conventions for one field. `checked` means "include in example", not required.
2. UI (`buildBodyDescription`) and MCP tools (`endpointToolsUtils.js`) read `bodyDescription.payload.value.<key>.{type,description,value}`. The report wrote flat `bodyDescription.<key>`, which is skipped. `createEndpointValidation` accepts any object (`bodyDescription: Joi.object()`), so the bad shape saves silently.

## Fixed
- UI now also treats `required === false` as optional (params, headers, form body rows).

## Still open
- Correct payload shape to write:
  `{"payload":{"type":"object","value":{"balanceStatus":{"type":"array","description":"...","value":[...]}}}}`
- Validate `bodyDescription` shape in `hitman-api/utils/Validation/endpointValidation.js`, or accept flat keys in the UI.
- Document `payload` wrapper and `optional` in the DocStar API collection; the MCP `update_endpoint` input schema omits `bodyDescription`.
- Params with neither `required` nor `optional` still render Required; decide whether the default should flip.

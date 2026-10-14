# Observed test record

Environment: disposable Azure lab, North Europe. Policy definition `871b6d14-10aa-478d-b590-94f262ecfa99`, display name `Require a tag on resources`, observed built-in version 1.0.1. Assignment scope: `rg-atlas-policy-20261012`, enforcement Default, parameter `tagName=LabPurpose`.

| Case | Input or action | Azure observation | Interpretation |
|---|---|---|---|
| P01 | Assign policy to the dedicated group | Named assignment appeared in the assignments list | Configuration persisted |
| P02 | NSG creation review, no tags | `RequestDisallowedByPolicy`; named the ATLAS assignment and custom message | Negative validation test passed; NSG not created by this attempt |
| P03 | Same resource, `LabPurpose=ATLAS-Policy-Guardrails` | Validation passed; deployment complete; tag visible on actual NSG | Positive deployment test passed |
| P04 | Delete the tag in the editor and select Apply | Could not save tags, `RequestDisallowedByPolicy` | Negative update test passed |
| P05 | Reopen resource Tags on 13 October | Original `LabPurpose` value still present; No changes | Failed update did not remove the tag |

The deployed NSG had zero custom inbound rules, zero custom outbound rules, zero subnet associations and zero network-interface associations. Azure's standard default rules were visible. No traffic filtering experiment was performed in this governance lab.

The positive deployment page reported completion and a start time of 12 October 2026, 17:50:51 in the portal's local display. No duration or propagation-time claim is inferred from it. The browser session was interrupted between work periods; long elapsed intervals are not active labor time.

## Limits

- One supported resource type and one scope were exercised. No out-of-scope deployment or other resource-provider coverage was tested.
- Scope containment was verified in configuration; no subscription-wide enforcement is claimed.
- Creation denial was captured during ARM validation, while tag removal denial came from an actual attempted update.
- The policy requires existence of a tag. It does not validate the value or assign/inherit one. An intermediate portal validation also passed while the value field was blank; no blank-value resource was deployed, and that incidental observation is not counted as an additional completed test.
- No compliance-percentage or evaluation-latency benchmark was collected.
- ARM JSON files were parsed locally, but not deployed or Azure schema-validated.

## Evidence handling

Five screenshots were captured on 12 October. Account headers were cropped out and the PNGs optimized. Image 01 is included in this release; the four test screenshots remain local pending publication review. Uncropped originals and full portal text records are retained privately. The observed result text and visible lab resource names were preserved.


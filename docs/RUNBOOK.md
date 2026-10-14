# Reproduction and design

Use a disposable resource group in an authorized Azure subscription. Check the offer, spending protection, remaining credit and expiration before creating anything. This lab used North Europe, a resource group, one resource-level tag policy and an unattached network security group. No workloads, public endpoints, flow logs, identities or role grants are needed.

## Portal procedure used in this lab

1. Create a dedicated resource group, `rg-atlas-policy-20261012`.
2. In **Policy > Assignments > Assign policy**, select ONLY that resource group as scope. Leave exclusions, overrides and selectors empty.
3. Select the built-in **Require a tag on resources** (version observed: 1.0.1; assignment version selector: `1.*.*`). Set enforcement to **Default** and Tag Name to `LabPurpose`. Do not create a managed identity or remediation task.
4. Set the non-compliance message to `ATLAS lab: add the LabPurpose tag before deploying this resource.` Review the full scope before creating.
5. Open **Network security groups > Create**. Select the same group, North Europe and `nsg-atlas-policy-test`. Leave Tags empty. Run **Review + create**.
6. Inspect the validation failure. It must identify `RequestDisallowedByPolicy`, the lab assignment and the custom message. A generic validation error alone is insufficient evidence.
7. Return to Tags. Add `LabPurpose=ATLAS-Policy-Guardrails`, then review again. Check the resulting tag and resource details before creating.
8. Verify the resource exists and inspect its tag. Keep it unattached. Capture evidence before removing the disposable lab group.

Policy propagation and compliance evaluation are asynchronous. If an untagged resource is unexpectedly accepted, record that result, verify scope and enforcement, allow propagation, and repeat with a new disposable name. Do not rewrite an unexpected result as a successful denial.

## What the control does

The built-in policy uses `Indexed` mode and denies eligible resources when the named tag does not exist. Resource groups and subscriptions are not covered by this resource-tag policy. The policy does **not** require a specific value, validate tag accuracy, automatically repair resources, or impose a spending cap. A present empty or misleading value is a design limitation; no blank-value resource was deployed in this run.

No exemption, enforcement bypass, subscription-wide deny rule or automatic remediation was used. The existing subscription initiative was preserved.

## Infrastructure reference

`infra/policy-assignment.json` and `infra/test-nsg.json` are hand-authored reproduction references. They were not deployed as ARM templates in the observed run. The actual deployment path was the portal. The portal generates an assignment name; the reference uses a readable deterministic name.

Only target a new disposable resource group when adapting the templates. Test the negative case with an empty `resourceTags` object, and the positive case with `{"LabPurpose":"ATLAS-Policy-Guardrails"}`. Creating the policy and the test resource in one deployment does not guarantee policy propagation before resource evaluation.

## Sources

- [Microsoft built-in policy source](https://github.com/Azure/azure-policy/blob/master/built-in-policies/policyDefinitions/Tags/RequireTag_Deny.json)
- [Tag policies](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/tag-policies)
- [Policy assignment ARM reference](https://learn.microsoft.com/en-us/azure/templates/microsoft.authorization/2024-04-01/policyassignments)
- [Network security group ARM reference](https://learn.microsoft.com/en-us/azure/templates/microsoft.network/2024-05-01/networksecuritygroups)


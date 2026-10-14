# Cleanup record

**Completed on 13 October 2026.**

Before deletion, the dedicated group contained exactly one visible resource: `nsg-atlas-policy-test`, a network security group in North Europe. The NSG had no subnet or network-interface associations. Its `LabPurpose=ATLAS-Policy-Guardrails` tag remained present after the rejected removal test.

The Azure portal deletion confirmation named only `rg-atlas-policy-20261012` and its test NSG. The group was deleted after documentation and evidence collection. Azure subsequently displayed **Deleted resource group rg-atlas-policy-20261012** as a success notification; the displayed resource inventory changed to 0 of 0.

The group-scoped assignment is part of the deleted group. No subscription-wide initiative was changed. The existing alert budget was retained; it does not create a spend cap.

Raw deletion status and the original capture were retained privately because the portal also displays account/billing information. No cost-bearing workload, storage, public IP or log collection service was created for this lab.

This is a record of the observed portal result. It is not an independently queried post-deletion API inventory. The local ARM templates remain as reproduction references and no longer-running lab service is needed for the portfolio.

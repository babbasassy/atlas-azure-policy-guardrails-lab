# Cost boundaries

The 12 October 2026 preflight showed an active trial subscription, USD 200 remaining credit and 17 days remaining. The previously observed exact credit expiry was 29 October 2026. Twelve-month free-service entitlements are distinct from the trial credit expiration.

Expected incremental infrastructure cost for this design: USD 0 (Azure Policy on Azure resources and an unattached NSG, without traffic, compute or logging). The subscription overview reported current cost 0.00 at preflight. This is a portal observation, not a final invoice or a measured per-project billing total.

The existing conservative budget remained in place. Budgets send alerts; they do not stop expenditure. No account upgrade, removal of the trial spending limit, paid plan, Marketplace purchase or payment authorization was performed for this lab.

Pricing and offer references checked on 12 October 2026:

- [Azure Policy pricing](https://azure.microsoft.com/en-us/pricing/details/azure-policy/): no charge for Azure Policy on Azure resources.
- [Virtual Network pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-network/): distinguishes the network from charged appliances and peering traffic.
- [Azure offer terms](https://azure.microsoft.com/en-us/pricing/offers/ms-azr-0017g/): credit eligibility and exclusions.

Do not add VMs, disks, public IPs, NAT, gateways, paid DDoS protection, log storage or traffic analytics to reproduce the tag-policy test. Such additions change its cost assumptions.

NSG cost confirmation: [Microsoft employee explanation](https://learn.microsoft.com/en-us/answers/questions/1314374/azure-design-azure-firewall-nsg) distinguishes the free NSG from separately charged flow logging.

After cleanup on 13 October, the subscription overview still showed USD 200 remaining, 16 days to credit expiration and Current cost 0.00. This remains a provisional portal reading.

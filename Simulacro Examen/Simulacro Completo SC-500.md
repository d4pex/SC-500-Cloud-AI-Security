
> **Nota:** Despliega el botón de solución al final de cada pregunta para comprobar tu respuesta.

---

## Pregunta 1

*Secure compute*

Your platform team runs Azure Kubernetes Service (AKS) clusters with images stored in Azure Container Registry (ACR). You must (1) detect misconfigurations such as privileged containers and exposed dashboards, (2) get runtime threat detection for suspicious activity inside the clusters, and (3) get vulnerability assessments for the images in ACR — all from one Defender for Cloud plan. What should you enable?

- [ ] An open-source image scanner in the CI pipeline that scans every image before it is pushed to ACR
- [ ] Microsoft Defender for Servers on the AKS node pools, since the nodes are just Linux VMs
- [ ] Microsoft Defender for Containers on the subscription, which combines Kubernetes hardening recommendations, runtime threat detection via the Defender sensor, and agentless vulnerability assessment of registry images

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Microsoft Defender for Containers on the subscription, which combines Kubernetes hardening recommendations, runtime threat detection via the Defender sensor, and agentless vulnerability assessment of registry images**
</details>

---

## Pregunta 2

*Secure storage, databases, and networking*

**Tallowfen Grocers** operates a chain of supermarkets and runs a wholesale marketplace in Azure that also serves several independent retail partners.

**Current Environment:**

- Marketplace document exports for all retail partners land in one general-purpose v2 storage account, with one blob container per partner. The storage account currently uses Microsoft-managed keys for encryption at rest.
- The loyalty platform uses an Azure SQL database. Applications and analysts connect with SQL logins whose passwords are stored in various configuration files; the same `sqladmin` password has been shared among three teams for years.
- Product-catalog and basket data for the e-commerce site is stored in an Azure Cosmos DB for NoSQL account. All services access it with the account's primary read-write key, which has never been rotated because nobody knows what would break.
- A recent partner-facing security questionnaire asked whether each partner's data could be encrypted with a key dedicated to that partner, and whether Tallowfen could stop reading a specific partner's data on request. Tallowfen could not answer yes.

You need to meet Tallowfen Grocers' loyalty database authentication requirements: SQL authentication completely disabled on the logical server, the loyalty API connecting without any password or stored credential and holding minimal database permissions, and analyst access granted through an Entra security group. What should you do?

- [ ] Delete the sqladmin login and create individual SQL logins for the API and for each analyst, each with a strong unique password
- [ ] Rotate the sqladmin password, store it in Azure Key Vault, and have the loyalty API and the analysts retrieve it from the vault at connection time
- [ ] Set a Microsoft Entra admin on the logical server and enable Microsoft Entra-only authentication; enable a managed identity on the loyalty API's compute resource, create a contained database user from that identity and grant it only the needed database roles; and create a contained database user from the analysts' Entra security group
- [ ] Enable Microsoft Entra-only authentication and register a service principal with a client secret for the loyalty API, granting the service principal db_owner so it never hits permission errors

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Set a Microsoft Entra admin on the logical server and enable Microsoft Entra-only authentication; enable a managed identity on the loyalty API's compute resource, create a contained database user from that identity and grant it only the needed database roles; and create a contained database user from the analysts' Entra security group**
</details>

---

## Pregunta 3

*Secure compute*

An oversharing assessment before your Microsoft 365 Copilot rollout identified 60 SharePoint sites with excessive access — including sites shared with 'Everyone except external users' that contain financial data. You must now **remediate**: stop Copilot from reasoning over the highest-risk sites until they are cleaned up, put the cleanup of excessive permissions in the hands of the people who know the content, and ensure files in the finance sites get baseline protection even when users save new documents without thinking about permissions. Which combination should you implement?

- [ ] Move the 60 sites into a separate tenant that does not have Copilot licenses
- [ ] Delete the 'Everyone except external users' claim from the tenant and re-add users to sites one by one as they complain
- [ ] Apply Restricted Content Discovery to the highest-risk sites so their content stops surfacing through Copilot and organization-wide search; run SharePoint site access reviews so site owners recertify and remove excessive permissions; and configure default sensitivity labels with protection settings on the finance sites' document libraries
- [ ] Disable Microsoft 365 Copilot for the whole tenant until every site's permissions have been manually audited by the security team

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Apply Restricted Content Discovery to the highest-risk sites so their content stops surfacing through Copilot and organization-wide search; run SharePoint site access reviews so site owners recertify and remove excessive permissions; and configure default sensitivity labels with protection settings on the finance sites' document libraries**
</details>

---

## Pregunta 4

*Secure storage, databases, and networking*

Your company is migrating its global network to Azure Virtual WAN with virtual hubs in three regions, each with multiple connected spoke virtual networks. Security requires that **all** spoke-to-spoke (private) traffic and **all** spoke-to-internet traffic is inspected by a firewall in the regional hub — and the design must not depend on maintaining user-defined routes (UDRs) on every spoke subnet. What should you implement?

- [ ] Deploy a network virtual appliance into one spoke virtual network per region and create UDRs on every spoke subnet pointing 0.0.0.0/0 and the RFC 1918 ranges at the appliance
- [ ] Peer all spokes directly with each other and place Azure DDoS Network Protection on the virtual WAN to inspect inter-spoke traffic
- [ ] Apply network security groups with deny-by-default rules on every spoke subnet, and enable NAT gateway on each spoke for internet egress
- [ ] Deploy Azure Firewall into each virtual hub to make it a secured virtual hub, then configure routing intent with private and internet traffic routing policies that send both traffic types through the hub firewall

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Deploy Azure Firewall into each virtual hub to make it a secured virtual hub, then configure routing intent with private and internet traffic routing policies that send both traffic types through the hub firewall**
</details>

---

## Pregunta 5

*Secure compute*

Your company builds AI agents in Microsoft Foundry and Copilot Studio. Each agent receives a **Microsoft Entra Agent ID**, giving it its own identity in the tenant. Security requires that these agent identities can obtain tokens only from approved network locations, with non-compliant sign-ins blocked at the identity layer — without affecting policies that apply to human users. What should you configure?

- [ ] A PIM eligible assignment for each agent so its identity is only active when a human approves it
- [ ] Network security group rules on the virtual network that deny outbound traffic from unapproved IP ranges
- [ ] A Conditional Access policy that targets the agent identities and blocks token issuance from outside the approved locations
- [ ] An Entra ID user Conditional Access policy requiring multifactor authentication, applied to the agents

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **A Conditional Access policy that targets the agent identities and blocks token issuance from outside the approved locations**
</details>

---

## Pregunta 6

*Manage identity, access, and governance*

Following a ransomware assessment, your organization must guarantee that Azure Backup recovery points cannot be deleted or have their retention shortened before they expire — even by a compromised account holding full administrative rights on the Recovery Services vaults — and that this guarantee itself cannot be quietly switched off later. What should you configure?

- [ ] Enable the immutable vault setting on each Recovery Services vault, verify the protection behaves as intended, and then lock the setting to make immutability irreversible
- [ ] Put a CanNotDelete lock on every Recovery Services vault
- [ ] Configure geo-redundant storage with cross-region restore so a second copy of every recovery point exists in the paired region
- [ ] Enable soft delete on the vaults so that deleted backup data is retained for 14 additional days

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable the immutable vault setting on each Recovery Services vault, verify the protection behaves as intended, and then lock the setting to make immutability irreversible**
</details>

---

## Pregunta 7

*Secure compute*

A Consumption Logic App processes employee salary-adjustment requests. A security review finds that: anyone with Reader access on the resource group can open the run history and see the salary figures in each action's inputs and outputs; the workflow's HTTP request trigger URL — which contains its shared access signature — has leaked into a wiki; and the workflow authenticates to Azure SQL with a connection string stored in plain text in a workflow parameter. Which combination of changes fixes all three findings?

- [ ] Enable diagnostic logging to a Log Analytics workspace, rotate the SQL password monthly, and add a comment to the workflow warning against sharing the trigger URL
- [ ] Convert the workflow to a Standard Logic App, since Standard workflows do not record run history or use trigger URLs
- [ ] Enable secure inputs and secure outputs on the actions that handle salary data; restrict the trigger with an inbound IP range for calls (or require Microsoft Entra ID authorization policies) and regenerate the leaked SAS access key; and replace the connection string with a managed identity connection to the database
- [ ] Move the Logic App to a resource group with no Reader assignments, add a random query parameter to the trigger URL, and base64-encode the connection string in the parameter

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable secure inputs and secure outputs on the actions that handle salary data; restrict the trigger with an inbound IP range for calls (or require Microsoft Entra ID authorization policies) and regenerate the leaked SAS access key; and replace the connection string with a managed identity connection to the database**
</details>

---

## Pregunta 8

*Manage identity, access, and governance*

**Orenfall Energy** is a regional electricity utility that runs its grid-telemetry ingestion platform and customer-billing systems in Azure. The company uses two subscriptions (Platform and Corporate) under a single Microsoft Entra ID tenant.

**Current Environment:**

- The platform operations team holds the Contributor role on the Platform subscription, although its day-to-day work is limited to starting, stopping, restarting, and viewing the telemetry-ingestion virtual machines.
- Customer-billing data is encrypted with customer-managed keys stored in an Azure key vault named `kv-orenfall-billing`. Key rotation is performed manually by an engineer roughly twice a year, and it has been missed twice.
- TLS certificates for the SCADA gateway endpoints are stored in the same vault; one certificate expired unnoticed last quarter and caused a four-hour telemetry outage.
- External engineering contractors from a partner firm are onboarded by emailing the service desk, which manually adds them to various groups and applications. Offboarding is inconsistent, and several contractor accounts from a project that ended last year still have access.

You need to redesign contractor onboarding for Orenfall Energy so that contractors request a predefined bundle of groups and applications, the project manager approves each request, access expires automatically after 90 days, and remaining access is recertified quarterly. What should you implement?

- [ ] A Microsoft Entra entitlement management access package containing the project's groups and applications, with the project manager as approver, a 90-day expiration on assignments, and a quarterly access review attached to the package
- [ ] A Conditional Access policy that grants contractors access only for 90 days after their first sign-in and then blocks them
- [ ] A dynamic security group whose membership rule matches the contractors' company name, granted permanent access to the project resources
- [ ] Microsoft Entra Privileged Identity Management, making each contractor eligible for the groups and requiring activation every morning

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **A Microsoft Entra entitlement management access package containing the project's groups and applications, with the project manager as approver, a 90-day expiration on assignments, and a quarterly access review attached to the package**
</details>

---

## Pregunta 9

*Manage and monitor security posture*

**Dunmoral Airways** is a regional airline. Its security operations center (SOC) uses a Microsoft Sentinel workspace, and the company runs Microsoft 365 for email, SharePoint, and Teams alongside its Azure workloads.

**Current Environment:**

- The airline's booking platform emits roughly 100 GB per day of verbose JSON application logs through a REST-capable log shipper. The logs are needed only occasionally, during incident investigations, but the aviation regulator requires that they remain available for one year.
- The booking logs contain a `passengerDocument` field with passport numbers that must not be stored in the SIEM at all.
- Core security tables such as `SigninLogs` and `SecurityEvent` are queried by analysts and analytics rules every day.
- SOC analysts currently have no way to search Microsoft 365 activities (mailbox access, SharePoint file operations, Entra admin changes) from their security tooling; they file tickets with the Microsoft 365 team instead.

You need to design table plans and retention for Dunmoral Airways' Microsoft Sentinel workspace: booking-platform logs (100 GB/day, rarely queried, 1-year availability) at the lowest cost, and core security tables fully interactive for 90 days with 2 years of total retention. What should you configure?

- [ ] Continuously export all tables to a storage account, keep only 7 days in the workspace, and have analysts download blobs during investigations
- [ ] Ingest the booking logs into a custom table on the Auxiliary (or Basic) table plan with total retention set to 12 months, and keep SigninLogs and SecurityEvent on the Analytics plan with 90 days interactive retention and total retention set to 2 years
- [ ] Create a second workspace for the booking logs and set the workspace pricing tier to a 100 GB/day commitment tier for a discount
- [ ] Ingest everything into Analytics-plan tables with 2-year interactive retention so that all data is always query-ready

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Ingest the booking logs into a custom table on the Auxiliary (or Basic) table plan with total retention set to 12 months, and keep SigninLogs and SecurityEvent on the Analytics plan with 90 days interactive retention and total retention set to 2 years**
</details>

---

## Pregunta 10

*Manage identity, access, and governance*

Microsoft Entra ID Protection reports two recurring detection types in your tenant: users whose credentials appear in a leaked-credential dump (elevated user risk), and sign-ins with unfamiliar properties from new locations (elevated sign-in risk). You must configure automated, self-service remediation so that genuinely compromised credentials get replaced and suspicious sign-ins are challenged — without help-desk involvement and without blanket-blocking users. What should you configure?

- [ ] A single Conditional Access policy that blocks access whenever any user or sign-in risk is detected, forcing users to call the help desk for reinstatement
- [ ] Enable security defaults for the tenant, which automatically remediates user and sign-in risk
- [ ] A risk-based Conditional Access policy that requires a secure password change when user risk is high, and a second policy that requires multifactor authentication when sign-in risk is medium or higher
- [ ] A Conditional Access policy requiring MFA for high user risk, and a policy requiring password change for medium sign-in risk

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **A risk-based Conditional Access policy that requires a secure password change when user risk is high, and a second policy that requires multifactor authentication when sign-in risk is medium or higher**
</details>

---

## Pregunta 11

*Secure storage, databases, and networking*

**Brindlecote Manufacturing** produces industrial packaging equipment at six plants. Its Azure estate has grown organically to about 30 virtual networks across five subscriptions, each managed by a different application team.

**Current Environment:**

- Every application team creates and edits its own network security groups (NSGs). Last year an application team deleted an NSG rule that blocked inbound internet traffic to management ports, exposing several VMs for two weeks before it was noticed.
- A machine-telemetry API used by an external analytics partner is currently published on a public IP address protected only by an IP allowlist.
- The partner's Azure environment uses address spaces that overlap with Brindlecote's, so virtual network peering has already been ruled out.
- Field service engineers connect remotely through a legacy SSL VPN appliance that uses a shared credential stored in a team wiki.

You need to replace Brindlecote Manufacturing's legacy SSL VPN for field engineers with a point-to-site VPN that authenticates individual Microsoft Entra ID accounts, enforces MFA through Conditional Access, and allows immediate central revocation for a departing engineer. How should you configure the VPN?

- [ ] Keep the SSL VPN appliance and place Azure Bastion in front of it to add Microsoft Entra ID authentication
- [ ] Deploy the VPN gateway with certificate authentication, generate one client certificate from the root, and distribute it to all field engineers
- [ ] Deploy the VPN gateway with RADIUS authentication against a local database on the appliance and rotate the shared password quarterly
- [ ] Deploy an Azure VPN gateway with OpenVPN and Microsoft Entra ID authentication, have engineers connect with the Azure VPN Client, and target the Azure VPN enterprise application with a Conditional Access policy that requires multifactor authentication

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Deploy an Azure VPN gateway with OpenVPN and Microsoft Entra ID authentication, have engineers connect with the Azure VPN Client, and target the Azure VPN enterprise application with a Conditional Access policy that requires multifactor authentication**
</details>

---

## Pregunta 12

*Secure storage, databases, and networking*

Your data estate spans four platforms: Azure SQL Database, SQL Server instances running on Azure VMs and on Azure Arc-enabled on-premises servers, Azure Database for PostgreSQL flexible servers, and Azure Cosmos DB. Security requires threat detection — such as SQL injection attempts, anomalous access patterns, and brute-force attacks — across **all four** platforms, surfaced as Defender for Cloud security alerts. What should you enable?

The Defender for Databases plans that match the estate: Defender for Azure SQL Databases, Defender for SQL Servers on Machines (with the SQL Server extension on the Azure and Arc-enabled machines), Defender for Open-Source Relational Databases, and Defender for Azure Cosmos DB

- [ ] Auditing on every database with logs streamed to a Log Analytics workspace, because auditing raises security alerts for SQL injection and brute-force attacks
- [ ] Defender for Azure SQL Databases only — it automatically extends to SQL Server on VMs, PostgreSQL, and Cosmos DB in the same subscription
- [ ] Defender for Servers on the VMs and Arc-enabled machines — endpoint detection and response on the host covers the database engines running on it

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Defender for Azure SQL Databases only — it automatically extends to SQL Server on VMs, PostgreSQL, and Cosmos DB in the same subscription**
</details>

---

## Pregunta 13

*Manage identity, access, and governance*

**Veynhart Robotics** designs warehouse automation robots and runs its control-plane services in Azure across a Development and a Production subscription in one Microsoft Entra ID tenant.

**Current Environment:**

- Infrastructure is deployed with Bicep templates from an internal deployment pipeline. Several parameter files in the repository contain plaintext SQL connection strings and third-party API keys; two of them were flagged during a recent code audit.
- Many resources — including key vaults and SQL logical servers — were created by different teams over three years. An internal review found that resource logs are enabled on some resources and missing on others, and nobody notices when a new resource is created without them.
- A fleet-diagnostics team occasionally needs to read secrets from the vault `kv-veyn-fleet` during live incident bridges. Today, six engineers hold a permanent Key Vault Secrets User assignment on the vault even though such incidents occur roughly once a month.
- The team that reviews access complains that the six engineers appear in every quarterly review even though most have never actually used the access.

You need to redesign the fleet-diagnostics engineers' access to `kv-veyn-fleet` for Veynhart Robotics: no standing access, activation only during incidents with approval by the on-call incident manager, automatic expiry after 8 hours, a recorded justification for every activation — and the existing Azure RBAC assignment model on the vault must keep working. What should you implement?

- [ ] Create a Conditional Access policy that blocks the engineers' access to Key Vault except when their sign-in risk is low and an incident ticket exists
- [ ] Replace the engineers' access with a shared break-glass account whose password is stored in a sealed envelope held by the incident manager
- [ ] Create a role-assignable security group, assign it the Key Vault Secrets User role on the vault, onboard the group to Privileged Identity Management (PIM) for Groups, make the engineers eligible members, and configure the membership activation policy with approval, justification, and an 8-hour maximum duration
- [ ] Onboard the Key Vault Secrets User Azure role itself to PIM and make each of the six engineers individually eligible for the role on the vault

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create a role-assignable security group, assign it the Key Vault Secrets User role on the vault, onboard the group to Privileged Identity Management (PIM) for Groups, make the engineers eligible members, and configure the membership activation policy with approval, justification, and an 8-hour maximum duration**
</details>

---

## Pregunta 14

*Secure storage, databases, and networking*

Microsoft Defender for Storage is enabled across your subscriptions. The data protection office now asks for two additions: (1) know **which storage accounts actually contain sensitive data** (such as passport numbers and payment data) so those accounts can be prioritized, and (2) receive **higher-fidelity alerts** when threat activity — like an unusually large download from an unfamiliar location — touches a container that holds sensitive data. What should you do?

- [ ] Enable the sensitive data threat detection (sensitive data discovery) feature of Defender for Storage, which scans accounts for sensitive information types and enriches threat alerts on resources that hold sensitive data
- [ ] Enable on-upload malware scanning on every storage account, since malware scanning also classifies the sensitivity of scanned blobs
- [ ] Turn on Azure Storage inventory reports and have the SOC review the produced blob lists weekly for sensitive file names
- [ ] Apply Microsoft Purview sensitivity labels manually to each container and configure an alert rule on label creation events

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable the sensitive data threat detection (sensitive data discovery) feature of Defender for Storage, which scans accounts for sensitive information types and enriches threat alerts on resources that hold sensitive data**
</details>

---

## Pregunta 15

*Secure compute*

Before expanding its Microsoft 365 Copilot rollout, your organization is worried that Copilot could surface content from **overshared SharePoint sites** — files with broad "Everyone" permissions that users would never have found manually. You need to assess this oversharing risk, see how sensitive data is being used in Copilot prompts and responses, and get recommended policies to reduce the exposure. What should you use?

- [ ] A Conditional Access policy that blocks the Microsoft 365 Copilot service for all users
- [ ] Microsoft Purview Data Security Posture Management (DSPM) for AI, running its oversharing assessment and applying the recommended protection policies
- [ ] Defender for AI Services in Microsoft Defender for Cloud, enabled on the Microsoft 365 tenant
- [ ] Disabling search indexing on all SharePoint sites so Copilot cannot retrieve their content

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Microsoft Purview Data Security Posture Management (DSPM) for AI, running its oversharing assessment and applying the recommended protection policies**
</details>

---

## Pregunta 16

*Secure storage, databases, and networking*

**Brindlecote Manufacturing** produces industrial packaging equipment at six plants. Its Azure estate has grown organically to about 30 virtual networks across five subscriptions, each managed by a different application team.

**Current Environment:**

- Every application team creates and edits its own network security groups (NSGs). Last year an application team deleted an NSG rule that blocked inbound internet traffic to management ports, exposing several VMs for two weeks before it was noticed.
- A machine-telemetry API used by an external analytics partner is currently published on a public IP address protected only by an IP allowlist.
- The partner's Azure environment uses address spaces that overlap with Brindlecote's, so virtual network peering has already been ruled out.
- Field service engineers connect remotely through a legacy SSL VPN appliance that uses a shared credential stored in a team wiki.

You need to implement Brindlecote Manufacturing's organization-wide network guardrails: mandatory rules (such as denying inbound internet traffic to RDP/SSH) that apply automatically to all current and future virtual networks, are evaluated before the application teams' NSG rules, and cannot be overridden or deleted by those teams. What should you implement?

- [ ] Create a standard NSG named nsg-baseline in each subscription and instruct every application team to associate it with their subnets alongside their own NSGs
- [ ] Route all traffic through a central Azure Firewall by using user-defined routes so that NSG rules become irrelevant
- [ ] Apply CanNotDelete resource locks to every NSG so that application teams cannot delete security rules
- [ ] Deploy Azure Virtual Network Manager, add the virtual networks to a network group with dynamic membership defined by Azure Policy, and deploy a security admin configuration containing the mandatory deny rules

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Deploy Azure Virtual Network Manager, add the virtual networks to a network group with dynamic membership defined by Azure Policy, and deploy a security admin configuration containing the mandatory deny rules**
</details>

---

## Pregunta 17

*Manage and monitor security posture*

**Dunmoral Airways** is a regional airline. Its security operations center (SOC) uses a Microsoft Sentinel workspace, and the company runs Microsoft 365 for email, SharePoint, and Teams alongside its Azure workloads.

**Current Environment:**

- The airline's booking platform emits roughly 100 GB per day of verbose JSON application logs through a REST-capable log shipper. The logs are needed only occasionally, during incident investigations, but the aviation regulator requires that they remain available for one year.
- The booking logs contain a `passengerDocument` field with passport numbers that must not be stored in the SIEM at all.
- Core security tables such as `SigninLogs` and `SecurityEvent` are queried by analysts and analytics rules every day.
- SOC analysts currently have no way to search Microsoft 365 activities (mailbox access, SharePoint file operations, Entra admin changes) from their security tooling; they file tickets with the Microsoft 365 team instead.

You need to give Dunmoral Airways' SOC analysts the ability to search audited Microsoft 365 user and admin activities (mailbox access, SharePoint file operations, Entra admin changes) from the Microsoft Defender portal during incident investigations. What should you do?

- [ ] Verify that Microsoft Purview auditing is enabled for the tenant, grant the analysts a role that includes audit search permissions, and have them query the Purview Audit log from the unified Microsoft Defender portal during investigations
- [ ] Export the Entra ID sign-in logs to a storage account and have analysts download the CSV files when a case involves Microsoft 365
- [ ] Enable Microsoft Defender for Storage on the Microsoft 365 tenant so that file operations in SharePoint generate security alerts
- [ ] Install the Azure Monitor Agent on the SharePoint Online and Exchange Online servers and create a data collection rule that forwards their security event logs

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Verify that Microsoft Purview auditing is enabled for the tenant, grant the analysts a role that includes audit search permissions, and have them query the Purview Audit log from the unified Microsoft Defender portal during investigations**
</details>

---

## Pregunta 18

*Manage and monitor security posture*

**Bellcairn Utilities** operates water treatment and distribution infrastructure. Its security operations team runs Microsoft Defender for Cloud across three Azure subscriptions and a Microsoft Sentinel workspace, and the company also keeps an on-premises Splunk deployment that the industrial-control (OT) team refuses to give up.

**Current Environment:**

- A contractor recently found a PDF on a build server containing a service-account password, which prompted the CISO to ask, "How many other credentials are lying around in files on our machines, and what could an attacker reach with them?" Nobody could answer.
- About 40 Linux VMs run the telemetry ingestion tier. Their authentication and sudo activity is written to the local syslog daemon. None of it reaches the SOC today.
- The Sentinel workspace generates Defender for Cloud security alerts and recommendations, but the OT team's on-call rotation works exclusively out of Splunk dashboards and refuses to monitor a second console.
- Defender for Cloud plans (Defender CSPM and Defender for Servers Plan 2) are already enabled on all three subscriptions.

You need to ingest authentication and sudo events (auth and authpriv facilities, warning severity and above) from Bellcairn Utilities' 40 Linux VMs into Microsoft Sentinel, exclude all other syslog facilities to control cost, and use the current Microsoft-supported agent deployed centrally. What should you implement?

- [ ] Enable Defender for Servers Plan 2 on the VMs, because it automatically streams all local syslog data to the connected Sentinel workspace
- [ ] Enable the Syslog via AMA data connector, create a data collection rule that targets the 40 VMs — deploying the Azure Monitor Agent through the DCR association — and configure the rule to collect only the auth and authpriv facilities at LOG_WARNING level and above, landing the events in the Syslog table
- [ ] Deploy a dedicated Linux log forwarder, point all 40 VMs' syslog daemons at it, and use the Common Event Format (CEF) via AMA connector
- [ ] Install the legacy Log Analytics (OMS) agent on the VMs and configure the syslog facilities in the workspace's agent configuration blade

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable the Syslog via AMA data connector, create a data collection rule that targets the 40 VMs — deploying the Azure Monitor Agent through the DCR association — and configure the rule to collect only the auth and authpriv facilities at LOG_WARNING level and above, landing the events in the Syslog table**
</details>

---

## Pregunta 19

*Secure compute*

For a fleet of Azure VMs, security requires that the OS disk, data disks, **and the temp disk plus disk caches** are encrypted end-to-end between the VM host and storage — and the solution must not install any agent or extension inside the guest operating system. Which encryption option should you enable?

- [ ] Server-side encryption of managed disks with a customer-managed key (CMK)
- [ ] Encryption at host
- [ ] Azure Disk Encryption (ADE) with BitLocker/DM-Crypt
- [ ] Confidential disk encryption

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Encryption at host**
</details>

---

## Pregunta 20

*Manage and monitor security posture*

Your organization has an internal hardening baseline that goes beyond the built-in compliance standards — for example, "every storage account must have both infrastructure encryption and a customer-managed key." The security team wants these internal requirements assessed continuously across Azure **and** the connected AWS environment, shown with pass/fail resource counts alongside the built-in standards in Microsoft Defender for Cloud. What should you do?

- [ ] Create a custom security standard in Defender for Cloud, author custom recommendations with KQL queries against the cloud asset graph for the internal requirements, add them to the standard, and assign the standard to the Azure subscriptions and the AWS connector
- [ ] Create Azure Policy custom definitions only, since Defender for Cloud cannot assess non-Azure resources against custom rules
- [ ] Enable every built-in regulatory compliance standard available, since together they cover any conceivable internal requirement
- [ ] Export all resources to a spreadsheet monthly and have the governance team mark each requirement as met or unmet

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create a custom security standard in Defender for Cloud, author custom recommendations with KQL queries against the cloud asset graph for the internal requirements, add them to the standard, and assign the standard to the Azure subscriptions and the AWS connector**
</details>

---

## Pregunta 21

*Manage and monitor security posture*

Microsoft Security Copilot is live in your tenant: capacity is provisioned, workspaces are configured, and analysts have their roles. During review, the security architect finds that any Copilot contributor can add new plugins — including custom plugins that call external APIs — and can toggle plugins on for their own sessions. Governance requires that only the platform team decides which plugins are available, that custom plugins pointing at unapproved external endpoints cannot be added by analysts, and that analysts keep using the approved plugin set without interruption. What should you configure?

- [ ] Reduce the provisioned Security Compute Units so that unapproved plugins fail to execute due to insufficient capacity
- [ ] Block outbound HTTPS from the analysts' workstations to any domain not on the corporate allowlist, so unapproved plugin APIs cannot be reached
- [ ] Remove the analysts' Copilot contributor role and require them to submit prompts to the platform team, who will run them with the correct plugins
- [ ] In the Security Copilot owner settings, restrict plugin management so that only Copilot owners can add and enable plugins (including setting who can add custom plugins), and curate the approved plugin list centrally — leaving the approved plugins enabled for analyst sessions

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **In the Security Copilot owner settings, restrict plugin management so that only Copilot owners can add and enable plugins (including setting who can add custom plugins), and curate the approved plugin list centrally — leaving the approved plugins enabled for analyst sessions**
</details>

---

## Pregunta 22

*Secure storage, databases, and networking*

Your hub virtual network runs Azure Firewall Premium. The security team wants exploit attempts and command-and-control callbacks inside **encrypted outbound HTTPS traffic** detected and blocked by signature, while one legacy payroll application's traffic — which breaks when its certificate chain is altered — must keep working and must not be decrypted. What should you configure?

- [ ] Replace the firewall with an Application Gateway WAF v2, which performs both TLS termination and signature-based intrusion prevention for outbound traffic
- [ ] Set IDPS to Alert and deny without enabling TLS inspection, since IDPS signatures operate on the encrypted stream
- [ ] Enable threat intelligence-based filtering in Deny mode, which decrypts TLS sessions automatically when a signature matches
- [ ] Enable TLS inspection with an intermediate CA certificate from Key Vault, set IDPS to Alert and deny, and exclude the payroll application's destination FQDNs from TLS inspection so its traffic bypasses decryption

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable TLS inspection with an intermediate CA certificate from Key Vault, set IDPS to Alert and deny, and exclude the payroll application's destination FQDNs from TLS inspection so its traffic bypasses decryption**
</details>

---

## Pregunta 23

*Secure storage, databases, and networking*

**Quillstone Retail Group** operates 240 stores and an e-commerce platform hosted in Azure. Customer order data is stored in an Azure SQL Database elastic pool, and product images, invoices, and data exports are kept in two general-purpose v2 storage accounts named `stqsorders` and `stqsmedia`.

**Current Environment:**

- Both storage accounts allow access from all networks and have shared key authorization enabled.
- Partner logistics companies upload delivery manifests to a container in `stqsorders` by using SAS tokens that were generated ad hoc and never expire.
- The Azure SQL logical server allows connections from all Azure services and has no auditing configured.
- A recent incident involved a malware-infected file being uploaded to the `stqsmedia` account by a compromised partner workstation.

Following the malware incident in the `stqsmedia` account, you must ensure uploaded blobs are scanned for malware in near real time with findings surfaced in Microsoft Defender for Cloud, and partner SAS tokens must become revocable with centrally controlled lifetimes. Which two changes should you make?

- [ ] Enable blob soft delete and versioning, and require partners to upload through SFTP with local users
- [ ] Enable Microsoft Defender for App Service, and rotate the storage account keys monthly to invalidate old SAS tokens
- [ ] Enable Azure Storage lifecycle management to move new blobs to the archive tier, and switch partners to user delegation SAS tokens with 10-year expiry
- [ ] Enable Microsoft Defender for Storage with on-upload malware scanning on the subscription, and reissue partner SAS tokens as service SAS tokens tied to a stored access policy on the container

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable Microsoft Defender for Storage with on-upload malware scanning on the subscription, and reissue partner SAS tokens as service SAS tokens tied to a stored access policy on the container**
</details>

---

## Pregunta 24

*Manage and monitor security posture*

You are standing up Microsoft Sentinel for a company whose Azure footprint and SOC are entirely in one region and one tenant. The IT operations team already runs a Log Analytics workspace for VM performance data, and its engineers must not gain access to security data. The SOC must control access to Sentinel independently, and security data must be kept separate from operational data. How should you create and connect the workspace?

- [ ] Create a new Log Analytics workspace in a dedicated resource group for security, enable Microsoft Sentinel on it, and assign the SOC its Microsoft Sentinel roles at that resource group scope — leaving the operations workspace untouched
- [ ] Enable Microsoft Sentinel on the existing operations workspace to avoid duplicate ingestion charges, and use table-level RBAC to hide the performance tables from the SOC
- [ ] Create the Sentinel workspace in a separate Microsoft Entra tenant and manage it through Azure Lighthouse for maximum isolation
- [ ] Create one workspace per data connector so that each data source's access can be controlled separately

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create a new Log Analytics workspace in a dedicated resource group for security, enable Microsoft Sentinel on it, and assign the SOC its Microsoft Sentinel roles at that resource group scope — leaving the operations workspace untouched**
</details>

---

## Pregunta 25

*Manage and monitor security posture*

**Dunmoral Airways** is a regional airline. Its security operations center (SOC) uses a Microsoft Sentinel workspace, and the company runs Microsoft 365 for email, SharePoint, and Teams alongside its Azure workloads.

**Current Environment:**

- The airline's booking platform emits roughly 100 GB per day of verbose JSON application logs through a REST-capable log shipper. The logs are needed only occasionally, during incident investigations, but the aviation regulator requires that they remain available for one year.
- The booking logs contain a `passengerDocument` field with passport numbers that must not be stored in the SIEM at all.
- Core security tables such as `SigninLogs` and `SecurityEvent` are queried by analysts and analytics rules every day.
- SOC analysts currently have no way to search Microsoft 365 activities (mailbox access, SharePoint file operations, Entra admin changes) from their security tooling; they file tickets with the Microsoft 365 team instead.

You need to implement the custom ingestion pipeline for Dunmoral Airways' booking logs: a dedicated custom table with a SOC-controlled schema, and the `passengerDocument` field removed before the data is stored in the workspace. What should you build?

- [ ] Send the records with the legacy HTTP Data Collector API, then schedule a nightly job that overwrites the stored rows to blank out the passengerDocument column
- [ ] You need to implement the custom ingestion pipeline for Dunmoral Airways' booking logs: a de
- [ ] Install the Azure Monitor Agent on the booking servers with a Windows event data collection rule, and exclude the passport events by event ID
- [ ] Stream the logs to an event hub and have a scheduled analytics rule in Microsoft Sentinel filter the sensitive field before analysts query the table
- [ ] Create a data collection rule (DCR)-based custom table (for example, BookingActivity_CL), send the JSON records from the log shipper to the Logs Ingestion API through a data collection endpoint, and add a KQL transformation in the DCR that drops the passengerDocument field at ingestion time

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create a data collection rule (DCR)-based custom table (for example, BookingActivity_CL), send the JSON records from the log shipper to the Logs Ingestion API through a data collection endpoint, and add a KQL transformation in the DCR that drops the passengerDocument field at ingestion time**
</details>

---

## Pregunta 26

*Manage identity, access, and governance*

A security review of your Microsoft Entra tenant finds three problems with application identity:

1. Any employee can create new app registrations, and dozens of forgotten registrations exist.
2. Several multi-tenant applications are protected only by client secrets, some set to never expire.
3. An internal HR application can be signed into by every user in the tenant, although only the HR department should reach it.

Which three actions should you take? (Select three.)
- [ ] Set 'Users can register applications' to No in the tenant's user settings and grant the developers who need it the Application Developer role (or an approved request process)
- [ ] Enable security defaults for the tenant to automatically clean up unused app registrations and expiring credentials
- [ ] On the HR application's enterprise application (service principal), enable 'Assignment required' and assign only the HR department's group
- [ ] Convert the multi-tenant applications to single-tenant so that client secrets are no longer required
- [ ] Replace the client secrets with certificate credentials (or managed identities where the workload runs in Azure), and use app management policies to block new long-lived secrets
- [ ] Delete all existing app registrations and require teams to re-register the applications they still use

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Set 'Users can register applications' to No in the tenant's user settings and grant the developers who need it the Application Developer role (or an approved request process)**

✅ **Replace the client secrets with certificate credentials (or managed identities where the workload runs in Azure), and use app management policies to block new long-lived secrets**
</details>

---

## Pregunta 27

*Secure storage, databases, and networking*

**Pellagrin Insurance** is a property-and-casualty insurer that processes claims in Azure. The company is subject to strict records-retention regulation and periodic external audits.

**Current Environment:**

- Finalized claim documents (scanned reports, settlement letters) are stored as blobs in a container named `claims-final` in a general-purpose v2 storage account.
- Departmental file shares are being migrated from an on-premises Windows file server to Azure Files. Users work on Windows devices joined to the on-premises Active Directory Domain Services (AD DS) domain, and years of carefully maintained NTFS permissions must keep working after the migration.
- The claims database is an Azure SQL database that stores national identification numbers and a `PaymentAdjustments` table that auditors examine for signs of manipulation.
- Database administrators routinely connect to the production database for troubleshooting and can currently read every column.

You need to meet Pellagrin Insurance's document retention requirements for the `claims-final` container: documents unmodifiable and undeletable for 7 years even by storage administrators, protection that cannot itself be removed, plus an indefinite case-based hold for documents under litigation. What should you configure?

- [ ] An immutability policy on the container with a 7-year time-based retention period that you lock after validation, and legal holds with case tags applied when litigation begins
- [ ] A lifecycle management rule that moves blobs to the archive tier after upload, because archived blobs cannot be modified
- [ ] You need to meet Pellagrin Insurance's document retention requirements for the `claims-final`
- [ ] Blob soft delete with a 7-year retention period, and a CanNotDelete resource lock on the storage account for litigation cases
- [ ] Azure RBAC deny assignments that remove write and delete permissions on the container from all users for 7 years

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **An immutability policy on the container with a 7-year time-based retention period that you lock after validation, and legal holds with case tags applied when litigation begins**
</details>

---

## Pregunta 28

*Secure storage, databases, and networking*

Microsoft Defender for Storage (with on-upload malware scanning) is enabled at the subscription level. One storage account, `stmediaingest`, receives millions of machine-generated telemetry files per day, and scanning them is projected to dominate the security budget while adding no value. Security requirements state that:

- Malware scanning must stay enabled for every other storage account in the subscription, with a monthly cost ceiling per account.
- `stmediaingest` must keep activity monitoring and threat detection, but must not have its uploads malware-scanned.
- Blobs uploaded to the `legal-archive` container **before** Defender for Storage was enabled must be scanned once.

What should you do?

- [ ] Keep the subscription-level plan; configure an override on `stmediaingest` that disables on-upload malware scanning while leaving the plan enabled; set the monthly GB cap for malware scanning on the other accounts; and run an on-demand malware scan against the existing blobs in `legal-archive`
- [ ] Route all uploads through Azure Firewall Premium with IDPS enabled so that malware is detected on the network path instead of in the storage service
- [ ] Exclude `stmediaingest` from the Defender for Storage plan entirely, and lower the subscription's overall Defender for Cloud spending limit to cap scanning costs
- [ ] Replace on-upload malware scanning with an Azure Automation runbook that downloads each new blob and checks it with a script, and rely on lifecycle management to age out unscanned blobs

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Keep the subscription-level plan; configure an override on `stmediaingest` that disables on-upload malware scanning while leaving the plan enabled; set the monthly GB cap for malware scanning on the other accounts; and run an on-demand malware scan against the existing blobs in `legal-archive`**
</details>

---

## Pregunta 29

*Manage and monitor security posture*

Your SOC is standing up Microsoft Sentinel and wants, for each product it monitors (a third-party firewall, Azure activity, a SaaS HR platform), the vendor's full package — data connector, analytics rules, hunting queries, workbooks, and playbooks — installed together, tracked as one unit, and updated when the publisher ships a new version. How should the team onboard this content?

- [ ] Export the analytics rules and workbooks from another Sentinel workspace as ARM templates and redeploy them into the new workspace for each product
- [ ] Enable each product's data connector individually from the connector gallery — analytics rules, workbooks, and playbooks are provisioned automatically with every connector
- [ ] Install the corresponding solutions from the Microsoft Sentinel content hub, then enable the included connectors and content, and apply solution updates from the content hub as publishers release them
- [ ] Clone community GitHub repositories for each product and import the detection YAML files and workbook JSON into the workspace manually

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Install the corresponding solutions from the Microsoft Sentinel content hub, then enable the included connectors and content, and apply solution updates from the content hub as publishers release them**
</details>

---

## Pregunta 30

*Secure storage, databases, and networking*

**Harrowfield Logistics** is an international freight and shipping company. Its Azure footprint uses a hub-and-spoke topology: a hub virtual network (`vnet-hub`) and three spoke virtual networks (`vnet-tracking`, `vnet-billing`, `vnet-analytics`) peered to the hub.

**Current Environment:**

- Each spoke hosts VMs and App Service apps for a business unit; outbound internet traffic currently leaves directly from each spoke.
- The billing application in `vnet-billing` calls an Azure SQL Database and an Azure Storage account over their public endpoints.
- Warehouse staff at 40 depots access an internal shipment-tracking web app through a legacy site-to-site VPN into the hub.
- Remote administrators connect to VMs by using public IP addresses with RDP restricted by source IP in NSG rules.

You need to ensure the Harrowfield billing application reaches Azure SQL Database and Azure Storage over private IP addresses only, with public endpoints disabled and name resolution working for both Azure and on-premises clients. What should you implement?

- [ ] Enable service endpoints for Microsoft.Sql and Microsoft.Storage on the billing subnet and add the subnet to each resource's firewall
- [ ] Create private endpoints for the SQL logical server and storage account in vnet-billing, link privatelink DNS zones (privatelink.database.windows.net and privatelink.blob.core.windows.net) to the VNets, configure a DNS forwarder or Azure DNS Private Resolver for on-premises resolution, and set Public network access to Disabled on both resources
- [ ] Create a Private Link service behind a Standard Load Balancer in vnet-billing and register the SQL and storage endpoints as backend targets
- [ ] Deploy a NAT gateway on the billing subnet so that outbound traffic to SQL and Storage uses a fixed public IP that you allow in each resource's firewall

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create private endpoints for the SQL logical server and storage account in vnet-billing, link privatelink DNS zones (privatelink.database.windows.net and privatelink.blob.core.windows.net) to the VNets, configure a DNS forwarder or Azure DNS Private Resolver for on-premises resolution, and set Public network access to Disabled on both resources**
</details>

---

## Pregunta 31

*Secure compute*

Business units build customer-facing conversational agents in Microsoft Copilot Studio. A red-team exercise demonstrated that crafted user messages could manipulate an agent into ignoring its instructions (a prompt-injection attack). Security requires that malicious prompts against these agents are detected **and blocked in near real time while the agents run**, with the resulting alerts appearing in Microsoft Defender XDR for SOC investigation. What should you do?

- [ ] Route each agent's traffic through the AI Gateway in Azure API Management and apply a token-limit policy to the agents' conversations
- [ ] Create a Power Platform data loss prevention policy that restricts which connectors Copilot Studio agents may use
- [ ] Apply Microsoft Purview sensitivity labels to the knowledge sources the agents reference so labeled content cannot be exfiltrated by injected prompts
- [ ] Enable real-time protection for Copilot Studio agents through the Microsoft Defender integration, so prompts are inspected at runtime, malicious ones are blocked, and alerts surface in the Defender portal

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable real-time protection for Copilot Studio agents through the Microsoft Defender integration, so prompts are inspected at runtime, malicious ones are blocked, and alerts surface in the Defender portal**
</details>

---

## Pregunta 32

*Manage identity, access, and governance*

Your organization's key vaults are accessed by dozens of applications with well-established patterns. The security team wants to be alerted when a vault is accessed in an anomalous way — for example, from a Tor exit node, by an unusual user or application, or through a sudden spike in secret list-and-get operations that suggests key harvesting — without changing how the applications currently access the vaults. What should you do?

- [ ] Enable the Key Vault firewall with a default Deny action so that only known networks can reach the vaults
- [ ] Stream Key Vault diagnostic logs to a Log Analytics workspace and ask an engineer to review the AzureDiagnostics table weekly
- [ ] Enable purge protection and soft delete on every vault to detect and reverse malicious deletions
- [ ] Enable the Microsoft Defender for Key Vault plan on the subscriptions so that machine-learning-based anomaly detections generate security alerts in Microsoft Defender for Cloud

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable the Microsoft Defender for Key Vault plan on the subscriptions so that machine-learning-based anomaly detections generate security alerts in Microsoft Defender for Cloud**
</details>

---

## Pregunta 33

*Manage and monitor security posture*

A breach notification reveals that attackers may have been active in your environment 14 months ago. Your Microsoft Sentinel workspace keeps `SecurityEvent` in interactive (analytics) retention for 90 days, with total retention of 2 years — so the relevant records are in long-term (archived) retention. An investigator needs to (1) find events involving a specific compromised account across that archived period and (2) bring several weeks of the archived table back for full interactive KQL investigation. What should the investigator use?

- [ ] Open a Microsoft support ticket, since data in long-term retention can be retrieved only by Microsoft
- [ ] Change the table's interactive retention setting from 90 days to 2 years, which retroactively moves the archived data back into analytics retention
- [ ] Query the archived period directly with a standard KQL query in Log Analytics, since archived data is transparently included in all queries
- [ ] Run a search job scoped to the archived time range to locate the account's events (results land in a new table), then run a restore of the needed weeks of SecurityEvent to make them queryable interactively

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Run a search job scoped to the archived time range to locate the account's events (results land in a new table), then run a restore of the needed weeks of SecurityEvent to make them queryable interactively**
</details>

---

## Pregunta 34

*Secure compute*

An internal line-of-business web app on Azure App Service must meet three requirements:

1. Only signed-in Microsoft Entra ID users may reach the app — unauthenticated requests must be rejected before app code runs.
2. The app must be reachable **only** from the corporate virtual network, never from the public internet.
3. The app's outbound calls to an Azure SQL database must traverse the virtual network.

Which three configurations should you apply? (Select three.)

- [ ] Enable regional virtual network integration on the app for its outbound traffic
- [ ] Create a private endpoint for the app in the corporate virtual network and disable public network access on the app
- [ ] Enable remote debugging so the security team can inspect live requests
- [ ] Enable FTP deployment with a strong deployment password
- [ ] Enable App Service built-in authentication (Easy Auth) with Microsoft Entra ID as the identity provider, set to require authentication
- [ ] Migrate the app to an App Service Environment, because private inbound access is impossible on multi-tenant App Service

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable App Service built-in authentication (Easy Auth) with Microsoft Entra ID as the identity provider, set to require authentication**

✅ **Create a private endpoint for the app in the corporate virtual network and disable public network access on the app**
</details>

---

## Pregunta 35

*Manage identity, access, and governance*

Administrators in your tenant activate their eligible Microsoft Entra roles through Privileged Identity Management (PIM). Security requires that the _moment of activation_ — not everyday sign-in — is protected by phishing-resistant MFA and only allowed from compliant devices, without imposing those controls on the administrators' routine, non-privileged work. What should you configure?

- [ ] Configure Identity Protection to block all sign-ins by administrators when sign-in risk is anything other than low
- [ ] Create a Conditional Access authentication context, build a Conditional Access policy targeting that context which requires the phishing-resistant MFA authentication strength and a compliant device, and configure the PIM role settings to require the authentication context on activation
- [ ] Enable the 'Require multifactor authentication on activation' option in each role's PIM settings
- [ ] Create a Conditional Access policy that targets all cloud apps for the administrators and requires phishing-resistant MFA and a compliant device at every sign-in

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create a Conditional Access authentication context, build a Conditional Access policy targeting that context which requires the phishing-resistant MFA authentication strength and a compliant device, and configure the PIM role settings to require the authentication context on activation**
</details>

---

## Pregunta 36

*Manage identity, access, and governance*

**Veynhart Robotics** designs warehouse automation robots and runs its control-plane services in Azure across a Development and a Production subscription in one Microsoft Entra ID tenant.

**Current Environment:**

- Infrastructure is deployed with Bicep templates from an internal deployment pipeline. Several parameter files in the repository contain plaintext SQL connection strings and third-party API keys; two of them were flagged during a recent code audit.
- Many resources — including key vaults and SQL logical servers — were created by different teams over three years. An internal review found that resource logs are enabled on some resources and missing on others, and nobody notices when a new resource is created without them.
- A fleet-diagnostics team occasionally needs to read secrets from the vault `kv-veyn-fleet` during live incident bridges. Today, six engineers hold a permanent Key Vault Secrets User assignment on the vault even though such incidents occur roughly once a month.
- The team that reviews access complains that the six engineers appear in every quarterly review even though most have never actually used the access.

You need to fix Veynhart Robotics' deployment pipeline so that secret values never appear in Bicep templates, parameter files, or deployment history, and are obtained from an approved vault only at deployment time. What should you do?

- [ ] Move the plaintext values from the parameter files into pipeline variable groups, and echo them into the template parameters as ordinary strings during the run
- [ ] Store the secrets as tags on the target resource group so the templates can read them with the resourceGroup() function
- [ ] Encrypt the parameter files with a symmetric key before committing them, and have the pipeline decrypt them just before deployment
- [ ] Declare the sensitive template parameters with the @secure() decorator and populate them at deployment time from Azure Key Vault references (the vault must have the 'Azure Resource Manager for template deployment' access setting enabled), removing all plaintext values from the repository

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Declare the sensitive template parameters with the @secure() decorator and populate them at deployment time from Azure Key Vault references (the vault must have the 'Azure Resource Manager for template deployment' access setting enabled), removing all plaintext values from the repository**
</details>

---

## Pregunta 37

*Secure storage, databases, and networking*

**Tallowfen Grocers** operates a chain of supermarkets and runs a wholesale marketplace in Azure that also serves several independent retail partners.

**Current Environment:**

- Marketplace document exports for all retail partners land in one general-purpose v2 storage account, with one blob container per partner. The storage account currently uses Microsoft-managed keys for encryption at rest.
- The loyalty platform uses an Azure SQL database. Applications and analysts connect with SQL logins whose passwords are stored in various configuration files; the same `sqladmin` password has been shared among three teams for years.
- Product-catalog and basket data for the e-commerce site is stored in an Azure Cosmos DB for NoSQL account. All services access it with the account's primary read-write key, which has never been rotated because nobody knows what would break.
- A recent partner-facing security questionnaire asked whether each partner's data could be encrypted with a key dedicated to that partner, and whether Tallowfen could stop reading a specific partner's data on request. Tallowfen could not answer yes.

You need to meet Tallowfen Grocers' partner data encryption requirements: each partner's container in the shared storage account encrypted with a different customer-managed key, per-partner key revocation that affects only that partner, and new blobs in a container forced to use that partner's key. What should you configure?

- [ ] Configure the storage account with a single customer-managed key in the key vault and use Azure RBAC to keep the partners' containers separated
- [ ] Create one encryption scope per partner, each backed by a customer-managed key in Tallowfen's key vault; set each scope as the default encryption scope on that partner's container and enable the container setting that denies encryption-scope overrides on upload
- [ ] Require each partner's uploads to supply a customer-provided key (CPK) in the request headers, and have partners send their key with every read and write operation
- [ ] You need to meet Tallowfen Grocers' partner data encryption requirements: each partner's container in the
- [ ] Enable infrastructure (double) encryption on the storage account so that each container automatically receives its own key hierarchy

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create one encryption scope per partner, each backed by a customer-managed key in Tallowfen's key vault; set each scope as the default encryption scope on that partner's container and enable the container setting that denies encryption-scope overrides on upload**
</details>

---

## Pregunta 38

*Manage identity, access, and governance*

**Vellmore Financial Group** is a digital-first retail bank operating in three countries. The company runs its customer-facing banking platform in Azure across two subscriptions (Production and Development) under a single Microsoft Entra ID tenant.

**Current Environment:**

- 14 administrators currently hold permanent Owner or Contributor role assignments on the Production subscription.
- Users sign in with passwords only; a recent internal audit flagged the absence of multifactor authentication for privileged accounts.
- The platform's microservices authenticate to Azure SQL Database and Azure Key Vault by using connection strings and client secrets stored in application configuration files.
- Several third-party SaaS applications have been granted tenant-wide delegated permissions by individual users.

You are designing the Conditional Access policies for Vellmore Financial Group's authentication requirements: phishing-resistant MFA for privileged users, geographic blocking for management endpoints, and automatic response to risky sign-ins. Which combination of policy controls should you use?
The Chief Information Security Officer has defined the following requirements:

**Privileged Access:**

- Administrative roles must be activated only when needed, for a maximum of 4 hours, and activation of the Owner role must be approved by a designated approver.
- All role activations must require justification and be auditable.

**Authentication and Access:**

- All privileged users must use phishing-resistant multifactor authentication.
- Access to the Azure portal and management endpoints must be blocked from countries where Vellmore has no employees.
- Sign-in risk detected by Microsoft Entra ID Protection must trigger additional controls automatically.

**Application Identity:**

- Application code must not contain any stored credentials or secrets.
- Users must no longer be able to consent to third-party applications on their own; consent must be routed through an administrator review process.

You are designing the Conditional Access policies for Vellmore Financial Group's authentication requirements: phishing-resistant MFA for privileged users, geographic blocking for management endpoints, and automatic response to risky sign-ins. Which combination of policy controls should you use?

- [ ] An authentication strength requiring FIDO2 or certificate-based authentication for directory role members; a policy blocking access to the Windows Azure Service Management API / Microsoft Admin Portals from countries outside named locations; and a risk-based policy using sign-in risk as a condition
- [ ] Security defaults enabled for the tenant, combined with a self-service password reset policy for privileged users
- [ ] Per-user MFA enabled on the 14 administrator accounts; an NSG rule blocking foreign IP ranges; and Microsoft Entra ID Protection set to notify administrators by email
- [ ] A policy requiring any MFA method for all users; a policy blocking all access from anonymous IP addresses; and a policy requiring password change every 30 days

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **An authentication strength requiring FIDO2 or certificate-based authentication for directory role members; a policy blocking access to the Windows Azure Service Management API / Microsoft Admin Portals from countries outside named locations; and a risk-based policy using sign-in risk as a condition**
</details>

---

## Pregunta 39

*Secure compute*

Business units build Copilot Studio agents that use connectors to reach business data. A security review of one HR agent finds that: it answers unauthenticated callers on its public demo channel; makers could add any connector they liked, including personal cloud-storage connectors, without approval; and nobody can say which knowledge sources its answers draw from. You must ensure agents authenticate end users with Microsoft Entra ID, makers can only use approved connectors, and the agent's knowledge sources are reviewed and constrained. What should you do?

- [ ] Configure the agent's authentication setting to require Microsoft Entra ID sign-in for end users, apply Power Platform data loss prevention (DLP) policies to the environment to allow only approved connectors, and review and restrict the agent's configured knowledge sources in Copilot Studio
- [ ] Move all Copilot Studio agents into the default Power Platform environment, where Microsoft's baseline security settings cannot be modified by makers
- [ ] Publish the agent only to the Teams channel, since Teams-published agents cannot access connectors or external knowledge sources
- [ ] Enable the Microsoft Defender integration for Copilot Studio, which automatically enforces user authentication and removes unapproved connectors from existing agents

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Configure the agent's authentication setting to require Microsoft Entra ID sign-in for end users, apply Power Platform data loss prevention (DLP) policies to the environment to allow only approved connectors, and review and restrict the agent's configured knowledge sources in Copilot Studio**
</details>

---

## Pregunta 40

*Manage and monitor security posture*

Microsoft Defender for Cloud shows hundreds of open recommendations across your subscriptions, and remediation has stalled because no one owns anything. Management wants each new recommendation automatically assigned to the owner defined in the affected resource's `owner` tag, with a remediation due date, automatic email reminders, and a grace period so the finding does not degrade the secure score before the due date passes. What should you configure?

- [ ] A Microsoft Sentinel analytics rule on the recommendations data that creates an incident per recommendation and assigns it round-robin to SOC analysts
- [ ] Governance rules in Defender for Cloud that set the owner from the resource tag, define the remediation timeframe, enable email notifications, and apply a grace period
- [ ] Disabling the noisy recommendations in the environment settings until teams have capacity to remediate them
- [ ] Workflow automation that triggers a Logic App on every recommendation to create a ticket, and Azure Policy exemptions to keep findings out of the secure score

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Governance rules in Defender for Cloud that set the owner from the resource tag, define the remediation timeframe, enable email notifications, and apply a grace period**
</details>

---

## Pregunta 41

*Manage identity, access, and governance*

Your organization wants to move its workforce to passwordless sign-in for Microsoft Entra ID. Frontline workers share kiosk devices, while engineers have dedicated Windows laptops with TPM chips. Which combination of authentication methods best fits, while remaining phishing-resistant?

- [ ] SMS one-time passcodes for frontline workers, and voice call approval for engineers
- [ ] FIDO2 security keys (or device-bound passkeys) for frontline workers on shared kiosks, and Windows Hello for Business for engineers on their dedicated laptops
- [ ] Windows Hello for Business for the shared kiosks, and email one-time passcodes for engineers
- [ ] Microsoft Authenticator push notifications with number matching for both groups, because push approval is phishing-resistant

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **FIDO2 security keys (or device-bound passkeys) for frontline workers on shared kiosks, and Windows Hello for Business for engineers on their dedicated laptops**
</details>

---

## Pregunta 42

*Secure compute*

An audit of your tenant's Microsoft Entra Agent ID inventory finds 240 registered AI agents. Dozens have no identifiable owner, several belong to employees who left the company, and some hold Graph permissions (such as reading all mail) far beyond what their function needs. You must bring agent identities under lifecycle governance: every agent must have an accountable human owner, agents must hold least-privilege permissions, and agents that are orphaned or no longer used must be found and disabled on a recurring basis — not as a one-time cleanup. What should you implement?

- [ ] Govern the agents through Entra Agent ID: enforce owner assignment for every agent identity, review and trim each agent's permission grants to least privilege, and set up recurring access reviews/inventory checks that flag orphaned or inactive agents for disablement
- [ ] Create a Conditional Access policy that blocks all agent identities from signing in until each agent's owner re-registers it
- [ ] Rotate the credentials of all 240 agents, since agents with fresh credentials are by definition actively maintained
- [ ] Export the agent list to a spreadsheet annually and email department heads asking them to claim their agents

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Govern the agents through Entra Agent ID: enforce owner assignment for every agent identity, review and trim each agent's permission grants to least privilege, and set up recurring access reviews/inventory checks that flag orphaned or inactive agents for disablement**
</details>

---

## Pregunta 43

*Secure compute*

A new fleet of Generation 2 Azure VMs must be hardened against boot-level threats. Requirements:

- Only cryptographically signed, trusted boot loaders and OS kernels may execute — rootkits and boot kits must be blocked at start-up.
- Boot measurements must be captured in a hardware-backed module and remotely attested, with failed boot-integrity checks surfaced as Defender for Cloud recommendations.
- No requirement exists to encrypt data **in use** or to shield the VM's memory from the host.

Which VM security configuration should you choose?

- [ ] Security type Confidential VM, because only hardware-based trusted execution environments can validate the boot chain
- [ ] Standard security type with Microsoft Defender for Endpoint deployed via Defender for Servers, which blocks unsigned kernels from loading
- [ ] Security type Trusted Launch, with secure boot and vTPM enabled, plus the integrity monitoring (guest attestation) feature
- [ ] Standard security type with Azure Disk Encryption on the OS disk, since an encrypted OS disk cannot be tampered with at boot

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Security type Trusted Launch, with secure boot and vTPM enabled, plus the integrity monitoring (guest attestation) feature**
</details>

---

## Pregunta 44

*Question 1*

Manage identity, access, and governance

**Vellmore Financial Group** is a digital-first retail bank operating in three countries. The company runs its customer-facing banking platform in Azure across two subscriptions (Production and Development) under a single Microsoft Entra ID tenant.

**Current Environment:**

- 14 administrators currently hold permanent Owner or Contributor role assignments on the Production subscription.
- Users sign in with passwords only; a recent internal audit flagged the absence of multifactor authentication for privileged accounts.
- The platform's microservices authenticate to Azure SQL Database and Azure Key Vault by using connection strings and client secrets stored in application configuration files.
- Several third-party SaaS applications have been granted tenant-wide delegated permissions by individual users.

You need to redesign privileged access for Vellmore Financial Group's Production subscription to meet the privileged access requirements. What should you configure in Microsoft Entra Privileged Identity Management (PIM)?

The Chief Information Security Officer has defined the following requirements:

**Privileged Access:**

- Administrative roles must be activated only when needed, for a maximum of 4 hours, and activation of the Owner role must be approved by a designated approver.
- All role activations must require justification and be auditable.

**Authentication and Access:**

- All privileged users must use phishing-resistant multifactor authentication.
- Access to the Azure portal and management endpoints must be blocked from countries where Vellmore has no employees.
- Sign-in risk detected by Microsoft Entra ID Protection must trigger additional controls automatically.

**Application Identity:**

- Application code must not contain any stored credentials or secrets.
- Users must no longer be able to consent to third-party applications on their own; consent must be routed through an administrator review process.

You need to redesign privileged access for Vellmore Financial Group's Production subscription to meet the privileged access requirements. What should you configure in Microsoft Entra Privileged Identity Management (PIM)?

- [ ] Move the 14 administrators into a security group and assign the group the Owner role permanently with a resource lock on the subscription
- [ ] Create a Conditional Access policy that requires the administrators to reauthenticate every 4 hours
- [ ] Convert the 14 administrators to eligible assignments, set a 4-hour maximum activation duration, and require approval for Owner role activation
- [ ] Keep the permanent assignments and create an access review that recertifies the 14 administrators every 90 days

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Convert the 14 administrators to eligible assignments, set a 4-hour maximum activation duration, and require approval for Owner role activation**
</details>

---

## Pregunta 45

*Secure compute*

Multiple development teams call the same Microsoft Foundry model deployments. Platform security requires per-team token quotas so one team cannot exhaust capacity, centralized logging of LLM usage for auditing, and that raw model API keys are never handed to the teams. What should you implement?

- [ ] Deploy AI Gateway capabilities in Azure API Management in front of the model deployments: apply token-limit and token-metric policies per team subscription, and let API Management authenticate to the backend with its managed identity
- [ ] Create a separate Foundry project and model deployment for every team and reconcile usage from monthly billing exports
- [ ] Distribute the model deployment's API keys to each team and ask them to log their own usage to a shared workspace
- [ ] Place Azure Front Door with a WAF policy in front of the model endpoints and use rate limiting by client IP address

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Deploy AI Gateway capabilities in Azure API Management in front of the model deployments: apply token-limit and token-metric policies per team subscription, and let API Management authenticate to the backend with its managed identity**
</details>

---

## Pregunta 46

*Secure storage, databases, and networking*

**Harrowfield Logistics** is an international freight and shipping company. Its Azure footprint uses a hub-and-spoke topology: a hub virtual network (`vnet-hub`) and three spoke virtual networks (`vnet-tracking`, `vnet-billing`, `vnet-analytics`) peered to the hub.

**Current Environment:**

- Each spoke hosts VMs and App Service apps for a business unit; outbound internet traffic currently leaves directly from each spoke.
- The billing application in `vnet-billing` calls an Azure SQL Database and an Azure Storage account over their public endpoints.
- Warehouse staff at 40 depots access an internal shipment-tracking web app through a legacy site-to-site VPN into the hub.
- Remote administrators connect to VMs by using public IP addresses with RDP restricted by source IP in NSG rules.

You need to design the central traffic inspection point for Harrowfield Logistics so that all spoke outbound internet traffic is filtered by FQDN and threat intelligence, and east-west traffic between spokes is deny-by-default. What should you deploy and configure?

- [ ] Deploy Azure Firewall Premium in vnet-hub, add user-defined routes (0.0.0.0/0 and spoke-to-spoke prefixes) on the spoke subnets pointing to the firewall's private IP, and use application rules with threat intelligence in deny mode for undefined traffic
- [ ] Deploy Azure Application Gateway with WAF in each spoke and configure path-based routing rules to filter outbound traffic
- [ ] Deploy an NSG in the hub with a deny-all outbound rule, and enable VNet peering with gateway transit between the spokes
- [ ] Deploy Azure DDoS Network Protection on all four virtual networks and enable Network Watcher flow logs

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Deploy Azure Firewall Premium in vnet-hub, add user-defined routes (0.0.0.0/0 and spoke-to-spoke prefixes) on the spoke subnets pointing to the firewall's private IP, and use application rules with threat intelligence in deny mode for undefined traffic**
</details>

---

## Pregunta 47

*Manage and monitor security posture*

Application owners refuse to allow any new agent or VM extension on several hundred production Azure VMs, yet security requires vulnerability assessment and software inventory for all of them, with findings in Microsoft Defender for Cloud and zero impact on VM performance. Which capability meets the requirement?

- [ ] Deploy the Microsoft Defender for Endpoint sensor to each VM through the Defender for Servers integration, since it is a lightweight component rather than a full agent
- [ ] Enable Azure Network Watcher on the virtual networks, which probes each VM over the network to detect vulnerable software versions
- [ ] Agentless machine scanning (available with Defender CSPM or Defender for Servers Plan 2), which analyzes snapshots of the VM disks out-of-band and surfaces vulnerability and inventory findings powered by Microsoft Defender Vulnerability Management
- [ ] Run an authenticated scan from a third-party scanner appliance using stored local administrator credentials for each VM

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Agentless machine scanning (available with Defender CSPM or Defender for Servers Plan 2), which analyzes snapshots of the VM disks out-of-band and surfaces vulnerability and inventory findings powered by Microsoft Defender Vulnerability Management**
</details>

---

## Pregunta 48

*Secure compute*

A customer-support agent built in Microsoft Foundry retrieves answers from a knowledge base of uploaded documents. A red-team exercise showed that a malicious document containing hidden instructions could hijack the agent's behavior (an indirect prompt-injection attack). You must harden the agent against both direct jailbreak attempts and instructions embedded in retrieved content. What should you do?

- [ ] Lower the model deployment's temperature setting so the agent behaves more deterministically
- [ ] Run the agent under an identity with Owner rights on the subscription so failed permission checks cannot disrupt its workflow
- [ ] Configure guardrails on the agent's model deployment: apply content filters that include Prompt Shields for both jailbreak (user prompt) and indirect (document-borne) attacks, and restrict the agent to approved tools and knowledge sources
- [ ] Strengthen the agent's system prompt with an instruction to ignore any commands found inside retrieved documents

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Configure guardrails on the agent's model deployment: apply content filters that include Prompt Shields for both jailbreak (user prompt) and indirect (document-borne) attacks, and restrict the agent to approved tools and knowledge sources**
</details>

---

## Pregunta 49

*Manage and monitor security posture*

Your CISO wants to know which combinations of weaknesses an attacker could actually chain together — for example, an internet-exposed VM with a critical vulnerability whose managed identity can reach a storage account containing sensitive data. The team is drowning in individual recommendations and needs the exploitable chains prioritized. Which Defender for Cloud capability should you use?

- [ ] Enable Defender for Servers and wait for security alerts on the exposed VMs
- [ ] Export the secure score to a spreadsheet and review the lowest-scoring controls each week
- [ ] Enable the Defender CSPM plan and review attack path analysis, using the cloud security explorer for custom risk queries across the environment
- [ ] Sort the recommendations list by severity and remediate all high-severity items first

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable the Defender CSPM plan and review attack path analysis, using the cloud security explorer for custom risk queries across the environment**
</details>

---

## Pregunta 50

*Secure compute*

Your teams run generative AI applications on model deployments in Microsoft Foundry (Azure AI services). The SOC needs threat protection for these AI workloads: detection of prompt-injection and jailbreak attempts, alerts that include enough context to investigate, and a single place to monitor AI security posture and findings. Which three actions should you take? (Select three.)

*Nota: Selecciona todas las opciones que apliquen.*

- [ ] Enable the Defender for AI Services plan under cloud workload protection on each subscription that hosts the model deployments
- [ ] Enable user prompt evidence so that relevant prompt and response snippets are included in the alerts for investigation
- [ ] Monitor findings and posture in the Data and AI security dashboard in Defender for Cloud
- [ ] Install the Azure Monitor Agent on the Foundry model endpoints to capture prompt traffic
- [ ] Enable Defender for Servers Plan 2 so its EDR component can inspect the model's prompts
- [ ] Turn off the deployments' content filters so Defender receives unmodified traffic to analyze

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable the Defender for AI Services plan under cloud workload protection on each subscription that hosts the model deployments**

✅ **Enable user prompt evidence so that relevant prompt and response snippets are included in the alerts for investigation**

✅ **Monitor findings and posture in the Data and AI security dashboard in Defender for Cloud**
</details>

---

## Pregunta 51

*Manage and monitor security posture*

**Bellcairn Utilities** operates water treatment and distribution infrastructure. Its security operations team runs Microsoft Defender for Cloud across three Azure subscriptions and a Microsoft Sentinel workspace, and the company also keeps an on-premises Splunk deployment that the industrial-control (OT) team refuses to give up.

**Current Environment:**

- A contractor recently found a PDF on a build server containing a service-account password, which prompted the CISO to ask, "How many other credentials are lying around in files on our machines, and what could an attacker reach with them?" Nobody could answer.
- About 40 Linux VMs run the telemetry ingestion tier. Their authentication and sudo activity is written to the local syslog daemon. None of it reaches the SOC today.
- The Sentinel workspace generates Defender for Cloud security alerts and recommendations, but the OT team's on-call rotation works exclusively out of Splunk dashboards and refuses to monitor a second console.
- Defender for Cloud plans (Defender CSPM and Defender for Servers Plan 2) are already enabled on all three subscriptions.

You need to answer the Bellcairn Utilities CISO's question: discover plaintext credentials (passwords, SSH keys, connection strings) in files on Azure VMs and multicloud machines without installing any additional agent, and see which discovered credentials enable lateral movement, prioritized by attack path. Which capability should you use?

The agentless secrets scanning capability included with Defender CSPM (and Defender for Servers Plan 2), reviewing the secrets-related recommendations and the attack paths that show where each exposed credential could lead

- [ ] A custom osquery package distributed by Azure Machine Configuration that greps the file systems for password patterns and writes matches to a Log Analytics workspace
- [ ] Microsoft Purview Information Protection scanner deployed to each subscription to classify files that contain the 'Credentials' sensitive information type
- [ ] Microsoft Defender for Key Vault, which detects credentials that exist outside of a managed vault

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Microsoft Purview Information Protection scanner deployed to each subscription to classify files that contain the 'Credentials' sensitive information type**
</details>

---

## Pregunta 52

*Secure compute*

Employees across your organization have started acquiring Copilot agents from various sources — some built in-house, some from the store — and IT has no picture of what is deployed. Governance requires a central place to see the agents available in the organization, decide which agents are approved for use, block specific agents entirely, and control which users or groups can access a given agent. Where should this be administered?

- [ ] In Microsoft Defender for Cloud Apps, mark the agents as unsanctioned so that Defender for Endpoint blocks their network traffic
- [ ] In the Microsoft 365 admin center, use the integrated apps / agent management experience to inventory agents, approve or block individual agents, and scope each agent's deployment to specific users and groups
- [ ] In each user's Copilot settings, ask employees to remove agents that are not on the published approved list
- [ ] In the Microsoft Entra admin center, delete the service principals of any agent the organization has not approved

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **In the Microsoft 365 admin center, use the integrated apps / agent management experience to inventory agents, approve or block individual agents, and scope each agent's deployment to specific users and groups**
</details>

---

## Pregunta 53

*Secure storage, databases, and networking*

Your compliance team requires that an Azure SQL Managed Instance capture an audit trail of database events, retain it for regulatory review, and additionally record the queries executed by Microsoft support engineers if they ever access the instance during a support case. How should you configure auditing?

- [ ] Install a third-party database activity monitoring agent on the managed instance's host, since managed instances do not support native auditing
- [ ] Create a server audit and audit specifications on the managed instance with T-SQL, targeting an Azure Storage account (or Event Hubs/Log Analytics), and additionally enable auditing of Microsoft support operations
- [ ] Enable the database-level auditing toggle in the Azure portal for each database on the managed instance, exactly as you would for Azure SQL Database
- [ ] Enable SQL Insights on the managed instance, since performance telemetry includes the text of all executed queries

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create a server audit and audit specifications on the managed instance with T-SQL, targeting an Azure Storage account (or Event Hubs/Log Analytics), and additionally enable auditing of Microsoft support operations**
</details>

---

## Pregunta 54

*Question 1*

Manage identity, access, and governance

**Orenfall Energy** is a regional electricity utility that runs its grid-telemetry ingestion platform and customer-billing systems in Azure. The company uses two subscriptions (Platform and Corporate) under a single Microsoft Entra ID tenant.

**Current Environment:**

- The platform operations team holds the Contributor role on the Platform subscription, although its day-to-day work is limited to starting, stopping, restarting, and viewing the telemetry-ingestion virtual machines.
- Customer-billing data is encrypted with customer-managed keys stored in an Azure key vault named `kv-orenfall-billing`. Key rotation is performed manually by an engineer roughly twice a year, and it has been missed twice.
- TLS certificates for the SCADA gateway endpoints are stored in the same vault; one certificate expired unnoticed last quarter and caused a four-hour telemetry outage.
- External engineering contractors from a partner firm are onboarded by emailing the service desk, which manually adds them to various groups and applications. Offboarding is inconsistent, and several contractor accounts from a project that ended last year still have access.

You need to give Orenfall Energy's platform operations team exactly the permissions defined in the role-based access control requirements: start, stop, restart, and read the telemetry virtual machines — assignable in both subscriptions but nowhere else in the tenant. What should you do?

- [ ] Create a custom Microsoft Entra ID directory role that grants virtual machine power management permissions and assign it to the team
- [ ] Assign the built-in Virtual Machine Contributor role to the team at the Platform subscription scope
- [ ] Create a custom Azure role whose Actions include Microsoft.Compute/virtualMachines/read, start/action, restart/action, powerOff/action, and deallocate/action, set assignableScopes to the Platform and Corporate subscriptions, and assign it to the team at the resource group holding the telemetry VMs
- [ ] Create a custom Azure role with assignableScopes set to the root management group so it can be reused by any future subscription
- [ ] Keep the Contributor assignment but apply a ReadOnly resource lock to every resource the team must not change

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create a custom Azure role whose Actions include Microsoft.Compute/virtualMachines/read, start/action, restart/action, powerOff/action, and deallocate/action, set assignableScopes to the Platform and Corporate subscriptions, and assign it to the team at the resource group holding the telemetry VMs**
</details>

---

## Pregunta 55

*Secure storage, databases, and networking*

**Brindlecote Manufacturing** produces industrial packaging equipment at six plants. Its Azure estate has grown organically to about 30 virtual networks across five subscriptions, each managed by a different application team.

**Current Environment:**

- Every application team creates and edits its own network security groups (NSGs). Last year an application team deleted an NSG rule that blocked inbound internet traffic to management ports, exposing several VMs for two weeks before it was noticed.
- A machine-telemetry API used by an external analytics partner is currently published on a public IP address protected only by an IP allowlist.
- The partner's Azure environment uses address spaces that overlap with Brindlecote's, so virtual network peering has already been ruled out.
- Field service engineers connect remotely through a legacy SSL VPN appliance that uses a shared credential stored in a team wiki.

You need to design the partner connectivity for Brindlecote Manufacturing's telemetry API: private consumption without VNet peering, unaffected by overlapping IP address spaces, initiated by the partner and approved by Brindlecote, with no new inbound public endpoint. What should you implement?

- [ ] Publish the API through Azure Front Door with a web application firewall policy and restrict access to the partner's egress IP addresses
- [ ] Establish a site-to-site VPN between the two companies and publish the API's private IP address to the partner
- [ ] Create a private endpoint in Brindlecote's virtual network that points to the partner's analytics platform
- [ ] Place the API behind an internal Standard Load Balancer, create an Azure Private Link service on it, and have the partner create a private endpoint in their own virtual network that Brindlecote approves

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Place the API behind an internal Standard Load Balancer, create an Azure Private Link service on it, and have the partner create a private endpoint in their own virtual network that Brindlecote approves**
</details>

---

## Pregunta 56

*Manage and monitor security posture*

You must stream Windows Security events from Azure VMs and Azure Arc-enabled on-premises servers into Microsoft Sentinel. To control ingestion cost, only a specific set of security event IDs may be collected. Which approach should you use?

- [ ] Use the Windows Security Events via AMA connector and create a data collection rule with a Custom event set that filters to the required event IDs using XPath queries
- [ ] Install the legacy Log Analytics (MMA) agent on all machines and select the Minimal tier in the workspace settings
- [ ] Use the Syslog via AMA connector with a data collection rule scoped to the Security facility
- [ ] Use the Windows Security Events via AMA connector with the All security events set, then delete unneeded records from the workspace nightly

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Use the Windows Security Events via AMA connector and create a data collection rule with a Custom event set that filters to the required event IDs using XPath queries**
</details>

---

## Pregunta 57

*Manage identity, access, and governance*

**Orenfall Energy** is a regional electricity utility that runs its grid-telemetry ingestion platform and customer-billing systems in Azure. The company uses two subscriptions (Platform and Corporate) under a single Microsoft Entra ID tenant.

**Current Environment:**

- The platform operations team holds the Contributor role on the Platform subscription, although its day-to-day work is limited to starting, stopping, restarting, and viewing the telemetry-ingestion virtual machines.
- Customer-billing data is encrypted with customer-managed keys stored in an Azure key vault named `kv-orenfall-billing`. Key rotation is performed manually by an engineer roughly twice a year, and it has been missed twice.
- TLS certificates for the SCADA gateway endpoints are stored in the same vault; one certificate expired unnoticed last quarter and caused a four-hour telemetry outage.
- External engineering contractors from a partner firm are onboarded by emailing the service desk, which manually adds them to various groups and applications. Offboarding is inconsistent, and several contractor accounts from a project that ended last year still have access.

You need to meet Orenfall Energy's key and certificate lifecycle requirements for `kv-orenfall-billing`: automatic 90-day rotation of the customer-managed keys with no application changes, and automated notification 30 days before any certificate expires. What should you configure?

- [ ] Convert the keys to secrets with a 90-day expiration date, because only secrets support expiry metadata and automatic renewal
- [ ] Enable soft delete and purge protection on the vault so that keys and certificates are refreshed automatically by the platform
- [ ] Set a key rotation policy on each key that creates a new key version every 90 days, and create an Event Grid subscription on the vault that routes the CertificateNearExpiry event to a notification workflow
- [ ] Create an Azure Automation runbook that exports each key, generates a replacement offline, and re-imports it every 90 days, and have the runbook also email a certificate inventory monthly

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Set a key rotation policy on each key that creates a new key version every 90 days, and create an Event Grid subscription on the vault that routes the CertificateNearExpiry event to a notification workflow**
</details>

---

## Pregunta 58

*Secure compute*

Microsoft Security Copilot is already provisioned in your tenant — capacity is purchased, workspaces exist, and analyst roles are assigned. The SOC now wants to hand off the triage of user-reported phishing emails to an autonomous capability that processes each submission, explains its verdict, and improves from analyst feedback; the team also wants to evaluate similar prepackaged capabilities from Microsoft partners. What should you do?

- [ ] Purchase additional Security Compute Units, since higher SCU capacity unlocks the autonomous triage features in every Copilot workspace
- [ ] Enable and configure the Microsoft Phishing Triage Agent in Security Copilot, and browse the Microsoft Security Store to install vetted partner-built agents — reviewing each agent's identity and permissions before deployment
- [ ] Author a promptbook that chains the prompts an analyst would run for a phishing investigation, and schedule it to execute against the shared mailbox
- [ ] Build a Microsoft Sentinel automation rule with a Logic Apps playbook that closes phishing incidents whose sender fails DMARC

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable and configure the Microsoft Phishing Triage Agent in Security Copilot, and browse the Microsoft Security Store to install vetted partner-built agents — reviewing each agent's identity and permissions before deployment**
</details>

---

## Pregunta 59

*Secure storage, databases, and networking*

**Harrowfield Logistics** is an international freight and shipping company. Its Azure footprint uses a hub-and-spoke topology: a hub virtual network (`vnet-hub`) and three spoke virtual networks (`vnet-tracking`, `vnet-billing`, `vnet-analytics`) peered to the hub.

**Current Environment:**

- Each spoke hosts VMs and App Service apps for a business unit; outbound internet traffic currently leaves directly from each spoke.
- The billing application in `vnet-billing` calls an Azure SQL Database and an Azure Storage account over their public endpoints.
- Warehouse staff at 40 depots access an internal shipment-tracking web app through a legacy site-to-site VPN into the hub.
- Remote administrators connect to VMs by using public IP addresses with RDP restricted by source IP in NSG rules.

You need to modernize remote access for Harrowfield Logistics: depot staff need Zero Trust, per-application access to the internal shipment-tracking app without being placed on the network, and administrators must reach VMs without any public IPs on the VMs. Which pair of solutions should you choose?

- [ ] Point-to-site VPN with certificate authentication for depot staff, and public IPs with just-in-time VM access for administrators
- [ ] Azure Front Door for depot staff, and a jump-box VM with a public IP protected by an NSG for administrators
- [ ] Microsoft Entra Private Access for depot staff, and Azure Bastion for VM administration
- [ ] A larger site-to-site VPN gateway for depot staff, and RDP through Azure Firewall DNAT rules for administrators

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Microsoft Entra Private Access for depot staff, and Azure Bastion for VM administration**
</details>

---

## Pregunta 60

*Manage and monitor security posture*

Thousands of domain-joined Windows servers already forward their Security events over Windows Event Forwarding (WEF) to a small set of Windows Event Collector servers. The SOC must ingest these events into Microsoft Sentinel while keeping the existing WEF infrastructure and **without** deploying anything to the thousands of source servers. What should you implement?

- [ ] Configure the collector servers to relay the events as syslog messages to a Linux log forwarder running the Azure Monitor Agent with a CEF data collection rule
- [ ] Enable Windows DNS-over-HTTPS on the collectors so events are pushed directly to the Sentinel workspace endpoint without an agent
- [ ] Install the Azure Monitor Agent on the collector servers only, and use the Windows Forwarded Events connector with a data collection rule that reads events from the collectors' ForwardedEvents channel
- [ ] Deploy the Azure Monitor Agent to every source server via Group Policy and create a data collection rule for the Security event log on each of them

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Install the Azure Monitor Agent on the collector servers only, and use the Windows Forwarded Events connector with a data collection rule that reads events from the collectors' ForwardedEvents channel**
</details>

---

## Pregunta 61

*Secure storage, databases, and networking*

**Tallowfen Grocers** operates a chain of supermarkets and runs a wholesale marketplace in Azure that also serves several independent retail partners.

**Current Environment:**

- Marketplace document exports for all retail partners land in one general-purpose v2 storage account, with one blob container per partner. The storage account currently uses Microsoft-managed keys for encryption at rest.
- The loyalty platform uses an Azure SQL database. Applications and analysts connect with SQL logins whose passwords are stored in various configuration files; the same `sqladmin` password has been shared among three teams for years.
- Product-catalog and basket data for the e-commerce site is stored in an Azure Cosmos DB for NoSQL account. All services access it with the account's primary read-write key, which has never been rotated because nobody knows what would break.
- A recent partner-facing security questionnaire asked whether each partner's data could be encrypted with a key dedicated to that partner, and whether Tallowfen could stop reading a specific partner's data on request. Tallowfen could not answer yes.

You need to meet Tallowfen Grocers' Cosmos DB access requirements: applications authenticate with Microsoft Entra identities holding data-plane permissions scoped to only the containers they use, and after migration the account keys must no longer work at all. What should you do?

- [ ] Assign each application's managed identity the Cosmos DB Operator Azure RBAC role on the account and then rotate the primary and secondary keys
- [ ] Assign each application's managed identity a Cosmos DB data-plane RBAC role (such as Cosmos DB Built-in Data Contributor, or a custom data-plane role) scoped to its specific database or container, migrate the applications to Entra authentication, then disable local (key-based) authentication on the account
- [ ] Move each application's containers into separate Cosmos DB accounts and give each application only its own account's primary key
- [ ] You need to meet Tallowfen Grocers' Cosmos DB access requirements: applications authenticate with M
- [ ] Create one resource token per application using the Cosmos DB resource-token pattern and distribute the tokens through Azure Key Vault

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Assign each application's managed identity a Cosmos DB data-plane RBAC role (such as Cosmos DB Built-in Data Contributor, or a custom data-plane role) scoped to its specific database or container, migrate the applications to Entra authentication, then disable local (key-based) authentication on the account**
</details>

---

## Pregunta 62

*Secure storage, databases, and networking*

An external analytics partner needs read-only access to a single blob container for the next six hours. Security requirements state that:

- The credential must be signed with Microsoft Entra credentials, not with a storage account key.
- You must be able to invalidate the credential before it expires without rotating the storage account keys.

What should you provide?

- [ ] A user delegation SAS scoped to the container with a six-hour expiry; revoke the user delegation key early if the credential must be invalidated
- [ ] A service SAS created ad hoc (without a stored access policy) with read permission on the container
- [ ] An account SAS with read permission on the Blob service and a six-hour expiry

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **A user delegation SAS scoped to the container with a six-hour expiry; revoke the user delegation key early if the credential must be invalidated**
</details>

---

## Pregunta 63

*Manage and monitor security posture*

**Bellcairn Utilities** operates water treatment and distribution infrastructure. Its security operations team runs Microsoft Defender for Cloud across three Azure subscriptions and a Microsoft Sentinel workspace, and the company also keeps an on-premises Splunk deployment that the industrial-control (OT) team refuses to give up.

**Current Environment:**

- A contractor recently found a PDF on a build server containing a service-account password, which prompted the CISO to ask, "How many other credentials are lying around in files on our machines, and what could an attacker reach with them?" Nobody could answer.
- About 40 Linux VMs run the telemetry ingestion tier. Their authentication and sudo activity is written to the local syslog daemon. None of it reaches the SOC today.
- The Sentinel workspace generates Defender for Cloud security alerts and recommendations, but the OT team's on-call rotation works exclusively out of Splunk dashboards and refuses to monitor a second console.
- Defender for Cloud plans (Defender CSPM and Defender for Servers Plan 2) are already enabled on all three subscriptions.

You need to stream new Defender for Cloud security alerts and recommendation state changes continuously to Bellcairn Utilities' on-premises Splunk in near real time — using configuration rather than code — and ensure the security operations manager and subscription owners receive email for high-severity alerts. What should you configure in Microsoft Defender for Cloud?

- [ ] Enable the workflow automation feature with a Logic App that emails the OT team a summary of every alert
- [ ] Configure continuous export to a Log Analytics workspace and have Splunk administrators download the workspace tables as CSV each morning
- [ ] Configure continuous export of security alerts and recommendations to an Azure Event Hub that Splunk consumes through its Azure add-on, and configure email notifications in the environment settings for the manager's address plus the Owner role, filtered to high severity
- [ ] Grant the OT team the Security Reader role and schedule a nightly Azure Logic App that queries the Defender for Cloud REST API and writes the results to a Splunk HTTP endpoint

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Configure continuous export of security alerts and recommendations to an Azure Event Hub that Splunk consumes through its Azure add-on, and configure email notifications in the environment settings for the manager's address plus the Owner role, filtered to high severity**
</details>

---

## Pregunta 64

*Secure storage, databases, and networking*

**Quillstone Retail Group** operates 240 stores and an e-commerce platform hosted in Azure. Customer order data is stored in an Azure SQL Database elastic pool, and product images, invoices, and data exports are kept in two general-purpose v2 storage accounts named `stqsorders` and `stqsmedia`.

**Current Environment:**

- Both storage accounts allow access from all networks and have shared key authorization enabled.
- Partner logistics companies upload delivery manifests to a container in `stqsorders` by using SAS tokens that were generated ad hoc and never expire.
- The Azure SQL logical server allows connections from all Azure services and has no auditing configured.
- A recent incident involved a malware-infected file being uploaded to the `stqsmedia` account by a compromised partner workstation.

Which three configurations should you apply? (Select three.)

- [ ] Enable Microsoft Defender for Azure SQL to get data discovery and classification support plus Advanced Threat Protection alerts for anomalies such as SQL injection and unusual access
- [ ] Configure Azure SQL auditing to send audit logs to a Log Analytics workspace or storage account with at least 180 days of retention
- [ ] Configure geo-replication of the database to a secondary region
- [ ] Apply dynamic data masking to the payment card number column
- [ ] You need to meet Quillstone Retail Group's database security requirements for the order database: 180-day activity capture, classification of sensitive columns with alerting on anomalous access, and preventing administrators from seeing payment card numbers during routine troubleshooting. 
- [ ] Enable transparent data encryption (TDE) with a customer-managed key

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **You need to meet Quillstone Retail Group's database security requirements for the order database: 180-day activity capture, classification of sensitive columns with alerting on anomalous access, and preventing administrators from seeing payment card numbers during routine troubleshooting.

✅ **Configure Azure SQL auditing to send audit logs to a Log Analytics workspace or storage account with at least 180 days of retention**

✅ **Enable Microsoft Defender for Azure SQL to get data discovery and classification support plus Advanced Threat Protection alerts for anomalies such as SQL injection and unusual access**
</details>

---

## Pregunta 65

*Manage identity, access, and governance*

**Vellmore Financial Group** is a digital-first retail bank operating in three countries. The company runs its customer-facing banking platform in Azure across two subscriptions (Production and Development) under a single Microsoft Entra ID tenant.

**Current Environment:**

- 14 administrators currently hold permanent Owner or Contributor role assignments on the Production subscription.
- Users sign in with passwords only; a recent internal audit flagged the absence of multifactor authentication for privileged accounts.
- The platform's microservices authenticate to Azure SQL Database and Azure Key Vault by using connection strings and client secrets stored in application configuration files.
- Several third-party SaaS applications have been granted tenant-wide delegated permissions by individual users.

You need to meet Vellmore Financial Group's application identity requirements: remove stored credentials from the microservices and stop users from consenting to third-party applications on their own. What should you do?

- [ ] Create one app registration with a long-lived client secret shared by all microservices, and require MFA for third-party application sign-ins
- [ ] Store the secrets in Azure Key Vault and grant every developer the Key Vault Secrets Officer role, then block all enterprise applications with Conditional Access
- [ ] Move all connection strings and client secrets into a configuration file encrypted with a customer-managed key, then delete the third-party enterprise applications from the tenant
- [ ] Enable managed identities on the compute resources hosting the microservices, grant those identities RBAC/database roles on Key Vault and Azure SQL, then configure the user consent settings to disable user consent and enable the admin consent workflow

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable managed identities on the compute resources hosting the microservices, grant those identities RBAC/database roles on Key Vault and Azure SQL, then configure the user consent settings to disable user consent and enable the admin consent workflow**
</details>

---

## Pregunta 66

*Secure storage, databases, and networking*

A three-tier application (web, app, database) runs on VMs in one virtual network. VMs are frequently redeployed with new IP addresses. You must enforce that only web-tier VMs reach app-tier VMs on port 443, and only app-tier VMs reach database VMs on port 1433 — **without hardcoding IP addresses in any rule** and with rules that survive VM redeployments. What should you implement?

- [ ] Create application security groups for each tier, associate the VM NICs with their tier's ASG, and write NSG rules that use the ASGs as source and destination
- [ ] Create one network security group per VM and maintain inbound rules listing the current IP address of every permitted peer
- [ ] Deploy Azure Firewall between the tiers and create DNAT rules translating each tier's public IP to the next tier
- [ ] Place each tier in a separate virtual network and rely on the default deny between virtual networks

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create application security groups for each tier, associate the VM NICs with their tier's ASG, and write NSG rules that use the ASGs as source and destination**
</details>

---

## Pregunta 67

*Secure compute*

You must harden an Azure Container Registry that serves an AKS cluster and a set of build agents in a dedicated virtual network. Requirements:

1. No shared, static registry credentials may exist — all pushes and pulls must be tied to Microsoft Entra identities.
2. The registry must not be reachable from the public internet.
3. The AKS cluster must pull images without any password or pull secret being stored in the cluster.

Which three actions should you take? (Select three.)
- [ ] Grant the AKS cluster's kubelet managed identity the AcrPull role on the registry (attach the registry to the cluster)
- [ ] Enable the registry admin user with a long random password, store the password in Azure Key Vault, and rotate it quarterly
- [ ] Disable the registry's admin user and authorize pushes and pulls through Microsoft Entra ID with RBAC roles such as AcrPush for the build identities
- [ ] Disable public network access on the registry and create a private endpoint for it in the virtual network used by the build agents and the cluster
- [ ] Create a Kubernetes image-pull secret containing the registry credentials and reference it from every pod specification
- [ ] Enable anonymous pull access on the registry so the cluster needs no credentials at all

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Disable the registry's admin user and authorize pushes and pulls through Microsoft Entra ID with RBAC roles such as AcrPush for the build identities**

✅ **Disable public network access on the registry and create a private endpoint for it in the virtual network used by the build agents and the cluster**
</details>

---

## Pregunta 68

*Question 1*

Manage identity, access, and governance

**Veynhart Robotics** designs warehouse automation robots and runs its control-plane services in Azure across a Development and a Production subscription in one Microsoft Entra ID tenant.

**Current Environment:**

- Infrastructure is deployed with Bicep templates from an internal deployment pipeline. Several parameter files in the repository contain plaintext SQL connection strings and third-party API keys; two of them were flagged during a recent code audit.
- Many resources — including key vaults and SQL logical servers — were created by different teams over three years. An internal review found that resource logs are enabled on some resources and missing on others, and nobody notices when a new resource is created without them.
- A fleet-diagnostics team occasionally needs to read secrets from the vault `kv-veyn-fleet` during live incident bridges. Today, six engineers hold a permanent Key Vault Secrets User assignment on the vault even though such incidents occur roughly once a month.
- The team that reviews access complains that the six engineers appear in every quarterly review even though most have never actually used the access.

You need to meet Veynhart Robotics' logging compliance requirement: every existing and future key vault and SQL logical server must send resource logs to the central Log Analytics workspace, non-compliant resources must be corrected automatically without human intervention, and compliance must be visible in one place. What should you implement?

- [ ] Assign Azure Policy definitions with the Audit effect and schedule a monthly review of the compliance dashboard so the platform team can fix flagged resources
- [ ] Assign Azure Policy definitions with the DeployIfNotExists effect that configure diagnostic settings targeting the workspace, grant the assignments' managed identities the required roles, and create remediation tasks to correct the existing non-compliant resources
- [ ] Write an Azure Automation runbook that scans all subscriptions nightly and calls the REST API to add missing diagnostic settings
- [ ] Assign Azure Policy definitions with the Deny effect so that key vaults and SQL logical servers cannot be created without diagnostic settings

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Assign Azure Policy definitions with the DeployIfNotExists effect that configure diagnostic settings targeting the workspace, grant the assignments' managed identities the required roles, and create remediation tasks to correct the existing non-compliant resources**
</details>

---

## Pregunta 69

*Manage and monitor security posture*

You are onboarding Microsoft Security Copilot for the SOC. Analysts must be able to run investigations with least privilege, compute spend must be provisioned and controlled by the security platform team, and Copilot must be able to reason over Defender XDR and Microsoft Sentinel data. Which setup is correct?

- [ ] Provision Security Compute Unit (SCU) capacity and attach it to the Security Copilot workspace, grant the platform team the Copilot owner role and analysts the Copilot contributor role via security groups, and enable only the required plugins (such as Defender XDR and Sentinel)
- [ ] Assign every analyst the Global Administrator role, because Security Copilot requires tenant-wide administrative rights to answer questions
- [ ] Enable every available plugin by default and give all users the Copilot owner role so no investigation is ever blocked by a permission error
- [ ] Skip capacity provisioning, since Security Copilot usage is included with existing Defender XDR licenses

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Provision Security Compute Unit (SCU) capacity and attach it to the Security Copilot workspace, grant the platform team the Copilot owner role and analysts the Copilot contributor role via security groups, and enable only the required plugins (such as Defender XDR and Sentinel)**
</details>

---

## Pregunta 70

*Manage and monitor security posture*

Your organization runs 600 Azure VMs and 200 Azure Arc-enabled servers, all onboarded to Microsoft Defender for Endpoint through Defender for Servers Plan 1. The security team now additionally requires: agentless scanning of VM disks for vulnerabilities and installed software, detection of plaintext secrets on machines, file integrity monitoring for critical system files, and the premium capabilities of Microsoft Defender Vulnerability Management (such as certificate assessment and security baseline assessment). What is the most efficient change?

- [ ] Upgrade the subscriptions to Defender for Servers Plan 2, which adds agentless machine scanning, secrets discovery, file integrity monitoring, and the Defender Vulnerability Management premium capabilities on top of Plan 1's EDR
- [ ] Replace Defender for Servers with Azure Machine Configuration policies that audit file hashes and installed software versions
- [ ] Keep Plan 1 and separately purchase Microsoft Defender Vulnerability Management standalone licenses for every server
- [ ] Keep Plan 1 and enable Defender CSPM, which includes file integrity monitoring and endpoint detection and response for servers

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Upgrade the subscriptions to Defender for Servers Plan 2, which adds agentless machine scanning, secrets discovery, file integrity monitoring, and the Defender Vulnerability Management premium capabilities on top of Plan 1's EDR**
</details>

---

## Pregunta 71

*Secure compute*

A retrieval-augmented chat application built on a Microsoft Foundry model deployment already screens **incoming** prompts for injection attacks. Legal review now flags two risks in what the model **returns** to users:

1. Responses might reproduce copyrighted third-party text verbatim.
2. Responses might state "facts" that are not supported by the retrieved source documents.

Which guardrail configuration addresses both risks?

- [ ] In the deployment's content filtering configuration, enable protected material detection and groundedness detection on model outputs
- [ ] Set the model's temperature to zero and reduce the maximum output tokens so the model cannot generate long copied passages
- [ ] Add a custom blocklist containing the titles of known copyrighted works to the deployment's content filter
- [ ] Enable Prompt Shields on the deployment, which validates both user prompts and the documents supplied to the model

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **In the deployment's content filtering configuration, enable protected material detection and groundedness detection on model outputs**
</details>

---

## Pregunta 72

*Manage identity, access, and governance*

After a ransomware tabletop exercise, your organization concludes that a single compromised backup administrator could currently disable soft delete on the Recovery Services vaults, reduce retention, and delete backup data. You must ensure that such destructive operations additionally require authorization controlled by a _separate_ security team that backup administrators cannot influence. What should you implement?

- [ ] Enable multi-user authorization by associating each Recovery Services vault with a Resource Guard that resides in a subscription (or tenant) administered only by the security team, so critical operations require the security team's approval path
- [ ] Increase the soft-delete retention period on the vaults from 14 to 30 days
- [ ] Apply a CanNotDelete resource lock to each Recovery Services vault
- [ ] Require the backup administrators to use PIM to activate their Backup Contributor role with MFA

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable multi-user authorization by associating each Recovery Services vault with a Resource Guard that resides in a subscription (or tenant) administered only by the security team, so critical operations require the security team's approval path**
</details>

---

## Pregunta 73

*Manage and monitor security posture*

After several acquisitions, your security team suspects there are internet-facing assets nobody tracks: forgotten subdomains, servers hosted with third-party providers, expiring TLS certificates, and shadow-IT websites — many of them **outside** your Azure subscriptions. You need continuous discovery and risk assessment of this unknown external footprint. What should you deploy?

- [ ] Use Azure Network Watcher to run IP flow verify and effective security rules diagnostics across the virtual networks
- [ ] Enable Defender CSPM on all Azure subscriptions and review its inventory of internet-exposed resources
- [ ] Create a Microsoft Defender External Attack Surface Management (EASM) resource and seed it with the organization's known domains and hosts so it can discover and inventory related internet-facing assets
- [ ] Add more data connectors to Microsoft Sentinel so logs from all known websites are ingested

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create a Microsoft Defender External Attack Surface Management (EASM) resource and seed it with the organization's known domains and hosts so it can discover and inventory related internet-facing assets**
</details>

---

## Pregunta 74

*Manage and monitor security posture*

Microsoft Defender for Cloud flags the recommendation "Management ports should be closed on your virtual machines" for a set of isolated lab VMs. The lab VMs sit behind a dedicated firewall appliance that already restricts the ports (a compensating control), and the risk owner has accepted the residual risk for these machines only. The finding keeps dragging down the secure score and distracting the operations queue. The recommendation must remain active for every other VM. What should you do?

- [ ] Create an exemption for the recommendation scoped to the lab VMs (or their resource group), select 'Mitigated' as the reason, document the compensating control and an expiration date, and leave the recommendation evaluating everywhere else
- [ ] Move the lab VMs to a subscription that is not onboarded to Defender for Cloud
- [ ] Assign the lab VMs' recommendation to an owner with a due date using governance rules, and extend the due date every quarter
- [ ] Disable the recommendation's underlying policy at the management group so the finding disappears from the portal

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create an exemption for the recommendation scoped to the lab VMs (or their resource group), select 'Mitigated' as the reason, document the compensating control and an expiration date, and leave the recommendation evaluating everywhere else**
</details>

---

## Pregunta 75

*Secure compute*

Engineers have been pasting proprietary source code and customer records into consumer generative-AI websites from their corporate devices. Security must:

1. Discover which AI apps and sites are actually being used across the organization, with risk ratings, and cut off the risky ones.
2. Prevent users on managed devices from pasting or uploading sensitive information into AI websites.
3. Monitor sensitive-data usage in third-party AI site interactions and get recommended one-click policies to reduce the risk.

Which three actions should you take? (Select three.)
- [ ] Use an Intune device configuration profile to disable the clipboard across all browsers on corporate devices
- [ ] Use Microsoft Purview Data Security Posture Management (DSPM) for AI to monitor sensitive data in interactions with third-party AI sites and apply its recommended one-click policies
- [ ] Apply sensitivity labels to every file in SharePoint, because labeled content cannot be typed or pasted into external websites
- [ ] Maintain a static blocklist of AI website FQDNs on the perimeter firewall, updated manually as new sites appear
- [ ] Use cloud app discovery in Microsoft Defender for Cloud Apps to inventory generative-AI app usage with risk scores, and mark risky apps as unsanctioned to block them
- [ ] Create a Microsoft Purview endpoint DLP policy for onboarded devices that blocks pasting and uploading content matching sensitive info types into AI websites in the browser

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Use cloud app discovery in Microsoft Defender for Cloud Apps to inventory generative-AI app usage with risk scores, and mark risky apps as unsanctioned to block them**

✅ **Create a Microsoft Purview endpoint DLP policy for onboarded devices that blocks pasting and uploading content matching sensitive info types into AI websites in the browser**
</details>

---

## Pregunta 76

*Manage identity, access, and governance*

A DevOps engineer accidentally deleted a production key vault secret last month; it was recovered because soft delete was enabled. You must now guarantee that no one — including subscription Owners — can permanently remove deleted vault objects before the retention period expires, and you must grant a deployment pipeline read-only access to secrets only (not keys or certificates) using the least-privileged built-in role. What should you do?

- [ ] Enable purge protection on the vault, use Azure RBAC authorization, and assign the pipeline's identity the Key Vault Secrets User role scoped to the vault
- [ ] Enable a CanNotDelete resource lock on the vault and assign the pipeline the Key Vault Reader role at subscription scope
- [ ] Increase the soft-delete retention to 90 days and assign the pipeline the Key Vault Administrator role scoped to the vault
- [ ] Back up all secrets to a storage account nightly and assign the pipeline the Key Vault Secrets Officer role scoped to the vault

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable purge protection on the vault, use Azure RBAC authorization, and assign the pipeline's identity the Key Vault Secrets User role scoped to the vault**
</details>

---

## Pregunta 77

*Secure compute*

Your organization builds generative AI applications on Microsoft Foundry in Azure, with additional model workloads in AWS Bedrock and GCP Vertex AI. Leadership wants **posture** answers before an attacker finds them: an inventory of every AI workload and its components (models, grounding data stores, SDKs) across all three clouds, identification of misconfigurations like an internet-exposed compute resource that can reach a vector store of proprietary data, and prioritized, exploitable chains involving AI resources — all **before runtime attacks happen**, not alerts after. 

Which three actions should you take? (Select three.)

*Nota: Selecciona todas las opciones que apliquen.*

- [ ] Deploy Azure AI Content Safety Prompt Shields on every model deployment to inventory the models and their grounding data
- [ ] Enable the Defender CSPM plan with its AI security posture management capabilities on the Azure subscriptions and on the AWS and GCP connectors
- [ ] Enable Microsoft Purview DSPM for AI to map the multicloud AI infrastructure and its network exposure
- [ ] Review the discovered AI inventory (the AI 'bill of materials': deployed models, datasets, grounding sources, and AI services) and remediate the AI-specific posture recommendations
- [ ] Use attack path analysis and the cloud security explorer to find and prioritize exploitable chains that lead to AI resources, such as exposed compute with a route to grounding data
- [ ] Enable the Defender for AI Services workload protection plan, since posture misconfigurations are detected from analyzing runtime prompt traffic

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable the Defender CSPM plan with its AI security posture management capabilities on the Azure subscriptions and on the AWS and GCP connectors**

✅ **Review the discovered AI inventory (the AI 'bill of materials': deployed models, datasets, grounding sources, and AI services) and remediate the AI-specific posture recommendations**

✅ **Use attack path analysis and the cloud security explorer to find and prioritize exploitable chains that lead to AI resources, such as exposed compute with a route to grounding data**
</details>

---

## Pregunta 78

*Secure storage, databases, and networking*

**Pellagrin Insurance** is a property-and-casualty insurer that processes claims in Azure. The company is subject to strict records-retention regulation and periodic external audits.

**Current Environment:**

- Finalized claim documents (scanned reports, settlement letters) are stored as blobs in a container named `claims-final` in a general-purpose v2 storage account.
- Departmental file shares are being migrated from an on-premises Windows file server to Azure Files. Users work on Windows devices joined to the on-premises Active Directory Domain Services (AD DS) domain, and years of carefully maintained NTFS permissions must keep working after the migration.
- The claims database is an Azure SQL database that stores national identification numbers and a `PaymentAdjustments` table that auditors examine for signs of manipulation.
- Database administrators routinely connect to the production database for troubleshooting and can currently read every column.

You are planning the Azure Files migration for Pellagrin Insurance. Users on AD DS domain-joined Windows devices must access the shares with their existing AD DS identities, existing NTFS ACLs must keep working at file and folder level, and storage account keys must not be given to users. What should you do?

- [ ] Mount the shares on each device by using the storage account key stored in a login script, and re-create the permissions as Azure RBAC role assignments per folder
- [ ] Migrate the file shares to Azure Blob Storage with hierarchical namespace and grant users Storage Blob Data Reader
- [ ] Generate a user delegation SAS for each department and embed it in the mapped-drive path, renewing it monthly
- [ ] Enable on-premises Active Directory Domain Services authentication on the storage account, sync the AD DS users to Microsoft Entra ID, assign share-level Azure RBAC roles (such as Storage File Data SMB Share Contributor), and preserve the migrated NTFS ACLs for file and folder-level authorization

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable on-premises Active Directory Domain Services authentication on the storage account, sync the AD DS users to Microsoft Entra ID, assign share-level Azure RBAC roles (such as Storage File Data SMB Share Contributor), and preserve the migrated NTFS ACLs for file and folder-level authorization**
</details>

---

## Pregunta 79

*Secure storage, databases, and networking*

A logical SQL server hosts eight Azure SQL databases, and two more are added every quarter. Compliance requires that database events for **all current and future databases** on the server are audited, and that auditors can run interactive KQL queries over the audit records. What should you configure?

- [ ] Enable Microsoft Defender for SQL on the server and rely on its security alerts as the audit trail
- [ ] Enable database-level auditing individually on each of the eight existing databases with a storage account as the destination
- [ ] Enable server-level auditing on the logical server with a Log Analytics workspace as the destination
- [ ] Enable Transparent Data Encryption (TDE) on the logical server and review the encryption scan logs

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Enable server-level auditing on the logical server with a Log Analytics workspace as the destination**
</details>

---

## Pregunta 80

*Secure compute*

Compliance requires that operating-system settings **inside** your Windows servers — disabling SMBv1, enforcing the local password policy, and setting audit policy values — are continuously assessed and automatically corrected when they drift, on both Azure VMs and Azure Arc-enabled on-premises servers, with compliance results visible in Azure Policy. What should you implement?

- [ ] Defender for Servers Plan 2, whose endpoint protection component enforces OS configuration baselines on every onboarded machine
- [ ] Azure Machine Configuration: assign machine configuration policy definitions for the required OS settings with remediation, so the in-guest agent audits the settings and automatically corrects drift
- [ ] Azure Policy with a custom definition using the Deny effect that rejects VMs whose in-guest settings do not match the baseline
- [ ] A scheduled Run Command script on each VM that reapplies the settings nightly and writes the result to a storage account

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Azure Machine Configuration: assign machine configuration policy definitions for the required OS settings with remediation, so the in-guest agent audits the settings and automatically corrects drift**
</details>

---

## Pregunta 81

*Secure storage, databases, and networking*

**Quillstone Retail Group** operates 240 stores and an e-commerce platform hosted in Azure. Customer order data is stored in an Azure SQL Database elastic pool, and product images, invoices, and data exports are kept in two general-purpose v2 storage accounts named `stqsorders` and `stqsmedia`.

**Current Environment:**

- Both storage accounts allow access from all networks and have shared key authorization enabled.
- Partner logistics companies upload delivery manifests to a container in `stqsorders` by using SAS tokens that were generated ad hoc and never expire.
- The Azure SQL logical server allows connections from all Azure services and has no auditing configured.
- A recent incident involved a malware-infected file being uploaded to the `stqsmedia` account by a compromised partner workstation.

You need to restrict network access to Quillstone Retail Group's storage accounts so that only the e-commerce virtual network and the corporate office IP range can connect. What should you configure on each storage account?

- [ ] Set the storage account firewall default action to Deny, add a virtual network rule for the e-commerce subnet (with the Microsoft.Storage service endpoint enabled), and add an IP network rule for 203.0.113.0/24
- [ ] Create an NSG on the storage account and add inbound allow rules for the virtual network and the office IP range
- [ ] Disable shared key authorization and require Microsoft Entra ID authentication for all storage requests
- [ ] Enable infrastructure encryption and rotate both storage account access keys

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Set the storage account firewall default action to Deny, add a virtual network rule for the e-commerce subnet (with the Microsoft.Storage service endpoint enabled), and add an IP network rule for 203.0.113.0/24**
</details>

---

## Pregunta 82

*Secure storage, databases, and networking*

Your company is retiring a legacy full-tunnel VPN. Remote employees need to reach three internal applications (an SMB file server, an intranet site, and an RDP jump host) — and nothing else on the network. Access must be per-application, evaluated by Conditional Access with MFA per app, and must not place users on the corporate network. How should you implement this with Microsoft Entra Private Access?

- [ ] Deploy a point-to-site VPN gateway with Entra ID authentication and use NSGs to limit which subnets remote users can reach
- [ ] Install the Global Secure Access client on user devices, deploy private network connectors in front of the applications, publish each application as an enterprise app with its specific FQDNs/IPs and ports, and bind Conditional Access policies requiring MFA to each application individually
- [ ] Configure Quick Access with the entire corporate address space as one application segment, and apply a single Conditional Access policy to the Quick Access app
- [ ] Publish the three applications through Microsoft Entra application proxy, since Private Access only supports HTTP and HTTPS applications

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Install the Global Secure Access client on user devices, deploy private network connectors in front of the applications, publish each application as an enterprise app with its specific FQDNs/IPs and ports, and bind Conditional Access policies requiring MFA to each application individually**
</details>

---

## Pregunta 83

*Manage identity, access, and governance*

An Azure key vault stores TLS certificates used by an internal application. Security policy requires that the vault reject all public network traffic, that the application's VNet reach the vault privately, and that Azure disk encryption sets and trusted Microsoft services continue to function. How should you configure the vault's network settings?

- [ ] Create a service endpoint for Microsoft.KeyVault on the application subnet and set the vault's default action to Allow
- [ ] Create a private endpoint for the vault in the application VNet, set Public network access to Disabled, and enable 'Allow trusted Microsoft services to bypass this firewall'
- [ ] Enable the vault firewall with the application VNet's public egress IP in the allow list, and disable soft delete to simplify certificate renewal
- [ ] Set Public network access to Enabled for all networks but require the Key Vault Administrator role for every request

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Create a private endpoint for the vault in the application VNet, set Public network access to Disabled, and enable 'Allow trusted Microsoft services to bypass this firewall'**
</details>

---

## Pregunta 84

*Secure compute*

Your tenant contains hundreds of AI agents registered with Microsoft Entra Agent ID. The SOC suspects that one agent's credentials were compromised. Before responding, the incident commander needs to understand the potential impact: which permissions the agent holds, which sensitive resources and data it can reach, and which other identities or agents it could affect. How should the team perform this analysis?

- [ ] Use Microsoft Defender XDR to analyze the agent's blast radius — exploring the agent's permissions, connections, and reachable resources from its entity page to scope the potential impact
- [ ] Immediately delete the agent's identity, then restore it after the investigation to see which applications report errors
- [ ] Filter the Microsoft Entra sign-in logs for the agent's ID, because the sign-in history shows everything the agent is able to access
- [ ] Create a Conditional Access policy targeting the agent identity and review the policy's "what if" results to enumerate its reachable resources

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Use Microsoft Defender XDR to analyze the agent's blast radius — exploring the agent's permissions, connections, and reachable resources from its entity page to scope the potential impact**
</details>

---

## Pregunta 85

*Secure storage, databases, and networking*

**Pellagrin Insurance** is a property-and-casualty insurer that processes claims in Azure. The company is subject to strict records-retention regulation and periodic external audits.

**Current Environment:**

- Finalized claim documents (scanned reports, settlement letters) are stored as blobs in a container named `claims-final` in a general-purpose v2 storage account.
- Departmental file shares are being migrated from an on-premises Windows file server to Azure Files. Users work on Windows devices joined to the on-premises Active Directory Domain Services (AD DS) domain, and years of carefully maintained NTFS permissions must keep working after the migration.
- The claims database is an Azure SQL database that stores national identification numbers and a `PaymentAdjustments` table that auditors examine for signs of manipulation.
- Database administrators routinely connect to the production database for troubleshooting and can currently read every column.

Which three actions should you take? (Select three.)
- [ ] Configure Always Encrypted on the national ID column, keeping the column master key in Azure Key Vault so only the claims-fraud application can decrypt the values client-side
- [ ] Enable active geo-replication of the database to a paired region
- [ ] Apply dynamic data masking to the national ID column so administrators see masked values in query results
- [ ] Configure transparent data encryption (TDE) with a customer-managed key stored in Pellagrin's Azure key vault
- [ ] Convert PaymentAdjustments to an updatable ledger table so that all changes are recorded in cryptographically chained history that can be verified against tampering
- [ ] You need to meet Pellagrin Insurance's three database protection requirements for the claims database: national ID numbers never exposed in plaintext to database administrators (even in query results or server memory), cryptographic tamper-evidence for the `PaymentAdjustments` table, and encryption at rest under a key Pellagrin controls and can revoke.
- [ ] Enable row-level security so administrators cannot query rows that contain national ID numbers

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **You need to meet Pellagrin Insurance's three database protection requirements for the claims database: national ID numbers never exposed in plaintext to database administrators (even in query results or server memory), cryptographic tamper-evidence for the `PaymentAdjustments` table, and encryption at rest under a key Pellagrin controls and can revoke.

✅ **Configure Always Encrypted on the national ID column, keeping the column master key in Azure Key Vault so only the claims-fraud application can decrypt the values client-side**

✅ **Convert PaymentAdjustments to an updatable ledger table so that all changes are recorded in cryptographically chained history that can be verified against tampering**
</details>

---

## Pregunta 86

*Manage identity, access, and governance*

Your security team must implement three governance requirements across an Azure environment:

1. New storage accounts must be **prevented** from allowing public blob access — non-compliant deployments must fail.
2. The `rg-prod-core` resource group must be protected from accidental deletion, while still allowing engineers to modify resources inside it.
3. Role assignments in which the assigned identity has not used its permissions for months must be identified and reduced.

Which three actions should you take? (Select three.)
- [ ] Enable Defender Cloud Security Posture Management (Defender CSPM) and act on its recommendations to remove unused, overprivileged role assignments
- [ ] Assign an Azure Policy definition with the Deny effect that blocks creation of storage accounts permitting public blob access
- [ ] Apply a ReadOnly resource lock to the rg-prod-core resource group
- [ ] Apply a CanNotDelete resource lock to the rg-prod-core resource group
- [ ] Replace all role assignments in the subscription with the Reader role
- [ ] Assign an Azure Policy definition with the Audit effect that reports storage accounts permitting public blob access

<details>
<summary><b>💡 Ver Respuesta y Explicación</b></summary>

✅ **Assign an Azure Policy definition with the Deny effect that blocks creation of storage accounts permitting public blob access**

✅ **Apply a CanNotDelete resource lock to the rg-prod-core resource group**
</details>

---


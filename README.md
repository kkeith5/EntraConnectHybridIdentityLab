<h1>Entra Connect Hybrid Identity Lab</h1>

<h2>Description</h2>
This project connects the on-prem Active Directory domain from my [Active Directory Home Lab](https://github.com/kkeith5/ActiveDirectoryHomeLab) to Microsoft Entra ID using Microsoft Entra Connect Sync, creating a hybrid identity environment. On-prem users and groups now sync into Entra ID alongside the cloud-only users from my [Microsoft 365 / Entra ID Admin Lab](https://github.com/kkeith5/Microsoft365EntraIdAdminLab), and both sets of users are picked up correctly by the same dynamic security groups.
<br />

<h2>Skills Demonstrated</h2>

- Installing and configuring Microsoft Entra Connect Sync (Custom installation)
- Password Hash Synchronization and Seamless SSO
- Scoped OU filtering to control what syncs to the cloud
- Least-privilege sync account configuration (dedicated service account instead of Domain Admin)
- Troubleshooting UPN suffix and attribute-format mismatches between on-prem AD and Entra ID
- Understanding one-way vs two-way sync behaviour (AD → Entra ID, and password writeback)

<h2>Utilities Used</h2>

- <b>Microsoft Entra Connect Sync</b>
- <b>Active Directory Users and Computers</b>
- <b>Microsoft Entra admin center</b>
- <b>PowerShell</b>

<h2>Environments Used</h2>

- <b>Windows Server</b> (VERSION) — on-prem Domain Controller
- <b>Microsoft Entra ID</b> tenant (Microsoft 365 E5 / Entra ID P2 trial)

<h2>Lab walk-through:</h2>

<p align="center">

<h3>Entra Connect Sync installer — Custom installation:</h3>
<img src="screenshots/01-custom-install.png" height="80%" width="80%" alt="Entra Connect custom installation"/>
<br /><br />

<h3>Dedicated sync account created instead of using Domain Admin:</h3>
<img src="screenshots/02-sync-account.png" height="80%" width="80%" alt="Dedicated sync account"/>
<br /><br />

<h3>UPN suffix warning — lab domain not a verified Entra domain:</h3>
<img src="screenshots/03-upn-warning.png" height="80%" width="80%" alt="UPN suffix warning"/>
<br /><br />

<h3>OU filtering — only Lab OU scoped for sync:</h3>
<img src="screenshots/04-ou-filtering.png" height="80%" width="80%" alt="OU filtering"/>
<br /><br />

<h3>Configuration complete:</h3>
<img src="screenshots/05-configuration-complete.png" height="80%" width="80%" alt="Configuration complete"/>
<br /><br />

<h3>Synced users appearing in Entra ID:</h3>
<img src="screenshots/06-synced-users.png" height="80%" width="80%" alt="Synced users in Entra ID"/>
<br /><br />

<h3>Dynamic security group showing both synced and cloud-only members:</h3>
<img src="screenshots/07-mixed-group-membership.png" height="80%" width="80%" alt="Mixed group membership"/>

</p>

<h2>Troubleshooting</h2>

**Issue:** Entra Connect refused to use a Domain Admin account for the sync.
**Fix:** Let the wizard create a dedicated least-privilege sync account instead.

**Issue:** AD-synced users' `Country` attribute stored full names (e.g. "Ireland"), while cloud-only users used short codes (e.g. "IE"), so dynamic group rules matched inconsistently.
**Fix:** Standardised both sides on full country names and updated the dynamic group rules to match.

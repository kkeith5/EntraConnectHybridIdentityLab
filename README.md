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

<h3>1. Custom installation selected:</h3>
<img src="screenshots/01-custom-setup.png" height="80%" width="80%" alt="Custom installation"/>
<br /><br />

<h3>2. Required components installed:</h3>
<img src="screenshots/02-required-components.png" height="80%" width="80%" alt="Required components"/>
<br /><br />

<h3>3. User sign-in method — Password Hash Synchronization:</h3>
<img src="screenshots/03-user-sign-in.png" height="80%" width="80%" alt="User sign-in method"/>
<br /><br />

<h3>4. Connect to Microsoft Entra ID:</h3>
<img src="screenshots/04-connect-directories.png" height="80%" width="80%" alt="Connect directories"/>
<br /><br />

<h3>5. Connect your on-prem AD forest:</h3>
<img src="screenshots/05-ad-forest-connection.png" height="80%" width="80%" alt="AD forest connection"/>
<br /><br />

<h3>6. Microsoft Entra sign-in configuration — UPN suffix check:</h3>
<img src="screenshots/06-entra-sign-in-config.png" height="80%" width="80%" alt="Entra sign-in configuration"/>
<br /><br />

<h3>7. Domain and OU filtering — scoped to the Lab OU:</h3>
<img src="screenshots/07-domain-ou-filtering.png" height="80%" width="80%" alt="Domain and OU filtering"/>
<br /><br />

<h3>8. Uniquely identifying users:</h3>
<img src="screenshots/08-identifying-users.png" height="80%" width="80%" alt="Uniquely identifying users"/>
<br /><br />

<h3>9. Filtering users and devices:</h3>
<img src="screenshots/09-filtering.png" height="80%" width="80%" alt="Filtering users and devices"/>
<br /><br />

<h3>10. Optional features:</h3>
<img src="screenshots/10-optional-features.png" height="80%" width="80%" alt="Optional features"/>
<br /><br />

<h3>11. Configuration complete:</h3>
<img src="screenshots/11-configuration-complete.png" height="80%" width="80%" alt="Configuration complete"/>
<br /><br />

<h3>12. All users successfully synchronised:</h3>
<img src="screenshots/12-all-users-synced.png" height="80%" width="80%" alt="All users synced"/>
<br /><br />

<h3>13. AD users in their OU, now matched in Entra ID:</h3>
<img src="screenshots/13-ad-users-ou.png" height="80%" width="80%" alt="AD users in OU"/>
<img src="screenshots/13-entra-users-ou.png" height="80%" width="80%" alt="Same users in Entra ID"/>
<br /><br />

<h3>14. Synced Ireland user confirmed in Entra ID:</h3>
<img src="screenshots/14-ireland-user-connected.png" height="80%" width="80%" alt="Ireland user connected"/>

</p>
<h2>Troubleshooting</h2>

**Issue:** Entra Connect refused to use a Domain Admin account for the sync.
**Fix:** Let the wizard create a dedicated least-privilege sync account instead.

**Issue:** AD-synced users' `Country` attribute stored full names (e.g. "Ireland"), while cloud-only users used short codes (e.g. "IE"), so dynamic group rules matched inconsistently.
**Fix:** Standardised both sides on full country names and updated the dynamic group rules to match.

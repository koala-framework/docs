# PartnerNet
This repository is used to implement partner-net integration.

## Features
### PartnerNet-Sync
This synchronises users allowed to access a specific menuItemMc of partnernet.
This also synchronises Companies (BNR) and Brands of users. There is also the
possibility to synchronise advisors, but this is only used in TIS.
This is used in webs to
* provide a list for web specific newsletters
* as access-control

### PartnerNet Components
* Links into partnernet applications (With certificate banner)
* Login Component
* Newsletter
* User-Profile box

### PartnerNet-Login (Saml2)
This is a newer feature to implement access-control without syncing every user.
There is still missing "Funktionen" and "Tätigkeiten" of a user.

## Changelogs
### 2.0
* support for kwf >= 4.0
* implements PartnerNet-Sync as maintenance-job

### 1.0
* extracted from vkwf 3.11. (composer needed)
* saml2 login

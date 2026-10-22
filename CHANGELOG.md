# Changelog

Changes in each release of Smart Cache for Joomla, newest first.
## 1.1.1 - 2026-10-22
### Added
- Licence: a free trial shows "Free trial until (date), then added to your plan", and a free staging site shows "Free staging site of (your main site)", each with its own label.
### Fixed
- A copy of a site (for example a staging site) no longer connects under the original site's address. The connect screen shows which address it will use and offers "Use (this address)" when it differs from the one you are on. A connected site whose address differs from the one in the browser now says so.
- Add the CDN: the certificate check no longer stops with "Not served … /.well-known/acme-challenge/…". Smart Cache now writes that validation file too (used when Cloudflare issues the certificate through Let's Encrypt or Google).


## 1.1.0 - 2026-10-22
### Added
- An "Add the CDN" step: put Cloudflare in front of your site with one DNS record. Smart Cache shows the exact record for your hostname, checks it, and keeps a certificate ready before you change DNS. It works for www, any subdomain such as dev, and the bare domain (on a DNS host without a bare-domain CNAME, serve visitors on www and Smart Cache forwards the bare domain to it).
- Guided Cloudflare for SaaS setup for sites that use their own Cloudflare token, with each step and its result shown as it runs.
- Cache purges are relayed to the CDN once it is live, so visitors get the new page after you publish.
- History: every CDN step and every change of its state is written to the Activity log.
### Notes
- Nothing changes for a site that has not added the CDN.


## 1.0.6 - 2026-10-22
### Changed
- Home: when your licence is active, it shows as a card on the green "Your site is fast" banner (paid until, renews automatically, Check now, Manage subscription) instead of a row in the list. Payment due, ended or offline states still show as a row with a warning. Disconnect is in Advanced → Danger zone.


## 1.0.5 - 2026-10-21
### Added
- Home Dashboard block: Smart Cache status, pages cached, Google speed score and licence at a glance, with a button to open Smart Cache. It is placed at the top of the Home Dashboard on install; move or unpublish it under System → Administrator Modules.
- Licence row on Home: connected to speed.themexpert.com, paid until (or ends on) the date of your payment term, when it was last checked, a Check now button, Manage subscription and Disconnect.
- A welcome message after installing, with the three steps to a fast site and a button to open Smart Cache.
- Smart Cache has its lightning icon in the admin menu.
- Advanced → Exclusions: never cache pages with chosen query parameters (also page, start, limit or utm_ ones), and never cache chosen menu items (pick them from your menus; the articles reached through an item are included). Both apply on the server and on Cloudflare.
### Changed
- Edit and input forms are never cached, whatever the component: edit/form layouts (also on SEF addresses), views with "edit" in their name, any request with a task, and com_content's article form. Menu items that open such a form are also bypassed on Cloudflare.
### Fixed
- The licence date now follows your payment term. Before, "valid until" showed the date of a short-lived security token.
- Billing changes (renewal date, cancellation) sent with the daily check are no longer missed.


## 1.0.4 - 2026-10-21
### Added
- Updates through Joomla: new versions of Smart Cache now appear under System → Update → Extensions, with a changelog.
### Notes
- First public release.



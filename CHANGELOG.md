# Changelog

Changes in each release of Smart Cache for Joomla, newest first.
## 1.2.4 - 2026-10-24
### Added
- Try before you buy: the Connect screen has a new "Start a 30-day free trial" button. No card needed, every feature included, and nothing is charged when it ends. One trial per site.


## 1.2.3 - 2026-10-24
### Changed
- Speed checks no longer need your own Google API key: a site connected to a Smart Cache plan runs its PageSpeed and real-visitor (Chrome UX Report) checks on Smart Cache's key, so "Google's quota is used up" stops being a daily problem. The Speed tab says the key is included instead of asking for one. Your own key, if you added one, is still used first. A site that isn't connected checks with Google directly, as before.
### Fixed
- After Joomla's System → Clear Cache or Regular Labs Cache Cleaner emptied Joomla's cache folder, the Home tab showed "1 step left: Finish setup" again, because they also deleted Smart Cache's small rules file there. Smart Cache now puts it back by itself, so the site stays served straight from disk and Home stays "All set". The same file keeps cached copies from being opened directly, so that protection comes back too.


## 1.2.2 - 2026-10-23
### Added
- Keep pages warm: a new scheduled task (every hour, created on install and update) rebuilds expired and important pages in the background, up to 200 per run and two at a time, so visitors don't wait for a slow first load. Like JCH Optimize's Recache, without a setting.
- On sites served by Cloudflare (our CDN or your own account), warming also fetches up to 10 of the pages it just cached through Cloudflare, home page first, so the Cloudflare city nearest your server has them before a visitor does.
### Changed
- A new screen after installing or updating: one card that says what happened (settings kept, exclusions brought over from other cache plugins, pages served from disk, Cloudflare rules updated) and the one thing to do next, instead of several loose status lines. A site that isn't connected to a plan is told so, with a Connect button. The installer no longer shows the routine "live on the site" check.
- Clearer package description in Joomla's extension list.
### Fixed
- Dark mode in Joomla's administrator: the number tiles, score box, status pills, save bar, Advanced menu and grey help texts were light-only and hard to read on the dark background. They now have dark colours too. The new install card also follows dark mode.


## 1.2.1 - 2026-10-23
### Fixed
- Another page cache on the site (JotCache, LiteSpeed Cache, JCH Optimize's page cache or Server Cache) now shows on the Home tab as a setup step instead of "All set": Smart Cache doesn't cache pages while one is on. Finish setup switches it off for you, as it already did for Joomla's own page cache. Before, Home could say "Your site is fast" while pages were built every time.
### Changed
- The Settings tab is now called Fine-tune and sits after History: Home, Speed and History are the everyday tabs; Fine-tune and Advanced are optional, since Smart Cache picks the settings itself.
- Once the CDN is live, the "Add the CDN" card leaves the Home tab. Home shows one "CDN: Live since …" line instead; the card with the undo record and its history stays under Advanced.


## 1.2.0 - 2026-10-23
### Added
- Exclusions from other cache and speed plugins are imported when Smart Cache is installed or updated: JCH Optimize (JS/CSS exclusions, critical scripts, excluded URLs and menu items, its page cache's excluded URLs, menu items and components), Joomla's System - Page Cache, JotCache, LiteSpeed Cache, Server Cache and Cache Exclude. A plugin that is disabled but still holds settings counts too. The install message lists what was added and what could not be (lazy-load exclusions, real regular expressions). Lines you remove later stay removed until that plugin's settings change.
- Never cache these components (Advanced, Exclusions): component names such as com_rsform, one per line.
- Extensions can tell Smart Cache not to cache a page through Joomla's own page cache event (onPageCacheIsExcluded), as RSForm Pro does for a page showing a form, J2Commerce for a shopper with a cart, and Quix for an incomplete page.
- JotCache, LiteSpeed Cache, JCH Optimize's page cache (JCH 8 and 9) and Server Cache are recognised: while one is enabled, Smart Cache pauses its own page cache and says why, as it does for Joomla's page cache.
### Fixed
- Shops (VirtueMart, HikaShop, J2Store, Phoca Cart, EShop): a visitor who adds to the cart or opens the cart, wishlist or checkout is no longer served from or stored in any cache for the rest of their browser visit, so one guest's mini-cart can't be shown to everyone. Product and category pages stay cached. HikaShop's cart cookies are recognised directly.
- Scripts loaded from another site that are not trackers or widgets (for example jQuery, Bootstrap or a payment form from a CDN) are no longer held back until the visitor interacts. Scripts that need them could fail with "jQuery is not defined". Analytics, chat, ads and social widgets are still delayed.
- Max level: Joomla's core script and jQuery are no longer held back until the visitor interacts. A script that runs on time (for example a mobile menu you excluded) failed with "Joomla is not defined". They are now deferred in order like the site's own scripts.
- Multilingual sites: the bare home address is never cached, because Joomla's language filter picks each visitor's language there. Language pages (/en/…) stay cached.


## 1.1.3 - 2026-10-22
### Fixed
- Purge everything with your own Cloudflare account connected now clears only this site's addresses (its hostname and the www or bare twin), not the whole Cloudflare zone. A zone that also serves other sites (subdomains, a shared CDN zone) keeps their caches.


## 1.1.2 - 2026-10-22
### Added
- Download debug log (Advanced → Tools, and on the Connect screen): one file with the versions, the Joomla settings that affect how the site is reached, the licence, Cloudflare and CDN status with the CDN history, the Activity log, the validation files on disk and the end of the error log. Passwords, keys and tokens are removed. Send it to support when something gets stuck.
### Fixed
- Desktop layout shift on pages with a bar above the site header (an announcement or marquee section): Smart Cache took that bar for the hero, so the layout CSS of what follows the hero (for example cards pulled up over it) arrived late and the page jumped. A section that ends before the site header is now treated as a top bar. Clear the cache after updating.
- Cached pages are now sent gzip-compressed when the browser accepts it, like a page Joomla renders itself. Before, a page served from Smart Cache's page cache went out uncompressed (about 6× larger).
- Images in your own folders that already were WebP (or SVG) kept a plain address and were cached by browsers for only a week. They now get a version in the address, so browsers keep them for a year, and a replaced file gets a new address the next time the page is built.
- A logo or icon shown much smaller than 480px (for example a 135px header logo) now also gets a version at twice its shown width, instead of downloading a 480px file.


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



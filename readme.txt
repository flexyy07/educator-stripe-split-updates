=== Vendors Payment Split ===
Contributors: CHANGE-TO-WPORG-USERNAME
Tags: stripe connect, split payments, vendors, learndash, woocommerce
Requires at least: 6.5
Tested up to: 7.1
Requires PHP: 7.4
Stable tag: 2.5.1
License: GPLv2 or later
License URI: https://www.gnu.org/licenses/gpl-2.0.html

Pay every vendor their share of each course sale and subscription renewal, automatically, straight to their Stripe account.

== Description ==

Vendors Payment Split is for course businesses with more than one vendor. When a student buys a course, or a subscription renews, the plugin works out who owns the course and sends that vendor their share through **Stripe Connect**. It works with LearnDash, Tutor LMS, Sensei LMS, LearnPress, LifterLMS, MasterStudy and other course platforms, as long as payments go through **WooCommerce**.

**What it does**

* **Automatic payouts:** every paid order sends each vendor's share to their Stripe connected account (separate charges and transfers).
* **Every renewal:** WooCommerce Subscriptions renewals are split every billing cycle, not only the first payment.
* **Course-aware:** the course owner is the vendor. Links from LearnDash, Tutor LMS and Sensei LMS are detected automatically; any other platform picks the course on the product.
* **Flexible shares:** a percent or fixed amount, set per product, per course, per vendor or as a global default.
* **Co-vendors:** one sale can pay several vendors, each with their own Stripe transfer.
* **Refunds:** the vendor's share is reversed in proportion to the refund (or you can choose to be alerted only).
* **Vendor dashboard:** add the `[edss_educator_dashboard]` shortcode to a page. Vendors see their earnings and connect Stripe themselves with one button (Stripe-hosted onboarding).
* **Safe by design:** a Dry run mode (calculate without sending money), protection against paying twice, automatic hold and hourly retry while an vendor's Stripe account is not ready, and test/live accounts kept apart.
* **Clear admin:** an Overview with a setup checklist, a Payouts log with plain status names, a Course Mapping page, and a "why was this order not split?" panel.
* **Webhook:** every result can be sent to Pabbly, Zapier, Make, n8n, GoHighLevel or any URL you choose.
* **Split optional:** turn the split off for any product or course (e.g. memberships), and the platform keeps 100%.

**Pro version:** a Pro version with extra features is coming soon. Everything in this free version stays free.

**Requirements**

* WooCommerce, with payments taken by the WooCommerce Stripe gateway.
* A Stripe account with Connect enabled; vendors need connected accounts (they can create one from the dashboard page).
* Optional: WooCommerce Subscriptions for recurring courses.

== Installation ==

1. Install and activate the plugin (WooCommerce must be active).
2. Open **Vendor Splits → Overview** and follow the setup checklist.
3. **Settings → Start:** add the secret key of the Stripe account that receives your course payments, save, then click **Test Stripe connection**.
4. Give each vendor a Stripe account: paste their `acct_…` ID on their user profile, or let them use **Connect Stripe** on a page containing `[edss_educator_dashboard]`.
5. On each course (or product), choose the vendor and their share in the **Vendor payout** box.
6. Keep Run mode on **Dry run**, make a test purchase, check **Payouts**, then switch to **Live transfers**.

== Frequently Asked Questions ==

= Does it work without WooCommerce? =

No. The plugin splits WooCommerce orders. If your course platform uses its own checkout instead of WooCommerce, those payments are not seen.

= Who pays the Stripe fees? =

The vendor's share is calculated from the sale amount. Stripe's processing fees and any Stripe Connect fees stay with the platform (your Stripe account).

= What happens if an vendor's Stripe account is not ready? =

Their payout is put **On hold** and retried every hour. Nothing is lost; it is sent as soon as Stripe allows transfers to that account.

= Can a payout be sent twice? =

Each order line has one payout record per vendor, and Stripe idempotency keys plus a check for existing transfers stop duplicates, even if the same order event arrives more than once.

= Can I test without moving money? =

Yes. Use Stripe test mode and the plugin's **Dry run** mode. Rows recorded in test mode are never paid out in live mode.

== External services ==

This plugin connects to **Stripe** (api.stripe.com) to do its job:

* To create transfers and transfer reversals to your vendors' connected accounts, look up connected accounts and payment intents, read your balance, and (when vendors use "Connect Stripe") create Express accounts, onboarding links and dashboard login links.
* Data sent: amounts, currency, connected account IDs, the order, item, product, course, vendor and subscription IDs as transfer metadata, your site's host name, and, for new vendor accounts, the vendor's email address.
* It only happens when an order is paid, refunded or retried, or when an administrator or vendor uses a Stripe-related button.
* Stripe terms: https://stripe.com/legal/ssa. Privacy policy: https://stripe.com/privacy

**Webhook (optional, off by default):** if you enter a webhook URL, each payout result is sent to that URL. This includes the customer's name, email and phone, order, course, vendor and amounts. The data goes only to the address you configure; that service's own terms and privacy policy apply.

== Screenshots ==

1. Overview: setup checklist, money paid this month and what needs attention.
2. Payouts: every vendor payout with plain status names.
3. Course Mapping: who gets paid for each product.
4. Vendor dashboard with earnings and Connect Stripe.

== Changelog ==

= 2.5.1 =
* More reliable updates.

= 2.5.0 =
* Renamed to Vendors Payment Split; "educator" is now "vendor" throughout. The dashboard shortcode is [edss_vendor_dashboard] (the old one still works) and webhooks carry `vendor` fields next to the old ones.

= 2.4.6 =
* Code review fixes: all database queries use prepared identifiers, stricter input sanitizing and output escaping.

= 2.4.5 =
* No more "not tested with your version of WordPress" warning on WordPress 7.1.x.

= 2.4.4 =
* "View details" now shows the full description, installation steps, FAQ and changelog.

= 2.4.3 =
* Confirms one-click updates from the Plugins screen.

= 2.4.2 =
* Fixed "Download failed. Unauthorized" when updating from the Plugins screen.
* Clearer key messages in Settings.

= 2.4.1 =
* Shorter plugin description.

= 2.4.0 =
* Updates arrive on the Plugins screen with no setup.

= 2.3.1 =
* Small admin fixes.

= 2.3.0 =
* WordPress.org release. Scripts and styles are loaded as files. Fixed the "key not saved" warning on the Test Stripe connection button.

= 2.2.0 =
* New Overview page with a setup checklist, tabbed settings, plain status names and a Course Mapping summary.

= 2.1.0 =
* Co-vendors, vendor earnings dashboard, and self-service "Connect Stripe" onboarding.

= 2.0.4 =
* "Do not split" option per product and per course.

== Upgrade Notice ==

= 2.3.0 =
First public release.

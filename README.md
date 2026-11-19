# Website Chat for FreeScout

A WordPress plugin that puts a live chat on your website. A visitor's message lands in your own [FreeScout](https://freescout.net) help desk as a conversation, and your team's reply appears in the visitor's chat window.

The plugin is the visitor-facing half. The other half is the FreeScout module [Website Chat (WordPress)](https://github.com/automaze-me/freescout-wordpresschat), which turns chats into conversations. Messages go from the visitor's browser straight to your FreeScout. They never pass through your WordPress site or a third-party chat service.

The plugin and the module are made by [automaze.me](https://automaze.me). They are not affiliated with the FreeScout team, and they are not FreeScout's own Live Chat module.

![The chat on a WordPress shop page](https://raw.githubusercontent.com/automaze-me/freescout-wordpresschat/main/docs/screenshots/widget.png)

## Requirements

- WordPress 6.3 or newer, PHP 7.4 or newer.
- FreeScout with the [Website Chat (WordPress)](https://github.com/automaze-me/freescout-wordpresschat) module, reachable over HTTPS.

## Installation

1. In WordPress, open **Plugins → Add New Plugin**, search for "Website Chat for FreeScout", install and activate it. Until the plugin is listed on wordpress.org, download `website-chat-for-freescout.zip` from the [latest release](https://github.com/automaze-me/live-chat-for-freescout/releases/latest) instead and upload it under **Plugins → Add New Plugin → Upload Plugin**.
2. In FreeScout, open **Manage → Website Chat** and add your website. Its entry shows the Site ID and the secret.
3. In WordPress, open **Settings → Website Chat for FreeScout**, enter the FreeScout URL, the Site ID and the secret, and save. **Test connection** tells you whether everything matches.

## Updates

From version 1.0.0 on, the plugin gets its updates from wordpress.org: new versions show up under **Dashboard → Updates** like any other plugin update, and you can switch on automatic updates for the plugin.

### Coming from "Live Chat for FreeScout" 0.1.x

Versions 0.1.x were published here under the name "Live Chat for FreeScout", in the plugin folder `live-chat-for-freescout`. They do not update to Website Chat for FreeScout on their own. Both share their settings, so the switch keeps your FreeScout URL, Site ID, secret and appearance:

1. Under **Plugins**, deactivate Live Chat for FreeScout. Do not click **Delete**: deleting runs its uninstall routine, which removes the settings both plugins share.
2. Install and activate Website Chat for FreeScout.
3. Remove the folder `wp-content/plugins/live-chat-for-freescout` by FTP or your host's file manager, or with WP-CLI: `wp plugin delete live-chat-for-freescout` (WP-CLI deletes the files without running the uninstall routine).

After an update, purge your page cache. A cached page still carries the old widget settings.

## What you can set

- Team name, avatar, accent color and welcome messages.
- A button color of its own, and a white ring that keeps the button visible on a background of the same color.
- The corner the chat sits in.
- Working hours for each day, with an away message outside them.
- Pages where the chat stays hidden, such as the checkout.
- A link to your privacy policy inside the chat.

With WooCommerce, the chat recognizes logged-in customers, and visitors can give an order number so your team sees who they are talking to. German is included for Germany, Austria and Switzerland, in the "du" and the "Sie" form.

What the plugin stores and sends is listed in [readme.txt](readme.txt), under "Privacy" and "External services".

## Development

Run the tests from the plugin folder:

```bash
for f in tests/*.php; do php "$f"; done
node tests/hours.test.js
```

To release, set the new version in the plugin header (`Version`), in `LCFF_VERSION` and in readme.txt's `Stable tag`, commit, and push a tag `vX.Y.Z`. The release workflow checks that the tag matches the version, runs the tests, builds `website-chat-for-freescout.zip` and publishes it on the GitHub release.

`.wordpress-org/` holds the banner, the icon and the screenshots of the wordpress.org listing. They belong in the plugin's SVN `assets/` folder and stay out of the zip. The banner illustration and the icon were generated with an image model (gpt-image); the type on the banner is set separately.

## License

GPLv2 or later, see [LICENSE](LICENSE).

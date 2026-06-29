---
description: >-
  Quickly and easily change the displayed Server Name, IP, Store Link, Discord
  Link & Voting Links
---

# Branding

### Adding Your Branding <a href="#changing-the-server-list-appearance" id="changing-the-server-list-appearance"></a>

To easily change the server name, IP, store link, Discord link, and voting links, go to the following file and update the details in the `text:` field with your own. Restart your server, and the changes will take effect. do not change anything other than content in the `text:` field otherwise, placeholders will not work!

**File:** `/plugins/RocketPlaceholders/placeholders/branding.yml`

{% hint style="info" %}
For each file, only replace the text inside the text field. Do not change anything else, or your configuration may break!
{% endhint %}

### Changing the Server's MOTD <a href="#changing-the-server-list-appearance" id="changing-the-server-list-appearance"></a>

To change the text displayed for your server in the server list (MOTD), go to `plugins/MiniMOTD/main.conf` and update both lines of text.

To change the server icon (the image to the left of the text), replace the `server-icon.png` file in the main directory. Make sure it's 64x64 pixels and in PNG format, or the new image won’t show up!


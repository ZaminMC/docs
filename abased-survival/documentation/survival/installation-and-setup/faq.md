---
description: >-
  Find useful tips for your setup, like things to configure, commands, and where
  to change items.
---

# Faq

### Managing Token Currency <a href="#managing-coin-currency" id="managing-coin-currency"></a>

Tokens are a premium currency in this setup. Use the PlayerPoints plugin to manage tokens, and use the `/points` command to give or remove them from players. Essential commands are listed below or visit this page for the full command list.

* `/points give <name> <amount>` - Give Tokens to a player.
* `/points take <name> <amount>` - Take Tokens from a player.

### In-Game Shop <a href="#in-game-shop" id="in-game-shop"></a>

Adjust shop items and prices in the `/plugins/EconomyShopGUI/shops` folder. Each shop category has its file for editing.

### AFK Area <a href="#afk-area" id="afk-area"></a>

This setup includes an AFK area where players earn passive income. Adjust rewards and settings in the `/plugins/Skript/scripts/AFK.sk` file. This Skript file allows changes to rewards, messages, and more.

To move the AFK area, use WorldEdit to select a new region (get a wand with `//wand`) and then run `/rg redefine afk`.

To remove the AFK area, delete the `/plugins/Skript/scripts/AFK.sk` file and remove the AFK region with `/rg delete afk`.

### **Changing Daily Rewards** <a href="#daily-rewards" id="daily-rewards"></a>

To adjust the daily rewards, edit the `/plugins/AxRewards/gui.yml` file..

### Automatic Announcements <a href="#automatic-announcements" id="automatic-announcements"></a>

To update automatic announcement text, edit the `/plugins/InfiniteAnnouncements/announcements.yml` file.

### Donation Perks <a href="#donation-perks" id="donation-perks"></a>

Below are the donation perks for this setup. Use these to configure your Tebex store. can also be viewed using \`\`/ranks\`\` command in-game.

#### Fighter Rank: <a href="#vip-rank" id="vip-rank"></a>

* Fighter Kit (3 Days cooldown)&#x20;
* 3x Backpack Rows&#x20;
* 3x Home Slots&#x20;
* 3x Player Vaults&#x20;
* Player Vaults will be 6 rows.&#x20;
* 5x Auction Slots&#x20;
* 1 Token Daily Reward&#x20;
* /craft Command&#x20;
* /recipe Command
* &#x20;/fix hand Command&#x20;
* /enderchest Command

#### Soldier Rank: <a href="#pro-rank" id="pro-rank"></a>

* Soldier Kit (3 Days Cooldown)&#x20;
* 5x Backpack Rows&#x20;
* 5x Home Slots&#x20;
* 5x Player Vaults&#x20;
* Player Vaults will be 6 rows.&#x20;
* 7x Auction Slots&#x20;
* 2 Tokens Daily Reward&#x20;
* /craft Command&#x20;
* /recipe Command&#x20;
* /fix hand Command&#x20;
* /hat Command&#x20;
* /near Command&#x20;
* /enderchest Command

#### Champion Rank: <a href="#mvp-rank" id="mvp-rank"></a>

* Champion Kit (3 Days Cooldown)&#x20;
* 5x Backpack Rows&#x20;
* 6x Home Slots&#x20;
* 7x Player Vaults&#x20;
* Player Vaults will be 6 rows&#x20;
* 9x Auction Slots&#x20;
* 3 Tokens Daily Reward&#x20;
* /craft Command&#x20;
* /recipe Command&#x20;
* /near Command&#x20;
* /hat Command&#x20;
* /invsee Command&#x20;
* /enderchest Command

#### Immortal Rank: <a href="#immortal-rank" id="immortal-rank"></a>

* Immortal Kit (3 Days Cooldown)&#x20;
* 6x Backpack Rows&#x20;
* 10x Home Slots&#x20;
* 9x Player Vaults&#x20;
* Player Vaults will be 6 rows&#x20;
* 12 Auction Slots&#x20;
* 4 Tokens Daily Reward&#x20;
* /craft Command&#x20;
* /recipe Command&#x20;
* /hat Command&#x20;
* /invsee Command&#x20;
* /enderchest Command&#x20;
* /fix hand Command&#x20;
* /fix all Command&#x20;
* /ptime Command&#x20;
* /pweather Command

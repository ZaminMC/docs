---
description: Learn how to easily set up the Abased Survival Server!
---

# Installation & Setup

### 1. Download Server Files <a href="#id-1.-unzip-your-download" id="id-1.-unzip-your-download"></a>

Locate the survival server zip file you got from BuiltByBit. Unzip it and copy the folder inside.

### 2. Uploading to Your Host <a href="#id-3.-download-a-server-jar" id="id-3.-download-a-server-jar"></a>

* Turn off your server and connect to it using FTP or SFTP (ask your hosting provider for help if needed).
* Delete or move all existing server files from the main directory. If you want to keep these files, put them in a different folder or download them elsewhere.
* Upload the `Server Files.zip` to your server. It should be the only file there.
* Unzip the file, which will create many files in the main directory. After unzipping, you can delete the .zip file.

### 3. Downloading the right Server Jar <a href="#id-3.-download-a-server-jar" id="id-3.-download-a-server-jar"></a>

You need a server jar to run your server. You can use any Spigot fork, but I recommend Paper for ease. If your hosting provider has a built-in jar downloader, you can use that and skip this step.

Make sure to use a `1.21.1` server file. You can [download a Paper jar file](https://api.papermc.io/v2/projects/paper/versions/1.21.1/builds/74/downloads/paper-1.21.1-74.jar) directly here. Your server must be on version 1.21.1. Using an earlier or later version might cause problems with world loading or plugins. To allow players on different versions to connect, use ViaVersion and ViaBackwards.

### 4. Plugin Dependencies <a href="#id-4.-plugin-dependencies" id="id-4.-plugin-dependencies"></a>

Due to licensing rules, some plugins need to be downloaded separately and added to your `/plugins` folder. Here are the links to download them:

* TAB Plugin - [Download](https://github.com/NEZNAMY/TAB/releases)
* Citizens Plugin - [Download](https://ci.citizensnpcs.co/job/Citizens2/)
* CrazyVouchers Plugin - [Download](https://modrinth.com/plugin/crazyvouchers/versions?g=1.21.1)
* PL-Hide Plugin [Download](https://www.spigotmc.org/resources/68767/)

### 5. Starting the Server <a href="#id-5.-starting-the-server" id="id-5.-starting-the-server"></a>

Start your server to enjoy your setup. The first start may take longer because it needs to generate files.

When you first log in, you might see many plugin updates. It’s a good idea to update them to prevent issues later on.

{% hint style="info" %}
Further moving on we still have some more things to configure, like DiscordSRV, Geyermc, Votifier, and your webstore. Follow the provided guides to complete these setups.
{% endhint %}

### 6. Configuring GeyserMC

To set up Geysermc to allow bedrock players to join your server, watch and follow the tutorial video provided.

{% embed url="https://youtu.be/eMD2rZWu7xU" %}
How to setup GeyserMC on your Server. Video by [CraftedCroix](https://www.youtube.com/@CraftedCroix)
{% endembed %}

### 7. Configuring DiscordSRV

To sync your Minecraft chat with your Discord chat, watch and follow the tutorial provided.

If you don't want to use DiscordSRV, simply delete the DiscordSRV plugin from your `/plugins` folder and restart your server.

{% embed url="https://youtu.be/JgSRXd95Nt0" %}
How to setup DiscordSRV on your Server. Video by [KasaiSora](https://www.youtube.com/@KasaiSora)
{% endembed %}

### 8. Configuring Votifer <a href="#configuring-votifer" id="configuring-votifer"></a>

To set up Votifier and send voting rewards to players on your server, watch and follow the tutorial video provided.

{% embed url="https://www.youtube.com/watch?v=RVPgmyE20Gs" %}
How to setup Votifier on your Server. Video by [Atomatrix Development](https://www.youtube.com/@AtomatrixDevelopment)
{% endembed %}

### **9. Configuring Tebex** <a href="#id-6.-styling-your-server" id="id-6.-styling-your-server"></a>

Create your webstore project on Tebex by setting up a new project. You can sell whatever you like in your store. watch and follow the tutorial video provided.

{% embed url="https://www.youtube.com/watch?v=4AvVCTXAHQs" %}
How to setup Tebex on your Server. Video by [Tebex Academy](https://www.youtube.com/@tebex)
{% endembed %}

### 10. Additional Details <a href="#id-6.-styling-your-server" id="id-6.-styling-your-server"></a>

For details on server styling check out the [Branding page](https://docs.abasing.xyz/server-setups/survival/installation-and-setup/branding), rank permissions, and important tips, which can be found on the [Extra information](https://docs.abasing.xyz/server-setups/survival/extra-information) page

# Installation

1. After purchasing the resource on our store, log in to Fivem's KeyMaster site ([https://keymaster.fivem.net/](https://keymaster.fivem.net/)).
2. In the menu on the left, go to **Granted Assets** located in the **Server Owners** section.

<figure><img src="../../.gitbook/assets/Sans titre.png" alt=""><figcaption></figcaption></figure>

3. In the list of resources, select the Download button corresponding to MadonnePVP. This will download you a .zip file.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

4. Open the archive you just downloaded. There you will find two folders named **MS\_Madonne\_PVP** and **oxmysql**.
5. Drag this folders into your server's resources folder.
6. Since the resource is already configured and ready to use, all you have to do is edit your server's configuration file (often caller _server.cfg_) and add ensure _ensure oxmysql_ and _MS\_Madonne\_PVP_ at the bottom of it.

<figure><img src="../../.gitbook/assets/Sans titre (1).png" alt=""><figcaption></figcaption></figure>

7. If it's not already done, add this line at the top of your server.cfg, and replace each XXX by your database server informations.

```properties
set mysql_connection_string "server=XXX;port=XXX;userid=XXX;password=XXX;database=XXX"
```

8. Start your server and enjoy your new script !


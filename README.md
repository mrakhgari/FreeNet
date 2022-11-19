# FreeNet
A guide to setting up kind of VPN.
<details>
<summary><b>Table of Contents</b> (click to open)</summary>
<!-- MarkdownTOC -->

1. [Buy a VPS (Virtual Private Server)](#buy-vps)
1. [Set simple V2ray with X-UI panel](#setting-a-simple-v2ray-with-x-ui-panel)
1. [Connect To V2ray](#connect-to-v2ray)
1. [References](#references)

<!-- /MarkdownTOC -->
</details>

## Buy VPS 
You should:

* Before making payment ping an IP address of the VPS provider
* Prefer hourly billing VPS services
* Prefer less popular VPS services
* Check for ratings and user reviews
* Prefer KVM virtualization
* Use a VPN when using Putty or an alternative SSH programme, to prevent IP address blocking

I can suggest these VPS services:

* [Vultr](https://www.vultr.com/) – hourly billing – starting from $3.5 per month – vultr.com (get a $100 bonus)
* [DigitalOcean](https://www.digitalocean.com/) – hourly billing – starting from $5 per month – digitalocean.com (get a $100 bonus) (You can use refer code to use free plans)
* [RackNerd](https://my.racknerd.com/) – monthly billing – starting from $2 per month (annual subscription) – racknerd.com

**In some cases, when you can't connect directly to the internet, you need to buy a server in your country, also if you can't buy a server from upper links, you can buy servers that are located in other countries, from these providers. (Not Recommended)**

Some of Iranian VPS services: 
* [server](https://server.ir/)
* [sarv data](https://sarvdata.com/) 
* [pars dev](https://parsdev.com/vps/)
* [saba host](https://saba.host/virtual-server)
* [blue server](https://blueserver.ir/vps)
* [arvan cloud](https://www.arvancloud.com/) 

## Setting a simple v2ray with X-UI panel 
Thanks to the one-command [script](https://github.com/vaxilu/x-ui), you can install v2ray easily, even if you are not familiar with Linux commands. 

You need to have at least Ubuntu 16, Debian 8 or CentOS 7. 

This guide will be for Ubuntu.

This part just contains v2ray script installation:

### install the script
1. First make updates and upgrades, and install curl
```
   sudo apt-get update -y 
   sudo apt-get upgrade -y
   sudo apt install curl -y 
```

2. Run the x-ui script

```
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```
And that is it for the installation part.

![Panel Image](./Image/v2ui.png "Panel Image")

**Maybe in installation, you see a message that wants you to enter (Yes/No), just enter n (No)**

### Managing  v2ray
You can go to x-ui web panel typing your IP address and the port (54321) on a browser. By default, both login and password are admin. You can change them in the panel settings.

```http://"your-ip-address":54321```

**Language of the panel is Chinese, you can translate it with sites like [Translate](https://translate.google.com/) or [DeepL](https://www.deepl.com).**

To add a user, you need to go to “accounts”, press add button and fill in the blanks according to  your preferences.

* Remark – here you can write anything you want
* Protocol – vmess
* Listening IP, Port, ID (UUID) and Alter ID generated automatically. You can change them manually. 
* Transport – ws (websocket)
* Path – you can leave it the way it is or add anything you want
* Turn off TLS
* Domain – write your domain name or sub-domain name (not for this part)
* You can choose certificate file path and copy the file paths, or copy the certificate and key directly to certificate file content (not for this part)
* Copy and paste certificate and key file paths, respectively (not for this part)
* Press “Add”

And that is it. You can add, edit, delete users within seconds, and check bandwidth usage using x-ui web-panel. 

You are not only limited to vmess+ws with this web panel, you can configure and test various combinations of v2ray.

### Speed up server 
If you think your v2ray has slow speed, or have an older Linux version on your VPS, you can use bbr script by teddysun, to install google bbr. 

```
wget -N --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh && chmod +x bbr.sh && bash bbr.sh
```

### Use bridge to connect
In conditions where you can't connect to the server directly, you can tunnel an iran server in mid of the request. the following commands should are entered in the terminal (Ubuntu server):

```
apt-get update -y && apt-get upgrade -y

sysctl net.ipv4.ip_forward=1
iptables -t nat -A PREROUTING -p tcp --dport 22 -j DNAT --to-destination IRAN_IP
iptables -t nat -A PREROUTING -j DNAT --to-destination EU_IP
iptables -t nat -A POSTROUTING -j MASQUERADE
```

**Also, you can use other ways that are listed in this repo, if you don't want to buy 2 VPS** 


## Connect to v2ray
v2ray apps for Android

You can use v2ray on several apps on Android, and all of them are available for free Google Play (You can download from [here](https://www.sudoer.ir/documents/), in case you can't access Google Play).

    v2RayNG
    NapsternetV
    Clash for Android
 
v2ray apps for iOS

You can use v2ray on several apps on your iPhone/iPad as well, most of the v2ray apps are paid apps, except for 91VPN.

    NapsternetV
    ShadowRocket
    Kitsunebi
    Quantumult
    i2Ray
    Pepi
    91VPN
    Pharos Pro
    FairVPN

v2ray clients for Windows

For your Windows PC, you can choose one of these five v2ray Windows clients. And here is a download link for the three of them. There are also new softwares called Clash (download it here) and Qv2ray (download it here).

    Nekoray 
    V2RayN
    V2RayW
    V2RayS
    Clash
    Qv2ray
    Netch

v2ray clients for macOS

For your Mac, you can choose one of these four v2ray clients. Here is a download link for V2RayX and here for V2RayU. The newsest additions to the list are ClashX (Click here to download) and Qv2ray (download it here) for macOS. 

    V2RayX
    V2RayU
    ClashX
    Qv2ray


## References
* [sudoer group](https://www.sudoer.ir)
* [privacymelon](https://privacymelon.com/how-to-setup-v2ray-ws-tls-cdn/)
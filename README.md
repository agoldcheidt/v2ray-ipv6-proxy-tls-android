# V2Ray IPv6 Proxy TLS
Quickly set up an IPv6 proxy through Shadowsocks, V2Ray plugin, Nginx and Cloudflare. Android client only.

## Source Post
This bash script is based on [this post](https://talk.lowendspirit.com/discussion/1564/personal-proxy-on-ipv6-nat-ipv4-server). However, the "Let's Encrypt SSL Certificate" steps are not included, I use a Cloudflare Flexible SSL Certificate and I assume you do that as well.

## Before You Use This Script You Must Have:
<ul>
  <li>A VPS under Ubuntu 20.04 OS with a IPv6 address.</li>
 	<li>A domain name or sub-domain added on a Cloudflare account.</li>
 	<li>A "AAA" record of the VPS IPv6 added into Cloudflare account.</li>
</ul>

## Pre-Dependencies
In order to execute this script, no web servers must be previously installed. On my end, Ubuntu 20.04 comes with Apache as pre-installed web server, if that's your case, you need to uninstall apache and install curl. You can do all this by executing:
<pre>sudo apt remove --purge apache2 -y && sudo apt install curl -y</pre>

## Quick Usage
You can execute this script on-the-fly by executing:
<pre>curl -s https://raw.githubusercontent.com/agoldcheidt/v2ray-ipv6-proxy-tls/main/ipv6-proxy | bash -s yourdomainname</pre>
Replace **yourdomainname** with your current domain name or sub-domain.

![IPv6-Proxy](https://home.alexgoldcheidt.com/upload-arfalyjs/hotlink-ok/ipv6-proxy-github-image-01-1632855290-31.png "V2Ray IPv6 Proxy TLS")

## Changing Default Settings
Since this is a very simple script you can change its settings with the sed command.
<ul>
  <li>Default Shadowsocks Password: pass1234</li>
 	<li>Default V2Ray Location: /fiberweb</li>
</ul>

**To change the default password you can execute:**
<pre>sed -i "s/pass1234/mypassword/g" /etc/shadowsocks-libev/config.json && sudo systemctl restart shadowsocks-libev</pre>
Replace **mypassword** with your custom password.

**To change the default V2Ray location you can execute:**
<pre>sed -i "s/fiberweb/myrandomwords/g" /etc/shadowsocks-libev/config.json && sudo systemctl restart shadowsocks-libev</pre>
<pre>sed -i "s/fiberweb/myrandomwords/g" /etc/nginx/sites-available/default && sudo systemctl restart nginx</pre>
Replace **myrandomwords** with your custom location.

## Ubuntu 20.04 Only
During development, I've tested this script on Debian Buster/Bullseye based on KVM/NAT VPS instances from several web hosting providers, all the tests failed on Debian. For the meantime, I recommend Ubuntu 20.04 OS only.

## Android Client Only
To connect through this IPv6 proxy, you must install Shadowsocks and V2Ray plugin (both by Max Lv.) in your android device. Check the "Configure Client" section in the [Source Post](https://talk.lowendspirit.com/discussion/1564/personal-proxy-on-ipv6-nat-ipv4-server).

![IPv6-Proxy-Android](https://home.alexgoldcheidt.com/upload-arfalyjs/hotlink-ok/Screenshot_2021-09-28-15-09-41_2-1632856802-412.png "Android ShadowSocks & V2Ray Plugin")

## Credits
All credits goes to the [Source Post](https://talk.lowendspirit.com/discussion/1564/personal-proxy-on-ipv6-nat-ipv4-server) and all the great community behind it. Many thanks to [WebHorizon](https://webhorizon.in/) for provide high-speed and reliable VPS instances located on Japan and Poland.

### Support my project at: <a target="_blank" href="https://berryboot.alexgoldcheidt.com/go/support-paypal">https://paypal.me/AlexGoldcheidt</a>
&nbsp;

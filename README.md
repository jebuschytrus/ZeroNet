# ZeroNet [![Documentation](https://img.shields.io/badge/docs-faq-brightgreen.svg)](https://zeronet.io/docs/faq/)

## «Decentralized websites using Bitcoin cryptography and BitTorrent»

### Why?
* We believe in open, free, and uncensored network and communication.
* No single point of failure: Site remains online so long as at least 1 peer is
  serving it.
* No hosting costs: Sites are served by visitors.
* Impossible to shut down: It's nowhere because it's everywhere.
* Fast and works offline: You can access the site even if Internet is
  unavailable.

### Features:
 * Real-time updated sites,
 * Namecoin .bit domains support,
 * Easy to setup: unpack & run,
 * Clone websites in one click,
 * Password-less [BIP32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki)
   based authorization: Your account is protected by the same [cryptography](https://docs.google.com/presentation/d/1_2qK1IuOKJ51pgBvllZ9Yu7Au2l551t3XBgyTSvilew/pub?start=false&loop=false&delayms=3000) as your Bitcoin wallet,
 * Built-in SQL server with P2P data synchronization: Allows easier site development and faster page load times,
 * Anonymity: Full Tor network support with .onion hidden services instead of IPv4 addresses,
 * TLS encrypted connections,
 * Automatic uPnP port opening,
 * Plugin for multiuser (openproxy) support,
 * Works with any browser/OS.

### How does it work?
* After starting `zeronet.py` you will be able to visit ZeroNet sites using
  `http://127.0.0.1:43110/{zeronet_address}` (eg.
  `http://127.0.0.1:43110/1HeLLo4uzjaLetFx6NH3PMwFP3qbRbTf3D`).
* When you visit a new ZeroNet site, it tries to find peers using the BitTorrent
  network so it can download the site files (html, css, js...) from them.
* Each visited site is also served by you.
* Every site contains a `content.json` file which holds all other files in a sha512 hash
  and a signature generated using the site's private key.
* If the site owner (who has the private key for the site address) modifies the
  site, then he/she signs the new `content.json` and publishes it to the peers.
  Afterwards, the peers verify the `content.json` integrity (using the
  signature), they download the modified files and publish the new content to
  other peers.




### Screenshot:
![Screenshot](https://i.imgur.com/H60OAHY.png)



## Install ZeroNet

### Windows:
 - Download [ZeroNet-py3-win64.zip](https://github.com/HelloZeroNet/ZeroNet-win/archive/dist-win64/ZeroNet-py3-win64.zip) (18MB)
 - Unpack anywhere
 - Run `ZeroNet.exe`
 
### Linux:
 - `wget https://github.com/HelloZeroNet/ZeroNet-linux/archive/dist-linux64/ZeroNet-py3-linux64.tar.gz`
 - `tar xvpfz ZeroNet-py3-linux64.tar.gz`
 - `cd ZeroNet-linux-dist-linux64/`
 - Start with: `./ZeroNet.sh`
 - Open the ZeroHello landing page in your browser by navigating to: http://127.0.0.1:43110/
 
 __Tip:__ Start with `./ZeroNet.sh --ui_ip '*' --ui_restrict your.ip.address` to allow remote connections on the web interface.

### Install from source:
 - `wget https://github.com/HelloZeroNet/ZeroNet/archive/py3/ZeroNet-py3.tar.gz`
 - `tar xvpfz ZeroNet-py3.tar.gz`
 - `cd ZeroNet-py3`
 - `sudo apt-get update`
 - `sudo apt-get install python3-pip`
 - `sudo python3 -m pip install -r requirements.txt`
 - Start with: `python3 zeronet.py`
 - Open the ZeroHello landing page in your browser by navigating to: http://127.0.0.1:43110/



## Use ZeroNet

### Create a ZeroNet site:
Shut down ZeroNet if you are running it already.
```bash
$ zeronet.py siteCreate
...
- Site private key: 23DKQpzxhbVBrAtvLEc2uvk7DZweh4qL3fn3jpM3LgHDczMK2TtYUq
- Site address: 13DNDkMUExRf9Xa9ogwPKqp7zyHFEqbhC2
...
- Site created!
$ zeronet.py
...
```
Congratulations, you're finished! Now anyone can access your site using:
`http://localhost:43110/13DNDkMUExRf9Xa9ogwPKqp7zyHFEqbhC2`


### Modify a ZeroNet site:
* Modify files located in data/13DNDkMUExRf9Xa9ogwPKqp7zyHFEqbhC2 directory.
  After you're finished:

```bash
$ zeronet.py siteSign 13DNDkMUExRf9Xa9ogwPKqp7zyHFEqbhC2
- Signing site: 13DNDkMUExRf9Xa9ogwPKqp7zyHFEqbhC2...
Private key (input hidden):
```

* Enter the private key you got when you created the site, then:

```bash
$ zeronet.py sitePublish 13DNDkMUExRf9Xa9ogwPKqp7zyHFEqbhC2
...
Site:13DNDk..bhC2 Publishing to 3/10 peers...
Site:13DNDk..bhC2 Successfuly published to 3 peers
- Serving files....
```
* That's it! You've successfully signed and published your modifications!


#### Documentation & FAQ: 
* [ZeroNet Documentation »](https://zeronet.io/docs/site_development/getting_started/)
* [Frequently asked questions »](https://zeronet.io/docs/faq/)

#### Donate:
- Bitcoin: 1QDhxQ6PraUZa21ET5fYUCPgdrwBomnFgX

#### Contact:
* Web: https://zeronet.io
* Email: hello@zeronet.io

![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2021-01-19)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
171.25.193.78|tor-exit4-readme.dfri.se|10
171.25.193.20|tor-exit0-readme.dfri.se|10
222.187.238.97|-|9
171.25.193.77|tor-exit1-readme.dfri.se|9
185.220.102.253|tor-exit-relay-7.anonymizing-proxy.digitalcourage.de|9
185.220.102.249|tor-exit-relay-3.anonymizing-proxy.digitalcourage.de|8
185.56.80.65|onion.xor.sc|8
62.102.148.69|-|8
62.102.148.68|-|8
185.220.101.9|-|8
185.220.102.4|communityexit.torservers.net|8
77.247.181.162|chomsky.torservers.net|8
80.67.172.162|algrothendieck.nos-oignons.net|8
107.189.10.27|-|7
80.82.77.33|sky.census.shodan.io|7
31.220.1.233|-|7
185.220.102.244|185-220-102-244.torservers.net|7
185.220.102.245|185-220-102-245.torservers.net|7
185.220.102.248|tor-exit-relay-2.anonymizing-proxy.digitalcourage.de|7
217.182.192.217|ns3073700.ip-217-182-192.eu|7
178.20.55.16|marcuse-1.nos-oignons.net|7
185.220.100.253|tor-exit-2.zbau.f3netze.de|7
185.220.100.252|tor-exit-1.zbau.f3netze.de|7
185.220.100.254|tor-exit-3.zbau.f3netze.de|7
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|7
141.98.80.29|-|7
185.220.101.215|-|7
51.178.52.245|tor-exit-node.neowutran.ovh|7
174.138.12.116|-|7
185.220.101.193|-|7
162.247.74.27|turing.tor-exit.calyxinstitute.org|7
178.73.215.171|178-73-215-171-static.glesys.net|7
176.10.104.240|tor1e1.digitale-gesellschaft.ch|7
51.77.135.89|ns31066279.ip-51-77-135.eu|7
51.75.144.43|ns3129517.ip-51-75-144.eu|7
104.244.76.13|tor-exit-node.spongebob.nicdex.com|7
185.220.102.250|tor-exit-relay-4.anonymizing-proxy.digitalcourage.de|7
54.39.16.73|ns555166.ip-54-39-16.net|7
185.220.100.247|tor-exit-8.zbau.f3netze.de|7
185.220.101.17|-|7
185.220.100.241|tor-exit-14.zbau.f3netze.de|7
198.98.48.77|prod-ny1.lmao.tf|7
185.220.102.246|185-220-102-246.torservers.net|7
89.234.157.254|marylou.nos-oignons.net|7
185.191.124.151|-|7
91.192.103.10|-|7
167.88.7.134|the-windy-onion.tor-exits.alec.ninja|7
80.82.77.139|dojo.census.shodan.io|7
185.220.101.24|-|7
185.220.101.22|-|7
193.218.118.235|235.118.218.193.urdn.com.ua|7
93.174.95.106|battery.census.shodan.io|7
176.10.99.200|accessnow.org|7
198.144.120.177|-|7
45.155.205.86|-|7
45.155.205.87|-|7
91.192.103.24|-|7
185.220.101.194|-|7
5.199.130.188|tor.piratenpartei-nrw.de|7
149.202.238.204|204.238.202.149.fr-sbg.flexcloud.seflow.it|7
51.79.69.241|vps-16fb7987.vps.ovh.ca|7
45.10.55.243|unspecified.mtw.ru|7
185.220.101.207|-|7
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|7

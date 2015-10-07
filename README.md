# VPN Deploy Playbook [![Build Status](https://travis-ci.org/ftao/vpn-deploy-playbook.svg?branch=master)](https://travis-ci.org/ftao/vpn-deploy-playbook)

A collection of [Ansible](http://docs.ansible.com) Playbooks to deploy VPN and proxy services.


## Playbooks:

- [auth.yml](./auth.yml) : setup [FreeRadius](http://freeradius.org) server for authentication and accounting
- [pptp.yml](./pptp.yml) : setup PPTP server
- [l2tp.yml](./l2tp.yml) : setup IPSec/L2TP server (with pre-shared key)
- proxy-*.yml : setup [Shadowsocks](https://github.com/clowwindy/shadowsocks)
- cow-*.yml : setup [COW](https://github.com/cyfdecyf/cow)
- [ipsec.yml](./ipsec.yml) : setup IPSec IKEv1/IKEv2 VPN server with [StrongSwan](http://www.strongswan.org)
- [sane-dns.yml](./sane-dns.yml) : setup [fqdns](https://github.com/fqrouter/fqdns)
- [chinadns.yml](./chinadns.yml) : setup [ChinaDNS](https://github.com/clowwindy/ChinaDNS/)
- [openconnect.yml](./openconnect.yml) : setup [OpenConnect VPN server](http://www.infradead.org/ocserv/) for Cisco AnyConnect client
- [spdy-proxy.yml](./spdy-proxy.yml) : setup [nghttp2](https://github.com/tatsuhiro-t/nghttp2) & squid for http2/spdy proxy
- [openvpn.yml](./openvpn.yml) : setup [OpenVPN](https://openvpn.net) server
- apnp-*.yml : setup APNP (Squid + Shadowsocks tunnel)
- [sigmavpn.yml](./sigmavpn.yml) : setup [SigmaVPN](https://github.com/neilalexander/sigmavpn/)


## How to use

1. `[sudo] pip install ansible` install [Ansible](http://docs.ansible.com/intro_installation.html#id11) in control machine
2. `cp ansible_hosts{.example,}` copy `ansible_hosts.example` to `ansible_hosts`
3. edit the file to add your servers
4. edit files in `group_vars` or create and edit `host_vars/SERVER_NAME.yml` to fit your needs
5. run `ansible-playbook PLAYBOOK_NAME.yml` to setup servers

There are also some guides (in Chinese) in the [Wiki](https://github.com/ftao/vpn-deploy-playbook/wiki)


## Testing
### Vagrant

Simply clone this repo and make sure you have [Vagrant](http://www.vagrantup.com) + [Virtual Box](https://www.virtualbox.org) installed and...

``` bash
vagrant up ubuntu --no-provision
vagrant provision ubuntu
```

It may take about 10 ~ 60 minutes depends on your network. Vagrant is using Ubuntu 14.04 (ubuntu/trusty64) for it's OS. If you'd like to test on Debian Wheezy:

``` bash
vagrant up debian --no-provision
vagrant provision debian
```


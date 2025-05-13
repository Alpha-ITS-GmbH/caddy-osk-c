# caddy-osk-c

Caddy Konfiguration für das lokale Netzwerk von osk-c.osk-kiefer.com

## Installation

1. Caddy und Caddy Packages installieren
```bash
apt install -y debian-keyring debian-archive-keyring apt-transport-https curl
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | sudo gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | sudo tee /etc/apt/sources.list.d/caddy-stable.list
sudo apt update
sudo apt install caddy

dpkg-divert --divert /usr/bin/caddy.default --rename /usr/bin/caddy
cp /usr/bin/caddy.default /usr/bin/caddy.custom 
update-alternatives --install /usr/bin/caddy caddy /usr/bin/caddy.default 10
update-alternatives --install /usr/bin/caddy caddy /usr/bin/caddy.custom 50

caddy add-package github.com/mholt/caddy-l4 github.com/mholt/caddy-events-exec
```

2. In /opt clonen
```bash
git clone https://github.com/HolgerHeckeroth/caddy-alpha-its
chown -R holger:caddy /opt/caddy-alpha-its
chmod -R g+s  /opt/caddy-alpha-its
```

3. Symbolische Links erstellen
```bash
ln -s /opt/caddy-alpha-its/Caddyfile /etc/caddy/Caddyfile
```

## Update

```bash
caddy update
```
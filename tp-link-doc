
### 1. Network & Internet (Subnet & IPv4)
This moved the router to `192.168.10.1` and configured it to get internet from your Telecentro modem while ignoring problematic IPv6.

```bash
# Set LAN IP
uci set network.lan.ipaddr='192.168.10.1'

# Configure WAN to use Google DNS
uci set network.wan.peerdns='0'
uci add_list network.wan.dns='8.8.8.8'
uci add_list network.wan.dns='1.1.1.1'

# Disable IPv6 (to prevent routing conflicts)
uci delete network.wan6
uci set network.lan.ipv6='0'

uci commit network
```

### 2. Wireless (accces point)
This enabled the hardware radio and set up your Wi-Fi network.

```bash
# Enable the radio hardware
uci set wireless.radio0.disabled='0'

# Set SSID and Password
uci set wireless.default_radio0.ssid='HomeLab_WiFi'
uci set wireless.default_radio0.encryption='psk2'
uci set wireless.default_radio0.key='YourPasswordHere'

uci commit wireless
wifi reload
```

### 3. DHCP (IP Management)
This ensures devices get the correct IPs and know where the DNS server is.

```bash
# Set range from .100 to .250
uci set dhcp.lan.start='100'
uci set dhcp.lan.limit='150'

# Point clients to the Router for DNS
uci set dhcp.lan.dhcp_option='6,192.168.10.1'

# Disable IPv6 Announcements
uci delete dhcp.lan.ra
uci delete dhcp.lan.dhcpv6

uci commit dhcp
/etc/init.d/dnsmasq restart
```

---


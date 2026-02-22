# WireGuard
The thing that connects both the `VPS` and the `Lab` together.

## Public & Private Keys
Generate a private and public key for both the `VPS` and the `Lab`

```bash
wg genkey > out.key
cat out.key | wg pubkey > out.pub
```

## Configurations

### VPS
```conf
[Interface]
PrivateKey = <VPS Private>
Address = 10.8.0.1/24
ListenPort = 51820

[Peer]
PublicKey = <Lab Public>
AllowedIPs = 10.8.0.2/32
```
> /etc/wireguard/wg0.conf


### Lab
```conf
[Interface]
PrivateKey = <Lab Private>
Address = 10.8.0.2/24

[Peer]
PublicKey = <VPS Public>
Endpoint = 173.255.228.98:51820
AllowedIPs = 10.8.0.0/24
PersistentKeepalive = 25
```
> /etc/wireguard/wg0.conf

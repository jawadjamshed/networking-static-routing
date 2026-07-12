# Configuration Instructions — Networking Static Routing (3 Routers)

Full step-by-step CLI configuration for R1, R2, and R3. Enter global configuration mode (`enable` → `configure terminal`) before running each router's block.

---

## R1

```
hostname R1

interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown

interface GigabitEthernet0/1
 ip address 192.168.2.1 255.255.255.0
 no shutdown

interface Serial0/1/0
 ip address 10.0.0.1 255.255.255.0
 clock rate 2000000
 no shutdown

! Static routes toward R2's and R3's networks (via R2)
ip route 192.168.3.0 255.255.255.0 10.0.0.2
ip route 192.168.4.0 255.255.255.0 10.0.0.2
ip route 192.168.5.0 255.255.255.0 10.0.0.2
ip route 10.0.1.0 255.255.255.0 10.0.0.2
```

---

## R2

```
hostname R2

interface GigabitEthernet0/1
 ip address 192.168.5.1 255.255.255.0
 no shutdown

interface Serial0/1/0
 ip address 10.0.0.2 255.255.255.0
 no shutdown

interface Serial0/1/1
 ip address 10.0.1.2 255.255.255.0
 no shutdown

! Static routes toward R1's LANs (via R1)
ip route 192.168.1.0 255.255.255.0 10.0.0.1
ip route 192.168.2.0 255.255.255.0 10.0.0.1

! Static routes toward R3's LANs (via R3)
ip route 192.168.3.0 255.255.255.0 10.0.1.1
ip route 192.168.4.0 255.255.255.0 10.0.1.1
```

---

## R3

```
hostname R3

interface GigabitEthernet0/0
 ip address 192.168.3.1 255.255.255.0
 no shutdown

interface GigabitEthernet0/1
 ip address 192.168.4.1 255.255.255.0
 no shutdown

interface Serial0/1/1
 ip address 10.0.1.1 255.255.255.0
 clock rate 2000000
 no shutdown

! Static routes toward R1's and R2's networks (via R2)
ip route 10.0.0.0 255.255.255.0 10.0.1.2
ip route 192.168.1.0 255.255.255.0 10.0.1.2
ip route 192.168.2.0 255.255.255.0 10.0.1.2
```

---

## Save Configuration (all routers)

```
end
copy running-config startup-config
```

## Verification

Run on any router:

```
show ip route
show ip route static
show ip interface brief
ping <remote-IP>
traceroute <remote-IP>
```

Confirm every LAN can reach every other LAN across all three routers (e.g., a PC on R1's LAN 1 can ping a PC on R3's LAN 2, and a PC on R2's LAN can ping a PC on R1's LAN 2).

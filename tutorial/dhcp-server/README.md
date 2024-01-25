# Konfigurasi DHCP Server

## Pengertian
DHCP Server adalah sistem digunakan untuk memberikan layanan jaringan secara otomatis berupa pemberikan IP, Netmask, Network, Gateway, DNS, dll. Maka klien tidak perlu manual untuk pemberikan IP, Gateway, DNS, dll untuk terhubung ke jaringan.

## Konfigurasi CLI
```Html
[admin@MikroTik] > ip dhcp-server setup
Select interface to run DHCP server on 

dhcp server interface: ether2
Select network for DHCP addresses 

dhcp address space: 192.168.1.0/24
Select gateway for given network 

gateway for dhcp network: 192.168.1.1
Select pool of ip addresses given out by DHCP server 

addresses to give out: 192.168.1.2-192.168.1.254
Select DNS servers 

dns servers: 192.168.1.1,1.1.1.1
Select lease time 

lease time: 1d
[admin@MikroTik] > 
```
### Keterangan:

- **dhcp server interface:**  
  Interface yang akan dikonfigurasi DHCP Server.
- **dhcp address space:**  
  IP Network dari interface tersebut.

Untuk hasilnya bisa kita tampilkan dengan perintah **print**.

```html
[admin@MikroTik] > ip dhcp-server print 
Flags: D - dynamic, X - disabled, I - invalid 
 #    NAME                                  INTERFACE                                RELAY           ADDRESS-POOL                                LEASE-TIME ADD-ARP
 0    dhcp1                                 ether2                                                   dhcp_pool1                                  1d        
[admin@MikroTik] > ip dhcp-server network print 
Flags: D - dynamic 
 #   ADDRESS            GATEWAY         DNS-SERVER                                                 WINS-SERVER     DOMAIN                                          
 0   192.168.1.0/24     192.168.1.1     192.168.1.1,1.1.1.1,192.168.100.1,1.1.1.1                 
[admin@MikroTik] > ip pool print 
 # NAME                                                                                                                             RANGES                         
 0 dhcp_pool0                                                                                                                       192.168.1.2-192.168.1.254      
 1 dhcp_pool1                                                                                                                       192.168.1.2-192.168.1.254      
[admin@MikroTik] > 
```

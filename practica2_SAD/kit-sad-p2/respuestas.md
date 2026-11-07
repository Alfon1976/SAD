Starting Nmap 7.95 ( https://nmap.org ) at 2026-11-06 12:58 UTC
Nmap scan report for sad-p2-fw.sad-p2_calle (198.51.100.254)
Host is up (0.000097s latency).

PORT     STATE    SERVICE
22/tcp   filtered ssh
80/tcp   open     http
443/tcp  open     https
5432/tcp filtered postgresql
8080/tcp filtered http-proxy
MAC Address: 36:9F:8A:A8:72:B5 (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 1.28 seconds


09:02:57.941077 IP 198.51.100.62.50933 > 198.51.100.254.51820: UDP, length 148
09:02:57.941611 IP 198.51.100.254.51820 > 198.51.100.62.50933: UDP, length 92
09:02:57.942700 IP 198.51.100.62.50933 > 198.51.100.254.51820: UDP, length 96
09:02:57.944563 IP 198.51.100.254.51820 > 198.51.100.62.50933: UDP, length 96
09:02:57.945618 IP 198.51.100.62.50933 > 198.51.100.254.51820: UDP, length 96
09:02:57.945795 IP 198.51.100.62.50933 > 198.51.100.254.51820: UDP, length 176
6 packets captured
8 packets received by filter
0 packets dropped by kernel


# Respuestas · Práctica 2 · Bodegas Atlántico

    Rellena este fichero en tu ordenador. Va en la entrega (./lab.sh entregar) y en la defensa te pueden preguntar por él.

# Bloque A · Piensa como un atacante (nmap)

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


Desde la calle: ./lab.sh cliente y dentro nmap -Pn -p 22,80,443,5432,8080 198.51.100.254. Pega la salida:

(pega aquí la salida de nmap)




# Bloque A · El contador

Después de ./lab.sh comprobar, mira ./lab.sh ver. ¿Cuántos paquetes lleva el contador de A6? ¿Quién los ha mandado?

# Bloque B · La prueba del cifrado

En el firewall (./lab.sh fw): tcpdump -ni wan host 198.51.100.62 -c 6. Mientras, en otra terminal, el comercial (./lab.sh comercial) hace curl http://172.16.10.20:8080. Pega lo que sale en el firewall:

(pega aquí la salida de tcpdump)


09:02:57.941077 IP 198.51.100.62.50933 > 198.51.100.254.51820: UDP, length 148
09:02:57.941611 IP 198.51.100.254.51820 > 198.51.100.62.50933: UDP, length 92
09:02:57.942700 IP 198.51.100.62.50933 > 198.51.100.254.51820: UDP, length 96
09:02:57.944563 IP 198.51.100.254.51820 > 198.51.100.62.50933: UDP, length 96
09:02:57.945618 IP 198.51.100.62.50933 > 198.51.100.254.51820: UDP, length 96
09:02:57.945795 IP 198.51.100.62.50933 > 198.51.100.254.51820: UDP, length 176
6 packets captured
8 packets received by filter
0 packets dropped by kernel

En dos líneas: ¿qué se ve por la calle y qué NO se ve?

# Bloque C · Para la defensa (C4)

### C4 Surica y WAF antes el mismo ataque

Del mismo ataque (la inyección a la web): ¿qué ve el vigilante de la red (el IDS) y qué ve el portero de la web? ¿Por qué hacen falta los dos?

Vigilante de la red (IDS): Ve los paquetes de red brutos (IPs, puertos y payload). Solo alerta, no bloquea, y si el tráfico va cifrado por HTTPS, es ciego al contenido del ataque.

Portero de la web (WAF): Trabaja en capa 7 (HTTP). Como descifra el HTTPS, ve la petición completa y la bloquea al instante (403 Forbidden) antes de que llegue a la web o la base de datos.

¿Por qué hacen falta los dos? Porque se complementan (defensa en profundidad): el WAF frena ataques web cifrados en tiempo real, mientras que el IDS vigila el resto de la red interna y protocolos (SSH, escaneos, movimiento lateral) donde el WAF no llega.

# Bloque D · La nota del servidor (D0 y D4)

Nota del análisis antes de bastionar (D0):

Nota después (D4). ¿Por qué no llega a 100? ¿Significa que el servidor sigue inseguro? Comenta un aviso que siga saliendo.







# SSH-Tunnel
Zugriff auf Resourcen im Heimnetzwerk aus der Ferne per SSH-Tunnel

## SSH-Tunnel: Zugriff auf ein Heimnetzwerk aus der Ferne
Ihr möchtet aus der Ferne auf ein Gerät in eurem Heimnetzwerk zugreifen, das aus dem Internet nicht direkt erreichbar ist – z. B. die Weboberfläche eines Routers (FritzBox). Mit einem SSH-Tunnel ist das möglich.  
Voraussetzung: Ihr benötigt ein anderes Gerät in eurem Heimnetzwerk (z. B. einen Raspberry Pi), das ihr über einen separaten VPN-Tunnel wie WireGuard erreichen könnt.

**Beispiel:**

Szenario
- **Ziel:** Zugriff auf die Weboberfläche des Routers mit der IP 192.168.178.1, der auf Port 80 läuft.
- **Problem:** Der Router ist nur aus dem Heimnetz erreichbar.
- **Lösung:** Nutzt ein Gerät im Heimnetz (z. B. einen Raspberry Pi), das ihr über den VPN-Tunnel erreichen könnt, um einen SSH-Tunnel aufzubauen.
- 
### Vorgehen
#### SSH-Tunnel aufbauen
Verbindet euch per SSH via VPN zu einem Gerät im Heimnetz (z. B. der Raspberry Pi mit der WireGuard-IP 172.16.90.15) und leitet einen lokalen Port zu Port 80 des Routers weiter.

Befehl:
```
ssh pi@172.16.90.15 -L 9000:192.168.178.1:80
```
- -L 9000:192.168.178.1:80: Leitet den lokalen Port 9000 (auf eurem Computer) zu Port 80 des Routers weiter.


#### Zugriff über den Browser
1. Öffnet euren Browser.  
2. Gebt 127.0.0.1:9000 ein.  
→ Die Anfrage wird über den SSH-Tunnel an den Router weitergeleitet, und ihr seht dessen Weboberfläche.

## Warum SSH-Tunnel?
- Sicherheit: Die Verbindung ist verschlüsselt, das Gerät bleibt aus dem Internet unsichtbar.
- Flexibilität: Ihr könnt lokal auf entfernte Ressourcen zugreifen, als wärt ihr direkt im Heimnetz.
## Fazit
SSH-Tunneling ist eine einfache und sichere Methode, um entfernte Ressourcen zugänglich zu machen – ideal für Hobb-Netzwerkadministration und Fernwartung.

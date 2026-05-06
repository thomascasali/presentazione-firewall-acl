# Quiz Completo - Firewall e ACL

## Domande a Scelta Multipla (15 domande)

**1. Qual è la funzione principale di un firewall?**
a) Aumentare la velocità della rete
b) Filtrare il traffico in base a regole definite*
c) Crittografare tutti i dati
d) Eliminare i virus dai file

**2. Quale tra questi è un tipo di firewall stateful?**
a) Packet Filter puro
b) Application Level Gateway
c) Firewall che traccia le connessioni attive*
d) Nessuno dei precedenti

**3. In una DMZ, quali server devono essere posizionati?**
a) Solo i server database
b) I server raggiungibili da Internet (Web, Mail, DNS)*
c) Tutti i server aziendali
d) Solo i server di backup

**4. Qual è la differenza principale tra una Standard ACL e una Extended ACL?**
a) La Standard filtra per IP sorgente, l'Extended filtra per sorgente, destinazione e porta*
b) La Standard è più veloce della Extended
c) La Extended non può bloccare il traffico
d) Non c'è differenza, sono sinonimi

**5. Cosa rappresenta il numero "0" in una wildcard mask?**
a) Un bit che può avere qualsiasi valore
b) Un bit che DEVE corrispondere esattamente*
c) Un bit che viene sempre ignorato
d) Un bit di controllo di parità

**6. Quale wildcard mask matcha l'intera rete /24?**
a) 0.0.0.0
b) 255.255.255.0
c) 0.0.0.255*
d) 255.255.255.255

**7. Se una ACL non corrisponde a nessuna regola esplicita, cosa accade?**
a) Il pacchetto viene automaticamente permesso
b) Il pacchetto viene bloccato dall'implicit deny*
c) Il pacchetto viene duplicato
d) Il pacchetto viene reinviato al mittente

**8. Dove devono essere posizionate le Standard ACL per essere più efficienti?**
a) Vicino alla sorgente del traffico
b) Vicino alla destinazione del traffico*
c) Nel mezzo della rete
d) Sulla WAN

**9. Qual è il principio di base della Defense in Depth?**
a) Usare un solo firewall molto potente
b) Implementare più livelli di sicurezza per proteggere i dati*
c) Bloccare tutti i pacchetti in arrivo
d) Affidare la sicurezza solo a password forti

**10. Cosa filtra principalmente un IDS (Intrusion Detection System)?**
a) Indirizzi IP in arrivo
b) Anomalie e attacchi nel traffico di rete*
c) Solo il traffico sulla porta 80
d) Virus nei file locali

**11. Quale affermazione su IPS è corretta?**
a) L'IPS è sempre passivo e non blocca il traffico
b) L'IPS è posizionato in parallelo alla rete
c) L'IPS è posizionato in linea e può bloccare attacchi*
d) L'IPS funziona solo per email

**12. In quale scenario è preferibile usare una Extended ACL?**
a) Quando si vuole filtrare solo per IP sorgente
b) Quando si deve filtrare per sorgente, destinazione, protocollo e porta*
c) Quando non si ha accesso al router
d) Quando la rete ha meno di 10 host

**13. Quale comando Cisco applica un'ACL 100 in ingresso su un'interfaccia?**
a) access-group 100 in*
b) ip access-group 100 in*
c) apply acl 100 inbound
d) filter 100 in

**14. Cos'è una Named ACL?**
a) Un'ACL con il nome del router
b) Un'ACL che usa nomi invece di numeri e permette modifiche singole*
c) Un'ACL che filtra solo i nomi di dominio
d) Un'ACL visibile a tutti gli utenti della rete

**15. In una architettura a DMZ, il DB Server dove dovrebbe trovarsi?**
a) Su Internet insieme ai Web Server
b) Nella DMZ con i Web Server
c) Nella rete interna, raggiungibile solo dai server DMZ necessari*
d) In una rete separata senza connessione ad Internet

---

## Domande a Risposta Aperta (5 domande)

**1. Spiega la differenza tra il principio "Default Deny" e "Default Allow" in una firewall policy. Quale è più sicuro e perché?**

**Chiave di Risposta (circa 80 parole):**
Default Deny blocca tutto il traffico non esplicitamente permesso (approccio whitelist), è più sicuro perché richiede di autorizzare consapevolmente ogni servizio. Default Allow permette tutto tranne ciò che è esplicitamente bloccato (approccio blacklist), è meno sicuro perché un nuovo tipo di attacco non previsto può passare. In ambienti aziendali si preferisce Default Deny: fornisce controllo granulare, migliore conformità normativa, e riduce la superficie di attacco.

---

**2. Descrivi il processo di negoziazione di una connessione in un firewall Stateful Inspection. Come il firewall mantiene traccia della connessione?**

**Chiave di Risposta (circa 80 parole):**
Quando un client apre una connessione, il firewall Stateful crea una entry nella Connection State Table registrando: IP sorgente/destinazione, porte, protocollo, stato della connessione (NEW, ESTABLISHED, CLOSED), timestamp. Il firewall traccia il three-way handshake TCP (SYN, SYN-ACK, ACK). I pacchetti di risposta da destinazione sono automaticamente permessi senza consultare le ACL di ingresso, perché riconosciuti come parte di una connessione già autorizzata. Quando la connessione termina o scade il timeout, l'entry viene rimossa.

---

**3. Sei un amministratore di rete e devi configurare una ACL per permettere solo HTTP/HTTPS da Internet verso un Web Server (192.168.1.10) in DMZ, bloccando tutto il resto. Scrivi le linee di configurazione necessarie.**

**Chiave di Risposta (circa 80 parole):**
```
access-list 100 permit tcp any host 192.168.1.10 eq 80
access-list 100 permit tcp any host 192.168.1.10 eq 443
access-list 100 deny ip any any

interface GigabitEthernet0/0
  ip access-group 100 in
```
La prima regola permette HTTP (porta 80), la seconda HTTPS (porta 443) solo verso l'host specifico. La terza riga nega tutto il resto (explicit deny). Si applica in ingresso per bloccare subito traffico indesiderato. Fondamentale l'ordine: la prima regola che matcha vince (first match wins).

---

**4. Spiega cosa è una DMZ, perché è importante, e come le ACL la rendono funzionante. Fai un esempio concreto con 3 server.**

**Chiave di Risposta (circa 80 parole):**
Una DMZ è una zona cuscinetto tra Internet e la rete interna. Se un server Web (DMZ) viene compromesso, l'attaccante non accede automaticamente al DB interno. Le ACL implementano questa segmentazione: permettono Internet→Web (porte 80, 443), bloccano Internet→LAN interna, permettono Web→DB (porta 3306) soltanto dal Web Server. Esempio: Web Server (DMZ) raccoglie dati, FTP Server (DMZ) riceve upload, DB Server (LAN interna) accessibile solo dal Web. Se FTP viene compromesso, non può toccare il DB.

---

**5. Confronta un Packet Filter puro con un firewall Stateful Inspection. Quali sono i vantaggi e i limiti di ciascuno?**

**Chiave di Risposta (circa 80 parole):**
Packet Filter puro esamina ogni pacchetto isolatamente (sorgente, destinazione, porta), è veloce ma stateless: non sa se un pacchetto è risposta a una connessione precedente, quindi spesso permette tutto il traffico di risposta (inefficiente). Stateful Inspection traccia lo stato delle connessioni, permette risposte solo se la connessione è stata autorizzata, è più sicuro contro attacchi come spoofing. Vantaggi Stateful: migliore sicurezza, minor carico CPU (regole semplici), protegge contro SYN flood. Limite: più complesso, maggior overhead memoria per state table.

---

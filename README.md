# Firewall & Access Control List - Corso Completo

**[Apri la presentazione](https://thomascasali.github.io/presentazione-firewall-acl/)**

Presentazione interattiva su Firewall e ACL per il corso di Sistemi e Reti.

---

## Contenuti

| Modulo | Titolo | Slide | Argomenti |
|--------|--------|-------|-----------|
| 1 | Fondamenti Firewall | 7 | Definizione, posizionamento, DMZ, Defense in Depth, principi (Default Deny/Allow) |
| 2 | Tipologie Firewall | 10 | Packet Filter, Stateful Inspection, Application Level Gateway, NGFW |
| 3 | Access Control List | 15 | ACL Standard/Extended, Wildcard Mask, Named ACL, configurazione Cisco |
| 4 | Firewall Linux | 14 | iptables, nftables, UFW, NAT, Masquerading, tables/chains/rules |
| 5 | Windows Firewall | 8 | Profili di rete, Windows Defender Firewall, PowerShell, netsh |
| 6 | Quiz & Riepilogo | 5 | Quiz 15 domande, simulatori di scenario, riepilogo concetti |

**Totale: 59 slide**

---

## Simulatori Interattivi

La presentazione include **12 simulatori** per l'apprendimento pratico:

### Modulo 1 - Fondamenti
- **Network Topology Simulator**: Visualizza il flusso dei pacchetti in diverse architetture di rete (senza firewall, perimetrale, DMZ)
- **Defense in Depth Simulator**: Simula attacchi attraverso livelli di sicurezza multipli con probabilità di blocco

### Modulo 2 - Tipologie
- **Packet Filter Simulator**: Configura regole di filtraggio e testa pacchetti in tempo reale
- **Firewall Type Comparator**: Confronta le caratteristiche dei diversi tipi di firewall

### Modulo 3 - ACL
- **ACL Builder**: Costruttore interattivo di Access Control List Cisco
- **Wildcard Mask Calculator**: Calcola wildcard mask da subnet mask e viceversa

### Modulo 4 - Linux
- **iptables Rule Builder**: Genera comandi iptables selezionando table, chain, protocol e target
- **Packet Flow Visualizer**: Visualizza il percorso dei pacchetti attraverso le chain di Netfilter

### Modulo 5 - Windows
- **Profile Switcher**: Simula il cambio di profilo di rete e le relative policy
- **PowerShell Rule Builder**: Genera comandi PowerShell per Windows Firewall

### Modulo 6 - Quiz
- **Quiz Interattivo**: 15 domande con feedback immediato e spiegazioni
- **Scenario Challenge**: Sfide pratiche di configurazione firewall

---

## Caratteristiche

- **59 slide** interattive organizzate in 6 moduli
- **12 simulatori** per apprendimento pratico
- **Quiz finale** con 15 domande e spiegazioni dettagliate
- **Design moderno** con tema scuro e gradienti
- **Navigazione intuitiva** da tastiera (frecce, spazio, M per menu, ESC per indice)
- **Fully responsive**: ottimizzato per digital board, desktop, tablet e smartphone
- **Animazioni fluide** e feedback visivo interattivo

---

## Tecnologie

- HTML5 + CSS3 (con CSS Grid, Flexbox, clamp(), media queries)
- React 18 (via CDN)
- Babel standalone (transpiler JSX)
- SVG per diagrammi e visualizzazioni
- Google Fonts (Inter, JetBrains Mono, Space Grotesk)

---

## Come usare

### Online
Visita: **https://thomascasali.github.io/presentazione-firewall-acl/**

### Locale
1. Clona il repository: `git clone https://github.com/thomascasali/presentazione-firewall-acl.git`
2. Apri `index.html` nel browser
3. Naviga tra i moduli cliccando sulle card
4. Usa le frecce ← → o i pulsanti per navigare tra le slide
5. Premi ESC per tornare all'indice

### Controlli tastiera
| Tasto | Azione |
|-------|--------|
| → / Spazio | Slide successiva |
| ← | Slide precedente |
| ESC | Torna all'indice |
| M | Apri/chiudi menu |

---

## Struttura del progetto

```
presentazione-firewall-acl/
├── index.html                    # Pagina principale con indice moduli
├── modulo1-firewall-intro.html   # Fondamenti Firewall
├── modulo2-firewall-types.html   # Tipologie Firewall
├── modulo3-acl.html              # Access Control List
├── modulo4-linux-firewall.html   # Firewall Linux
├── modulo5-windows-firewall.html # Windows Firewall
├── modulo6-quiz.html             # Quiz e Riepilogo
└── README.md                     # Questo file
```

---

## Licenza

Materiale didattico per uso educativo.

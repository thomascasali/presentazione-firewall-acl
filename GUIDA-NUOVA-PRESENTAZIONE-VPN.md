# Guida: Creazione Presentazione VPN

## Passo 1: Crea il repository GitHub

1. Vai su https://github.com/new
2. Nome repository: `presentazione-vpn`
3. Descrizione: "Presentazione interattiva sulle VPN per il corso di Sistemi e Reti"
4. Pubblico
5. Spunta "Add a README file"
6. Clicca "Create repository"

## Passo 2: Attiva GitHub Pages

1. Vai in **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: **main** / **/ (root)**
4. Salva

## Passo 3: Clona il repository

```bash
git clone https://github.com/thomascasali/presentazione-vpn.git
cd presentazione-vpn
```

## Passo 4: Copia il file CLAUDE.md nella root del repo

Copia il file `CLAUDE.md` (sezione sotto) nella root del nuovo repository. Questo file viene letto automaticamente da Claude Code all'inizio di ogni sessione.

## Passo 5: Avvia Claude Code e incolla il prompt di avvio

```bash
claude
```

Poi incolla il **Prompt di Avvio** (sezione sotto).

---

# CLAUDE.md

Crea il file `CLAUDE.md` nella root del repository con questo contenuto:

```markdown
# Presentazione VPN - Corso Sistemi e Reti

## Stack Tecnologico
- HTML5 + CSS3 (CSS Grid, Flexbox, clamp(), media queries)
- React 18 via CDN (unpkg.com)
- Babel standalone per transpilazione JSX
- SVG per diagrammi e visualizzazioni
- Google Fonts: Inter, JetBrains Mono, Space Grotesk
- NESSUN bundler, NESSUN npm, NESSUN framework aggiuntivo. Solo file HTML standalone.

## Architettura
- `index.html`: pagina principale con indice dei moduli (card cliccabili)
- `modulo1-*.html`, `modulo2-*.html`, ecc.: un file HTML per modulo
- Ogni file HTML è completamente standalone (include React, Babel, CSS inline)
- I componenti React sono definiti dentro un tag `<script type="text/babel">` nel file HTML

## Design System
Tema scuro con questi colori (definiti come oggetto `colors` in ogni file):
```js
const colors = {
  bg: '#0a0e17', bgCard: '#111827', bgLight: '#1e293b',
  accent: '#00d4aa',      // colore primario (verde acqua)
  accentAlt: '#0ea5e9',   // colore secondario (blu)
  text: '#f1f5f9', textDim: '#94a3b8', textMuted: '#64748b',
  border: '#334155',
  success: '#22c55e', danger: '#ef4444', warn: '#f59e0b',
  info: '#0ea5e9', purple: '#a78bfa', cyan: '#22d3ee'
};
```
NOTA: il colore `accent` può variare per modulo per differenziare visivamente.

## Componenti Riutilizzabili (da definire in ogni file)
- `Code({ children, title })`: blocco codice con syntax highlighting
- `Box({ type, title, children })`: callout info/warn/danger/tip/success
- `Table({ headers, rows })`: tabella stilizzata
- `Glow({ children, color })`: card con bordo luminoso gradient

## Responsive Design - CRITICO
Il target primario è una **digital board 2400x1600** e deve funzionare anche su mobile.

### Container principale:
```css
maxWidth: '2200px', width: '94%', margin: '0 auto'
```

### Media queries obbligatorie in ogni file:
- `max-width: 1024px`: font-size 15px
- `max-width: 768px`: font-size 14px, grid 1fr, svg responsive, pre wrap
- `max-width: 480px`: font-size 13px, bottoni full-width
- `min-width: 1600px`: font-size 18px, h1 52px, h2 34px
- `min-width: 2000px`: font-size 20px, h1 60px, h2 38px
- `min-width: 2400px`: font-size 22px, h1 68px, h2 44px

### Testo responsivo: usare SEMPRE clamp()
```css
fontSize: 'clamp(14px, 1.3vw, 18px)'  /* testo normale */
fontSize: 'clamp(12px, 1.1vw, 15px)'  /* testo piccolo */
fontSize: 'clamp(16px, 1.5vw, 22px)'  /* titoli sezione */
```

### SVG responsivi: usare SEMPRE viewBox
```jsx
<svg viewBox="0 0 600 200" style={{ width: '100%', maxWidth: '700px' }}>
```

## Navigazione
- Freccia destra / Spazio: slide successiva
- Freccia sinistra: slide precedente
- ESC: torna all'indice
- Barra superiore fissa: nome modulo + contatore slide + progress bar
- Barra inferiore fissa: bottoni navigazione + link modulo precedente/successivo

## Simulatori Interattivi
Ogni modulo deve avere almeno 1-2 simulatori interattivi con:
- Input chiari con label
- Feedback visivo immediato (colori, animazioni)
- Scenari preconfigurati per test rapidi
- Spiegazione di cosa fa il simulatore prima degli input

## Struttura Slide
Ogni modulo segue questa struttura:
1. Slide titolo (centrata, con icona, nome modulo, titolo, sottotitolo)
2. Slide concetti teorici (con diagrammi SVG e box informativi)
3. Slide esempi pratici (con blocchi Code e scenari)
4. Slide simulatori interattivi
5. Slide best practices/riepilogo

## Link GitHub Pages
https://thomascasali.github.io/presentazione-vpn/
```

---

# Prompt di Avvio

Incolla questo prompt nella nuova sessione Claude Code:

---

Devi creare una presentazione interattiva completa sulle **VPN (Virtual Private Network)** per un corso di Sistemi e Reti di una scuola superiore (ITIS). La presentazione deve essere moderna, interattiva e ricca di simulatori.

## Riferimento
Prendi come riferimento di qualità, stile e struttura la presentazione esistente su Firewall/ACL:
https://thomascasali.github.io/presentazione-firewall-acl/

Leggi il file CLAUDE.md nella root del repository per le specifiche tecniche del design system, stack e pattern da seguire.

## Struttura dei Moduli

### Modulo 1: Fondamenti VPN (8-10 slide)
- Cos'è una VPN e perché serve (analogia: tunnel privato in autostrada pubblica)
- Problemi di sicurezza su rete pubblica (sniffing, MITM, intercettazione)
- Concetti chiave: tunneling, crittografia, autenticazione, integrità
- Tipi di VPN: Site-to-Site vs Remote Access vs Client-to-Client
- Protocolli di tunneling overview (IPsec, SSL/TLS, WireGuard)
- **Simulatore**: Visualizzatore di pacchetto prima e dopo incapsulamento VPN (mostra payload in chiaro vs crittografato)

### Modulo 2: IPsec in Dettaglio (8-10 slide)
- Architettura IPsec: AH vs ESP
- Modalità Transport vs Tunnel (con diagrammi SVG)
- IKE Phase 1 e Phase 2 (negoziazione, Diffie-Hellman)
- Security Association (SA) e SPI
- Configurazione IPsec site-to-site su router Cisco (comandi reali)
- **Simulatore**: Visualizzatore IKE handshake step-by-step (mostra ogni fase della negoziazione)
- **Simulatore**: Confronto visivo AH vs ESP (cosa viene protetto, cosa no)

### Modulo 3: VPN SSL/TLS e OpenVPN (8-10 slide)
- Come funziona SSL/TLS per le VPN
- Differenza tra IPsec VPN e SSL VPN
- OpenVPN: architettura e funzionamento
- Configurazione OpenVPN server e client (file .ovpn)
- Certificati e PKI (CA, certificato server, certificato client)
- **Simulatore**: Generatore di configurazione OpenVPN (l'utente sceglie parametri e vede il file .ovpn generato)

### Modulo 4: WireGuard e VPN Moderne (6-8 slide)
- WireGuard: perché è rivoluzionario (semplicità, performance, codice minimale)
- Confronto WireGuard vs IPsec vs OpenVPN (tabella comparativa)
- Configurazione WireGuard (chiavi, interfacce, peer)
- VPN commerciali vs VPN self-hosted
- **Simulatore**: Confronto performance/complessità tra protocolli VPN

### Modulo 5: Scenari Pratici e Laboratorio (6-8 slide)
- Scenario 1: Collegare due sedi aziendali (Site-to-Site)
- Scenario 2: Smart working sicuro (Remote Access)
- Scenario 3: Accesso sicuro a servizi interni
- Split tunneling vs Full tunneling
- Troubleshooting VPN comuni
- **Simulatore**: Configuratore di scenario VPN (l'utente sceglie lo scenario e vede la configurazione completa)

### Modulo 6: Quiz e Riepilogo (4-5 slide)
- Quiz interattivo 15 domande (stile presentazione Firewall)
- Riepilogo concetti chiave
- Risorse per approfondimento

## Istruzioni Operative

1. **Crea PRIMA `index.html`** con l'indice di tutti i moduli (card con icone, descrizioni, contatore slide, tag argomenti)
2. **Poi crea un modulo alla volta**, partendo dal Modulo 1
3. Ogni file HTML deve essere **completamente standalone**
4. Usa **SVG con viewBox** per tutti i diagrammi (NO immagini esterne)
5. Ogni simulatore deve avere **scenari preconfigurati** cliccabili per test rapidi
6. Il testo deve usare **clamp()** per essere responsivo
7. Aggiorna `README.md` con la struttura completa, link Pages e lista simulatori
8. Fai **commit dopo ogni modulo completato**

Inizia creando `index.html` e il `Modulo 1`.

---

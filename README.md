<p align="center">
  <img src="docs/immagini/banner.png" alt="HikAccess Pro Web, la console web per il controllo accessi Hikvision" width="100%">
</p>

<p align="center">
  <a href="https://github.com/brn78/HikAccess-Pro-Web/releases/latest"><img alt="Ultima versione" src="https://img.shields.io/github/v/release/brn78/HikAccess-Pro-Web?label=versione&color=2563eb"></a>
  <img alt="Windows 10, 11 e Server 2016 o successivi" src="https://img.shields.io/badge/Windows-10%20%7C%2011%20%7C%20Server%202016%2B-0078D4?logo=windows&logoColor=white">
  <img alt="Hikvision ISAPI e SDK" src="https://img.shields.io/badge/Hikvision-ISAPI%20%7C%20SDK-E3001B">
  <img alt="Notifiche Telegram" src="https://img.shields.io/badge/notifiche-Telegram-26A5E4">
  <img alt="Versione gratuita: 1 sito e 2 varchi" src="https://img.shields.io/badge/versione%20gratuita-1%20sito%20%C2%B7%202%20varchi-16A34A">
  <img alt="Interfaccia in italiano" src="https://img.shields.io/badge/lingua-italiano-009246">
</p>

<p align="center">
  <a href="https://github.com/brn78/HikAccess-Pro-Web/releases/latest"><b>⬇️ Scarica il setup</b></a>
  &nbsp;·&nbsp;
  <a href="docs/guida-utente.md"><b>📖 Guida utente</b></a>
  &nbsp;·&nbsp;
  <a href="#-versione-gratuita-e-licenza"><b>🔑 Licenza</b></a>
  &nbsp;·&nbsp;
  <a href="#-domande-frequenti"><b>❓ Domande frequenti</b></a>
</p>

---

**HikAccess Pro Web** gestisce il controllo accessi **Hikvision** di una o più sedi da un'unica console web: varchi,
gruppi di accesso con fasce orarie e festività, utenti con tessere Mifare e PIN, comandi delle porte, monitoraggio in
tempo reale, storico degli eventi e notifiche Telegram. Si installa su un PC o un server Windows della rete, gira come servizio e si usa da qualsiasi browser, dal PC,
dal tablet o dal telefono, con account personali e ruoli.

Funziona anche su reti isolate, senza Internet e senza abbonamenti cloud: configurazione ed eventi restano sul tuo server.

<p align="center">
  <img src="docs/immagini/dashboard.png" alt="Dashboard con stato dei varchi, attività in tempo reale e transiti del giorno" width="100%">
</p>

## ✨ Funzionalità

<table>
<tr>
<td width="50%" valign="top">

**🏢 Multisito**<br>
Più sedi in una sola console, ognuna con i suoi varchi e gruppi di accesso, anche con giorni e fasce orarie; gli
utenti sono unici per tutto l'impianto.

**📅 Festività**<br>
Festività nazionali calcolate da sole (anche Pasqua), il **santo patrono** della località e le chiusure aziendali:
i gruppi con fasce orarie restano chiusi in quei giorni, direttamente sui controller.

**🚪 Varchi Hikvision**<br>
Terminali e controller via HTTP/ISAPI oppure con l'SDK Hikvision sulla porta 8000, anche multi-porta (per esempio i
DS-K2604). Apertura, chiusura, sblocco e blocco permanente, stato della porta, orologio con ora legale, diagnostica,
operazioni su più varchi insieme.

**💳 Utenti, tessere e PIN**<br>
Anagrafica completa, più tessere per persona, validità e gruppi. Il badge si legge dal lettore del varco, e
*Identifica badge* dà un nome alle tessere sconosciute. Le tessere tolte vengono revocate subito su tutti i varchi (e
ritentate da sole sui controller spenti). Invio, gruppo, abilitazione ed eliminazione di più utenti in una volta.

**📊 Monitoraggio in tempo reale**<br>
I controller inviano ogni passaggio appena avviene e il server legge comunque i loro registri senza saltare eventi,
anche con la console chiusa: dashboard, accessi negati, storico degli eventi con ricerca ed esportazione CSV.

</td>
<td width="50%" valign="top">

**👥 Operatori e sicurezza**<br>
Account personali con ruoli (amministratore, operatore, sola lettura), verifica in due passaggi, blocco dei tentativi
errati e registro attività di ogni operazione.

**🔔 Notifiche Telegram**<br>
Ogni operatore collega la sua chat con un QR e un PIN e sceglie cosa ricevere: accessi negati, porta forzata o aperta
troppo a lungo, allarmi, varchi non raggiungibili, solo per alcuni varchi o alcune persone. Nessuna porta da aprire sul
router. *Con licenza.*

**🏠 Home Assistant e domotica**<br>
Servizio REST con chiavi API per aprire i varchi da Home Assistant o da altri sistemi, con varchi consentiti e
scadenza per ogni chiave. *Con licenza.*

**🌐 Accesso da fuori**<br>
Pubblicazione tramite un proxy HTTPS, per esempio KeenDNS dei router Keenetic, con il riconoscimento dei proxy
attendibili.

**⚙️ Pensato per il server**<br>
Servizio di Windows con avvio automatico e icona di stato, backup e ripristino, invio di tutti gli utenti a tutti i
varchi, avviso quando esce una nuova versione e aggiornamento in un clic con **Scarica e installa**.

</td>
</tr>
</table>

## 🖼️ Uno sguardo alla console

<table>
<tr>
<td width="50%" align="center"><img src="docs/immagini/varchi.png" alt="Pagina Varchi"><br><b>Varchi</b>: stato, canale, seriale e comandi</td>
<td width="50%" align="center"><img src="docs/immagini/utenti.png" alt="Scheda di un utente"><br><b>Utenti e tessere</b>: la scheda della persona</td>
</tr>
<tr>
<td align="center"><img src="docs/immagini/eventi.png" alt="Eventi e storico"><br><b>Eventi e storico</b>: filtri, ricerca ed esportazione</td>
<td align="center"><img src="docs/immagini/chiavi-api.png" alt="Chiavi API"><br><b>Chiavi API</b>: endpoint pronti per Home Assistant</td>
</tr>
<tr>
<td align="center"><img src="docs/immagini/notifiche.png" alt="Notifiche Telegram nel profilo dell'operatore"><br><b>Notifiche Telegram</b>: eventi, varchi e persone per ogni operatore</td>
<td align="center"><img src="docs/immagini/festivita.png" alt="Calendario delle festività"><br><b>Festività</b>: nazionali, santo patrono e chiusure</td>
</tr>
<tr>
<td align="center"><img src="docs/immagini/dashboard-chiaro.png" alt="Dashboard con il tema chiaro"><br><b>Tema chiaro o scuro</b>, anche automatico</td>
<td align="center"><img src="docs/immagini/sistema.png" alt="Pagina Sistema"><br><b>Sistema</b>: impostazioni, operatori, licenza e backup</td>
</tr>
<tr>
<td align="center"><img src="docs/immagini/accesso.png" alt="Pagina di accesso"><br><b>Accesso protetto</b>, con verifica in due passaggi</td>
<td align="center"><img src="docs/immagini/guida.png" alt="Guida utente nella console"><br><b>Guida integrata</b>: <kbd>F1</kbd> da qualsiasi pagina</td>
</tr>
<tr>
<td colspan="2" align="center"><img src="docs/immagini/mobile.png" alt="Dashboard sul telefono" width="23%"><br><b>Anche dal telefono</b></td>
</tr>
</table>

## ⬇️ Download

Scarica **`HikAccessWeb-<versione>-Setup.exe`** dalla pagina
[Releases](https://github.com/brn78/HikAccess-Pro-Web/releases/latest). Il setup contiene tutto il necessario, compreso
il runtime .NET: non serve installare altro.

## 💻 Requisiti

- **Server**: Windows 10 o 11, oppure Windows Server 2016, 2019, 2022 o 2025, a 64 bit, sempre acceso e in rete con i
  varchi.
- **Varchi**: terminali e controller di controllo accessi Hikvision raggiungibili via HTTP/ISAPI (porta 80) oppure SDK
  (porta 8000).
- **Postazioni**: un browser recente (Edge, Chrome, Firefox, Safari) su PC, tablet o telefono.

## 🚀 Installazione in quattro passi

1. **Esegui il setup sul server** come amministratore: scegli la porta della console (predefinita 5080) e, se vuoi, crea
   subito l'account amministratore. Il setup installa il servizio di Windows, apre la porta nel firewall e controlla
   che la console risponda.
2. **Apri la console** da qualsiasi PC della rete: `http://<nome-o-IP-del-server>:5080`.
3. **Aggiungi i varchi** da *Varchi → Aggiungi varco*: indirizzo IP, utente e password del dispositivo.
4. **Carica gli utenti**: riceverli dai varchi o inserirli a mano; tessere e permessi arrivano da soli ai dispositivi.

Per aggiornare basta premere **Scarica e installa** in *Sistema → Impostazioni → Aggiornamento del programma*: il
server scarica il setup da qui, ne controlla l'impronta, salva una copia della configurazione e lo installa; dati,
account e licenza restano. Quando esce una nuova versione la console avvisa gli amministratori, con le novità.
Tutti i dettagli sono nella [guida utente](docs/guida-utente.md#server).

## 🔑 Versione gratuita e licenza

HikAccess Pro Web si usa **gratis e senza scadenza** con un impianto piccolo. Per più sedi o varchi, per collegare
Home Assistant o per le notifiche Telegram serve una licenza.

| | Versione gratuita | Con licenza |
|---|:---:|:---:|
| Siti | 1 | secondo la licenza, anche illimitati |
| Varchi | 2 | secondo la licenza, anche illimitati |
| Utenti, tessere, PIN, gruppi, eventi, operatori, backup, accesso da fuori | ✓ | ✓ |
| Servizio REST per Home Assistant (chiavi API) | — | ✓ |
| Notifiche Telegram agli operatori | — | ✓ |
| Scadenza | nessuna | nessuna, oppure a tempo (per esempio la prova di 30 giorni) |

**Come si attiva**

1. Nella console apri **Sistema → Licenza**: in alto c'è il **codice macchina** del server.
2. Compila **Richiedi l'attivazione** e premi **Scrivi l'email**: la richiesta parte già pronta, con il codice macchina
   e i dati del server. Si può chiedere anche una **prova gratuita di 30 giorni** con tutte le funzioni.
3. Incolla la **chiave di attivazione** ricevuta (inizia con `HAP1-`) e premi **Attiva**: i nuovi limiti valgono subito,
   senza reinstallare.

La chiave vale solo per il server per cui è stata emessa. Se la licenza scade si torna alla versione gratuita senza
perdere nulla: i varchi in più restano configurati ma sospesi, e la revoca delle tessere li raggiunge comunque.

<p align="center">
  <img src="docs/immagini/licenza.png" alt="Pagina Licenza con codice macchina e richiesta di attivazione" width="85%">
</p>

## 📖 Guida utente

La **[guida utente completa](docs/guida-utente.md)** descrive ogni pagina della console, dall'installazione alla
risoluzione dei problemi. È la stessa che si apre nella console con <kbd>F1</kbd>, con l'indice, la ricerca e la stampa
in PDF.

## 🔒 Sicurezza in breve

- Accesso con password e ruoli, **verifica in due passaggi** con un'app di autenticazione e browser di fiducia.
- Blocco dei tentativi errati, sessioni che scadono per inattività, cookie protetti.
- Le password dei varchi non arrivano mai al browser; quelle degli operatori sono salvate solo come impronta.
- **Registro attività** di accessi, comandi e modifiche, esportabile in CSV.
- Nessun servizio cloud: configurazione ed eventi restano sul server.

## ❓ Domande frequenti

<details>
<summary><b>Quali dispositivi Hikvision posso usare?</b></summary>
<br>
I terminali e i controller di controllo accessi Hikvision raggiungibili in rete via HTTP/ISAPI, la gestione «a
persone» con nome, tessere, PIN e validità, oppure con l'SDK Hikvision sulla porta di servizio 8000, come fa
iVMS-4200: per esempio i controller DS-K2604 di prima generazione. Nei controller multi-porta si crea un varco per
ogni porta.
</details>

<details>
<summary><b>Se il server è spento, le porte si aprono ancora?</b></summary>
<br>
Sì. Tessere, PIN e permessi sono memorizzati nei dispositivi, che funzionano da soli. Il server serve a gestirli e a
raccogliere gli eventi: quando torna acceso recupera anche i passaggi avvenuti nel frattempo.
</details>

<details>
<summary><b>Serve una connessione a Internet?</b></summary>
<br>
No. Server e varchi lavorano nella rete locale. Internet serve solo se vuoi usare la console da fuori (tramite un proxy
HTTPS o una VPN), per le notifiche Telegram, per l'aggiornamento con *Scarica e installa* e per inviare la richiesta di
attivazione.
</details>

<details>
<summary><b>Come funzionano le notifiche Telegram?</b></summary>
<br>
Si crea un bot con @BotFather e se ne incolla il token in <b>Sistema → Impostazioni</b>. Ogni operatore collega poi la
sua chat dal proprio <b>Profilo</b>, inquadrando un QR e scrivendo al bot il PIN mostrato, e sceglie quali eventi, varchi
e persone gli interessano; gli amministratori possono impostarlo anche per gli altri. È il server a contattare Telegram,
quindi non serve aprire porte sul router. Con <code>/stop</code> nella chat si scollega.
</details>

<details>
<summary><b>Posso provare la versione completa?</b></summary>
<br>
Sì: dalla pagina <b>Licenza</b> scegli <b>Prova di 30 giorni</b> nella richiesta. Alla scadenza la console torna alla
versione gratuita senza perdere configurazione ed eventi.
</details>

<details>
<summary><b>Cosa succede se cambio server o reinstallo Windows?</b></summary>
<br>
Il codice macchina cambia, quindi serve una chiave nuova: dalla pagina <b>Licenza</b> del nuovo server invia una
richiesta indicando nelle note che si tratta di un trasferimento.
</details>

<details>
<summary><b>Come si aggiorna?</b></summary>
<br>
Da <b>Sistema → Impostazioni → Aggiornamento del programma</b> premi <b>Scarica e installa</b> e confermi con la tua
password: il server scarica il setup, ne verifica l'impronta, salva una copia della configurazione e lo installa; il
servizio si ferma per circa un minuto e la console si ricarica da sola. Si può anche caricare un setup scaricato a mano,
oppure eseguirlo sul server. Dati, account e licenza restano.
</details>

<details>
<summary><b>Come faccio a sapere che è uscita una nuova versione?</b></summary>
<br>
Dalla versione 1.4.0 lo dice la console: una volta al giorno il server chiede a GitHub qual è l'ultima versione
pubblicata e, se è più recente di quella installata, gli amministratori vedono un pallino sulla voce
<b>Sistema</b> e, nel riquadro dell'aggiornamento, le novità e il pulsante <b>Scarica e installa</b>. Nulla si
installa da solo e non viene inviato alcun dato dell'impianto; l'avviso si può disattivare dalle impostazioni.
</details>

## 📬 Contatti

Licenze, prove e assistenza: **b.leonardi78@gmail.com**. La richiesta di attivazione si prepara da sola dalla pagina
**Licenza** della console.

---

<p align="center">
  <sub>© 2026 Bruno Leonardi · Tutti i diritti riservati.<br>
  Hikvision e Telegram sono marchi dei rispettivi proprietari. HikAccess Pro Web è un prodotto indipendente, non affiliato a Hikvision né a Telegram.<br>
  Le immagini mostrano dati dimostrativi.</sub>
</p>

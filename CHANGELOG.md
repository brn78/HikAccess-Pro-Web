# Novità delle versioni

Il setup di ogni versione è nella pagina [Releases](https://github.com/brn78/HikAccess-Pro-Web/releases).
Per aggiornare basta caricarlo da *Impostazioni → Aggiornamento del programma*: dati, account e licenza restano.

## 1.4.2 · 6 ottobre 2026

- Controller DS-K2602T/K2604T: l'invio di utenti e tessere e la lettura degli eventi non restano più in attesa fino
  al timeout. Questi controller non rispondono a una seconda richiesta sulla stessa connessione: ora ogni richiesta usa
  una connessione nuova. La lettura degli eventi, che su questi controller arriva 5 alla volta, è limitata a 30 secondi
  per ciclo: gli eventi più vecchi restano sul dispositivo e la console non resta indietro.

## 1.4.1 · 6 ottobre 2026

- **Ricevi da tutti i varchi**: nella finestra *Ricevi da varco* si possono interrogare tutti i varchi del sito uno dopo
  l'altro; i varchi non raggiungibili vengono saltati e segnalati.
- Controller a più porte (DS-K2602T, DS-K2604T): gli eventi si leggono una volta per controller invece che una per
  porta, e le scritture di utenti e tessere verso lo stesso controller vanno in fila con più tempo di attesa. Prima
  l'invio di un utente poteva fallire con "Nessuna risposta entro 6 s".
- Guida: come configurare i controller con firmware "a persone" (porta 80, HTTP / ISAPI).

## 1.4.0 · 3 ottobre 2026

- **Avviso delle nuove versioni**. Una volta al giorno il server chiede a GitHub qual è l'ultima versione pubblicata:
  quando ne esce una nuova gli amministratori vedono un pallino sulla voce *Impostazioni*, un avviso al primo accesso
  e, nel riquadro *Aggiornamento del programma*, le novità con i pulsanti per scaricare il setup e aprire la pagina
  della versione.
- *Controlla ora* ripete subito il controllo; l'interruttore *Avvisa quando esce una nuova versione* lo disattiva.
- Nulla si installa da solo e non viene inviato alcun dato dell'impianto: il setup si scarica e si carica come prima.

## 1.3.1 · 2 ottobre 2026

- Esempi di indirizzi generici nella guida e nei suggerimenti della console.

## 1.3.0 · 2 ottobre 2026

- **Licenza**. Senza attivazione la console è la versione gratuita, con 1 sito, 2 varchi e senza servizio REST.
- Pagina **Sistema → Licenza** con stato e limiti, codice macchina, richiesta di attivazione precompilata per email
  (licenza o prova di 30 giorni) e inserimento della chiave ricevuta.
- I varchi oltre i limiti restano configurati ma sospesi; la revoca delle tessere tolte li raggiunge comunque.
- Avvisi della licenza nel menu laterale, nella Dashboard e nelle pagine interessate.

## 1.2.0 · 2 ottobre 2026

- **Chiavi API** e servizio REST per Home Assistant e altri sistemi: chiavi con nome, scadenza e varchi consentiti,
  endpoint di apertura pronti da copiare, esempio per Home Assistant, comandi nel registro attività con il nome della
  chiave.

## 1.1.5 · 2 ottobre 2026

- Dalla console aperta da fuori, collegamento diretto alla console locale per l'aggiornamento del programma.

## 1.1.4 · 2 ottobre 2026

- **Identifica badge**: la tessera passata sul lettore del varco apre la scheda di chi la possiede, oppure un nuovo
  utente con quella tessera, a raffica.

## 1.1.3 · 1 ottobre 2026

- **Icona di stato** nell'area di notifica del server: servizio e console a colpo d'occhio, avvio e riavvio dal menu.

## 1.1.2 · 1 ottobre 2026

- Il servizio parte sempre, anche dopo i riavvii notturni di Windows Update sui server più lenti; avvio automatico
  ritardato.

## 1.1.1 · 30 settembre 2026

- Setup per Windows Server con servizio di Windows, firewall e account amministratore.
- Accesso da fuori tramite un proxy HTTPS (per esempio KeenDNS) con i proxy attendibili.
- Aggiornamento del programma dalla console.

## 1.0.0 · 29 settembre 2026

- Prima versione della console web: siti, varchi ISAPI e SDK, gruppi di accesso, utenti con tessere e PIN, cattura del
  badge dal varco, dashboard in tempo reale, storico eventi con esportazione CSV, backup, ripristino e deploy,
  operatori con ruoli, verifica in due passaggi, registro attività, guida utente integrata.

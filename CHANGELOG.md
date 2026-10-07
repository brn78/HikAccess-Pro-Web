# Novità delle versioni

Il setup di ogni versione è nella pagina [Releases](https://github.com/brn78/HikAccess-Pro-Web/releases).
Per aggiornare basta caricarlo da *Impostazioni → Aggiornamento del programma*: dati, account e licenza restano.

## 1.6.2 · 7 ottobre 2026

- **Nome e matricola negli eventi** dei controller che registrano solo la tessera, come il Totem DS-K2602 collegato
  con l'SDK: la console li prende dall'anagrafica, anche per gli eventi già archiviati. Vale anche per una tessera non
  ancora inviata al varco ("accesso negato") e per una tessera assegnata a un utente dopo il passaggio.
- *Diagnostica*: allarme porta aperta "disattivato" invece di "dopo mai"; riga degli eventi in tempo reale più chiara.

## 1.6.1 · 7 ottobre 2026

- Gli invii ai varchi (utenti, gruppi, deploy, ricezione, revoche) proseguono **in background** senza aprire la finestra:
  in alto il contatore delle operazioni in corso, al termine una notifica con l'esito e **Vedi log** per il dettaglio.
- Pulsante per **copiare il log** delle operazioni e i testi di esito e diagnostica (per esempio l'esito di
  *Sincronizza orario* varco per varco, ora in una notifica con *Dettagli*).
- Controller DS-K2602T/K2604T: orologio, comandi porta, stato porta e diagnostica si mettono in fila con la lettura degli
  eventi invece di andare in timeout ("Nessuna risposta entro 5 s").
- Con gli eventi in tempo reale il registro dei controller si rilegge ogni 5 minuti e subito dopo una riconnessione,
  invece che a ogni scansione: i controller lenti restano liberi per invii e comandi.
- Se un controller con il collegamento in tempo reale aperto smette di rispondere alle altre richieste, il collegamento
  viene sospeso per 6 ore e gli eventi arrivano con la scansione periodica.
- Firmware senza filtro per orario: un invio durante la lettura degli eventi non fa più saltare gli eventi più vecchi.

## 1.6.0 · 7 ottobre 2026

- **Eventi in tempo reale**: i controller inviano ogni passaggio appena avviene (HTTP: flusso di notifiche; SDK:
  armamento, come iVMS-4200). Archivio, dashboard e *Cattura da varco* si aggiornano in un secondo, anche sui
  DS-K2602T/K2604T. La colonna *Eventi* della pagina Varchi mostra lo stato del collegamento; si disattiva in
  *Impostazioni*.
- **Nessun evento perso**: la lettura del registro di ogni controller riparte dall'ultimo evento letto, in ordine, anche
  sui controller che danno 5 eventi per pagina. Gli eventi registrati con un orario precedente (orologio corretto, fine
  dell'ora legale) vengono riconosciuti dal numero progressivo e recuperati. Corretti i casi in cui alcuni passaggi non
  comparivano nello storico.
- **Cattura badge immediata**: con il tempo reale il numero compare appena la tessera tocca il lettore; vale solo un
  passaggio fatto dopo l'apertura della finestra.
- **Porta rimasta aperta**: nuova voce *Stato porta* (modalità, serratura, sensore, lettori) con *Ripristina
  funzionamento normale*; la *Diagnostica* indica se è attiva la funzione "prima tessera" del controller, che lascia la
  porta aperta dopo il primo badge.
- **Orologio dei varchi**: *Sincronizza orario* imposta anche il fuso orario con le regole dell'ora legale (prima, d'estate,
  i dispositivi restavano indietro di un'ora).
- **Operazioni su più utenti e varchi**: con le caselle nelle tabelle si inviano più utenti ai varchi (tutti quelli
  interessati o solo alcuni), si assegna un gruppo, si abilitano, disabilitano o eliminano; sui varchi selezionati si
  inviano o ricevono gli utenti e si sincronizza l'orologio.
- **Una scrittura per controller**: ogni persona viene scritta una volta sola con tutte le porte del controller; le porte
  non gestite dalla console restano come sono.
- **Revoche in sospeso**: tessere tolte o persone eliminate mentre un controller non rispondeva vengono ritentate da sole;
  avviso in dashboard e nella pagina Utenti con dettagli e *Riprova ora*.
- Messaggi di errore dell'SDK Hikvision e dei dispositivi in italiano.
- La scheda di un utente si apre sempre con i dati attuali e non sovrascrive le modifiche fatte da altri nel frattempo;
  chiudendo una scheda con modifiche non salvate la console chiede conferma.
- Aggiornamento dalla console: il setup caricato deve coincidere con quello pubblicato su GitHub (impronta SHA-256).
- Salvataggi della configurazione più sicuri, con copia di riserva.

## 1.5.1 · 6 ottobre 2026

- Fasce orarie sui controller collegati con l'SDK Hikvision (porta 8000, es. Totem DS-K2602): corretta la scrittura
  del modello orario, che la 1.5.0 non riusciva a completare; se il firmware non supporta i comandi classici si usano
  quelli più recenti.

## 1.5.0 · 6 ottobre 2026

- **Giorni e fasce orarie nei gruppi di accesso**: per ogni gruppo "sempre" oppure fino a 8 fasce al giorno, da lunedì
  a domenica. Fuori fascia la tessera dei membri viene rifiutata. Le fasce si scrivono subito sui controller; cambiandole
  si aggiorna solo l'orario, senza reinviare le persone. Nuova voce *Reinvia le fasce orarie ai varchi* nel menu del gruppo.

## 1.4.4 · 6 ottobre 2026

- Revoca su un controller "a persone": se la persona non è presente sul controller non si scrive nulla (prima il
  controller rispondeva `badJsonContent`); se c'è e resta senza porte autorizzate viene tolta dal controller con le sue
  tessere.

## 1.4.3 · 6 ottobre 2026

- Invio di un utente mentre la console legge gli eventi dallo stesso controller: la lettura cede il passo alla
  scrittura invece di farla andare in timeout.
- Se la lettura delle porte già autorizzate della persona non riesce, l'invio si ferma con errore invece di scrivere
  solo la porta in corso (che toglieva le altre porte del controller).

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

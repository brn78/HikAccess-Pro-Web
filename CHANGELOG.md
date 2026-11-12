# Novità delle versioni

Il setup delle ultime versioni è nella pagina [Releases](https://github.com/brn78/HikAccess-Pro-Web/releases).
Per aggiornare: *Sistema → Impostazioni → Aggiornamento del programma*, **Scarica e installa** (dalla 1.7.0) oppure caricando il setup; dati, account e licenza restano.

## 1.10.1 · 12 novembre 2026

Piccole comodità di tutti i giorni: la matricola si propone da sola, le schede si allargano e gli elenchi si leggono meglio.

- **Matricola proposta**: creando un utente la scheda si apre con la matricola già scritta, la prima libera dopo
  l'ultima in uso, con lo schema del sito (001 → 002, 2026-001 → 2026-002) e tenendo conto delle matricole di tutti i
  siti. Il campo resta libero, per scriverne un'altra, e il cursore parte dal nome.
- **Schede laterali ridimensionabili**: ogni scheda si allarga o si stringe trascinando la linea sul suo bordo
  sinistro (doppio clic: larghezza normale); la linguetta con le frecce, che compare passandoci sopra, la porta a tutto
  schermo. Il browser ricorda la larghezza scelta.
- **Righe a colori alterni** in tutti gli elenchi, per seguirle meglio con l'occhio. Si spengono e si riaccendono con
  *Righe a colori alterni* nel menu del tasto destro di una riga, che ora c'è in ogni elenco.
- **Tasto destro**: dove la console non ha un suo menu non compare più quello del browser. Resta nelle caselle di testo
  (per incollare), sul testo selezionato (per copiare) e ovunque tenendo premuto Maiusc.

## 1.10.0 · 12 novembre 2026

Elenchi più comodi, il menu riordinato attorno al sito attivo e un calendario uguale in ogni browser.

- **Elenchi**: la ricerca è sempre il primo campo e i filtri a tendina (gruppo, varco, tipo di evento, categoria)
  stanno nella finestra che si apre con l'imbuto, con il numero dei filtri attivi e le loro etichette sotto la barra,
  da togliere con un clic. In alto a destra scegli la vista **Elenco** o **Schede**, che il browser ricorda per ogni
  elenco; nelle schede ogni voce è descritta per intero. In basso a sinistra trovi il numero delle righe («3 di 7
  utenti») e il tempo del caricamento. L'elenco arriva fino in fondo alla finestra con i titoli delle colonne sempre in
  vista, e quelli lunghi si disegnano 200 righe alla volta. Le righe si usano anche da tastiera: Tab, frecce e Invio.
- **Scegli più righe**: nelle pagine *Utenti* e *Varchi* le caselle compaiono con l'icona in alto a sinistra
  dell'elenco; le operazioni sulle righe scelte sono anche nel menu del tasto destro.
- **Menu**: il primo gruppo porta il nome del sito attivo, con **Panoramica** (la pagina che si chiamava Dashboard),
  **Eventi** e, per gli amministratori, **Attività** (il registro attività, che riguarda tutti i siti). Sotto c'è
  **Gestione**: Utenti, Gruppi, Varchi e Telecamere. I **Siti** si aprono dal selettore del sito in alto e dalla pagina
  *Sistema*.
- **Barra in alto**: lo stato del monitoraggio è al centro; **Sistema** e **Guida utente** sono icone in alto a destra,
  accanto al tema. Le pagine di amministrazione hanno davanti al titolo la freccia per tornare a *Sistema*.
- **Calendario**: i campi data aprono il calendario della console al posto di quello del browser, con il lunedì in
  testa, le domeniche e le festività dell'impianto in rosso e il nome della festa sotto il mese. Nei campi con data e
  ora c'è accanto l'elenco delle ore. Da tastiera si apre con Alt+↓ o F4.
- **Telecamere dal vivo**: sotto ogni video ci sono la matita per aprire la scheda della telecamera e il suo menu, anche
  con il tasto destro, senza passare dall'elenco.
- **Ricerca** anche negli elenchi di *Telecamere*, *Operatori* e *Siti*.

**Da sapere.** Gli indirizzi delle pagine non cambiano, quindi collegamenti e segnalibri continuano a funzionare. Sul
telefono *Sistema* e *Guida utente* restano voci in fondo al menu.

## 1.9.0 · 8 novembre 2026

Ogni sito ha le sue persone, il sito attivo è sempre sott'occhio e gli avvisi Telegram arrivano con la foto.

- **Persone per sito**: un sito nuovo nasce vuoto e la pagina *Utenti* mostra solo le persone del sito attivo. Chi
  viene creato, ricevuto da un varco o importato in un sito resta in quel sito; la matricola è sempre unica in tutto
  l'impianto, così la stessa persona può entrare in più sedi senza doppioni. Per chi lavora in più sedi c'è la
  **condivisione**: nella scheda (sezione *Siti in cui è presente*), dal menu della persona (*Condividi con un altro
  sito…*) o per più persone insieme (*Condividi con un sito*). *Togli dal sito* fa il contrario: le autorizzazioni sui
  varchi di quel sito vengono revocate con l'invio e il resto non cambia. Aggiornando, ogni persona finisce nei siti dei
  suoi varchi autorizzati e del suo gruppo (nel primo sito se non ne ha): nulla si perde, cambia solo dove la vedi.
- **Sito attivo in evidenza**: il selettore è ora in alto a sinistra, prima del nome della pagina, più grande e
  colorato. Al cambio di sito pulsa e un avviso dice in quale sito stai lavorando, con la descrizione del sito e i suoi
  numeri (varchi, gruppi, persone).
- **Telegram con la foto**: se il varco ha una telecamera associata che fotografa l'evento (o il terminale manda la sua
  foto), l'avviso arriva come foto con il testo sotto, appena lo scatto è pronto (di solito entro pochi secondi, al più
  una quindicina). Si spegne per ogni operatore in *Profilo → Notifiche* (*Allega la foto dell'evento*); gli
  amministratori lo impostano anche per gli altri. Le foto sono dati personali e passano dai server di Telegram:
  tienine conto nell'informativa.
- **Dashboard**: il riquadro *Persone del sito* conta le persone presenti nel sito, non più tutta l'anagrafica.
- **Eliminazione di un sito**: non si elimina un sito che ha ancora persone presenti solo lì.

**Da sapere.** Le persone già condivise di fatto (autorizzate su varchi di due siti) compaiono in entrambi. Gli avvisi
riassuntivi (più di 4 eventi insieme) e quelli sui varchi non raggiungibili restano solo testo.

## 1.8.3 · 8 novembre 2026

I dispositivi Hikvision si trovano da soli.

- **Rileva in rete** nelle pagine *Varchi* e *Telecamere* (amministratori): il server cerca nella rete locale
  terminali, controller, telecamere e videoregistratori Hikvision come fa il programma SADP, senza credenziali, e li
  elenca con modello, firmware, indirizzo, porte web e SDK, MAC, stato di attivazione e se sono già configurati nella
  console. **Varco** o **Telecamera** aprono la scheda già compilata con indirizzo, porta e protocollo giusti (un
  controller senza interfaccia web, per esempio il DS-K2602, viene proposto sulla porta 8000 con l'SDK): restano da
  scrivere utente e password. I filtri mostrano solo i varchi, solo le telecamere o solo i dispositivi nuovi; la
  ricerca cerca per modello, indirizzo, MAC e seriale.
- **Indirizzo specifico**: per un dispositivo dietro un router o raggiunto in VPN, dove la ricerca di rete non arriva,
  si scrive il suo indirizzo e la console lo interroga direttamente.
- **Rileva in rete nella scheda**: aprendo un nuovo varco o una nuova telecamera, il pulsante accanto a *Connessione*
  elenca i dispositivi e **Seleziona** compila i campi della scheda aperta.
- **Setup**: con il servizio di Windows il firewall apre anche la porta UDP 37020 con cui i dispositivi rispondono
  alla ricerca; gli script `Install-Service.ps1` e `Uninstall-Service.ps1` fanno lo stesso.
- **Guida utente**: nuovo paragrafo *Trovare i dispositivi in rete*, un'icona (i) nella finestra e una voce nella
  risoluzione dei problemi.

**Da sapere.** La ricerca parte dal server e raggiunge la sua sottorete. I dispositivi raggiunti in VPN rispondono alla
ricerca mirata solo se il firmware lo prevede: sugli apparati veri hanno risposto i controller, non le telecamere. La
ricerca non scrive nulla sui dispositivi e viene annotata nel registro attività.

## 1.8.2 · 8 novembre 2026

Menu più ordinati, telecamere più rapide da aggiungere e una correzione sugli utenti.

- **Menu delle telecamere** come quello dei varchi, con nome e modello in testa: video, *Verifica foto e video*, copia
  dell'indirizzo, interfaccia web della telecamera (la password si copia dopo la conferma con la propria), modifica ed
  eliminazione.
- **Nuova telecamera con le stesse credenziali** e **altro canale dello stesso dispositivo**: schede già compilate,
  comode soprattutto per le telecamere di un NVR, con il primo canale libero già proposto. Se la password copiata
  andrebbe a un altro indirizzo, porta o utente, la console chiede la conferma con la propria password.
- **Modello dei varchi a colpo d'occhio**: nella pagina *Varchi* la colonna *Dispositivo* mostra il modello (per esempio
  DS-K2602T) con il firmware, ricavato dal seriale; il seriale completo resta nel suggerimento e nella ricerca.
- **Menu laterale riordinato**: *Telecamere* è in *Gestione*, accanto a *Varchi*, e ogni pagina ha nel titolo l'icona
  della sua voce. La **conservazione delle immagini** è ora una pagina di *Sistema*.
- **Utenti senza matricola**: un record arrivato da un controller senza matricola non si poteva aprire né eliminare.
  Ora compare come *Record senza matricola* e si elimina con un clic, solo dall'anagrafica perché su un controller non
  può esistere; la ricezione dai varchi non li importa più e li conta nel log. Le matricole nuove con `/` o `\` non si
  possono più salvare, perché impedivano di aprire la scheda; quelle già presenti restano modificabili.
- **Setup**: l'ultima pagina della procedura guidata mostra il testo per intero.

**Da sapere.** La conservazione delle immagini è tra le pagine di amministrazione: operatori e utenti in sola lettura
non la vedono più.

## 1.8.1 · 7 novembre 2026

Versione dedicata alla sicurezza.

- **Pacchetti di configurazione cifrati**: il file esportato (`.hikpack`) contiene password dei dispositivi, tessere e
  PIN, quindi ora viene cifrato (AES-256) con una password scelta da chi esporta. Senza quella password non si apre e
  non si può recuperare. Per l'app desktop, che non apre i file cifrati, si può ancora esportare in chiaro: la scelta
  resta nel registro attività. I pacchetti già esportati e `hikaccess_config.json` si importano come prima.
- **Conferma con la propria password** prima delle operazioni delicate: esportazione e importazione della configurazione,
  *Copia password* di un dispositivo, nuova chiave API, copia della password di un varco verso un altro indirizzo, nuovo
  operatore e modifiche che danno accesso alla console (password, ruolo, riabilitazione, verifica in due passaggi).
- **Password dei dispositivi legate all'indirizzo**: cambiando indirizzo, porta o utente di un varco o di una telecamera
  la password va riscritta, anche per la *Verifica*. Una sessione rubata non può mandarla a un server a scelta.
- **Primo accesso protetto**: se l'account amministratore non viene creato dal setup, la console chiede un codice che si
  legge solo sul server. Il setup e l'icona di stato aprono la pagina con il codice già scritto.
- **Setup rinnovato**: alla prima installazione si sceglie anche la cartella dei dati; come servizio di Windows la
  cartella è accessibile solo ad amministratori e sistema. Porta e cartella ora stanno in `appsettings.Local.json`
  accanto al programma; l'aggiornamento le riporta lì da solo.
- **Disinstallazione**: se si sceglie di eliminare i dati, vengono tolti solo i file del programma, così gli altri file
  in una cartella scelta a mano restano.
- **Account al sicuro**: se il file degli account risulta illeggibile, la console riparte dalla copia precedente.
- **Proxy riconosciuti meglio**: le richieste che passano da Cloudflare, Akamai, Fastly o Apache non vengono scambiate per
  accessi diretti. Intestazioni di sicurezza aggiornate, e il testo tecnico degli errori interni lo vedono solo gli
  amministratori.

**Da sapere.** Le copie automatiche nella cartella `data\backups` restano in chiaro: le protegge l'accesso alla cartella
dei dati, perché il server non può conoscere una password scelta da te. Se porti altrove una copia della configurazione,
usa l'esportazione cifrata.

## 1.8.0 · 7 novembre 2026

- **Telecamere** (voce *Telecamere* nel menu): Hikvision, anche come canali di NVR e DVR, o di altra marca con RTSP. Per
  le altre marche indirizzo IP, utente e password bastano se la telecamera offre ONVIF. **Verifica** prova foto e video
  prima di salvare e non scrive nulla sul dispositivo.
- **Video dal vivo nel browser**, senza plugin e senza ricodifica: un riquadro per telecamera, flusso leggero o alta
  qualità, schermo intero, anche dal telefono e da fuori tramite il proxy. Il video non viene registrato e la telecamera
  vede un solo collegamento anche con più operatori. Se il browser non può riprodurlo, il riquadro mostra una foto al
  secondo.
- **Foto a ogni passaggio**: si associa la telecamera ai varchi e si sceglie cosa fotografare (accessi concessi, accessi
  negati, allarmi della porta). Le anteprime compaiono nello storico *Eventi* e nell'*Attività in tempo reale* della
  dashboard, con il bordo verde o rosso; un clic apre l'immagine grande con chi, dove e quando.
- **Terminali con fotocamera**: a scelta la console conserva anche la foto che il terminale allega all'evento.
- **Conservazione delle immagini**: giorni di conservazione (predefiniti 7) e spazio massimo (predefinito 10 GB). Le
  foto dei passaggi sono dati personali: la guida spiega cosa verificare prima di attivarle.
- **Licenza**: il numero di telecamere si aggiunge ai limiti della licenza. La versione gratuita comprende 1 telecamera
  completa di video e foto, e le licenze già emesse restano valide con 1 telecamera.
- **Guida utente** con il nuovo capitolo *Telecamere*.

**Da sapere.** Il flusso consigliato è quello secondario, quasi sempre H.264. Con H.264+ e H.265+ i fotogrammi chiave
sono rari: in Wi-Fi l'alta qualità può fermarsi qualche secondo, e la console riapre da sola il collegamento. Video e
foto sono stati provati su una telecamera Hikvision vera; NVR, DVR, H.265 e ONVIF finora solo su dispositivi simulati,
quindi segnala pure ciò che non va.

## 1.7.0 · 15 ottobre 2026

- **Festività** (*Gruppi di accesso → Festività*): un calendario per tutti i siti con le festività nazionali italiane
  calcolate da sole (anche Pasqua e Lunedì dell'Angelo, San Francesco il 4 ottobre), il **santo patrono** della
  località (nome, giorno e mese) e altre chiusure come ponti e ferie, una volta o ogni anno. Nei gruppi con fasce
  orarie l'opzione **Chiuso nelle festività** tiene chiusi i varchi in quei giorni: le date vengono scritte sui
  controller e aggiornate da sole ogni anno.
- **Notifiche Telegram** (con licenza): il bot si configura in *Sistema → Impostazioni*; ogni operatore collega la
  sua chat dal *Profilo* con un QR e un PIN e sceglie quali eventi ricevere (accessi negati, porta forzata, porta
  aperta troppo a lungo, allarmi e manomissioni, varco non raggiungibile, comandi da remoto, accessi concessi), su
  quali varchi e per quali persone. Gli amministratori le impostano anche per gli altri dalla pagina *Operatori*.
  Nessuna porta da aprire sul router: è il server a contattare Telegram.
- **Nuova grafica**: colori e ombre più morbidi, barra laterale chiara nel tema chiaro con il gruppo *Gestione*
  richiudibile e la voce **Sistema** in fondo, che apre una pagina a schede con impostazioni, operatori, licenza,
  backup, chiavi API e registro attività, più gli avvisi da guardare (nuova versione, licenza).
- **Scarica e installa** (*Sistema → Impostazioni → Aggiornamento del programma*): il server scarica il setup da
  GitHub, ne controlla dimensione, impronta e versione, salva una copia della configurazione e lo installa; la console
  si ricarica da sola. Resta possibile caricare un setup scaricato a mano.
- **Licenza**: le notifiche Telegram si aggiungono al servizio REST tra le funzioni della licenza e si possono chiedere
  nella richiesta di attivazione. Le licenze già emesse restano valide.
- **Guida utente** con l'icona di ogni capitolo e le parti nuove su festività, notifiche Telegram, pagina Sistema e
  Scarica e installa.

## 1.6.7 · 14 ottobre 2026

- **Esportazione di un solo sito** (*Backup e deploy* o menu del sito nella pagina *Siti*): il sito con i suoi varchi,
  gruppi e le sole persone autorizzate su di esso, con i soli permessi di quel sito. È il pacchetto da portare su un
  altro server (dal portatile di cantiere al server dell'ufficio, o da un impianto a un altro).
- **Importazione in unione**: il pacchetto si aggiunge alla configurazione attuale senza cancellare nulla, in un sito
  nuovo o in uno esistente a scelta. I varchi sono riconosciuti da indirizzo, porta e numero porta, i gruppi dal nome,
  le persone dalla matricola: chi esiste già riceve i varchi del sito e le tessere nuove, il resto dei suoi dati resta.
  Le tessere già di un'altra persona non vengono spostate e l'esito le elenca. Il ripristino completo
  (**sostituisci**) resta disponibile; al termine si può inviare la configurazione ai soli varchi del sito importato.
- Aiuto contestuale: suggerimento per *Registra in serie* e per la cattura da flusso e registro.

## 1.6.6 · 14 ottobre 2026

- **Cattura da varco con il tempo reale attivo**: alcuni terminali (es. DS-K1T805MX) non spingono nel flusso degli
  eventi la lettura di una tessera non registrata, che però compare nel loro registro; la cattura restava a vuoto anche
  se l'evento "badge sconosciuto" arrivava in archivio. Ora la cattura ascolta il flusso **e** rilegge il registro del
  varco in parallelo: vale la prima via che porta la tessera, su tutti i modelli.
- Il flusso degli eventi accetta anche le notifiche in XML (`EventNotificationAlert`), usate da qualche firmware al
  posto del JSON.
- *Diagnostica* del varco: quanti eventi di accesso sono arrivati dal flusso in tempo reale e quando l'ultimo; se il
  terminale manda qualcosa che la console non riconosce, la diagnostica ne mostra l'inizio (utile per segnalarlo).
- **Registra in serie** (pagina Utenti): impostazioni comuni una volta sola (varco di lettura, gruppo e varchi, prima
  matricola con lo schema in uso, nome scritto a ogni tessera o automatico), poi una sola finestra che resta aperta:
  badge sul lettore, nome, Invio: la persona è salvata e inviata ai varchi, la lettura riparte per la tessera successiva
  con la matricola incrementata (2026-001 → 2026-002). Le tessere già assegnate vengono saltate.
- Nella scheda utente **Salva e crea simile** salva e apre subito la scheda di un'altra persona con le stesse
  impostazioni e la matricola successiva; dal menu di un utente **Duplica utente** fa lo stesso partendo da lui.

## 1.6.5 · 11 ottobre 2026

- *Dashboard*: **Transiti oggi** conta solo le verifiche di persone (accessi concessi e negati). Sincronizzazioni
  dell'ora, aperture da pulsante, porta aperta o chiusa, anomalie e allarmi non vengono più contati come transiti:
  se ci sono, compaiono a parte come "altri eventi". Lo stesso vale per il confronto con ieri.
- Il grafico *Transiti di oggi per ora* mostra come "altri eventi di porta" solo gli eventi di porta (pulsante di
  uscita, porta aperta o chiusa, forzature), non più le operazioni di sistema.
- *Eventi e storico*: nuovo filtro **Transiti (concessi e negati)**, usato anche dall'indicatore della dashboard.

## 1.6.4 · 7 ottobre 2026

- *Impostazioni → Informazioni di sistema*: **grafico a ciambella del disco** della cartella dati, con archivio eventi
  (passaggi e registro attività), altri dati della console, altri file e programmi e la percentuale di spazio libero.
- *Operatori*: la descrizione dei tre ruoli torna su tre colonne.

## 1.6.3 · 7 ottobre 2026

- In alto a sinistra, accanto a «Console web», la **versione in uso** in verde fluo (al posto dell'icona).
- **Indicatori della dashboard cliccabili**: varchi totali e online portano alla pagina Varchi (ai soli varchi offline
  se qualcuno non risponde), utenti registrati alla pagina Utenti, transiti e accessi negati agli eventi di oggi.
- **Riquadri a tutta larghezza** in tutte le pagine, uno sotto l'altro invece che affiancati su due o tre colonne.
- Menu **Sistema** chiuso: si apre con un clic sul titolo e da solo quando sei su una delle sue pagine; il pallino della
  nuova versione compare sul titolo.

## 1.6.2 · 7 ottobre 2026

- **Nome e matricola negli eventi** dei controller che registrano solo la tessera, come il DS-K2602 collegato
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

- Fasce orarie sui controller collegati con l'SDK Hikvision (porta 8000, es. DS-K2602): corretta la scrittura
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

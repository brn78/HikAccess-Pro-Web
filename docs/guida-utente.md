# Guida utente di HikAccess Pro Web

[← Torna alla presentazione](../README.md) · [Scarica il setup](https://github.com/brn78/HikAccess-Pro-Web/releases/latest)

> [!NOTE]
> È la stessa guida che si apre nella console con <kbd>F1</kbd> (menu **Guida utente**), aggiornata alla versione **1.4.4**. Nella console le icone <b>(i)</b> accanto ai campi rimandano direttamente al paragrafo giusto.

## Indice

- [Panoramica](#panoramica)
- [Primo avvio e accesso](#accesso)
- [L'interfaccia](#interfaccia)
- [Ruoli e permessi](#ruoli)
- [Siti](#siti)
- [Varchi](#varchi)
- [Gruppi di accesso](#gruppi)
- [Utenti, tessere e PIN](#utenti)
- [Dashboard](#dashboard)
- [Eventi e storico](#eventi)
- [Operazioni in background](#operazioni)
- [Backup, ripristino e deploy](#backup)
- [Sistema](#sistema)
- [Profilo e sicurezza](#profilo)
- [Server e installazione](#server)
- [Buone pratiche di sicurezza](#sicurezza)
- [Risoluzione dei problemi](#problemi)
- [Glossario](#glossario)

HikAccess Pro Web è la console per gestire il controllo accessi Hikvision di uno o più impianti: varchi, gruppi di accesso, utenti con tessere e PIN, monitoraggio in tempo reale e storico degli eventi. Questa guida descrive ogni funzione della console così come la vedi a schermo.

> [!TIP]
> **Come orientarsi.** L'indice a lato porta al capitolo desiderato; la casella **Cerca nella guida** evidenzia tutte le occorrenze di una parola (<kbd>Invio</kbd> passa alla successiva). Nelle schede della console le icone ⓘ spiegano il singolo campo e rimandano al punto giusto di questa guida. <kbd>F1</kbd> apre la guida da qualsiasi pagina; **Stampa / PDF** la salva su carta o in un file.

## <a id="panoramica"></a>Panoramica

La console è composta da due parti:

- **Il server** (HikAccessWeb), installato su un PC o server Windows sempre acceso e collegato in rete ai varchi. Parla con i dispositivi Hikvision, archivia configurazione ed eventi nella propria cartella dati e sorveglia i varchi in continuo, anche quando nessuno ha la console aperta.
- **La console web**, cioè le pagine che stai usando: si aprono da qualsiasi browser recente (Edge, Chrome, Firefox, Safari; Internet Explorer non è supportato) su PC, tablet o telefono all'indirizzo `http://<nome-o-IP-del-server>:5080`. Più operatori possono lavorare contemporaneamente, ciascuno con il proprio account e ruolo.

### <a id="panoramica-concetti"></a>I concetti chiave

- **Sito**: Una sede fisica (stabilimento, filiale, edificio) con i propri varchi e gruppi di accesso. Il **sito attivo** si sceglie dal selettore in alto e filtra ciò che vedi.
- **Varco**: Una porta comandata da un terminale o da una porta di un controller Hikvision: è l'oggetto a cui si concedono i permessi e da cui arrivano gli eventi.
- **Gruppo di accesso**: Un modello di varchi autorizzati ("Tutti i varchi", "Solo uffici"...) che precompila le autorizzazioni degli utenti.
- **Utente**: Una persona, identificata da una **matricola** univoca, con una o più **tessere**, un eventuale **PIN**, una validità e l'elenco dei varchi autorizzati. Gli utenti sono unici per tutto l'impianto, non per sito.
- **Evento**: Un passaggio, un accesso negato, un allarme o un'azione registrata da un varco, archiviata nel database della console.
- **Operazione in background**: Un lavoro lungo (invio di un utente ai varchi, deploy, ricezione dell'anagrafica) che il server esegue mostrando l'avanzamento e il log.
- **Operatore**: Chi usa la console, con un account personale e un ruolo (amministratore, operatore, sola lettura).
- **Licenza**: Senza chiave di attivazione la console è la **versione gratuita**: 1 sito e 2 varchi, senza servizio REST. Una licenza, legata al server, amplia questi limiti (vedi [Licenza e attivazione](#sistema-licenza)).

## <a id="accesso"></a>Primo avvio e accesso

### <a id="accesso-primo-avvio"></a>Configurazione iniziale

Il setup può creare subito l'account amministratore (pagina **Account amministratore**): in quel caso accedi con quel nome utente e quella password da qualsiasi PC della rete. Altrimenti al primo avvio non esiste alcun account: aprendo la console **dal PC del server** (`http://localhost:5080`) compare la pagina **Configurazione iniziale**, che crea l'account amministratore: scegli nome utente, nome e cognome e una password. Per sicurezza questa pagina non è disponibile dagli altri PC della rete.

Se sul server non c'è un browser adatto (Windows Server Core, oppure Server 2016 e 2019 con il solo Internet Explorer), crea l'amministratore da un prompt dei comandi come amministratore con `HikAccessWeb.exe --reset-password <utente> <password>` (vedi [Recupero dell'accesso amministratore](#server-reset-password)) e accedi da un altro PC.

### <a id="accesso-login"></a>Accedere e uscire

Inserisci nome utente e password. L'opzione **Mantieni l'accesso su questo computer** conserva la sessione anche chiudendo il browser, sempre entro il tempo di inattività impostato. Per uscire usa **Esci** nel menu con il tuo nome in alto a destra: fallo sempre sui PC condivisi.

- Dopo **5 tentativi errati** l'accesso con quel nome utente da quel PC è sospeso per **5 minuti**.
- Con la [verifica in due passaggi](#profilo-2fa) attiva, dopo il codice puoi segnare il browser come **di fiducia**: per il periodo impostato dall'amministratore (predefinito 30 giorni) su quel browser basterà la password. Su un PC condiviso togli la spunta. Dettagli in [Browser di fiducia](#profilo-2fa-fiducia).
- La sessione si chiude da sola dopo un periodo di **inattività** (predefinito 8 ore, modificabile in [Impostazioni](#sistema-impostazioni)): contano solo le tue azioni, non gli aggiornamenti automatici delle pagine.
- Cambio password, cambio di ruolo o disattivazione dell'account chiudono subito tutte le sessioni aperte con quell'account.

### <a id="accesso-password-dimenticata"></a>Password dimenticata

Un amministratore può reimpostarla da **Operatori**. Se a non ricordare la password è l'unico amministratore, sul PC del server si esegue `HikAccessWeb.exe --reset-password <utente> <nuova password>` (vedi [Server e installazione](#server)).

## <a id="interfaccia"></a>L'interfaccia

### <a id="interfaccia-menu"></a>Menu laterale e barra superiore

- Il **menu laterale** è diviso in Monitoraggio, Gestione, Sistema (solo amministratori) e Aiuto. Il pulsante **Comprimi menu** in basso lo riduce alle sole icone; su telefono si apre con ☰. In fondo, il riquadro **Monitoraggio varchi** mostra se la scansione automatica è attiva e quando è avvenuta l'ultima. Agli amministratori, sopra, un riquadro segnala la [licenza](#sistema-licenza) quando serve attenzione: versione gratuita, varchi sospesi, licenza non valida o in scadenza.
- Nella **barra superiore** trovi il nome dell'impianto e della pagina, il contatore delle [operazioni in corso](#operazioni), il **selettore del sito attivo**, il pulsante del **tema** (chiaro, scuro o automatico come il sistema) e il menu con il tuo nome (profilo, impostazioni, guida, uscita).

### <a id="interfaccia-sito"></a>Il sito attivo

Dashboard, Varchi, Gruppi ed Eventi mostrano solo il sito attivo. La pagina Utenti mostra sempre tutta l'anagrafica, ma le colonne e le spunte dei varchi si riferiscono al sito attivo. Il sito scelto viene ricordato dal browser.

### <a id="interfaccia-tabelle"></a>Tabelle, schede e menu

- Clic sull'intestazione di una colonna per **ordinare**; le caselle e i pulsanti sopra la tabella **filtrano**.
- Regola unica in tutta la console: **un clic** su una riga, su un riquadro della dashboard o su un passaggio apre la scheda corrispondente (in sola consultazione per chi non può modificare); il **tasto destro** o il pulsante ⋯ aprono il menu delle azioni. Il piè di pagina di ogni tabella lo ricorda.
- Le schede di modifica si aprono in un **pannello laterale**; <kbd>Esc</kbd> le chiude senza salvare.
- Le conferme e gli esiti compaiono come **notifiche** in alto a destra; gli errori restano più a lungo.
- I campi contrassegnati da \* sono obbligatori.

### <a id="interfaccia-scorciatoie"></a>Scorciatoie da tastiera

| Tasto | Effetto |
| --- | --- |
| <kbd>F1</kbd> | Apre questa guida. |
| <kbd>Esc</kbd> | Chiude menu, finestre, pannelli e spiegazioni ⓘ. |
| <kbd>Invio</kbd> | Conferma la finestra o il campo attivo (accesso, ricerche, tessere aggiuntive). |
| <kbd>↑</kbd> <kbd>↓</kbd> | Si spostano tra le voci di un menu aperto. |

## <a id="ruoli"></a>Ruoli e permessi

Ogni account ha uno dei tre ruoli. Assegna a ciascuno il minimo necessario: la portineria non ha bisogno di modificare i varchi, un monitor a parete non ha bisogno di comandare le porte.

| Funzione | Amministratore | Operatore | Sola lettura |
| --- | :---: | :---: | :---: |
| Dashboard, stato dei varchi, storico eventi | ✓ | ✓ | ✓ |
| Elenchi di varchi, gruppi e utenti | ✓ | ✓ | solo consultazione, senza PIN |
| Comandi porta (apri, chiudi, sblocco e blocco permanente), orologio, diagnostica | ✓ | ✓ | — |
| Utenti, tessere, PIN, cattura badge, ricezione da varco, sincronizzazioni | ✓ | ✓ | — |
| Gruppi di accesso | ✓ | ✓ | — |
| Esportazione CSV degli eventi | ✓ | ✓ | — |
| Aggiunta, modifica ed eliminazione di varchi e siti | ✓ | — | — |
| Backup, ripristino, deploy atomico | ✓ | — | — |
| Conservazione e manutenzione del database eventi | ✓ | — | — |
| Operatori, chiavi API, licenza, impostazioni, registro attività | ✓ | — | — |
| Profilo personale, password e tema | ✓ | ✓ | ✓ |

Deve restare sempre almeno un amministratore abilitato: la console impedisce di eliminare o declassare l'ultimo.

## <a id="siti"></a>Siti

Pagina **Siti** (modifiche riservate agli amministratori). Un sito è una sede con i propri varchi e gruppi; gli utenti sono comuni a tutti i siti e possono essere autorizzati in più sedi.

- **Nuovo sito**: nome e descrizione. Alla creazione la console propone di renderlo attivo per aggiungere subito varchi e gruppi. La versione gratuita gestisce un solo sito; i siti oltre la [licenza](#sistema-licenza) sono segnati **Oltre la licenza** e i loro varchi sono sospesi.
- **Rendi attivo**: cambia il sito attivo (equivale al selettore in alto).
- **Elimina sito**: possibile solo se il sito non ha varchi né gruppi, e mai per l'ultimo sito rimasto.

> [!TIP]
> Con un solo impianto basta il sito predefinito. Crea più siti quando le sedi hanno varchi e regole distinte: ogni sito ha i suoi gruppi e la sua dashboard.

## <a id="varchi"></a>Varchi

Pagina **Varchi**: tutti i terminali e le porte dei controller del sito attivo, con stato, canale di comunicazione, seriale, firmware, tempo di risposta e ultimo contatto. I comandi sono nel menu del tasto destro; **Scansiona tutti** interroga subito tutti i varchi del sito.

### <a id="varchi-aggiungere"></a>Aggiungere un varco

**Aggiungi varco** (amministratori) apre la scheda del dispositivo. La versione gratuita gestisce 2 varchi: per aggiungerne altri serve una [licenza](#sistema-licenza).

1. **Nome varco** e **sito di appartenenza**. Usa nomi chiari ("Ingresso principale", "Magazzino porta 2"): compaiono negli eventi e nei menu.
2. **Indirizzo IP** e **porta TCP** del dispositivo: 80 per HTTP / ISAPI, 8000 per il canale SDK.
3. **Protocollo di comunicazione**:
   - **HTTP / ISAPI**: terminali e controller con interfaccia web e gestione "a persone" (nome, tessere, PIN e validità per ogni utente). È il canale consigliato.
   - **SDK Hikvision**: controller senza HTTP, raggiungibili solo sulla porta di servizio 8000 (es. DS-K2604 di prima generazione), come fa iVMS-4200. Su questi controller "a tessere" il dispositivo conosce solo i numeri di tessera, non i nomi.
   - I controller di generazione successiva (es. DS-K2602T, DS-K2604T) hanno il firmware "a persone" e rispondono anche sulla porta 8000, ma utenti e tessere si scrivono solo via HTTP: usa la porta **80** e il protocollo HTTP / ISAPI, con le stesse credenziali (via SDK la console li legge e li comanda, e all'invio di un utente segnala di passare a HTTP).
   - **Automatico**: decide la porta (8000 = SDK, altrimenti HTTP).
4. **Utente e password del dispositivo** (di solito l'account admin del terminale). La password non viene mai mostrata; in modifica, lasciandola vuota resta invariata.
5. **Porta del controller**: numero della porta (1 per i terminali), nome e **tempo relè**, cioè i secondi di sblocco della serratura. Con **Scrivi nome porta e tempo relè sul dispositivo** i valori vengono scritti sul dispositivo; altrimenti vengono riletti da lì a ogni scansione.

Al salvataggio la console verifica subito la connessione e legge modello, seriale e firmware.

> [!TIP]
> **Più terminali uguali.** Dal menu di un varco esistente, **Nuovo varco con le stesse credenziali** apre la scheda già compilata con protocollo, porta TCP, utente e password del varco di origine (nei terminali a singola porta la password è di solito la stessa per tutto il sito): basta inserire nome e indirizzo IP del nuovo dispositivo.

### <a id="varchi-multiporta"></a>Controller multi-porta

Un controller a 2 o 4 porte (es. DS-K2604) si gestisce creando **un varco per ogni porta usata**, tutti con lo stesso indirizzo IP e il numero di porta corrispondente. Il modo più rapido è **Aggiungi un'altra porta di questo controller** dal menu del primo: propone gli stessi parametri di connessione e la prima porta libera, riusando la password. La console coordina le scritture sulle porte dello stesso controller, così i permessi di una porta non cancellano quelli delle altre.

### <a id="varchi-stato"></a>Stato e scansione

- **Online**: il varco ha risposto all'ultima scansione; accanto il tempo di risposta in millisecondi.
- **Offline**: nessuna risposta o credenziali rifiutate; il motivo è indicato accanto allo stato.
- **In verifica**: il varco non è ancora stato interrogato (appena aggiunto o server appena avviato).
- **Sospeso**: il varco supera i varchi consentiti dalla [licenza](#sistema-licenza). Resta configurato, ma non viene monitorato, non riceve comandi né utenti e non legge tessere; sopra l'elenco un avviso indica quanti sono.

Lo stato viene aggiornato dalla **scansione automatica** del server (intervallo impostabile in [Impostazioni](#sistema-impostazioni), predefinito ogni 10 secondi) e a richiesta con **Scansiona tutti** o con **Aggiorna adesso** nella dashboard. La scansione legge anche i nuovi eventi.

### <a id="varchi-comandi"></a>Comandi porta

Disponibili ad amministratori e operatori dal menu del varco (pagina Varchi, dashboard ed eventi):

| Comando | Effetto |
| --- | --- |
| **Apri porta (impulso)** | Sblocca la serratura per il tempo relè, poi la porta torna chiusa. È anche il pulsante **Apri** nelle righe e nei riquadri. |
| **Chiudi porta** | Richiude subito la serratura (interrompe un impulso o ripristina lo stato normale). |
| **Sblocco permanente** | La porta resta **aperta** finché non invii un altro comando. Per eventi o emergenze; richiede conferma. |
| **Blocco permanente** | La porta resta **chiusa** e nemmeno le tessere autorizzate la aprono, finché non la ripristini con **Chiudi porta** o **Apri porta**. Richiede conferma. |

Ogni comando viene registrato nel [registro attività](#sistema-registro) con l'operatore che lo ha inviato.

### <a id="varchi-diagnostica"></a>Diagnostica e orologio

- **Diagnostica e test connessione** verifica il varco e mostra canale, seriale, firmware e le informazioni lette dal dispositivo oppure il motivo preciso dell'errore. Riabilita anche un tentativo dopo un rifiuto delle credenziali.
- **Sincronizza orologio con il server** imposta data e ora del dispositivo uguali a quelle del server. Un orologio sbagliato produce eventi con l'ora errata e può far rifiutare utenti con validità a date: controllalo periodicamente, in particolare dopo un'interruzione di corrente e ai cambi dell'ora legale. Il pulsante **Sincronizza orario** in alto nella pagina Varchi lo fa su tutti i varchi del sito in una volta, con l'esito per ciascuno.
- **Copia indirizzo IP** copia l'IP negli appunti, per aprire l'interfaccia web del terminale.

### <a id="varchi-interfaccia-web"></a>Interfaccia web del dispositivo

Le configurazioni avanzate che si fanno direttamente sul terminale (modalità di autenticazione, lettori, fasce orarie, rete, aggiornamento del firmware) restano nella sua pagina web. Il pulsante nella riga del varco, o la voce **Interfaccia web del dispositivo** nel menu, mostra l'indirizzo della pagina, l'utente e, per gli amministratori, **Copia password**; **Apri in una nuova scheda** apre la pagina del terminale, dove basta incollare la password.

> [!NOTE]
> L'accesso automatico non è possibile: la pagina di login del terminale non accetta credenziali passate da un'altra applicazione. Ogni copia della password viene registrata nel [registro attività](#sistema-registro) e la password resta negli appunti finché non copi altro.

### <a id="varchi-credenziali"></a>Credenziali rifiutate e blocco del dispositivo

I dispositivi Hikvision bloccano per un certo tempo (di solito 30 minuti) un account che sbaglia la password più volte di seguito. Per questo, quando un varco rifiuta le credenziali, il server **sospende i tentativi** su quel varco invece di insistere a ogni scansione, e lo segnala come Offline con il motivo "credenziali rifiutate".

1. Apri la scheda del varco, inserisci la password corretta e salva: i tentativi riprendono.
2. Se la password era giusta ma il dispositivo era già bloccato, attendi lo sblocco (il messaggio indica il tempo, quando il dispositivo lo comunica) e poi usa **Diagnostica e test connessione**.

### <a id="varchi-eliminare"></a>Modificare, duplicare, eliminare

Dal menu del varco (amministratori): **Modifica parametri varco**, **Nuovo varco con le stesse credenziali**, **Aggiungi un'altra porta di questo controller**, **Elimina varco**. L'eliminazione toglie il varco dalla console e dai permessi di gruppi e utenti, ma **non modifica il dispositivo**: le persone caricate sul terminale continuano a esistere lì. Prima di dismettere un terminale rimuovi gli utenti (deploy dopo aver tolto le autorizzazioni) oppure reinizializzalo.

## <a id="gruppi"></a>Gruppi di accesso

Pagina **Gruppi di accesso**. Un gruppo è un **modello** di varchi autorizzati del sito attivo, ad esempio "Tutti i varchi", "Solo uffici", "Magazzino e carico". Serve a non dover spuntare i varchi uno per uno per ogni persona.

- **Creare un gruppo**: nome, descrizione e spunta dei varchi del sito.
- **Assegnarlo a un utente**: nella scheda utente il campo **Gruppo** precompila i varchi; puoi poi aggiungere o togliere varchi per quella persona. Il pulsante **Da gruppo** ricarica in qualsiasi momento i varchi del modello.
- **Modificare un gruppo che ha già membri**: al salvataggio la console chiede cosa fare con le persone del gruppo: Le personalizzazioni dei membri su questo sito vengono sovrascritte dal riallineamento; gli altri siti non vengono toccati.
   - **Riallinea e invia ai varchi** (consigliato): aggiorna i varchi dei membri su questo sito e li sincronizza subito;
   - **Riallinea senza inviare**: aggiorna solo l'archivio della console; l'invio ai varchi si farà in seguito;
   - **Salva solo il gruppo**: il modello cambia per i prossimi utenti, i membri attuali restano com'erano.
- **Sincronizza utenti del gruppo**: invia tutti i membri ai varchi del sito, usando i varchi autorizzati di ciascuno.
- **Mostra utenti di questo gruppo**: apre l'anagrafica filtrata.
- **Elimina gruppo**: i membri restano senza gruppo ma conservano i loro varchi autorizzati.

## <a id="utenti"></a>Utenti, tessere e PIN

Pagina **Utenti e tessere**: l'anagrafica di tutto l'impianto. La colonna **Varchi sito** indica su quanti varchi del sito attivo la persona è autorizzata; i filtri sopra la tabella mostrano tutti, solo gli autorizzati sul sito, chi non ha varchi o i disabilitati. La ricerca lavora su nome, matricola e numeri di tessera. Per trovare il titolare di una tessera che hai in mano usa [Identifica badge](#utenti-identifica).

### <a id="utenti-anagrafica"></a>Anagrafica

- **Matricola / ID**: codice univoco con cui la persona esiste sui dispositivi. **Non si può modificare** dopo la creazione (per cambiarla si elimina e si ricrea l'utente). Meglio usare solo cifre, perché alcuni terminali non accettano lettere.
- **Nome e cognome**, **reparto**, **sesso**: informazioni inviate ai terminali "a persone" e mostrate negli eventi.
- **Gruppo**: il modello di varchi del sito attivo (vedi [Gruppi di accesso](#gruppi)).
- **Tipo utente**: **normale**; **visitatore**, con un numero massimo di passaggi (campo **Numero di visite consentite**); **persona in elenco bloccati**, sempre respinta con registrazione dell'allarme sul dispositivo.

### <a id="utenti-tessere"></a>Tessere

- **Tessera principale**: il numero letto dal terminale (in genere il numero stampato sulla tessera o il codice del chip in decimale). **Cattura da varco** lo acquisisce direttamente dal lettore: scegli il varco, avvicina la tessera entro 30 secondi, controlla il numero letto e premi **Usa questa tessera**. Se la tessera risulta già assegnata a un'altra persona la console lo segnala prima di accettarla. Se la scheda ha già una tessera principale, la console chiede se **aggiungere** quella letta come altra tessera (secondo badge) o **sostituire** la principale (badge smarrito). In alternativa puoi digitare il numero a mano.
- **Altre tessere della stessa persona**: aggiungi un numero e premi <kbd>Invio</kbd> (o virgola, spazio), oppure usa il pulsante **Cattura da varco** accanto al campo. Tutte le tessere ricevono gli stessi varchi autorizzati.
- Una tessera può appartenere a **una sola persona**: la console rifiuta i duplicati e, quando riceve dai varchi un record "solo tessera" che corrisponde a una persona già in anagrafica, li unisce.

> [!WARNING]
> **Tessera smarrita o restituita.** Toglila dalla scheda e salva: la console la **revoca su tutti i varchi di tutti i siti**, non solo su quelli del sito attivo, così smette subito di aprire. Se la persona resta in servizio con una nuova tessera, inseriscila nella stessa operazione.

### <a id="utenti-pin"></a>PIN

Il **PIN tastiera** è un codice da 4 a 8 cifre usato sui terminali con tastierino. È il terminale, con la propria modalità di autenticazione (solo tessera, tessera + PIN, PIN...), a decidere se e quando richiederlo: la console si limita a inviarlo insieme alla persona. Il PIN è visibile solo ad amministratori e operatori (pulsante ).

### <a id="utenti-validita"></a>Validità e accesso

- **Utente abilitato all'accesso**: se disattivato, alla sincronizzazione il diritto viene revocato su tutti i varchi. È il modo corretto per sospendere una persona senza cancellarla.
- **Utente effettivo a lungo termine**: nessuna scadenza (in pratica 31/12/2037). Togliendo la spunta puoi indicare **inizio** e **fine validità** precisi, utili per visitatori, tirocinanti e ditte esterne.
- **Numero di visite consentite**: per i visitatori, quanti passaggi sono ammessi prima che il terminale neghi l'accesso; **Nessun limite di visite** lo disattiva.

> [!NOTE]
> Le date le verifica il dispositivo con il proprio orologio: se l'ora del terminale è sbagliata, una validità corretta può essere rifiutata. Vedi [Diagnostica e orologio](#varchi-diagnostica).

### <a id="utenti-varchi"></a>Varchi autorizzati

Nella sezione **Varchi autorizzati · sito ...** spunti i varchi del sito attivo su cui la persona può passare. La casella di ricerca filtra l'elenco; **Da gruppo** ricarica i varchi del gruppo scelto; **Tutti** e **Nessuno** agiscono sull'intero elenco. Le autorizzazioni sugli **altri siti** restano invariate: per modificarle cambia sito attivo dal selettore in alto e riapri la scheda della persona (la nota sotto l'elenco ricorda su quanti varchi di altri siti è autorizzata).

### <a id="utenti-sincronizzazione"></a>Salvare e inviare ai varchi

Il pulsante **Salva utente** registra la scheda nella console. Con l'interruttore **Invia subito ai varchi** attivo (impostazione predefinita) parte anche l'invio a tutti i varchi del sito attivo: l'accesso viene **concesso** dove spuntato e **revocato** sugli altri varchi del sito. Una finestra mostra l'avanzamento e l'esito per ogni varco (vedi [Operazioni in background](#operazioni)).

Se disattivi l'interruttore, la modifica resta solo nella console. Per inviarla in seguito usa **Sincronizza su tutti i varchi del sito** dal menu dell'utente, oppure il [deploy atomico](#backup-deploy) per riallineare tutto l'impianto in una volta. I varchi offline al momento dell'invio vengono segnalati nel log: ripeti l'invio quando tornano raggiungibili.

### <a id="utenti-ricevere"></a>Ricevere gli utenti da un varco

**Ricevi da varco** scarica le persone e le tessere presenti su un dispositivo e le unisce all'anagrafica: chi esiste già viene aggiornato, chi è nuovo viene creato con l'autorizzazione sul varco interrogato. Le autorizzazioni sugli altri varchi non cambiano. È il modo più rapido per adottare la console su un impianto già in funzione: scegli **Tutti i varchi del sito** (vengono interrogati uno dopo l'altro; i varchi non raggiungibili sono saltati e segnalati nel log) oppure un varco alla volta, poi controlla gruppi e autorizzazioni. Sui controller a più porte ogni porta è un varco: con un solo varco si riceve il permesso di quella porta soltanto.

Dai controller "a tessere" (senza anagrafica) arrivano solo i numeri: la console crea record **solo tessera**, che puoi completare con il nome aprendo la scheda (la matricola resta il numero della tessera), anche passando le tessere una dopo l'altra con [Identifica badge](#utenti-identifica). Per una matricola diversa crea un nuovo utente con quella tessera: il record solo tessera viene unito. Se la stessa tessera è già di una persona nota, i record vengono uniti.

### <a id="utenti-identifica"></a>Identificare un badge

**Identifica badge**, in alto nella pagina, trova la persona a cui appartiene una tessera passandola sul lettore di un varco: è il modo più rapido per dare nome e cognome ai record **solo tessera**. Scegli il varco e avvicina la tessera entro 30 secondi, oppure digita il numero. La console mostra di chi è e apre da sola la sua scheda, con **Nome e cognome** già selezionato: scrivi il nome e premi <kbd>Invio</kbd> (o **Salva utente**). Se la tessera non è registrata si apre la scheda di un **nuovo utente** con quella tessera e, come matricola proposta, il suo numero.

Funziona **a raffica**: chiusa la scheda, salvata o no, la finestra di lettura si riapre per il badge successivo. L'invio ai varchi di ogni scheda salvata prosegue in background e un avviso ne indica l'esito. Per smettere premi **Annulla** nella finestra di lettura.

### <a id="utenti-azioni"></a>Altre azioni sull'utente

Dal menu del tasto destro sulla riga:

- **Mostra storico transiti**: gli eventi degli ultimi 30 giorni della persona.
- **Apri primo varco autorizzato**: comando di apertura sul primo varco del sito su cui la persona è autorizzata (utile in portineria).
- **Copia numero badge** / **Copia matricola** negli appunti.
- **Elimina utente da anagrafica e varchi**: cancella la persona dalla console e da **tutti i varchi di tutti i siti**; le sue tessere smettono di aprire. L'operazione mostra l'esito per ogni varco.

## <a id="dashboard"></a>Dashboard

La **Dashboard** è il quadro d'insieme del sito attivo:

- **Indicatori**: varchi totali e online, utenti registrati e autorizzati sul sito, transiti di oggi (con il confronto di ieri) e accessi negati.
- **Stato varchi**: un riquadro per varco con stato, indirizzo, canale, tempo di risposta ed eventuale errore; clic sul riquadro per la scheda del varco, pulsante **Apri** e menu ⋯ con tutti i comandi.
- **Attività in tempo reale**: gli ultimi 20 eventi del sito; i nuovi vengono evidenziati. Clic per aprire la persona, tasto destro o ⋯ per il menu dell'evento.
- **Transiti di oggi per ora**: accessi concessi e negati ora per ora; passa il mouse sulle colonne per i valori, **Tabella** mostra i numeri.

La pagina si **aggiorna da sola** con l'intervallo scelto in alto a destra (da 3 a 120 secondi, impostazione di questo browser) leggendo lo stato già noto al server. **Aggiorna adesso** chiede invece al server una scansione immediata dei varchi. Quando la scheda del browser è in secondo piano l'aggiornamento si ferma e riprende al ritorno.

## <a id="eventi"></a>Eventi e storico

Pagina **Eventi e storico**: tutti i passaggi, i tentativi negati e gli allarmi dei varchi del sito attivo, archiviati nel database della console.

### <a id="eventi-raccolta"></a>Come vengono raccolti

A ogni scansione automatica il server chiede a ogni varco gli eventi nuovi rispetto all'ultimo archiviato, quindi in pagina compaiono con un ritardo al massimo pari all'intervallo di scansione. Se il server è rimasto spento, al riavvio recupera gli eventi persi nel frattempo (fino a 3.000 per varco). **Sincronizza dai varchi** forza una lettura immediata di tutti i varchi del sito.

### <a id="eventi-consultare"></a>Consultare e filtrare

- Periodo rapido (**Oggi, Ieri, 7 giorni, 30 giorni**) oppure date **dal / al**; filtro per **varco** e per **tipo evento**; ricerca per nome, matricola o numero di badge.
- Il selettore **max** limita il numero di righe mostrate (500-5.000): se il limite viene raggiunto, restringi il periodo o i filtri.
- Menu del tasto destro su un evento: **Apri porta di questo varco**, copia badge/matricola/nome, **Cerca storico di questo utente/badge**, **Filtra storico per questo varco**, **Mostra tutti gli eventi di oggi**, **Assegna badge / crea utente**.
- Clic su un evento: apre la persona in anagrafica; se il badge non è di nessuno, propone di creare l'utente con quel numero già inserito.
- Le descrizioni ("Accesso concesso (PIN)", "Porta aperta troppo a lungo", "Manomissione lettore"…) seguono la tabella ufficiale dei codici evento Hikvision, la stessa per SDK e ISAPI. Un codice non ancora in tabella compare come `Evento 5/0x..` e viene ridescritto da solo al primo avvio di una versione che lo conosce.

> [!TIP]
> **Registrare una tessera sconosciuta.** Passa la tessera su un lettore, cerca l'evento "accesso negato" appena comparso e scegli **Assegna badge / crea utente**: la scheda si apre con il numero già compilato.

### <a id="eventi-esportare"></a>Esportare

**Esporta CSV** scarica gli eventi corrispondenti ai filtri correnti (fino a 100.000 righe) in un file apribile con Excel, con separatore e codifica già corretti per la versione italiana.

### <a id="eventi-archivio"></a>Archivio e manutenzione

La scheda **Archivio e manutenzione** mostra quanti eventi sono archiviati, lo spazio occupato e il periodo coperto.

- **Autoconservazione**: gli eventi più vecchi del numero di giorni impostato (predefinito 90) vengono eliminati all'avvio del server e poi ogni 6 ore. **Esegui pulizia** lo fa subito. Scegli il periodo in base alle regole sulla privacy del tuo impianto: ciò che viene cancellato non è recuperabile.
- **Ottimizza database**: compatta il file e ricostruisce gli indici; sicuro, utile dopo grandi cancellazioni.
- **Rigenera tabella eventi**: **cancella tutti gli eventi** e ricrea la tabella. Solo per un database danneggiato, dopo aver esportato ciò che serve.

## <a id="operazioni"></a>Operazioni in background

Gli invii ai varchi (utente, gruppo, deploy), le eliminazioni e la ricezione dell'anagrafica sono eseguiti dal server e mostrati in una finestra con barra di avanzamento, contatori di riusciti ed errori e **log in tempo reale**, una riga per varco. Al termine un riepilogo indica l'esito complessivo.

- **Continua in background** chiude la finestra senza fermare l'operazione: in alto compare il contatore **operazioni in corso**, da cui puoi riaprirla; al termine ricevi una notifica.
- **Annulla operazione** (dove disponibile: sincronizzazione di gruppo, deploy, ricezione) ferma il lavoro al termine del passo in corso. I varchi già scritti restano aggiornati.
- Le operazioni concluse restano consultabili, con il loro log, in **Backup e deploy → Operazioni recenti** (le ultime 40 dall'avvio del server). Gli operatori vedono le proprie, gli amministratori tutte.

Un varco offline durante un'operazione viene segnalato come errore in quella riga: la console conserva comunque la configurazione corretta, e basta ripetere l'invio (o un deploy) quando il varco torna raggiungibile.

## <a id="backup"></a>Backup, ripristino e deploy

Pagina **Backup e deploy** (amministratori).

### <a id="backup-esporta"></a>Esporta configurazione

Scarica un unico file JSON con siti, varchi (comprese le password dei dispositivi), gruppi, utenti, tessere, PIN e permessi. Gli eventi non sono inclusi. Fallo dopo ogni modifica importante e **conservalo in un luogo protetto**: contiene credenziali. Il formato è lo stesso dell'app desktop HikAccess Pro, quindi il file si può importare anche lì.

### <a id="backup-importa"></a>Importa e ripristina

Sostituisce l'intera configurazione con quella del file scelto: un'esportazione della console, il file `hikaccess_config.json` dell'app desktop oppure un pacchetto `HikAccess_FullBackup_*.json` (anche nel vecchio formato monosito, migrato automaticamente). Prima del ripristino la console mostra cosa contiene il file e salva una **copia di sicurezza** della configurazione attuale nella cartella dati del server (`data\backups`, ultime 30). Gli eventi archiviati non vengono toccati. Al termine la console propone di avviare il deploy atomico. Se il file contiene più siti o varchi di quelli consentiti dalla [licenza](#sistema-licenza), viene ripristinato tutto ma i varchi in più restano sospesi: l'esito lo indica.

> [!NOTE]
> **Migrare dall'app desktop.** Importa il suo `hikaccess_config.json` (si trova accanto a `HikAccessPro.exe`), lancia il deploy atomico e da quel momento usa la console come sistema principale. Non far lavorare app desktop e console sugli stessi varchi contemporaneamente: le modifiche si sovrascriverebbero.

### <a id="backup-deploy"></a>Deploy atomico

Riscrive **ogni utente su ogni varco di ogni sito**: accesso concesso dove autorizzato, revocato altrove. Serve a rimettere in coerenza dispositivi e console dopo un ripristino, la sostituzione o il reset di un terminale, oppure dopo modifiche salvate senza "Invia subito ai varchi". Può richiedere diversi minuti (il numero di operazioni è utenti × varchi); si può annullare e il log riporta l'esito varco per varco.

### <a id="backup-cartella-dati"></a>Backup della cartella dati del server

Oltre all'esportazione, includi nei backup del server l'intera cartella dati (vedi [Server e installazione](#server)): contiene configurazione, database degli eventi, account degli operatori, chiavi di sessione e licenza.

## <a id="sistema"></a>Sistema

### <a id="sistema-operatori"></a>Operatori

**Operatori**: gli account della console. Per ogni account: nome utente (non modificabile), nome e cognome, [ruolo](#ruoli), stato abilitato/disabilitato, ultimo accesso con indirizzo, data dell'ultimo cambio password.

- **Nuovo operatore**: crea l'account con una password iniziale; consiglia all'operatore di cambiarla al primo accesso da **Profilo e sicurezza**.
- **Reimposta password**: per chi l'ha dimenticata; le sue sessioni aperte vengono chiuse.
- **Disabilita account**: blocca l'accesso senza cancellare lo storico delle operazioni; preferibile all'eliminazione per chi lascia l'azienda.
- **Disattiva verifica in due passaggi**: per chi ha perso il telefono e i codici di recupero; l'operatore potrà riattivarla dal suo profilo. La colonna **Due passaggi** mostra chi l'ha attiva.
- **Elimina account**: rimuove l'account; il registro attività conserva le operazioni già eseguite.
- Il proprio account non può disabilitarsi né cambiare ruolo da qui; la propria password si cambia da **Profilo e sicurezza**. Deve restare almeno un amministratore abilitato.

Le password sono salvate solo come impronta crittografica: nessuno, nemmeno un amministratore, può leggerle.

### <a id="sistema-chiavi-api"></a>Chiavi API e integrazioni (Home Assistant)

**Chiavi API** (solo amministratori): le chiavi con cui **Home Assistant** o un altro sistema domotico apre i varchi tramite il **servizio REST** della console, senza un account da operatore. Ogni comando finisce nel [registro attività](#sistema-registro) con il nome della chiave al posto dell'operatore (per esempio «API · Home Assistant»).

> [!NOTE]
> Il servizio REST non è compreso nella versione gratuita: serve una [licenza](#sistema-licenza) che lo comprenda. Senza, la pagina lo segnala, non si creano chiavi e il servizio risponde **403** anche alle chiavi già create.

- **Nuova chiave**: nome (compare nel registro attività, quindi è unico), **scadenza** (nessuna, 30 o 90 giorni, un anno oppure fino a una data) e **varchi consentiti**: tutti, compresi quelli aggiunti in seguito, oppure solo quelli spuntati. Per un'integrazione che comanda un solo cancello conviene limitarla a quel varco.
- Alla creazione la chiave compare **una volta sola**, con il pulsante **Copia** e un esempio pronto per Home Assistant: copiala subito. Il server ne conserva solo l'impronta e nessuno potrà rileggerla; se la perdi, elimina la chiave e creane un'altra.
- Clic su una chiave: modifica di nome, scadenza e varchi, oppure **Chiave attiva** per sospenderla senza eliminarla. Con il tasto destro anche **Mostra nel registro attività** ed **Elimina chiave**, che la revoca subito.
- L'elenco mostra l'inizio di ogni chiave (es. `hap_AbC123…`, per riconoscerla), la scadenza, l'**ultimo uso** con l'indirizzo di provenienza e lo stato: attiva, disattivata o scaduta.

**Varchi ed endpoint**: per ogni varco l'**ID** e l'indirizzo di apertura, da copiare con il pulsante accanto; il tasto destro copia anche il comando `curl` e la configurazione per Home Assistant. In alto si sceglie l'**indirizzo della console** con cui il sistema raggiunge il server: nella rete locale quello interno (es. `http://192.168.1.10:5080`).

| Richiesta | Risposta |
| --- | --- |
| `POST /api/v1/doors/<ID>/open` | Apre il varco con un impulso, come **Apri** nella console. **200** se il varco ha eseguito il comando; **401** chiave mancante o errata; **403** chiave disattivata, scaduta o non abilitata per il varco, servizio REST non compreso nella licenza o varco sospeso; **404** varco inesistente; **502** varco che non ha eseguito il comando (spento o non raggiungibile); **429** troppe chiavi errate dallo stesso indirizzo. |
| `GET /api/v1/doors` | I varchi utilizzabili con la chiave (ID, nome, sito, online): serve anche a provarla. |

La chiave va nell'intestazione `Authorization: Bearer <chiave>`, oppure in `X-API-Key: <chiave>` quando l'intestazione Authorization è già usata da un proxy; mai nell'indirizzo, che resterebbe nei log. L'apertura risponde solo a **POST**: incollato nel browser, l'indirizzo non apre la porta. Le risposte sono in JSON, con `ok` e, in caso di errore, `error`.

**Esempio con Home Assistant**: in `configuration.yaml`

```yaml
rest_command:
  apri_ingresso:
    url: "http://192.168.1.10:5080/api/v1/doors/1/open"
    method: post
    headers:
      Authorization: !secret hikaccess_api
```

e in `secrets.yaml` la riga `hikaccess_api: "Bearer hap_…"` con la chiave. Dopo il riavvio di Home Assistant il servizio `rest_command.apri_ingresso` si usa in pulsanti, automazioni e script.

> [!WARNING]
> Chi ha la chiave apre i varchi consentiti: trattala come una password, limitala ai varchi che servono e usa una scadenza per le prove. Fuori dalla rete locale usa solo HTTPS (per esempio tramite KeenDNS): in HTTP la chiave viaggerebbe in chiaro. Dopo 10 chiavi errate in 5 minuti da uno stesso indirizzo, il server rifiuta per 5 minuti le richieste API da quell'indirizzo.

### <a id="sistema-licenza"></a>Licenza e attivazione

**Licenza** (solo amministratori). Senza chiave di attivazione la console è la **versione gratuita**: **1 sito** e **2 varchi**, senza il [servizio REST](#sistema-chiavi-api); tutte le altre funzioni (utenti, tessere, PIN, gruppi, eventi, operatori, backup, accesso remoto) sono complete. Una **licenza** amplia siti e varchi e può comprendere il servizio REST; può essere senza scadenza oppure a tempo, come la prova di 30 giorni.

- **Stato della licenza**: versione gratuita oppure licenza attivata, con intestatario, numero, limiti e scadenza; sotto, siti e varchi in uso rispetto a quelli consentiti.
- **Codice macchina**: identifica il server, e la chiave di attivazione vale solo per quel codice. Non cambia con riavvii, aggiornamenti, nome o indirizzo IP del server; cambia se reinstalli Windows o sposti il programma su un altro computer.
- **Richiedi l'attivazione**: indica la ragione sociale (sarà l'intestatario della licenza), referente, telefono, un'eventuale email per la risposta, se chiedi una licenza o una prova di 30 giorni, quanti siti e varchi ti servono e se ti serve il servizio REST. **Scrivi l'email** apre il programma di posta con la richiesta pronta per **b.leonardi78@gmail.com**, già completa di codice macchina, versione e dati del server. Con la posta nel browser usa **Copia la richiesta** e incollala in un nuovo messaggio a quell'indirizzo.
- **Chiave di attivazione**: incolla la chiave ricevuta (inizia con `HAP1-`; va bene anche il testo dell'intera email) e premi **Attiva**. La console controlla che sia autentica, emessa per questo server e non scaduta, e applica subito i nuovi limiti. Nella stessa casella si inserisce la chiave nuova di un ampliamento o di un rinnovo.
- **Rimuovi la licenza**: si torna alla versione gratuita, per esempio prima di trasferire la licenza su un altro server.

**Oltre i limiti.** Senza la licenza adatta non si aggiungono siti o varchi oltre quelli consentiti e non si creano chiavi API: la console lo segnala con il collegamento **Vai alla pagina Licenza**. Se i varchi configurati sono più di quelli consentiti (licenza scaduta o rimossa, ripristino di un backup più grande), restano in uso i primi in ordine di ID dei primi siti e gli altri diventano **sospesi**: restano in elenco, ma non vengono monitorati, non ricevono comandi né utenti e non si leggono tessere da lì. Per sicurezza la revoca delle tessere tolte e l'eliminazione degli utenti raggiungono anche i varchi sospesi.

Alla scadenza la console torna da sola ai limiti della versione gratuita, senza perdere configurazione ed eventi; il riquadro nel menu laterale avvisa gli amministratori negli ultimi 30 giorni. Attivazioni, chiavi rifiutate e rimozioni finiscono nel [registro attività](#sistema-registro) (categoria **Licenza**).

> [!NOTE]
> **Trasferire la licenza** su un altro server, o dopo aver reinstallato Windows: dalla pagina Licenza del server nuovo invia una richiesta e scrivi nelle note che si tratta di un trasferimento. La chiave nuova sarà emessa per il nuovo codice macchina.

### <a id="sistema-impostazioni"></a>Impostazioni

**Impostazioni**, valide per tutto il server e applicate subito:

- **Nome dell'impianto**: mostrato nella pagina di accesso e nell'intestazione.
- **Scansione automatica in background** e **intervallo** (5-120 secondi): il server interroga tutti i varchi di tutti i siti, aggiorna lo stato e scarica gli eventi anche a console chiusa. 10-30 secondi è un buon compromesso tra reattività e traffico verso i dispositivi. Spegnendola, stato ed eventi si aggiornano solo su richiesta.
- **Conservazione eventi** (predefinito 90 giorni) e **conservazione registro attività** (predefinito 365 giorni).
- **Chiusura della sessione per inattività**: da 15 minuti a 7 giorni. Per un monitor sempre acceso usa un account in sola lettura e una durata lunga.
- **Browser di fiducia dopo la verifica in due passaggi**: per quanti giorni (da 1 a 90, oppure "Mai") un browser segnato come di fiducia non richiede il codice OTP, e se la fiducia decade quando cambia l'indirizzo IP del browser. Vedi [Browser di fiducia](#profilo-2fa-fiducia).
- **Accesso remoto**: i **proxy attendibili** e la verifica **Questa connessione**. Vedi [Accesso remoto e proxy](#sistema-accesso-remoto).
- **Informazioni di sistema**: versione, licenza, nome del server, avvio e tempo di attività, modalità (servizio di Windows o finestra), disponibilità dell'SDK Hikvision, cartella dati, conteggi della configurazione, ultima scansione e ultima pulizia.
- **Aggiornamento del programma**: versione installata, avviso delle nuove versioni con le novità e il collegamento per scaricare il setup, esito dell'ultimo aggiornamento e installazione di una nuova versione caricando il setup. L'interruttore **Avvisa quando esce una nuova versione** si salva con le altre impostazioni. Vedi [Aggiornare e disinstallare](#server-aggiornamento) e [Avviso delle nuove versioni](#server-avviso-versioni).

### <a id="sistema-accesso-remoto"></a>Accesso remoto e proxy

Quando la console è pubblicata su Internet tramite un **reverse proxy** (il router Keenetic con KeenDNS, Caddy, nginx, IIS, Cloudflare Tunnel), le richieste arrivano al server dal proxy. Il proxy indica l'indirizzo reale di chi si collega nell'intestazione `X-Forwarded-For`, ma il server la usa solo se il proxy è nell'elenco dei **proxy attendibili**: altrimenti chiunque potrebbe falsificare il proprio indirizzo. Senza l'elenco, blocco dei tentativi e registro attività vedrebbero per tutti l'indirizzo del proxy: 30 password sbagliate di un estraneo bloccherebbero l'accesso remoto a tutti per 15 minuti.

- Un indirizzo IP o una rete (es. `192.168.1.0/24`) per riga; le modifiche valgono subito dopo il salvataggio. Le richieste che arrivano da un proxy in elenco contano sempre come accessi da fuori: per esempio da lì non si può aggiornare il programma.
- Alcuni proxy, come **KeenDNS** dei router Keenetic, non comunicano né l'indirizzo di chi si collega né il protocollo: aggiungili comunque e, se pubblicano la console in HTTPS, spunta **I proxy pubblicano la console in HTTPS**. Così i cookie di sessione diventano "solo HTTPS" e il browser userà sempre HTTPS.
- **Questa connessione** mostra come il server vede la tua richiesta: l'indirizzo aperto nel browser, l'indirizzo visto dal server, il protocollo (HTTP o HTTPS) e se sei passato da un proxy attendibile. Se arrivi da un proxy non ancora in elenco, il pulsante **Aggiungi** lo inserisce (poi salva).

**Esempio con KeenDNS** (router Keenetic): nel router, in *Domain name → KeenDNS → Access to Web Applications Running on Your Network*, pubblica il server (porta 5080) con *Remote access from the Internet* impostato su *Password protected*, così il router chiede una sua password prima della console. Poi apri l'indirizzo KeenDNS e vai in Impostazioni: **Questa connessione** mostra **Proxy da riconoscere** con l'indirizzo del router nella rete locale (es. 192.168.1.1). Premi **Aggiungi**, spunta **I proxy pubblicano la console in HTTPS** e salva: verificando di nuovo compaiono **Tramite proxy attendibile** e il protocollo HTTPS. Sul router non inoltrare mai la porta della console.

> [!WARNING]
> Con KeenDNS per la console tutti gli accessi da fuori arrivano dal router: il blocco dopo troppe password sbagliate vale per tutti gli accessi da fuori insieme e il registro attività mostra l'indirizzo del router. Per questo la password del router davanti alla console è importante. Per chi ha una VPN (per esempio Tailscale) l'accesso più sicuro resta quello diretto all'indirizzo interno del server.

### <a id="sistema-registro"></a>Registro attività

**Registro attività**: chi ha fatto cosa, quando, da quale indirizzo e con quale esito: accessi alla console (riusciti e falliti), comandi porta, modifiche a utenti, gruppi, varchi e siti, ripristini, deploy, cambi di impostazioni e operatori, aggiornamenti del programma e nuove versioni disponibili. Si filtra per periodo, categoria e testo libero e si esporta in CSV. La conservazione si imposta in Impostazioni.

I comandi arrivati con una [chiave API](#sistema-chiavi-api) hanno al posto dell'operatore il nome della chiave («API · Home Assistant»): cercandolo si vedono tutti i comandi di quell'integrazione. La categoria **Chiavi API** raccoglie creazioni, modifiche ed eliminazioni delle chiavi e le richieste con chiavi errate, scadute o disattivate. La categoria **Licenza** raccoglie attivazioni, chiavi di attivazione rifiutate (con il motivo) e rimozioni della licenza.

## <a id="profilo"></a>Profilo e sicurezza

Dal menu con il tuo nome, **Profilo e sicurezza**:

- **Cambia password**: serve la password attuale. La nuova deve avere almeno 8 caratteri con lettere e numeri o simboli e non può coincidere con il nome utente; l'indicatore colorato ne stima la robustezza. Le altre sessioni aperte con il tuo account vengono chiuse.
- **Verifica in due passaggi**: vedi sotto.
- **Aspetto**: tema chiaro, scuro o automatico (segue il sistema operativo). La scelta vale per questo browser.
- **Permessi del tuo ruolo**: promemoria di cosa puoi fare.

### <a id="profilo-2fa"></a>Verifica in due passaggi (OTP)

Con la verifica in due passaggi, dopo la password viene chiesto un **codice a 6 cifre** generato da un'app sul telefono: chi conoscesse la password non potrebbe comunque entrare. È facoltativa per ogni account ed è **indispensabile** per gli account che accedono da Internet.

1. Installa sul telefono un'app di autenticazione: Google Authenticator, Microsoft Authenticator, Aegis, FreeOTP o simili.
2. In **Profilo e sicurezza → Verifica in due passaggi** premi **Attiva**: compare un QR code.
3. Nell'app scegli **Aggiungi account** e inquadra il QR code (oppure digita la chiave mostrata accanto).
4. Inserisci il codice a 6 cifre che l'app mostra e conferma.
5. Salva gli **8 codici di recupero** (copia o scarica il file): ognuno vale una sola volta e sostituisce l'app se perdi il telefono. Non verranno mostrati di nuovo.

Da quel momento la pagina di accesso chiede il codice dopo la password (oppure un codice di recupero, nello stesso campo). Un codice vale 30 secondi e non può essere riusato; se il telefono ha l'ora sbagliata i codici vengono rifiutati. Per disattivare la verifica servono password e un codice valido.

> [!WARNING]
> **Telefono perso senza codici di recupero:** un amministratore può disattivare la verifica dal menu dell'account in **Operatori**; se sei l'unico amministratore, sul server il comando `HikAccessWeb.exe --reset-password <utente> <nuova password>` reimposta la password e toglie anche la verifica in due passaggi.

### <a id="profilo-2fa-fiducia"></a>Browser di fiducia

Digitare il codice a ogni accesso è scomodo sul proprio PC. Nella pagina del codice la casella **Non chiedere più il codice su questo browser per N giorni** (spuntata in partenza) segna il browser come **di fiducia**: per quel periodo, su quel browser, basta la password. La protezione resta: chi conoscesse la password ma usasse un altro PC o telefono troverebbe comunque la richiesta del codice.

- Il browser conserva un cookie riservato (non il codice né la chiave); sul server resta solo un'impronta, legata al tuo account.
- La fiducia scade dopo il periodo impostato dall'amministratore in [Impostazioni](#sistema-impostazioni) (predefinito 30 giorni) e, se così impostato, decade anche quando **cambia l'indirizzo IP** del browser (per esempio dal PC dell'ufficio al telefono in 4G): in quel caso viene chiesto di nuovo il codice, e puoi rinnovare la fiducia.
- In **Profilo e sicurezza → Verifica in due passaggi** vedi l'elenco dei tuoi browser di fiducia (browser e sistema, indirizzo, ultimo uso, scadenza) e li puoi **revocare** uno per uno o tutti insieme. Al massimo 10 per account.
- Disattivare la verifica in due passaggi, o farla disattivare da un amministratore, cancella anche tutti i browser di fiducia.
- Su un **PC condiviso** togli la spunta prima di inserire il codice: **Esci** chiude la sessione ma non revoca la fiducia del browser.

## <a id="server"></a>Server e installazione

### <a id="server-installazione"></a>Installazione

Il programma di installazione (`HikAccessWeb-<versione>-Setup.exe`) si esegue sul PC o server che farà da server, con diritti di amministratore. Chiede la **porta TCP** della console (predefinita 5080) e, se non esistono ancora account, l'**account amministratore** (facoltativo, vedi [Configurazione iniziale](#accesso-primo-avvio)). Installa poi il **servizio di Windows** "HikAccess Pro Web", che parte da solo a ogni avvio del sistema (con **avvio ritardato**: circa due minuti dopo l'avvio di Windows, quando il server è meno impegnato) anche senza utenti collegati e si riavvia in caso di errore, e controlla che la console risponda. Con il servizio installa anche l'[icona di stato](#server-icona-stato) per chi accede al server. Infine apre la porta nel Firewall di Windows per le reti Private e di Dominio (a richiesta anche per le Pubbliche) e crea i collegamenti nel menu Start. I dati (configurazione, database, account) stanno in `C:\ProgramData\HikAccessWeb`.

In alternativa, il pacchetto portabile (cartella con `HikAccessWeb.exe`) si avvia con un doppio clic e tiene i dati nella sottocartella `data`; gli script `Install-Service.ps1` e `Uninstall-Service.ps1` installano e rimuovono il servizio a mano. I dettagli tecnici (porta, HTTPS, cartella dati, riga di comando) sono nel file README della cartella di installazione.

### <a id="server-windows-server"></a>Windows Server

Sono supportati Windows Server 2016, 2019, 2022 e 2025, anche nella versione **Server Core** senza interfaccia grafica, oltre a Windows 10 e 11. Tutto il necessario è incluso nel setup: non serve installare altro prima.

- **Amministratore**: crealo nella pagina **Account amministratore** del setup e accedi da un PC della rete. Sul server spesso manca un browser adatto: Internet Explorer, l'unico di serie su Server 2016 e 2019, non è supportato (la console mostra un avviso) e Server Core non ha browser.
- **Rete Pubblica**: su un server non in dominio Windows classifica spesso la rete come Pubblica. Seleziona nel setup anche le **reti Pubbliche** (il riepilogo prima dell'installazione te lo segnala) oppure classifica la rete come Privata.
- **Server Desktop remoto**: usa sempre il servizio; senza, ogni utente collegato avvierebbe una propria copia del programma sulla stessa porta.

### <a id="server-icona-stato"></a>Icona di stato sul server

Con il servizio, il setup installa (opzione **Icona di stato**, selezionata) un'icona nell'area di notifica, accanto all'orologio, per chiunque accede al server, anche in Desktop remoto. Ogni 5 secondi controlla il servizio e la console; il pallino in basso a destra ne indica lo stato:

- **Verde**: in funzione, la console risponde. Il passaggio del mouse mostra anche la versione.
- **Giallo**: avvio, arresto o aggiornamento in corso; nei primi minuti dopo l'avvio di Windows (avvio ritardato); servizio avviato con la console che si sta ancora caricando.
- **Rosso**: servizio fermo, oppure avviato con la console che non risponde da più di 2 minuti. Se dura più di un minuto e mezzo compare un avviso di Windows, e un altro quando il servizio torna in funzione.
- **Grigio**: servizio non installato.

Doppio clic: apre la console. Clic destro: **Apri la console**, **Avvia il servizio** (se è fermo) o **Riavvia il servizio** (Windows chiede la conferma da amministratore), **Servizi di Windows**, **Chiudi l'icona**: il servizio continua a funzionare e l'icona ricompare al prossimo accesso, o subito dal menu Start → **Icona di stato di HikAccess Pro Web**. Dopo un aggiornamento l'icona passa da sola alla nuova versione. Su Server Core, senza area di notifica, non viene installata.

### <a id="server-icona"></a>Avvio con doppio clic: l'icona nell'area di notifica

Avviato con doppio clic o dal menu Start (senza servizio), il programma non apre finestre: compare un'**icona nell'area di notifica**, accanto all'orologio (se non la vedi, apri la freccia "Mostra icone nascoste"). Clic destro per il menu: **Apri la console**, **Mostra la finestra dei messaggi** (i messaggi tecnici del server, utili in caso di problemi), **Apri la cartella dati**, **Esci e arresta il server**. Il doppio clic sull'icona apre la console; un secondo avvio del programma non crea una seconda istanza ma apre la console. Con l'argomento `--console` si ottiene invece la finestra classica.

> [!WARNING]
> Finché il programma gira così, dipende dall'utente collegato: chiudendo la sessione di Windows si ferma. Per un server sempre attivo usa il **servizio di Windows** installato dal setup.

### <a id="server-rete"></a>Accesso dagli altri PC

Dagli altri PC della rete la console risponde su `http://<nome-del-server>:5080` (o l'IP del server). Se non si raggiunge: verifica che la rete del server sia classificata **Privata** o di Dominio (la regola del firewall vale per le reti Pubbliche solo se lo hai scelto nel setup), che la porta sia quella scelta e che il servizio sia in esecuzione.

### <a id="server-aggiornamento"></a>Aggiornare e disinstallare

Per aggiornare esegui il nuovo setup sopra l'installazione esistente: il servizio viene fermato, i file sostituiti e il servizio riavviato; dati, account e impostazioni restano. La disinstallazione (Impostazioni di Windows → App) rimuove servizio, regola del firewall e programma, e chiede se eliminare anche i dati.

Il setup di ogni versione si scarica dalla [pagina delle versioni](https://github.com/brn78/HikAccess-Pro-Web/releases) su GitHub; la console avvisa gli amministratori quando ne esce una nuova (vedi [Avviso delle nuove versioni](#server-avviso-versioni)).

**Dalla console**: **Impostazioni → Aggiornamento del programma**, scegli il nuovo setup (`HikAccessWeb-<versione>-Setup.exe`) e conferma con la tua password. Il server controlla che sia il setup di HikAccess Pro Web e che la versione non sia precedente a quella installata, poi lo installa. Il servizio resta fermo per circa un minuto e la console si ricarica da sola con la nuova versione. Per sicurezza, dato che il setup gira con i privilegi di sistema:

- solo gli **amministratori**, con la conferma della password;
- solo da un PC della **rete locale** del server (o dalla VPN), aprendo la console con l'indirizzo interno: non tramite KeenDNS o un altro proxy. Se hai aperto la console in un altro modo, il riquadro mostra l'indirizzo interno come collegamento e il pulsante **Apri la console locale**, che apre in una nuova scheda la console locale direttamente su questo riquadro (dopo l'accesso, se serve);
- solo con il **servizio di Windows installato dal setup**; il pacchetto portabile si aggiorna sostituendo i file.

L'esito dell'ultimo aggiornamento resta in Impostazioni; il log del setup è nella cartella dati, sottocartella `updates`.

### <a id="server-avviso-versioni"></a>Avviso delle nuove versioni

Una volta al giorno il server chiede a GitHub qual è l'ultima versione pubblicata di HikAccess Pro Web e la confronta con quella installata. Quando ne esce una nuova, gli **amministratori** vedono:

- un **pallino** sulla voce **Impostazioni** del menu, finché la versione nuova non viene installata;
- un avviso al primo accesso, una volta per versione e per browser, con il collegamento **Vedi le novità**;
- nel riquadro **Aggiornamento del programma**, la versione nuova con la data di pubblicazione, le **novità** e i pulsanti **Scarica il setup** e **Pagina della versione**, che aprono GitHub in un'altra scheda.

Nulla si installa da solo: scarichi il setup sul tuo PC e lo carichi nello stesso riquadro, come descritto sopra. Sotto il pulsante trovi l'impronta **SHA-256** del file pubblicato, per chi vuole confrontarla con quella del file scaricato (in PowerShell: `Get-FileHash HikAccessWeb-<versione>-Setup.exe`).

Il riquadro mostra anche quando è stato fatto l'ultimo controllo; **Controlla ora** lo ripete subito. Operatori e account in sola lettura non vedono l'avviso. La prima segnalazione di ogni versione finisce nel [registro attività](#sistema-registro) (categoria **Sistema**, «Nuova versione disponibile»).

> [!NOTE]
> **Riservatezza**: la richiesta va a `api.github.com` e non contiene alcun dato dell'impianto (né nome, né licenza, né versione installata). Per spegnere il controllo automatico disattiva **Avvisa quando esce una nuova versione** nel riquadro e salva le impostazioni: il server non interroga più GitHub e pallino e avviso non compaiono; **Controlla ora** resta disponibile. Se il server non raggiunge Internet il controllo non riesce e il riquadro ne indica il motivo, senza altre conseguenze: il server riprova dopo qualche ora.

### <a id="server-reset-password"></a>Recupero dell'accesso amministratore

Sul server, da un prompt dei comandi **come amministratore** nella cartella di installazione:

`HikAccessWeb.exe --reset-password <utente> <nuova password>`

Reimposta la password e riabilita l'account; se l'utente non esiste lo crea come amministratore. Funziona anche con il servizio in esecuzione: la modifica è attiva entro pochi secondi.

## <a id="sicurezza"></a>Buone pratiche di sicurezza

- **Un account per persona**, con il ruolo minimo necessario; niente account condivisi: il registro attività deve poter dire chi ha fatto cosa.
- **Password robuste** per gli operatori e per i dispositivi; cambia le password predefinite dei terminali.
- Per un **monitor a parete** o la portineria usa un account in sola lettura.
- **Chiavi API**: una per ogni sistema collegato, limitata ai varchi che servono e con una scadenza se è temporanea; eliminala quando l'integrazione non serve più.
- Se la console è raggiungibile da reti non fidate, attiva l'**HTTPS** (istruzioni nel README) o pubblicala tramite una VPN; non esporla direttamente su Internet.
- Tieni i varchi su una **rete separata** o protetta: chiunque raggiunga un terminale con le sue credenziali può comandarlo.
- Fai **backup regolari** dell'esportazione e della cartella dati; proteggi i file esportati, che contengono le password dei dispositivi.
- Rimuovi subito tessere smarrite e persone cessate: la revoca arriva ai varchi in pochi secondi.
- Controlla periodicamente **accessi negati** e **registro attività**: sono il primo segnale di un uso improprio.

### <a id="sicurezza-internet"></a>Raggiungere la console da fuori

La console nasce per la rete aziendale. Se serve usarla da fuori, in ordine di preferenza:

1. **VPN o rete privata** (es. Tailscale, WireGuard, la VPN del router): la console non viene pubblicata su Internet e non serve nulla di più. È la soluzione consigliata.
2. **Reverse proxy con HTTPS** (il router Keenetic con KeenDNS, Caddy, nginx, IIS, Cloudflare Tunnel) davanti alla console: il proxy gestisce certificato e dominio. In **Impostazioni → Accesso remoto** indica l'indirizzo del proxy tra i **proxy attendibili** (proxy o cloudflared sullo stesso server: `127.0.0.1` e `::1`) e verifica con **Questa connessione**; il proxy deve inviare le intestazioni `X-Forwarded-For` e `X-Forwarded-Proto`. Vedi [Accesso remoto e proxy](#sistema-accesso-remoto). Crea l'amministratore prima di pubblicare la console.
3. **HTTPS diretto** con un certificato nel server (vedi README) e porta aperta sul router solo verso quella porta.

In ogni caso: **verifica in due passaggi per tutti gli account** (almeno per gli amministratori), password lunghe, sessione più breve in Impostazioni, e un'occhiata al registro attività. La porta della console non deve essere raggiungibile direttamente da Internet: su un server con indirizzo pubblico non scegliere nel setup la regola del firewall per le reti Pubbliche. I [browser di fiducia](#profilo-2fa-fiducia) tolgono il fastidio del codice sul proprio PC senza rinunciare alla protezione: da un dispositivo nuovo il codice viene sempre chiesto. Le protezioni già attive: blocco dopo 5 tentativi errati per utente, blocco di 15 minuti per un indirizzo che sbaglia 30 volte, nessuna informazione su quali utenti esistono, intestazioni di sicurezza e HSTS quando si è in HTTPS.

## <a id="problemi"></a>Risoluzione dei problemi

<details>
<summary><b>La pagina resta bianca o "Console non disponibile"</b></summary>

Il server non risponde o è stato avviato da una cartella incompleta. Verifica che il servizio "HikAccess Pro Web" sia in esecuzione (Servizi di Windows) e riprova; se il programma è avviato a mano, usa la cartella pubblicata o installata, non quella di compilazione. Il messaggio di avvio nella finestra del server indica l'eventuale cartella mancante.

</details>

<details>
<summary><b>Compare "Browser non supportato"</b></summary>

La console è stata aperta con Internet Explorer, per esempio sul server con Windows Server 2016 o 2019, dove è l'unico browser di serie. Usa Microsoft Edge, Chrome o Firefox: installa Edge sul server oppure apri la console da un altro PC della rete.

</details>

<details>
<summary><b>Dagli altri PC la console non si apre</b></summary>

Controlla indirizzo e porta (`http://nome-server:5080`), che il servizio sia attivo e che la rete del server sia **Privata** o di Dominio: la regola del firewall creata dal setup vale per le reti Pubbliche solo se hai scelto l'opzione (per cambiarla esegui di nuovo il setup). Con un firewall di terze parti apri la porta TCP scelta.

</details>

<details>
<summary><b>All'invio di un utente: «firmware "a persone": utenti e tessere si modificano via HTTP»</b></summary>

Il controller (es. DS-K2602T) è configurato sulla porta 8000 ma tiene l'anagrafica delle persone: nella scheda del varco imposta porta **80** e protocollo **HTTP / ISAPI** per tutte le sue porte, con le stesse credenziali, e ripeti l'invio. Questi controller rispondono con qualche secondo di ritardo: la console mette in fila le scritture verso lo stesso controller e legge il registro eventi una volta sola per controller.

</details>

<details>
<summary><b>Un varco è Offline</b></summary>

Leggi il motivo accanto allo stato e usa **Diagnostica e test connessione**. Timeout: indirizzo, cavo o rete. "Credenziali rifiutate": password errata o dispositivo temporaneamente bloccato (vedi [Credenziali rifiutate](#varchi-credenziali)). Risposta non valida sulla porta 80: il firmware non espone l'ISAPI, prova il canale SDK sulla porta 8000.

</details>

<details>
<summary><b>Il varco resta "In verifica"</b></summary>

Non è ancora stato interrogato: attendi la prossima scansione o usa **Scansiona tutti**. Se la scansione automatica è spenta (riquadro in basso nel menu), riattivala in Impostazioni.

</details>

<details>
<summary><b>Una tessera non apre</b></summary>

Nella scheda della persona controlla: utente abilitato, validità non scaduta, tipo non "bloccato", varco spuntato, numero di tessera corretto (confrontalo con l'evento "accesso negato" nello storico). Poi **Sincronizza su tutti i varchi del sito**. Se il terminale ha l'ora sbagliata, sincronizza l'orologio. Verifica anche che la porta non sia in **blocco permanente**.

</details>

<details>
<summary><b>Una tessera rimossa apre ancora</b></summary>

La revoca avviene al salvataggio della scheda: controlla nel log dell'operazione se il varco era offline in quel momento e, in tal caso, ripeti l'invio o esegui un deploy atomico.

</details>

<details>
<summary><b>Mancano eventi o arrivano in ritardo</b></summary>

Gli eventi arrivano a ogni scansione: riduci l'intervallo o usa **Sincronizza dai varchi**. Se il server è stato spento a lungo, il recupero è limitato a 3.000 eventi per varco. Controlla l'orologio dei dispositivi se gli eventi compaiono con l'ora sbagliata.

</details>

<details>
<summary><b>La sessione scade troppo presto</b></summary>

Aumenta la **chiusura della sessione per inattività** in Impostazioni (amministratori). Per un monitor usa un account in sola lettura con durata lunga e l'opzione "Mantieni l'accesso".

</details>

<details>
<summary><b>Accesso sospeso per 5 minuti</b></summary>

Cinque tentativi errati di seguito. Attendi 5 minuti oppure chiedi a un amministratore di reimpostare la password. "Troppi tentativi da questo indirizzo" indica invece 30 errori in 15 minuti dallo stesso indirizzo IP, di qualunque utente: attendi 15 minuti.

</details>

<details>
<summary><b>L'app di autenticazione non ha più il codice (telefono perso o cambiato)</b></summary>

Usa uno dei codici di recupero salvati all'attivazione (nello stesso campo del codice). Se non li hai, un amministratore può disattivare la verifica dal menu del tuo account in Operatori; l'unico amministratore usa `--reset-password` sul server (vedi [Verifica in due passaggi](#profilo-2fa)).

</details>

<details>
<summary><b>Il codice dell'app viene rifiutato</b></summary>

Controlla che l'ora del telefono sia automatica e corretta (il codice dipende dall'orologio) e inserisci il codice appena generato, non uno già usato.

</details>

<details>
<summary><b>Password dell'unico amministratore dimenticata</b></summary>

Sul server: `HikAccessWeb.exe --reset-password <utente> <nuova password>` (vedi [Recupero dell'accesso](#server-reset-password)).

</details>

<details>
<summary><b>La cattura da varco (o Identifica badge) non legge la tessera</b></summary>

Il varco deve essere online e la tessera va avvicinata al lettore di **quel** varco entro 30 secondi. Se il tempo scade, **Riprova**; in alternativa inserisci il numero a mano (lo trovi nell'evento "accesso negato" dello storico).

</details>

<details>
<summary><b>Dopo "Ricevi da varco" gli utenti non hanno nome</b></summary>

Il dispositivo è un controller "a tessere" che conosce solo i numeri. Usa **Identifica badge**: passi una tessera dopo l'altra sul lettore e per ognuna si apre la scheda in cui scrivere il nome (vedi [Identificare un badge](#utenti-identifica)). In alternativa ricevi da un terminale "a persone" che contiene le stesse tessere: i record verranno uniti.

</details>

<details>
<summary><b>Home Assistant (o un altro sistema) non apre il varco</b></summary>

Guarda il codice della risposta, e nel **registro attività** cerca il nome della chiave («API · …»). **401**: chiave mancante o copiata male (l'intestazione è `Authorization: Bearer hap_…`) oppure chiave eliminata. **403**: chiave disattivata, scaduta o non abilitata per quel varco (vedi [Chiavi API](#sistema-chiavi-api)). **404**: ID del varco sbagliato. **405**: richiesta GET invece di POST. **502**: il varco non ha eseguito il comando (spento o non raggiungibile, come nella console). **429**: troppe chiavi errate dallo stesso indirizzo, riprova dopo 5 minuti. Un **403** con «servizio REST non compreso» o «varco sospeso» dipende dalla [licenza](#sistema-licenza). Se non arriva nessuna risposta, controlla l'indirizzo della console e il firewall.

</details>

<details>
<summary><b>«La versione gratuita comprende…»: non posso aggiungere un varco, un sito o una chiave API</b></summary>

Hai raggiunto i limiti della versione gratuita (1 sito, 2 varchi, niente servizio REST) o della licenza. Richiedi una licenza dalla pagina [Licenza](#sistema-licenza): il collegamento **Vai alla pagina Licenza** nell'avviso porta lì.

</details>

<details>
<summary><b>Un varco è «Sospeso»</b></summary>

Supera i varchi consentiti dalla licenza, per esempio dopo la scadenza o il ripristino di un backup più grande. Attiva una licenza adatta, oppure elimina i varchi in più: i varchi sospesi tornano in uso subito, senza riconfigurarli.

</details>

<details>
<summary><b>La chiave di attivazione non viene accettata</b></summary>

Il messaggio indica il motivo. **Incompleta o non valida**: copiala per intero, da `HAP1-` all'ultimo gruppo (puoi incollare tutta l'email). **Per un altro computer**: la chiave è stata emessa per un altro codice macchina; succede se l'hai richiesta da un altro server o se Windows è stato reinstallato: invia una nuova richiesta da questo server. **Scaduta**: chiedi una chiave nuova.

</details>

<details>
<summary><b>La porta 5080 è occupata da un altro programma</b></summary>

Il setup lo segnala alla fine dell'installazione ("la console non risponde"). Esegui di nuovo il setup e scegli un'altra porta (oppure, per il pacchetto portabile, modifica `Urls` in `appsettings.json`); il setup aggiorna collegamenti e regola del firewall.

</details>

<details>
<summary><b>Il controllo delle nuove versioni non riesce</b></summary>

In **Impostazioni → Aggiornamento del programma** il riquadro giallo indica il motivo. "Il server non raggiunge GitHub" o "non ha risposto": il server non esce su Internet, oppure un firewall o un proxy blocca `api.github.com` (HTTPS, porta 443); il servizio gira con l'account di sistema, che usa il proxy di sistema di Windows e non quello del tuo utente. "Troppe richieste": dalla stessa connessione a Internet sono partite molte richieste a GitHub, riprova dopo un'ora. Se il server deve restare senza Internet, disattiva l'avviso e controlla ogni tanto la [pagina delle versioni](https://github.com/brn78/HikAccess-Pro-Web/releases) da un altro PC.

</details>

<details>
<summary><b>L'aggiornamento dalla console non va a buon fine</b></summary>

In **Impostazioni → Aggiornamento del programma** leggi l'esito e il percorso del log del setup (cartella dati, sottocartella `updates`). "Solo dalla rete locale": apri la console con l'indirizzo interno del server, non con quello pubblico; il pulsante **Apri la console locale** del riquadro lo fa per te, se il tuo PC è nella rete locale o nella VPN. Se il servizio non riparte, avvialo da Servizi di Windows oppure esegui il setup direttamente sul server.

</details>

<details>
<summary><b>Dopo un riavvio del server la console non risponde</b></summary>

Il servizio ha l'**avvio ritardato**: parte circa due minuti dopo l'avvio di Windows, qualcosa di più dopo l'installazione degli aggiornamenti. Sul server lo mostra l'[icona di stato](#server-icona-stato) (gialla finché parte). Se dopo 5 minuti la console non risponde ancora, dal menu dell'icona scegli **Avvia il servizio**, oppure apri **Servizi** di Windows e avvia "HikAccess Pro Web". Fino alla versione 1.1.1, su un server lento, il servizio poteva restare fermo dopo i riavvii per gli aggiornamenti (registro di Sistema, eventi **7009** e **7000**: "Timeout durante l'attesa della connessione del servizio"): aggiorna il programma.

</details>

<details>
<summary><b>Il servizio non parte</b></summary>

Apri il Visualizzatore eventi di Windows, registro Applicazione, origine **HikAccessWeb** (o **.NET Runtime** per un errore durante il caricamento): il messaggio indica la causa (porta occupata, cartella dati non scrivibile, file mancante). Dopo un errore Windows riavvia il servizio da solo dopo 5, 30 e 60 secondi (registro di Sistema, origine Service Control Manager). Il setup verifica la console subito dopo aver avviato il servizio e avvisa se non risponde.

</details>

## <a id="glossario"></a>Glossario

- **ISAPI**: Il protocollo HTTP dei dispositivi Hikvision, usato dalla console sulla porta 80 (canale "HTTP / ISAPI").
- **SDK Hikvision (HCNetSDK)**: La libreria di comunicazione nativa Hikvision, usata per i controller che rispondono solo sulla porta di servizio 8000.
- **Firmware "a persone" / "a tessere"**: I terminali "a persone" memorizzano nome, tessere, PIN e validità di ogni utente; i controller "a tessere" conoscono solo i numeri di tessera e i loro diritti.
- **Matricola (employee number)**: Identificativo univoco della persona sui dispositivi e nella console.
- **Numero tessera**: Il codice letto dal lettore, come lo riporta il dispositivo negli eventi.
- **Tempo relè**: Durata dello sblocco della serratura dopo un accesso o un comando di apertura.
- **Sblocco / blocco permanente**: Stati della porta imposti da comando: sempre aperta o sempre chiusa finché non si ripristina.
- **Sincronizzazione**: Invio di una persona (o di un gruppo di persone) ai varchi, con concessione o revoca dei diritti.
- **Deploy atomico**: Sincronizzazione completa di tutti gli utenti su tutti i varchi di tutti i siti.
- **Scansione**: Interrogazione periodica dei varchi da parte del server: stato online/offline e nuovi eventi.
- **Recupero eventi**: Lettura degli eventi persi durante un fermo del server, a partire dall'ultimo archiviato.
- **Registro attività**: Elenco delle operazioni degli operatori sulla console, con esito.
- **Cartella dati**: La cartella del server con configurazione, database degli eventi, account e chiavi di sessione.
- **CSV**: File di testo tabellare apribile con Excel, usato per le esportazioni.
- **Codice macchina**: Codice di 16 caratteri che identifica il server (installazione di Windows e scheda madre): la chiave di attivazione vale solo per quel codice.
- **Chiave di attivazione**: Il testo che inizia con `HAP1-`, ricevuto via email, che attiva la licenza su un server.
- **Varco sospeso**: Varco oltre i limiti della licenza: resta configurato ma non viene monitorato né comandato.

---

*HikAccess Pro Web · Guida utente · © 2026 Bruno Leonardi · Tutti i diritti riservati. Le informazioni tecniche di installazione e configurazione sono nel file README distribuito con il programma.*

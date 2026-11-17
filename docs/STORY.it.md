[English](STORY.md) | Italiano

# Storia del progetto

## 1. Contesto e problema iniziale

Il progetto nasce dall'idea di riutilizzare un Nintendo DSi XL originale come macro controller fisico e dashboard a due schermi per Windows 11. Gli obiettivi erano shortcut configurabili, appuntamenti e attività. Inizialmente era prevista anche una seconda fase hardware con ESP32. Il percorso è stato suddiviso in piccoli test eseguibili, senza definire subito l'intero prodotto.

## 2. Evoluzione per fasi

**Fase 1 — Avvio homebrew.** La console è stata identificata come DSi XL europeo con firmware 1.4.5E. Il metodo tramite scheda SD interna si è fermato quando la console l'ha segnalata come inutilizzabile. Una R4 SDHC Dual Core Smart Update 2014 già funzionante ha consentito di eseguire file `.nds` senza cambiare il firmware della console. Linux Mint è stato usato per accedere alla microSD. All'inizio risultava in sola lettura (`RO=1`) e il lettore segnalava protezione da scrittura. Dopo i controlli della levetta dell'adattatore, la scheda è risultata scrivibile (`RO=0`).

**Fase 2 — Compilazione ed esecuzione.** L'installazione di devkitPro è stata ostacolata da risposte HTTP 403; il download è riuscito con uno user agent simile a quello di un browser. Sono stati installati `nds-dev` e verificato devkitARM GCC. `hello_world.nds` è stato compilato ed eseguito dalla R4, definendo un ciclo di sviluppo ripetibile.

**Fase 3 — Verifica degli input.** È stato compilato `ds_input_tester.nds`, capace di rilevare tasti, contare le pressioni di A, leggere le coordinate touch e controllare un'area virtuale. Il funzionamento è stato confermato sulla console, prima di aggiungere un'interfaccia più complessa.

**Fase 4 — Interfaccia grafica.** È stata creata `ds_control_hub.nds`, applicazione offline sui due schermi con stile neobrutalist: colori pieni, contorni marcati, ombre squadrate e grandi aree touch. Il funzionamento sul DSi XL è stato confermato. Le scorciatoie erano azioni locali dell'interfaccia, non comandi Windows.

**Fase 5 — Vincoli di rete.** Il PC Windows 11 era connesso via Ethernet all'extender Mercusys ME50G; il pannello è stato individuato all'indirizzo `192.168.1.247`. Nell'app erano visibili soltanto impostazioni wireless cifrate. La compatibilità WPA2 degli homebrew in modalità DS rappresentava un ostacolo: si è scelto di non indebolire la rete domestica. L'ipotesi di ponte ESP32 è stata accantonata quando è stato deciso di non acquistare il kit.

**Fase 6 — Esperimenti PictoChat.** La comunicazione locale è stata esplorata per evitare il collegamento IP tramite router. Su Linux Mint la RTL8821CE (`rtw_8821ce`) è stata portata in modalità monitor e sul canale 1. `tcpdump` ha acquisito traffico 802.11, poi analizzato anche in file PCAP. Nessun frame è stato attribuito con certezza a PictoChat. PictoChat Interceptor e l'interfaccia di invio sono stati avviati, ma servivano un MAC di un client già collegato e una sessione esistente; era disponibile un solo DS. Nessun messaggio PC–console è stato confermato.

## 3. Scelte e compromessi

La R4 ha consentito un punto di partenza ripetibile senza cambiare firmware, ma in genere esegue software in modalità DS. L'interfaccia offline è stata verificata prima del trasporto di rete. Non era dimostrata una rete legacy isolata e sicura sull'extender. PictoChat evitava in teoria la rete IP, ma introduceva complessità su frame proprietari, compatibilità radio e associazione. Ogni cambiamento di architettura è nato dall'ostacolo precedente.

## 4. Limiti e stato attuale

Il risultato verificato è un'interfaccia DS offline funzionante con input hardware testati. Non sono verificati collegamento Nintendo–Windows, macro remote o sincronizzazione di dati live. [DA VERIFICARE: snapshot finale dei sorgenti, licenza e date esatte di completamento.]

## 5. Prossimi passi

Verificare l'avvio in modalità DSi con stack WPA2 adatto oppure un altro trasporto sicuro. Dimostrare la ricezione di un evento pulsante su Windows prima di aggiungere mappatura macro o integrazione calendario/to-do.

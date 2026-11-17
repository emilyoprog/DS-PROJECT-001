[English](README.md) | Italiano
# DS Control Hub
Interfaccia homebrew offline per Nintendo DSi XL, sviluppata come primo passo verso un macro controller e una dashboard per Windows 11.
## Stato attuale
- **Verificati sulla console:** esecuzione di `hello_world.nds`, `ds_input_tester.nds` e `ds_control_hub.nds` con grafica neobrutalist.
- **Input testati:** pulsanti fisici e touchscreen, incluse coordinate e aree touch.
- **Non implementati:** collegamento a Windows, macro remote e dati live di calendario/to-do.
- **Esplorata ma non verificata:** comunicazione PC–DS via PictoChat.
## Hardware e strumenti
- Nintendo DSi XL (UTL-001 EUR), firmware 1.4.5E, console originale.
- R4 SDHC Dual Core Smart Update 2014 (`r4isdhc.com.cn`) con microSD.
- Linux Mint, devkitPro / devkitARM, libnds, Make.
- PC di destinazione: Windows 11, Ethernet tramite extender Mercusys ME50G.
## Percorso di sviluppo
1. `Hello World` ha verificato l'avvio dei file `.nds` compilati tramite R4.
2. Un tester ha verificato pulsanti e touchscreen.
3. Creata e testata un'interfaccia offline neobrutalist sui due schermi.
4. I vincoli WPA2 della modalità DS hanno bloccato la prima ipotesi di rete.
5. Esplorati PictoChat e la modalità monitor Linux; nessun collegamento PC–DS dimostrato.
Ogni cambio di approccio è nato da un vincolo o test concreto, non da una sostituzione di architettura pianificata a priori.
## Documentazione
- [Storia](docs/STORY.it.md) · [Decisioni](docs/DECISIONS.it.md) · [Changelog](CHANGELOG.md)
- [History in English](docs/STORY.md) · [Decisions in English](docs/DECISIONS.md)
## Sorgenti e compilazione
[DA VERIFICARE: sorgenti, Makefile e istruzioni di compilazione non sono ancora stati aggiunti al repository.]
## Prossimi passi
Verificare una soluzione homebrew DSi/WPA2 o un altro trasporto sicuro DS–PC; testare un singolo evento su Windows prima di introdurre dati live nella dashboard.
[DA VERIFICARE: licenza del repository e date storiche.]

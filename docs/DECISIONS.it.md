[English](DECISIONS.md) | Italiano

# Decisioni tecniche

## D1 — Usare la R4 funzionante anziché l'accesso via SD interna
**Problema:** il DSi segnalava la scheda SD come inutilizzabile.
**Decisione:** compilare homebrew `.nds` e avviarli tramite R4, senza modificare il firmware della console.
**Compromesso:** trasferimento pratico, ma esecuzione generalmente in modalità DS.

## D2 — Verificare gli input prima dell'interfaccia completa
**Problema:** Hello World non dimostrava la lettura di pulsanti e touchscreen da codice proprio.
**Decisione:** realizzare e provare `ds_input_tester.nds` prima del controller grafico.
**Risultato:** tasti, coordinate touch e area virtuale funzionanti.

## D3 — Mantenere offline il primo controller
**Problema:** non esisteva ancora un canale di comunicazione DS–Windows.
**Decisione:** realizzare e verificare l'interfaccia neobrutalist sui due schermi indipendentemente dalla rete.
**Compromesso:** interfaccia funzionante, ma shortcut non eseguite su Windows.

## D4 — Non indebolire la sicurezza Wi-Fi domestica
**Problema:** i limiti radio della modalità DS erano incompatibili con la rete cifrata del Mercusys ME50G.
**Decisione:** non ridurre la protezione della rete per supportare la connettività legacy.
**Compromesso:** integrazione di rete rimandata a una soluzione alternativa.

## D5 — Accantonare il ponte ESP32
**Problema:** l'acquisto previsto dello starter kit ESP32 è stato annullato.
**Decisione:** esplorare collegamenti solo software, usando i dispositivi già disponibili.
**Compromesso:** nessun intermediario radio esterno; maggiore dipendenza dalle capacità DS/DSi.

## D6 — Non considerare PictoChat un trasporto verificato
**Problema:** nelle catture monitor non è stato identificato traffico Nintendo e il sender richiedeva una sessione tra console già stabilita.
**Decisione:** mantenere PictoChat come esperimento, non come architettura di comunicazione confermata.
**Seguito:** valutare modalità DSi/WPA2 o un altro trasporto verificabile.

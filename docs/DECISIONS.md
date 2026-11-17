English | [Italiano](DECISIONS.it.md)

# Technical decisions

## D1 — Use the working R4 instead of the built-in SD entry point
**Trigger:** the DSi reported the SD card as unusable.
**Decision:** build `.nds` homebrew and run it using the existing R4 without changing console firmware.
**Trade-off:** accessible deployment, but typically DS-mode execution.

## D2 — Verify inputs before designing the full interface
**Trigger:** a successful Hello World did not prove buttons or touch input worked in custom code.
**Decision:** build and test `ds_input_tester.nds` before the graphical controller.
**Result:** physical buttons, touch coordinates, and a virtual touch region worked.

## D3 — Keep the first controller offline
**Trigger:** there was no established DS-to-Windows communication channel.
**Decision:** implement and validate the neobrutalist two-screen UI independently of networking.
**Trade-off:** a working interface, but shortcuts did not execute on Windows.

## D4 — Avoid changing home Wi-Fi security
**Trigger:** DS-mode wireless limitations conflicted with the encrypted Mercusys ME50G network.
**Decision:** do not weaken the household network to accommodate legacy connectivity.
**Trade-off:** network integration remained blocked pending an alternative.

## D5 — Drop the ESP32 bridge
**Trigger:** the planned ESP32 starter-kit purchase was cancelled.
**Decision:** explore software-only communication paths using existing devices.
**Trade-off:** no external wireless intermediary; greater reliance on DS/DSi radio capabilities.

## D6 — Stop treating PictoChat interception as a proven transport
**Trigger:** monitor-mode captures did not identify Nintendo traffic, and the sender expected an established multi-console session.
**Decision:** retain PictoChat as an experiment, not the communication architecture.
**Next:** investigate DSi-mode WPA2 or another verifiable transport.

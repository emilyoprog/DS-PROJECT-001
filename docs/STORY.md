English | [Italiano](STORY.it.md)

# Project history

## 1. Initial problem

The project began as an attempt to reuse an original Nintendo DSi XL as a physical macro controller and two-screen dashboard for Windows 11. The intended functions were configurable shortcuts, calendar entries, and to-do information. A second, hardware-oriented stage involving an ESP32 was initially considered. The work was structured around small executable tests rather than a complete product design.

## 2. Evolution by phase

**Phase 1 — Establishing a homebrew entry point.** The console was identified as a European DSi XL running firmware 1.4.5E. The built-in SD route was blocked when the console reported the SD card as unusable; a compatible, already-working R4 SDHC Dual Core Smart Update 2014 offered a way to launch `.nds` applications without changing the console firmware. Linux Mint was used to access its microSD. The card initially appeared read-only (`RO=1`), with the reader reporting write protection. After checks involving the adapter lock, it appeared writable (`RO=0`), allowing file transfer.

**Phase 2 — Compiling and running code.** devkitPro installation initially encountered HTTP 403 responses; a download using a browser-style user agent succeeded. The `nds-dev` toolchain was installed and devkitARM GCC was verified. `hello_world.nds` compiled and ran on the R4, establishing a working build-and-deploy loop.

**Phase 3 — Testing input.** A separate `ds_input_tester.nds` was compiled to detect keys, count A presses, read touchscreen coordinates and test a virtual touch region. Its behavior was confirmed on the console. This test preceded more complex UI work so input behavior could be checked independently.

**Phase 4 — Building the interface.** A two-screen offline application, `ds_control_hub.nds`, was developed with a neobrutalist visual direction: solid colors, thick outlines, block shadows, and large touch targets. It was reported working on the DSi XL. Its on-screen shortcuts were local UI actions, not Windows commands.

**Phase 5 — Network constraints.** The Windows 11 PC was connected by Ethernet through a Mercusys ME50G extender, whose management interface was found at `192.168.1.247`. The extender exposed only encrypted wireless settings in the app. Conventional DS-mode homebrew Wi-Fi raised a compatibility problem with WPA2, so weakening the home network was avoided. The previously considered ESP32 bridge was dropped after the decision not to purchase the kit.

**Phase 6 — PictoChat experiments.** Local wireless communication offered an alternative to router-based Wi-Fi. On Linux Mint, the RTL8821CE (`rtw_8821ce`) was placed in monitor mode and tuned to channel 1. `tcpdump` captured 802.11 traffic, and PCAP files were inspected. No captured frame was conclusively attributed to PictoChat. PictoChat Interceptor and its sender GUI were launched, but the sender required an already-joined client MAC and an existing session; only one DS was available. No message was confirmed delivered from the PC to the console.

## 3. Technical trade-offs

The R4 provided a repeatable starting point without changing firmware, but typically runs DS-mode software. An offline UI could therefore be tested before the transport layer existed. The extender could not be assumed to expose a safe, isolated legacy Wi-Fi network. PictoChat avoided normal IP connectivity in principle, but shifted the difficulty to proprietary framing, radio compatibility, and session establishment. Each architectural shift responded to the preceding obstacle.

## 4. Current limits

The verified result is a working offline DS interface with tested hardware input. There is no verified Nintendo-to-Windows link, no remote macro execution, and no live dashboard synchronization. [TO VERIFY: final source snapshot, repository license, and exact completion dates.]

## 5. Next steps

Investigate whether this homebrew can run in DSi mode with a suitable WPA2-capable stack, or identify another safe transport. Demonstrate receipt of one button event on Windows before adding macro mapping or calendar/to-do integration.

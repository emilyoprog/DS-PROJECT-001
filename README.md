English | [Italiano](README.it.md)
# DS Control Hub
An offline homebrew interface for a Nintendo DSi XL, developed as a step toward a Windows 11 macro controller and information dashboard.
## Current status
- **Confirmed on hardware:** `hello_world.nds`, `ds_input_tester.nds`, and the neobrutalist `ds_control_hub.nds` ran on the console.
- **Inputs tested:** physical buttons and touchscreen, including coordinates and touch regions.
- **Not implemented:** connectivity to Windows, remote macros, and live calendar/to-do data.
- **Investigated but not verified:** PictoChat-based PC communication.
## Hardware and tools
- Nintendo DSi XL (UTL-001 EUR), firmware 1.4.5E; unmodified console.
- R4 SDHC Dual Core Smart Update 2014 (`r4isdhc.com.cn`) with microSD.
- Linux Mint, devkitPro / devkitARM, libnds, Make.
- Target computer: Windows 11, connected by Ethernet through a Mercusys ME50G extender.
## Development path
1. A microSD write-protection issue was resolved before copying homebrew.
2. `Hello World` confirmed the R4 could launch compiled `.nds` files.
3. An input tester confirmed buttons and touchscreen operation.
4. An offline two-screen neobrutalist UI was built and tested.
5. WPA2 constraints in DS mode blocked the initial network plan.
6. PictoChat and Linux monitor-mode experiments were explored; PC-to-DS communication was not established.
Each change in approach followed a specific constraint or failed test rather than a pre-planned architecture switch.
## Documentation
- [Project history](docs/STORY.md) · [Decisions](docs/DECISIONS.md) · [Changelog](CHANGELOG.md)
- [Storia in italiano](docs/STORY.it.md) · [Decisioni in italiano](docs/DECISIONS.it.md)
## Source and build
[TO VERIFY: source files, Makefile and build instructions have not yet been added to this repository.]
## Next steps
Verify a feasible DSi-mode/WPA2 homebrew path or another secure DS-to-PC transport, then test a single event on Windows before implementing live dashboard data.
[TO VERIFY: repository license and historical dates.]

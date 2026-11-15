# Builds — second office, four office workstations

All prices in KZT, taken 2026-11-14 (see `budget.csv`; row numbers count the header as row 1). These are office machines: no discrete graphics cards, no gaming parts. Every machine uses the CPU's integrated graphics.

## What the four machines share, and why

Same platform on all four: Ryzen 5 7600X, MSI PRO B650M-P (AM5, mATX), Netac NV3000 1 TB, MSI MAG A550BN 550 W, Deepcool WAVE V2 case, ID-Cooling SE-214-XT, Windows 11 Pro OEM. **Shared base: 338,289 KZT per machine.**

The director's instinct ("buy the same four") is right about the platform and wrong about the configuration. One platform means one spare-parts set and one disk image for whoever supports them. The loads differ, so memory and monitors differ.

* The Ryzen 5 7500F used in the pre-built offers has **no integrated graphics** and would force a graphics card into every machine. The 7600X has an iGPU, so no machine needs a card.
* Memory is the expensive part right now: a 32 GB DDR5 kit (217,300) costs about 2.6x the CPU (83,251). Only the roles that hit the memory limit get 32 GB.

## Build 1 — accountant

**Load:** spreadsheets and accounting software (assumed 1C or similar), browser with banking and tax portals, PDF scanning. One or two large files open at a time.

**Bottleneck:** single-thread CPU speed and SSD latency when a big database or workbook opens. Memory is not the limit: 16 GB covers it.

**Trade-off:** 16 GB (2x8 GB, dual channel) instead of 32 GB, saving 95,320 KZT. Two 8 GB sticks rather than one 16 GB stick keep dual channel, which matters because the iGPU shares system memory. Upgrading later means replacing the sticks or filling the two free slots.

**Total:** 669,340 KZT (budget.csv, rows 2-10)

## Build 2 — sales manager

**Load:** CRM in a browser, 30-40 tabs, Excel, about four hours of video calls a day, often at once.

**Bottleneck:** memory, not CPU. A browser with forty tabs plus a video call sits around 11-12 GB; add Excel and a messenger and 16 GB is gone mid-call.

**Trade-off:** 32 GB of DDR5-5200, the cheapest 2x16 kit found, instead of a faster kit. The CPU idles in this role; the memory does not.

**Total:** 756,600 KZT (budget.csv, rows 11-19)

## Build 3 — web developer

**Load:** IDE, Docker or WSL2 with a local database, several browsers, terminal, chat client.

**Bottleneck:** memory, then disk during builds. WSL2 claims up to half the RAM by default.

**Trade-off:** 32 GB, not 64 GB (a 64 GB kit costs about 500,000 KZT today), and one monitor instead of two. The board has four DIMM slots, so memory is the planned first upgrade.

**Total:** 748,400 KZT (budget.csv, rows 20-28)

## Build 4 — designer

**Load:** Photoshop, Illustrator, Figma; layered files of hundreds of MB, several applications open.

**Bottleneck:** memory for big documents and disk space for files and scratch.

**Trade-off:** no graphics card and no wide-gamut or calibrated screen. The iGPU is enough for office-level design work but will be slow on heavy filters and very large files. I paid only for a 99% sRGB monitor (116,074) because colour accuracy is the one thing this role cannot do without. Colours are good for screen and web, not guaranteed for print.

**Total:** 700,134 KZT (budget.csv, rows 29-37)

## Budget summary

|Machine|KZT|
|-|-:|
|Accountant|669,340|
|Sales manager|756,600|
|Web developer|748,400|
|Designer|700,134|
|**Total**|**2,874,474**|
|Budget|3,000,000|
|**Reserve**|**125,526 (4,1842%)**|




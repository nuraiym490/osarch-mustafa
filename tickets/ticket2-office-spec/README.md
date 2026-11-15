# Ticket 2 — "We are kitting out the new office"

## 1\. What was asked

> From: Daniyar K. (Director)
> Subject: computers for the new office
>
> We are opening the second office and need four computers — accountant,
> sales, web developer, designer. Budget 3,000,000 tenge for everything.
> Everyone says we should just buy the same four machines, is that right?
> Make sure they last a few years. Monitors included.

## 2\. What was actually needed

**Where the request is wrong.** "Buy the same four machines" is not right. The four roles hit four different limits: the accountant is limited by single-thread speed and disk, the sales manager and web developer by memory, the designer by memory and disk space. Identical machines are either too weak for two of them or wasteful for the other two. The part of the idea worth keeping is a **common platform** (same motherboard, case, PSU, SSD, OS), which gives the company one spare-parts set and one disk image. The four builds keep that and differ only in memory and monitors (`builds.md`).

**What the request left out, and what I assumed instead.** I could not ask the director, so these are assumptions he should confirm:

|Question I would have asked|What I assumed|
|-|-|
|Does "everything" include delivery, VAT, keyboards, mice, UPS?|Parts and monitors only. Peripherals and delivery are not priced; the 479,633 KZT reserve is meant to absorb them.|
|Who assembles and supports the machines?|Whoever buys them builds them. If nobody can, see answer 2 below.|
|How long is "a few years"?|Four years of use. This is why I chose the AM5 platform, which allows a CPU upgrade later.|
|What software does the accountant run?|1C or similar plus Excel. If it is a network 1C, the server matters more than this PC.|
|What does the developer run?|IDE, Docker or WSL2, a local database, several browsers.|
|What does the designer produce, and is it printed?|Screen and web work with large layered files. Not colour-critical print.|
|Windows licences: what kind?|Windows 11 Pro OEM, one per machine, tied to that machine. A licence costs 81,461 KZT, so four cost 325,844 KZT, more than the CPU line.|
|Where is the office?|Almaty. Prices come from Kazakhstani shops that list delivery from Almaty or Astana.|

**Two things the requirements hid.**

1. The Ryzen 5 7500F, a popular budget CPU and the one used in the pre-built offers I found, has **no integrated graphics**. Taking it would mean a graphics card in all four machines. I used the Ryzen 5 7600X instead, which has an iGPU, so no machine needs a graphics card. These are office machines, not gaming or workstation-class ones.
2. Memory is the most expensive component in this market right now. A 32 GB DDR5 kit (217,300) costs about 2.6x the CPU. The usual advice "put 32 GB everywhere" would add 95,320 KZT for the accountant alone. I kept the accountant at 16 GB, which the requirement allows, and spent memory money only where the load needs it.

## 3\. What I did

1. Wrote down, for each role, the load, the component that limits it, and what the minimum spec had to be: at least 16 GB RAM and a 1 TB SSD each, a licensed OS and a monitor.
2. Chose one platform (Ryzen 5 7600X, B650M, 550 W PSU, mATX case) so that all four machines share spares and an image, and checked compatibility (`evidence/pcpartpicker-links.md`).
3. Priced every part from Kazakhstani shops (e-katalog.kz aggregate listings and ALFA.kz, vendors named in `budget.csv`), recording the date for every row.
4. Raised memory only for the roles that are memory-bound; all four use the CPU's integrated graphics.
5. Summed per role and checked the total against 3,000,000 KZT: 2,520,367 KZT, reserve 479,633 KZT.
6. Priced the same four as pre-built machines (answer 2) and compared.

Decisions and alternatives are in `builds.md`. The main alternatives I rejected: four identical machines (wasteful or too weak); the 7500F (needs a GPU in every machine); 64 GB for the developer (about 500,000 KZT for the kit, over budget); an older DDR4 platform (cheaper RAM, but a dead-end socket against "last a few years").

### The three questions

**1. Which machine do I upgrade first, eighteen months from now, and why?**
The web developer's memory: 32 GB to 64 GB. Containers, an IDE and browsers are what fill memory first, and it is the upgrade with the biggest effect for the least money. I chose a board with four DIMM slots so this is an addition, not a replacement. Caveat: four DDR5 modules may force a lower memory speed, so the alternative is replacing the kit with 2x32 GB. Either way, the price should be re-checked then, because I am buying at a high point for memory prices.

**2. Price the same four as pre-built machines. What does the company gain and lose?**
Pre-built offers found on ALFA.kz on 2026-11-14 (Ryzen 5 7500F, DDR5, SSD, discrete GPU; none include a monitor, and I assumed none include Windows):

|Role|Pre-built offer|Price|+ monitor|+ Windows|Total|
|-|-|-:|-:|-:|-:|
|Accountant|7500F / 16 GB / 1 TB / RTX 5050 ([link](https://alfa.kz/pc/computers/amd/ryzen_5/all/8556473))|594,490|92,419|81,461|768,370|
|Sales|ANTS Extreme: 7500F / 32 GB / 1 TB / RTX 5060 ([link](https://alfa.kz/pc/computers/amd/ryzen_5/ants/8561722))|770,590|92,419|81,461|944,470|
|Web developer|same as sales|770,590|92,419|81,461|944,470|
|Designer|same as sales|770,590|116,074|81,461|968,125|
|**Total**|||||**3,625,435**|

That is 988,447 KZT (about 39%) more than the self-built 2,520,367 and **508,814 KZT over the budget**. Most of the gap is a discrete GPU that none of the four roles needs.

*Gains from buying pre-built:* no assembly and testing time (roughly a day of work for four machines); one seller to call for a warranty claim instead of seven parts from several shops; the option of instalments or a company invoice from one vendor.
*Losses:* it does not fit the budget; the company pays for GPUs it will not use; it cannot choose the PSU, board or cooler, so the "last a few years" claim rests on what the seller picked; and the listings do not show the exact memory configuration, so I cannot confirm dual channel. If nobody at the company can assemble PCs, the extra cost is the price of that, and it should be offered to the director as a choice.

**3. One of these four people will complain about performance within a month. Who, and about what?**
The designer, about large files: Photoshop or Illustrator slowing down on multi-gigabyte layered documents and heavy filters (integrated graphics only), and the disk filling up. A 1 TB SSD holds the OS, applications, Creative Cloud cache, scratch space and project files, and 32 GB of RAM is the minimum for this work, not the comfortable amount. The second complaint will be that the screen does not match a printed proof, because the 99% sRGB monitor is uncalibrated.

## 4\. Evidence

* `budget.csv` — every component, price in KZT, source and date; the totals in `builds.md` and above are computed from it.
* `builds.md` — the four builds with load, bottleneck, trade-off and total.
* `evidence/pcpartpicker-links.md` — compatibility checks of the shared platform.
* `evidence/vendor-quotes/` — one screenshot per price in `budget.csv`, with the date visible. This is what makes the prices checkable.

## 5\. What I would do differently

I took prices from shop-aggregator listings, where the lowest "from" price may belong to an item that is out of stock or sold by a vendor with different delivery terms. Next time I would ask two vendors for a formal quote for the whole configuration, with delivery to the office and VAT stated, and compare those, instead of adding up listing prices part by part. I would also confirm the memory price with the vendor, since it is the number that moves most and changes the answer to question 2.


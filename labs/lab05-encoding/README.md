# Lab 5 — Encoding forensics
Pair:   Driver first half: 
Machine:DESKTOP-TMR0L2E, Ubuntu Server guest (VMware Workstation)
Date: 12.11.26

## What I did

### 1. Diagnosis (before changing anything)

```bash
file staff-broken.csv
file -i staff-broken.csv
xxd -l 16 staff-broken.csv
grep -c $'\r' staff-broken.csv
iconv -f CP1251 -t UTF-8 staff-broken.csv | head -5
```

- `file` reported: <вставь, что написал file>
- The first 16 bytes were: `<вставь hex из hexdump-before.txt>`. They do not start with `EF BB BF`, `FF FE` or `FE FF`, so there is no BOM.
- `grep -c $'\r'` returned <число>, so the line ending is <CRLF / LF>.
- The terminal showed � symbols when I ran `cat`, which means the file is not UTF-8.
- `iconv -f CP1251 -t UTF-8` printed readable Russian names, so the source encoding is Windows-1251.

### 2. Conversion

```bash
bash scripts/fix.sh
```

`fix.sh` does three things:
1. writes a UTF-8 BOM (`EF BB BF`) at the start of the file,
2. converts CP1251 to UTF-8 with `iconv`,
3. removes the carriage returns (`sed 's/\r$//'`), so CRLF becomes LF.

### 3. Verification

```bash
file staff-fixed.csv
xxd -l 16 staff-fixed.csv
head -5 staff-fixed.csv
```

I opened `staff-fixed.csv` in Excel (double click, no import wizard), in LibreOffice, and with `cat` in the Linux terminal.

## Result

| Property | Before | After |
|---|---|---|
| Encoding | Windows-1251 (CP1251) | UTF-8 |
| Line ending | <CRLF / LF> | LF |
| BOM | none | present (`EF BB BF`) |

I kept the BOM on purpose. Excel decides that a CSV is UTF-8 only if it finds a BOM. Without it, Excel reads the file as Windows-1251 and shows text like `РЎР°`. The BOM is invisible in the Linux terminal, so `cat` still works.

### Kazakh letters

Windows-1251 has no Kazakh-specific letters (Ә, Ғ, Қ, Ң, Ө, Ұ, Ү, Һ, І). In the source file they are stored as look-alike Cyrillic characters from the CP1251 table: Қ as Ќ, Ұ as Ў, Ғ as Ѓ, Ә as Ј. For example, "Нұрланов" appears as "Нўрланов" and "Қасымова" as "Ќасымова".

The conversion cannot restore these letters by itself. `iconv` only maps each CP1251 byte to the Unicode character that CP1251 assigns to it, and for these bytes that is Ќ, Ў, Ѓ, Ј. The information about which letter was originally meant was lost when the file was first written in CP1251. Getting the original letters back would need a manual replacement table, and that would be a guess, not a conversion.
## What did not work the first time

My first version of `fix.sh` only ran `iconv -f CP1251 -t UTF-8`. It did not add a BOM and did not remove CR. Excel opened the result as Windows-1251 and showed text like `РЎР°`, even though the file was valid UTF-8. I added `printf '\xEF\xBB\xBF'` and `sed 's/\r$//'`, ran the script again, and Excel then read the Russian text correctly.



## Evidence

--evidence/staff-broken.csv — original file from Canvas
- evidence/staff-fixed.csv — converted file
- evidence/file-before.txt — file and grep output on the original, shows the encoding and the line ending
- evidence/hexdump-before.txt — first 16 bytes of the original, shows there is no BOM
- evidence/file-after.txt — file and xxd on the fixed file, shows UTF-8 with BOM and LF
- evidence/opens-correctly.png — Excel, LibreOffice and cat showing the names correctly
- scripts/fix.sh — the conversion script

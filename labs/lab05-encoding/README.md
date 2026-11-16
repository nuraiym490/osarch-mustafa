# Lab 5 — Encoding forensics
Pair:   Driver first half: 
Machine:DESKTOP-TMR0L2E
Date: 13.11.26

## What I did

### 1. Diagnosis (before changing anything)
what was file saying before: staff-broken.csv: Non-ISO extended-ASCII text, with CRLF line terminators
and
00000000: d2e0 e12e b93b d4c8 ce3b c4ee ebe6 edee  .....;...;......
so it showes that there is no BOM 

### 2. Conversion
`fix.sh` does three things:
1. writes a UTF-8 BOM (`EF BB BF`) at the start of the file,
2. converts RK1048 to UTF-8 with `iconv`,
3. removes the carriage returns (`sed 's/\r$//'`), so CRLF becomes LF.
file staff-fixed.csv
xxd -l 16 staff-fixed.csv
head -5 staff-fixed.csv

I opened `staff-fixed.csv` in Excel (double click, no import wizard), in LibreOffice, and with `cat` in the Linux terminal.

## Result

| Property | Before | After |
|---|---|---|
| Encoding | RK1048 | UTF-8 |
| Line ending | <CRLF / LF> | LF |
| BOM | none | present (`EF BB BF`) |



## What did not work the first time

I could not get permission for shared file properly and in first attempt used incorrect encoding method(CP1251 instead of RK1048).


## Evidence

--evidence/staff-broken.csv — original file from Canvas
- evidence/staff-fixed.csv — converted file
- evidence/file-before.txt — file and grep output on the original, shows the encoding and the line ending
- evidence/hexdump-before.txt — first 16 bytes of the original, shows there is no BOM
- evidence/file-after.txt — file and xxd on the fixed file, shows UTF-8 with BOM and LF
- evidence/opens-correctly.png — Excel, LibreOffice and cat showing the names correctly
- scripts/fix.sh — the conversion script

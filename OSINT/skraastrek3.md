# skråstrek3
> This challenge is in norwegian for some extra spice 😉 Denne hytta har jeg sett før, men jeg vet ikke hvor. Kan du finne ut hva hytta heter?

## Solution
The hint for the flag is in the sub-location exif attribute. It is represented in a What3Words string. Use https://what3words.com/ to find find "Høiås".

```bash
$ exiftool hytte.jpg

ExifTool Version Number         : 12.97
File Name                       : hytte.jpg
Directory                       : .
File Size                       : 18 kB
Zone Identifier                 : Exists
File Modification Date/Time     : 2024:10:14 10:09:29+02:00
File Access Date/Time           : 2024:10:15 15:06:24+02:00
File Creation Date/Time         : 2024:10:14 10:09:29+02:00
File Permissions                : -rw-rw-rw-
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 96
Y Resolution                    : 96
Current IPTC Digest             : 8ead02cedfbfe741276062aa4dcc9848
Sub-location                    : repeat.anguished.frosted
Application Record Version      : 4
Image Width                     : 468
Image Height                    : 309
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 468x309
Megapixels                      : 0.145
```

> Flag: SiktCTF{Høiås}
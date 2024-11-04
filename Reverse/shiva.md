# shiva + shiva2 + shiva2

## Solution
Probably not the intended solution, but it was the quickest. Use the `strings` command to extract the flag from the apk file.

```bash
$ strings shiva.apk | grep "SiktCTF{"
SiktCTF{InTheEndHopePrevails}
SiktCTF{TheFinalDaysAreUponUs}
SiktCTF{UnlimitedPower}
```
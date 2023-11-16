![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg) ![](../../workflows/test/badge.svg)


# Philips SAA1099 PSG in Verilog for Tiny Tapeout

* Wiki: https://en.wikipedia.org/wiki/Philips_SAA1099 and https://www.wikiwand.com/en/Philips_SAA1099
* Wiki: https://www.vgmpf.com/Wiki/index.php?title=SAA1099
* Manuals: https://www.vgmpf.com/Wiki/images/1/19/SAA1099_-_Manual_-_1984.pdf
* Manuals from SGI: http://www.sgistuff.net/mirrors/4dfaq/#appendixB
* Manuals from Sam Coupe: https://velesoft.speccy.cz/saa1099-cz.htm
* Manuals from Sam Coupe: https://velesoft.speccy.cz/samcoupe/saa1099/saa-1099_pinouts.txt
* Manuals from Sam Coupe: https://velesoft.speccy.cz/samcoupe/saa1099/saa1099-doc5-en.png
* Manuals from Sam Coupe: https://www.worldofsam.org/products/saa1099

## Chip technical capabilities

* 6 frequency generators, 8 octaves, 256 tones per octave, frequency range ffrom 31 Hz to 7.81 kHz
* 2 noise generators, range from 61 to 15.6 kHz
* 2 envelope generators
* common clock frequency 8 MHz, the SAA1099s on the GameBlaster are clocked at 7.15909 MHz ( highest frequency the tone generators can reach is about 6.99 kHz)

## Historical use of the Philips SAA1099
* Silicon Graphics IRIS Professional 4D and IRIS Power 4D machines
* Creative Sound Blaster 1.0 card
* Sam Coupe home computer
* System 5 arcade game system

## Pinout
```
SAA1099  (Philips)
------------------------

  func	pin	pin   func

   /WR	 1	 18   Vcc
   /CS	 2	 17   D7
    A0	 3	 16   D6
  OutR	 4	 15   D5
  OutL	 5	 14   D4
  Iref	 6	 13   D3
/DTACK	 7	 12   D2
   CLK	 8	 11   D1
   GND	 9	 10   D0
```

## Tests
* envelope test: https://www.youtube.com/watch?v=-ELEH-RX0JE

## Recordings from the real chip
* PDM tables by stripwax https://www.vogons.org/viewtopic.php?f=9&t=51695&start=60
* by Jepael http://www.vogons.org/viewtopic.php?f=9&t=51695
* by van Heusden https://vanheusden.com/electronics/SAA1099-clock/
* http://www.etheroneph.com/machinery/529-zvukogenerator-saa1099.html

### PDM

```
AMPLITUDE PDM SEQUENCES
 0: 0000000000000000000000000000000000000000000000000000000000000000 = 0
 1: 0000000011110000000000000000000000000000000000000000000000000000 = 4/64
 2: 0000000000001111111100000000000000000000000000000000000000000000 = 8/64
 3: 0000000011111111111100000000000000000000000000000000000000000000 = 12/64
 4: 0000000000000000000000000000000000001111111111111111000000000000 = 16/64
 5: 0000000011110000000000000000000000001111111111111111000000000000 = 20/64
 6: 0000000000001111111100000000000000001111111111111111000000000000 = 24/64
 7: 0000000011111111111100000000000000001111111111111111000000000000 = 28/64
 8: 1111000000000000000011111111111111110000000000000000111111111111 = 32/64
 9: 1111000011110000000011111111111111110000000000000000111111111111 = 36/64
10: 1111000000001111111111111111111111110000000000000000111111111111 = 40/64
11: 1111000011111111111111111111111111110000000000000000111111111111 = 44/64
12: 1111000000000000000011111111111111111111111111111111111111111111 = 48/64
13: 1111000011110000000011111111111111111111111111111111111111111111 = 52/64
14: 1111000000001111111111111111111111111111111111111111111111111111 = 56/64
15: 1111000011111111111111111111111111111111111111111111111111111111 = 60/64

ENVELOPE PDM SEQUENCES
 0: 0000000000000000000000000000000000000000000000000000000000000000 = 0/64
 1: 0000000000001000000000000000100000000000000010000000000000001000 = 4/64
 2: 0000010000000100000001000000010000000100000001000000010000000100 = 8/64
 3: 0000010000001100000001000000110000000100000011000000010000001100 = 12/64
 4: 0011000000110000001100000011000000110000001100000011000000110000 = 16/64
 5: 0011000000111000001100000011100000110000001110000011000000111000 = 20/64
 6: 0011010000110100001101000011010000110100001101000011010000110100 = 24/64
 7: 0011010000111100001101000011110000110100001111000011010000111100 = 28/64
 8: 1100001111000011110000111100001111000011110000111100001111000011 = 32/64
 9: 1100001111001011110000111100101111000011110010111100001111001011 = 36/64
10: 1100011111000111110001111100011111000111110001111100011111000111 = 40/64
11: 1100011111001111110001111100111111000111110011111100011111001111 = 44/64
12: 1111001111110011111100111111001111110011111100111111001111110011 = 48/64
13: 1111001111111011111100111111101111110011111110111111001111111011 = 52/64
14: 1111011111110111111101111111011111110111111101111111011111110111 = 56/64
15: 1111011111111111111101111111111111110111111111111111011111111111 = 60/64
```

### Noise
```
SAA1099P noise generator as documented by Jepael
seed unknown, must be non-zero
18-bit Galois LFSR
Feedback polynomial = x^18 + x^11 + x^1
Period = 2^18-1 = 262143 bits
Verified to match recorded noise from my SAA1099P
```

### Octaves
Apparently that makes the noisegen to be clocked by the undivided octave clock, so lowest octave 0 is same as rate X. And each octave higher doubles the noise frequency.

### Notes
```
B         5
C         33
C#       60
D         85
D#       109
E         132
F          153
F#        173
G         192
G#       210
A         227
A#       243
```

## Implementations
* MAME https://github.com/mamedev/mame/blob/master/src/devices/sound/saa1099.cpp
* Unreal emu, seems to be identical to MAME https://github.com/tslabs/zx-evo/blob/master/pentevo/unreal/Unreal/saa1099.cpp
* System Verilog for MIST Board https://github.com/sorgelig/SAMCoupe_MIST/blob/master/saa1099.sv
* C https://github.com/stripwax/SAASound
* Play MIDI on Arduino with SAA1099: https://github.com/Bobcatmodder/SAATunes
* https://github.com/SudoMaker/RetroWave

# What is Tiny Tapeout?

TinyTapeout is an educational project that aims to make it easier and cheaper than ever to get your digital designs manufactured on a real chip.

To learn more and get started, visit https://tinytapeout.com.

## Verilog Projects

Edit the [info.yaml](info.yaml) and uncomment the `source_files` and `top_module` properties, and change the value of `language` to "Verilog". Add your Verilog files to the `src` folder, and list them in the `source_files` property.

The GitHub action will automatically build the ASIC files using [OpenLane](https://www.zerotoasiccourse.com/terminology/openlane/).

## How to enable the GitHub actions to build the ASIC files

Please see the instructions for:

- [Enabling GitHub Actions](https://tinytapeout.com/faq/#when-i-commit-my-change-the-gds-action-isnt-running)
- [Enabling GitHub Pages](https://tinytapeout.com/faq/#my-github-action-is-failing-on-the-pages-part)

## Resources

- [FAQ](https://tinytapeout.com/faq/)
- [Digital design lessons](https://tinytapeout.com/digital_design/)
- [Learn how semiconductors work](https://tinytapeout.com/siliwiz/)
- [Join the community](https://discord.gg/rPK2nSjxy8)

## What next?

- Submit your design to the next shuttle [on the website](https://tinytapeout.com/#submit-your-design). The closing date is **November 4th**.
- Edit this [README](README.md) and explain your design, how it works, and how to test it.
- Share your GDS on your social network of choice, tagging it #tinytapeout and linking Matt's profile:
  - LinkedIn [#tinytapeout](https://www.linkedin.com/search/results/content/?keywords=%23tinytapeout) [matt-venn](https://www.linkedin.com/in/matt-venn/)
  - Mastodon [#tinytapeout](https://chaos.social/tags/tinytapeout) [@matthewvenn](https://chaos.social/@matthewvenn)
  - Twitter [#tinytapeout](https://twitter.com/hashtag/tinytapeout?src=hashtag_click) [@matthewvenn](https://twitter.com/matthewvenn)

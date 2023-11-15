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

## Chip technical capabilitie

* 6 frequency generators, 8 octaves, 256 tones per octave, frequency range ffrom 31 Hz to 7.81 kHz
* 2 noise generators, range from 61 to 15.6 kHz
* 2 envelope generators
* common clock frequency 8 MHz

## Historical use of the Philips SAA1099
* Silicon Graphics IRIS Professional 4D and IRIS Power 4D machines
* Creative Sound Blaster 1.0 card
* Sam Coupe home computer
* System 5 arcade game system

## Pinout

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


## Implementations
* MAME https://github.com/mamedev/mame/blob/master/src/devices/sound/saa1099.cpp
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

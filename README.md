<p align="center">
    <img src="images/logo.png">
</p>

HEXcart is a cartridge for Commodore 64. It can fit 16pcs of 8 or 16kB ROM images and supports regular and ultimax ROMs. ROM is selected with a hex-switch. The cartridge was designed mainly for diagnostics use with different tools like Dead Test and Diagnostics. Selection is done with a hex-switch so it can be used with a faulty C64 without any selection menus.

## Theory of operation
<p align="center">
    <img src="images/schematic.png">
</p>
HEXcart contains two flash ROM ICs U1 and U2. One is used for software and the other one is for logic. The softawe ROM IC must be at least 256kB in size to fit 16 pcs of 16kB ROM images./
The logic ROM IC sets the EXROM and GAME signals to the correct state for regular or ultimax ROMs. No need for jumpers or switches.
The EXROM and GAME signals need to be in the correct state so the ROM is mapped into the correct address space. Notice the signals are active low.
<p align="center">
    <img src="images/EXROM_GAME_table.png">
</p>
The hex-switch outputs go to a transparent latch IC. 



Making your own compilations is easy. 
## Schematic

[HEXcart PDF schematic](docs/HEXcart_R2_schematic.pdf)


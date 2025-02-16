<p align="center">
    <img src="images/logo.png">
</p>

HEXcart is a cartridge for Commodore 64. It can fit 16pcs of 8 or 16kB ROM images and supports regular and ultimax ROMs. ROM is selected with a hex-switch. The cartridge was designed mainly for diagnostics use with different tools like Dead Test and Diagnostics. Selection is done with a hex-switch so it can be used with a faulty C64 without any selection menus.
<p align="center">
    <img src="images/Cart_PCB-case.PNG">
</p>

## Theory of operation
<p align="center">
    <img src="images/schematic.png">
</p>
HEXcart contains two flash ROM ICs U1 and U2. One is used for software and the other one is for logic. The softawe ROM IC must be at least 256kB in size to fit 16 pcs of 16kB ROM images.<br/><br/>
The logic ROM IC is used to set the EXROM and GAME signals to the correct state for regular or ultimax ROMs. No need for jumpers or switches.
The EXROM and GAME signals need to be in the correct state so the ROM is mapped into the correct address space. Notice the signals are active low.
<p align="center">
    <img src="images/EXROM_GAME_table.png">
</p>
The hex-switch outputs go to a transparent latch IC U3. The latch is used for saving the state of the hex-switch during power-up/reset. This allows to set the hex-switch to different position while the machine is on. The new selected ROM is activated at the next power-up/reset. The LE (latch Enable) input of the latch IC is low active. Reset signal is therefore inverted with fet Q1 and resistor R2. If you don't need this latch feature you can leave out U3, Q1 and R2. Circuit is then replaced with four jumpers shorting pads 2&19, 3&18, 4&17 and 5&16 of U3 bypassing it. Short positions are marked on the PCB.<br/>

The latched hex-switch signals control the 4 highest address inputs of the software ROM IC. Therefore the hex-switch selects 16 different 16kB slots. The software ROM IC is enabled if either ROML or ROMH signal is low. This is done by diodes D2 and D3. The low active ROML and ROMH signals are used by the C64 to select low or high half of the 16kB ROM. That is why ROML signal must be connected to software ROM IC  pin A13.<br/>

The hex-switch signals control the 4 lowest address inputs of the logic ROM IC. Therefore it selects one of the first 16 bytes. These bytes are used to program the type of the cartridge. Outputs DQ0 and DQ1 control the GAME and EXROM signals. If the first 16kB slot in the software ROM IC contains a regular 16kB game then the first byte of the logic ROM IC must have two lowest bits zero.<br/>


Making your own compilations is easy. 
## Schematic

[HEXcart PDF schematic](docs/HEXcart_R2_schematic.pdf)


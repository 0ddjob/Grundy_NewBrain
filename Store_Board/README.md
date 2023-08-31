# Grundy NewBrain Store Board

This is the internal RAM board in the NewBrain.<br>

![Original Store Board](DRAM_Store_Board.jpg)

It comprises two banks of 16KB, making 32KB in total.  Each bank has eight MM5290N-2 (16K x 1bit) DRAM chips.<br>

The DRAM is multiplexed using two RAS signals (RAS16 for bank 1 and RAS32 for bank 2) and one CAS signal.<br>

My idea to replace these DRAM with a single 32KB SRAM is as follows:<br>
- There are only six address lines taken across to the store board<br>
- As per other DRAM-to-SRAM designs, latch the RAS signals and apply with CAS<br>
- To get the A14 address, I thought to also latch the RAS32 signal ... <br>
- Lower 16KB: latch A0 to A6 clocking on RAS16,<br>
- Upper 16KB: latch A0 to A6 plus RAS32, clocking on RAS32<br>

![SRAM Store Board](SRAM_Store_Board_schematic.png)

Let's see ... (31-Aug-2023)<br>

Thanks to John Bradley for his Kicad schematics:<br>
https://github.com/flypie/NewBrain

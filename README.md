# PCIe x16-to-x8 Debifurcator

Designed for use with the [Alveo U25](https://www.xilinx.com/products/boards-and-kits/alveo/u25.html) which has an x16 PCIe interface that is bifurcated to two x8 interfaces, one for the [SFC9250 X2 GbE Controller](https://www.xilinx.com/products/boards-and-kits/x2-series.html) and the other for the [XCZU19EG FPGA](https://www.xilinx.com/products/silicon-devices/soc/zynq-ultrascale-mpsoc.html#eg). This board connects the FPGA's PCIe x8 interface directly to a host system. The X2 GbE Controller is disconnected and ignored.

Only a straddle-mount PCIe x16 Connector is required, such as: [10025026-10103TLF](https://www.trustedparts.com/en/search/10025026-10103TLF), [10025026-10003TLF](https://www.trustedparts.com/en/search/10025026-10003TLF), or [10146027-A40010LF](https://www.trustedparts.com/en/search/10146027-A40010LF).

![PCIe x16-to-x8 Debifurcator for Alveo U25](img/PCIe_x16-to-x8_Debifurcator_for_Alveo_U25.jpg)

Related Projects: [alveo_u25_notes](https://github.com/mwrnd/alveo_u25_notes), [AlveoU25_JTAG_Adapter](https://github.com/mwrnd/AlveoU25_JTAG_Adapter), [ATX_Boot_Delay](https://github.com/mwrnd/ATX_Boot_Delay)


# Testing and Use Example

I have been able to [successfully test an XDMA design](https://github.com/mwrnd/alveo_u25_notes) using the debifurcator and an Alveo U25 in a system that does not support PCIe Bifurcation.

![PCIe x16-to-x8 Debifurcator with Alveo U25 In-System](img/Alveo_U25_System.jpg)

The XCZU19EG uses its ARM processor to configure the FPGA's Programmable Logic (PL) bitstream. It is difficult to get this to finish within the [PCIe Specification's 100ms time limit](https://pcisig.com/specifications/ecr_ecn_process?speclib=100+ms). Motherboard boot must be delayed to allow the FPGA to configure itself before PCIe devices are enumerated by the host system. This can be accomplished by toggling the POWER button, then pressing and holding the RESET button for a second before releasing it. Or, [connect a capacitor across the reset pins of an ATX motherboard's Front Panel Header](https://github.com/mwrnd/ATX_Boot_Delay):

![Motherboard Boot Delay Capacitor](img/Delay_Boot_Using_FrontPanelHeader_Capacitor.jpg)


# PCB Layout

![PCIe x16-to-x8 Debifurcator PCB Layout](img/PCIe_x16-to-x8_Debifurcator_PCB_Layout.png)

All differential pairs are length-matched to within 1mm both inter-pair and intra-pair.


# Schematic

![PCIe x16-to-x8 Debifurcator Schematic](img/PCIe_x16-to-x8_Debifurcator_Schematic.png)


# Assembly

The PCIe Connector's Mounting Post needs to be snapped off with needle-nose pliers.

![Snap Off PCIe Connector Mounting Post](img/Snap_Off_PCIe_Connector_Mounting_Post.jpg)


# PCB Layer Stackup

4-Layer PCB stackup taken from [JLCPCB](https://jlcpcb.com/capabilities/pcb-capabilities).

![PCB Layer Stackup](img/Layer_Stackup.png)

Differential Impedance parameters were calculated using the [DigiKey Online Calculator](https://www.digikey.com/en/resources/conversion-calculators/conversion-calculator-pcb-trace-impedance).

![PCB Differential Impedance Calculation](img/PCB_Impedance_0.30mm_0.18mm_on_0.21mm_7628.png)



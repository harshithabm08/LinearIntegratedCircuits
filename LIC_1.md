# Abstract
This report presents an analysis of two MOSFET-based amplifier configurations: a common-source (CS) amplifier with a resistive load and a common-source amplifier with an active PMOS load. 
The study focuses on comparing gain, bandwidth, and power consumption using LTSpice simulations. The channel length is fixed at 180 nm, and the total power dissipation is constrained to 100 µW with . 
The results show that replacing  with a PMOS current source significantly improves gain and bandwidth, while also affecting power dissipation. The impact of W/L ratio variation on performance is also discussed.

# Introduction
In analog circuit design, the choice of load element significantly impacts an amplifier’s performance. The common-source (CS) amplifier is a fundamental circuit used in signal amplification, 
and its performance can be optimized by selecting an appropriate load.
This report compares two configurations:
1. CS Amplifier with a Load Resistor (1K)
2. CS Amplifier with a PMOS Current Source (Active Load)

![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/bf92d5dbcc417a9a0b9416e27812f701e5d94a55/configuration_ckt.png)
## Circuit configuration and circuit parameters
The NMOS operates in the saturation region, with acting as the load.
The gain is determined by the transconductance and the drain resistance:
Av=-(gm*Rd)

Uses a fixed  as the load of Rd=1K ohm.

Vgs=0.54 V

Vdd=1.8 V

W=9 u

L=180 nm

Power considered for design=100 microWatts

![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/b41418ad8fcd2c59384f2c9f5bbb354f1383ba56/Op_withRd.png)

Instead of a passive resistor, a PMOS acts as an active load, functioning as a current source.
Offers higher gain due to increased output resistance.
Av = -(gm*rop)

Vdd= 1.8 V

Vgs=0.54 V

Vb= 0.5 V

W=20 u

L=180 nm

## Simulation Results and Observations
### Gain Comparison
With Rd: 2.2 V/V or 6.8 dB

With PMOS Load: 32 V/V or 30 dB

The PMOS current source significantly increases gain, as expected.

![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/ac7c1cc6f133346f3111d09f3cff93e784dba017/Op_withPMOS.png)
### Bandwidth Analysis(fH)
With Rd: ~90 MHz

With PMOS Load: >200 MHz

Higher bandwidth in PMOS configuration due to improved output impedance.
### Power consumption
### Effect of Aspect Ratio (W/L) on Performance
Increasing W/L of NMOS increases transconductance , improving gain.

Increasing PMOS W/L increases output resistance, increasing gain but reducing bandwidth due to higher parasitic capacitance.

Optimized PMOS W/L = 3× NMOS W/L, ensuring high gain with minimal bandwidth loss.

![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/654eee6bce788a731e4e66aeeb0282d49b114230/CMOS_Av.png)
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/6c507141123cfa8f0ecb6b366735364bc8444e6e/Rd_Av.png)

# Conclusion
The PMOS load significantly enhances gain and bandwidth compared to a resistive load.

Power consumption is higher initially, but can be optimized by selecting an appropriate PMOS W/L ratio.

A PMOS W/L of 3× NMOS W/L provides a good balance between gain, bandwidth, and power efficiency.

This study confirms that aspect ratio tuning is critical in optimizing MOSFET amplifier performance.

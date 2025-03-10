# Absrtact
---
_This report presents the analysis and simulation of a differential pair amplifier with a resistor at the source. The primary objective of this experiment is to examine the behavior of the amplifier by varying different parameters and evaluating its stability in terms of differential gain, common-mode gain, and overall frequency response._

# Introduction
A differential amplifier is a fundamental building block in analog circuit design, commonly used for signal amplification while rejecting common-mode noise. 
It amplifies the difference between two input signals, making it highly effective in applications such as sensor signal processing, communication circuits, and operational amplifier stages.

The basic structure of a differential amplifier consists of two transistors (MOSFETs or BJTs) sharing a common emitter/source connection. 
The resistor at the source terminal plays a crucial role in setting the bias current and improving linearity, but it introduces certain limitations. 
These include reduced gain, increased thermal sensitivity, and limited common-mode rejection ratio (CMRR).

To overcome these drawbacks, current sources can be used in place of the resistor. A current source provides a more stable biasing mechanism, improving gain stability, CMRR, and overall performance.

![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/8e7c4231216a9db4699286025d51953e77b410dd/dq.jpeg)
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/8aa512cb5c316aadb7b5bc8d02fb24b5fc762d98/wl%20ratio.jpeg)

# Procedure (PART-1)
## DC Analysis:
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/8aa512cb5c316aadb7b5bc8d02fb24b5fc762d98/opp_RSS.png)
To maintain the proper operation of the differential amplifier, both MOSFETs were ensured to be in the saturation region by keeping all key parameters identical for both transistors. 
This step was crucial in ensuring symmetry and balanced operation, which is essential for stable differential amplification.

1. Initial Biasing:
   
The drain current (Id) and the saturation current (Iss) were initially set slightly lower than the theoretically calculated values 0.599mA and 1.199mA respectively.
This was done to account for practical considerations in chip manufacturing, where even nano-scale variations in current can significantly impact power dissipation.

2. Fine-tuning Rd for Vout:
   
Once the initial biasing was established, the drain resistor (Rd) was adjusted to achieve the desired output voltage (Vout).

3. Theoretical Calculations:
   
The exact values of Rd, the source resistance (Rss), and the MOSFET width (W) were slighty modified/made more precise to ensure the amplifier operates within the required constraints.

## Transient Analysis
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/51b1e2c656030e3764c4903a2ca119ede8c3fa30/T_RSS.png)
1. Theoretical vs. Simulated Gain Verification:

The theoretical voltage gain of a single MOSFET stage was first calculated.
Since a differential pair amplifier provides twice the gain of a single MOSFET, this theoretical value was compared with the simulated differential gain to ensure accuracy.

2. Linearity and Distortion Analysis:
   
As the input signal approached the maximum and minimum swing limits, the output waveform began to show distortion and loss of linearity.
This behavior highlighted the limitations of the amplifier in handling large signals and emphasized the importance of maintaining operation within the linear range for accurate signal processing.

With this transient analysis, the amplifier’s differential gain, common-mode swing behavior, and linearity constraints were effectively studied and verified.

#### `Gain:(Differential output)/(Differential input)= 9 V/V`
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/9c5b03e92a8fd571923efa5839ac03142039d839/symm-swing.jpeg)
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/9c5b03e92a8fd571923efa5839ac03142039d839/vicm.jpeg)

## Frequency Analysis
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/51b1e2c656030e3764c4903a2ca119ede8c3fa30/AC_RSS.png)
A small-signal AC analysis was performed to obtain the gain vs. frequency plot (Bode plot).
The -3 dB bandwidth was determined by identifying the frequency at which the gain drops by 3 dB from its low-frequency value.

The presence of Rss reduces the bandwidth. It also affects the common-mode rejection ratio (CMRR) at higher frequencies due to the finite impedance of Rss.
As frequency increases, the gain drops due to the dominant pole behavior, and at very high frequencies, the circuit exhibits a roll-off.

Replacing Rss with a current source (using a MOSFET as an active load) increases output impedance, improving bandwidth and gain.
## Conclusion

The differential amplifier with a source resistor (Rss) is simple and effective, but it has limitations in gain, common-mode rejection, and high-frequency performance. While it provides some stability, it is not ideal for practical IC implementations due to power dissipation, bias current variations, and frequency limitations.

To overcome these drawbacks, Rss is often replaced with a constant current source (Iss), which offers higher impedance, improved gain, and better common-mode rejection. This transition is essential for high-performance analog circuit design and is a key step toward practical integrated differential amplifier implementations.

---

# Procedure (PART-2)
## DC Analysis 
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/51b1e2c656030e3764c4903a2ca119ede8c3fa30/op_ISS.png)
1. Setting up the circuit:

The source resistance (Rss) was replaced with an ideal current source (Iss) to ensure a constant bias current.
The MOSFETs were biased to ensure operation in the saturation region, where:
**Id=1/2*Kn* (Vov)^2
The drain resistances (Rd) were adjusted to set the desired output common-mode voltage.

2. Current Matching and Stability:

The constant current source ensures equal current division between the two MOSFETs, improving matching and symmetry.
This results in better bias stability and reduces dependence on process variations.

3. Comparison with Resistor Biasing:

In the previous case with Rss, the tail current varied due to process and temperature changes.
With Iss, the tail current remains constant, ensuring stable operating points and reducing mismatch effects.

## Transient Analysis
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/51b1e2c656030e3764c4903a2ca119ede8c3fa30/T_ISS.png)
1. Verification of Gain:

A sinusoidal differential input was applied, and the output differential gain was measured.
The measured gain was twice that of a single MOSFET amplifier, confirming theoretical expectations.

2. Common-Mode Swing:

The input and output common-mode swings were analyzed.
The current source provides higher bias stability, allowing a wider common-mode swing compared to Rss.
The output remained undistorted within the linear operating range, and distortion only occurred at very high input levels.

#### `Gain:(Differential output)/(Differential input)= 9.06 V/V`

## Frequency Analysis
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/51b1e2c656030e3764c4903a2ca119ede8c3fa30/AC_ISS.png)
1. Gain vs. Frequency Analysis:
   
A Bode plot was generated to observe the frequency response.
The -3 dB cutoff frequency (f_c) was higher than in the Rss case due to the absence of additional resistance at the source.
Bandwidth increased, confirming the advantage of using Iss.

2. High-Frequency Behavior:
   
The circuit showed less gain roll-off compared to the Rss configuration.

## Conclusion

By replacing the source resistance (Rss) with a constant current source (Iss), the differential amplifier exhibited significant performance improvements:
1. Higher differential gain due to increased impedance at the source.

2. Better common-mode rejection (CMRR) since Iss presents infinite impedance to common-mode signals.

3. Wider common-mode swing and improved bias stability.

4. Increased bandwidth and better high-frequency response, making the circuit more suitable for high-speed applications.

5. Reduced distortion, ensuring improved linearity over a wider range of input signals.

---

# Procedure (PART-3)
## DC Analysis
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/51b1e2c656030e3764c4903a2ca119ede8c3fa30/op_fet.png)
1. Setting the DC Operating Point (Q-Point):

The ideal current source was replaced with a MOSFET operating in saturation mode, forming an active current source.
The tail current was set as:
The drain resistances (Rd) were adjusted to maintain a stable common-mode voltage.

2. Comparison with Previous Implementations:

Compared to Rss, the MOSFET current source offers better gain and bias stability.
Compared to the ideal current source, the MOSFET introduces some non-idealities, such as finite output impedance and temperature variations.

## Transient Analysis 
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/51b1e2c656030e3764c4903a2ca119ede8c3fa30/T_FET.png)
1. Gain Verification:

A differential input signal was applied, and the output voltage swing was measured.
The gain was slightly similar to the design with an ideal current source.

#### `Gain:(Differential output)/(Differential input)= 9.094 V/V`

## Frequency Response (Bandwidth & Stability Analysis)
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/51b1e2c656030e3764c4903a2ca119ede8c3fa30/AC_FET.png)
1. Gain vs Frequency:

The Bode plot was generated, showing that the -3 dB bandwidth was lower than the ideal current source case but higher than the Rss case.

2. High-Frequency Behavior:

The MOSFET’s parasitic capacitances affected the gain roll-off at high frequencies.
The dominant pole was at a lower frequency compared to the ideal current source case, causing slightly lower bandwidth.
Despite this, performance was still significantly better than the resistor-based design.

## Conclusion

By replacing the ideal current source (Iss) with a MOSFET-based active current source, the differential amplifier exhibited the following key observations:

1. Higher differential gain than the resistor-based design but slightly lower than the ideal current source case.

2. Slightly degraded common-mode rejection (CMRR) due to the finite impedance of the MOSFET current source.

3. Improved bias stability compared to Rss but some dependence on MOSFET parameters like channel length modulation and temperature variations.

4. Reduced bandwidth compared to the ideal current source case due to the finite output impedance and parasitic effects.

5. More practical implementation, making it suitable for real-world integrated circuit designs.

---

# There is still more to go!!

* In practical integrated circuit (IC) implementations, using resistors at the drain of the differential amplifier is not ideal due to the following reasons:

* Large area consumption: Resistors require significant chip area, making integration difficult in VLSI circuits where millions to billions of transistors are used.

* Process variations: Resistors are more sensitive to fabrication variations, affecting performance consistency.

* Limited output resistance: The resistance value is fixed and not tunable dynamically, which can limit the design flexibility.


### Replacing Drain Resistors with PMOS Current Sources

To overcome these limitations, the drain resistors (Rd) are replaced with PMOS transistors operating in the saturation region. These PMOS devices act as active load current sources, improving overall circuit performance.

#### _Key Parameters of PMOS Current Sources:_

- The small-signal output resistance (ro) of a PMOS transistor is significantly higher than a resistor, which helps in achieving a higher voltage gain.

- PMOS transistors require proper biasing through a current mirror, ensuring a stable and tunable drain current.

- Unlike resistors, current sources offer programmable bias currents, allowing for adaptive gain control in analog ICs.

- PMOS transistors scale well with CMOS fabrication processes, making them suitable for nanometer-scale technologies.

### Conclusion

By replacing drain resistors with PMOS current sources, the differential amplifier achieves higher gain, better stability, and improved integration in modern ICs. This step marks the transition from basic differential amplifiers to fully integrated, high-performance analog circuits, which are widely used in operational amplifiers, analog front-end circuits, and mixed-signal designs.
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/bc28fd512c1f07f5a2651224af6627245b6bac35/PMOS_DA.png)

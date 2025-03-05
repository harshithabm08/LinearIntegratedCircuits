# Absrtact
This report presents the analysis and simulation of a differential pair amplifier with a resistor at the source. The primary objective of this experiment is to examine the behavior of the amplifier 
by varying different parameters and evaluating its stability in terms of differential gain, common-mode gain, and overall frequency response.

# Introduction
A differential amplifier is a fundamental building block in analog circuit design, commonly used for signal amplification while rejecting common-mode noise. 
It amplifies the difference between two input signals, making it highly effective in applications such as sensor signal processing, communication circuits, and operational amplifier stages.

The basic structure of a differential amplifier consists of two transistors (MOSFETs or BJTs) sharing a common emitter/source connection. 
The resistor at the source terminal plays a crucial role in setting the bias current and improving linearity, but it introduces certain limitations. 
These include reduced gain, increased thermal sensitivity, and limited common-mode rejection ratio (CMRR).

To overcome these drawbacks, current sources can be used in place of the resistor. A current source provides a more stable biasing mechanism, improving gain stability, CMRR, and overall performance. 

# Procedure (PART-1)
## DC Analysis:

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

1. Theoretical vs. Simulated Gain Verification:

The theoretical voltage gain of a single MOSFET stage was first calculated.
Since a differential pair amplifier provides twice the gain of a single MOSFET, this theoretical value was compared with the simulated differential gain to ensure accuracy.

2. Linearity and Distortion Analysis:
   
As the input signal approached the maximum and minimum swing limits, the output waveform began to show distortion and loss of linearity.
This behavior highlighted the limitations of the amplifier in handling large signals and emphasized the importance of maintaining operation within the linear range for accurate signal processing.

With this transient analysis, the amplifier’s differential gain, common-mode swing behavior, and linearity constraints were effectively studied and verified.

## Frequency Analysis

A small-signal AC analysis was performed to obtain the gain vs. frequency plot (Bode plot).
The -3 dB bandwidth was determined by identifying the frequency at which the gain drops by 3 dB from its low-frequency value.

The presence of Rss reduces the bandwidth. It also affects the common-mode rejection ratio (CMRR) at higher frequencies due to the finite impedance of Rss.
As frequency increases, the gain drops due to the dominant pole behavior, and at very high frequencies, the circuit exhibits a roll-off.

Replacing Rss with a current source (using a MOSFET as an active load) increases output impedance, improving bandwidth and gain.
# Conclusion

# Procedure (PART-2)

## DC Analysis 

1. Setting up the circuit:

The source resistance (Rss) was replaced with an ideal current source (Iss) to ensure a constant bias current.

## Transient Analysis

1. Verification of Gain:

A sinusoidal differential input was applied, and the output differential gain was measured.
The measured gain was twice that of a single MOSFET amplifier, confirming theoretical expectations.

2. Common-Mode Swing:

The input and output common-mode swings were analyzed.
The current source provides higher bias stability, allowing a wider common-mode swing compared to Rss.
The output remained undistorted within the linear operating range, and distortion only occurred at very high input levels.

## Frequency Analysis

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


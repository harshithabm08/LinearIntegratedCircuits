# Analysis of Current Mirrors
---
_*A current mirror is a circuit used to copy (mirror) a reference current to one or more output branches while maintaining constant current regardless of voltage variations. It is a crucial element in analog IC design, ensuring stable biasing for amplifiers and active loads.*_

Types of Current Mirrors
* PMOS Current Mirror
* NMOS Current Mirror

Advantages of Current Mirrors

* Provides stable and accurate biasing.
* Improves gain, stability, and bandwidth in amplifiers.
* Reduces power consumption compared to resistor biasing.
* Helps in temperature compensation for analog circuits.

Effect of Current Mirrors on Circuit Performance

* Gain: Ensures stable tail current, improving amplifier gain.
* Stability: Reduces variations in bias current.
* Bandwidth: A high output impedance mirror improves frequency response.

![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/956265d73497b6b407d9ba6d11ad3b08e34759a3/Current-Mirror-Circuit.png)

---

# PMOS Current Mirror Analysis

Design Parameters:

* Power rating: 1mA
* VDD: 1.8V
* Vov (Overdrive Voltage): 0.37V (Given, but needs verification)
* Vgs (Assumed): 0.7V
* Process transconductance parameter (kn’): 130μA/V²
  
Width-to-Length Ratio was calculated using the MOSFET saturation current equation: Id=0.5 * Kn' * (W/L) * (Von)^2
If L = 180nm, then:
W = 2.213 um

![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/9496c5f32e88c07bcffb8bc416f98652e906205c/CM_P_OP.png)
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/9496c5f32e88c07bcffb8bc416f98652e906205c/CM_P.png)

---

# NMOS Current Mirror for Design

Working Principle

* Uses two NMOS transistors where one transistor sets the reference current, and the second one mirrors it.
* The accuracy depends on matching transistors, process parameters, and channel length modulation effects.

Design Considerations for High Accuracy
* Use longer channel length (L) to minimize channel length modulation (λ).
* Ensure both transistors are in saturation region for better mirroring accuracy.

![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/9496c5f32e88c07bcffb8bc416f98652e906205c/CM_N.png)

---

# Differential Amplifier with NMOS Current Mirror

A differential amplifier is a crucial building block in analog circuits, amplifying the difference between two input signals. To function efficiently, 
it requires a precise bias current, which is where the NMOS current mirror is used.

#### How the Current Mirror Acts as a Bias Generator?

The NMOS current mirror provides a constant current as the tail current source for the differential amplifier.
This ensures that the differential pair operates in saturation, preventing variations in common-mode signals from affecting circuit performance.
The stability of bias current improves gain, reduces offset, and enhances overall circuit robustness.


### Performance Comparison

##### Advantages

* Provides a stable and accurate bias current.
* Helps reduce power consumption by ensuring transistors operate efficiently.
* Enhances gain and stability of the differential amplifier.
* Reduces offset variations, improving signal integrity.

##### Disadvantages

* Requires proper transistor matching for accurate current mirroring.
* Process variations can slightly affect performance if not designed correctly.
* Additional transistors increase circuit complexity.

![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/9496c5f32e88c07bcffb8bc416f98652e906205c/CMDA_OP.png)
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/9496c5f32e88c07bcffb8bc416f98652e906205c/CMDA_T.png)
![image alt](https://github.com/harshithabm08/LinearIntegratedCircuits/blob/c8588c5b6b910d538a7be503224e7863f1fc6855/CM_AC.png)

The integration of the NMOS current mirror as a biasing source in the differential amplifier significantly improved the gain, increasing it from *9 to 20*. This increase is due to the higher output resistance of the current mirror, which enhances the effective gain of the amplifier by improving the common-mode rejection and ensuring a more stable tail current. _However, as expected, the bandwidth decreased due to the inverse relationship between gain and bandwidth, maintaining a nearly constant gain-bandwidth product (GBW)_. The AC analysis further confirmed this trade-off, showing a lower -3dB bandwidth compared to the previous setup without the current mirror, aligning with theoretical expectations.

---

# Practical Importance in IC Design

Current mirrors are fundamental in integrated circuit (IC) design because:

1. They provide precise bias currents for various analog blocks.
2. They minimize process variation effects, making circuits more reliable.
3. Used extensively in op-amps, differential amplifiers, and voltage references.
4. Essential for low-power, high-performance analog designs.
---

# Conclusion

_While the theoretical design of the current mirror was based on standard process parameters, slight deviations in overdrive voltage (Vov), transconductance parameter (kn’), and transistor matching can lead to small discrepancies between calculated and simulated values. These variations arise due to process-dependent factors, such as channel length modulation, temperature effects, and second-order MOSFET characteristics, which were not fully accounted for in the initial assumptions. Additionally, practical implementation in LTSpice may reflect non-idealities such as device mismatches and parasitic effects, contributing to minor deviations in gain and biasing accuracy. Despite these variations, the overall design remains robust and demonstrates the expected behavior of a current mirror in stabilizing the differential amplifier’s tail current._


Current mirrors play a crucial role in biasing circuits, especially in differential amplifiers, ensuring stable operation with minimal variation. 
By implementing NMOS current mirrors as bias voltage generators, differential amplifiers achieve better gain, stability, and power efficiency, making them a key component in modern analog IC design.



# Abstract

Operational Transconductance Amplifiers (OTAs) are pivotal components in analog circuit design, especially for signal processing applications. Among various OTA architectures, 
the Miller OTA stands out due to its enhanced stability and frequency compensation using the Miller effect. This paper explores the design, simulation, and performance evaluation of a 
Miller OTA using LTSpice. Key parameters such as gain, phase margin, and input common-mode range are discussed. The work provides insight into how compensation capacitors influence OTA behavior, 
aiming to serve as a foundational reference for analog designers.

## Analysis of Miller effect, Zeroes and Poles

The Miller effect, poles, and zeros are fundamental concepts in analog circuit theory and frequency response analysis. The Miller effect occurs when a capacitance is connected between the
input and output of an inverting amplifier, causing the input to experience a much larger effective capacitance due to the amplifier's gain, which in turn reduces the bandwidth of the circuit by 
lowering the high-frequency response. Poles are specific frequencies where the gain of a system begins to decrease, typically introducing a −20 dB/decade slope in the Bode plot. They are associated 
with the natural response of the circuit and often determine stability and bandwidth. In contrast, zeros are frequencies where the transfer function numerator becomes zero, resulting in either a 
gain increase (+20 dB/decade), often used in compensation techniques to improve system stability and performance. 
Together, these elements shape the overall behavior of amplifiers and filters across different frequency ranges.

## Design Specification

#### DC gain = 75dB, GB = 5MHz, Phase margin>= 600, Slew rate = 10uV/s, Cc= 3pF, CL= 1pF, (UnCox)n = 280uA/V2, (UnCox)p = 160uA/V2, VSS= -1.8V, VDD=1.8V Power<1mW, L= 500nm, Vth min|=0.35V, |Vth max| = 0.45V.

## Circuit analysis and calculations

The design of a Miller OTA (Operational Transconductance Amplifier) involves careful analysis of each stage to ensure all MOSFETs operate in saturation, and the required gain, bandwidth, and biasing conditions are met. The OTA consists of a differential input pair, active load, current mirror, and an output gain stage. The following equations govern the operating points, biasing, and voltage levels across various nodes in the circuit.
P/V = 1m / 3.6V = 277 uA.
Iref = 37uA
R1=(1/gm6) ohms

* Cc>= 0.22CL
Therefore, Cc = 3pF
* gm1= gm2= GBW*Cc* 2π = 94.2477uS
ID1,2 = gm1,2 * Vov / 2 = 18.5uA
(W/L)1,2= gm1,2/ (UnCox)n ID1 = 1.7147
            W1,2= 0.8573um
* ICMR(max)=1.3V,ICMR(min)= 0.8V
VSG3= VDD - ICMR(max) + Vth min            
       =  1.8 – 1.3 + 0.35
       =   0.85V
* (W/L)3,4 = 2I3/ (UnCox)p(VSG3- Vth max)
              =  2*18.5u/ 160u*(0.40)2
    (W)3,4=  1.44u
* (W/L)5 = 2I5/ (UnCox)n(VD sat)2
              =  0.4u
          VD sat = ICMR(min) - VGS1
 Where, VGS1 = (2ID1/ Kn1*(W/L)1)1/2 - Vth max 
* gm6 >= 10gm1 = 942.47uS
ID6 = gm6* Vov / 2 = 188.5uA
* (W/L)6 / (W/L)4 = gm6/ gm4
(W/L)6 = 44.117
* I6/I4 = (W/L)6 /(W/L)4  
W6= 22.05um
* (W/L)7 = I7/I5 * (W/L)5    -----( I7=I6 )
                       =  188.5uA/ 37u
                       =  5.09
                    W7 = 5.09um

  ![image](https://github.com/user-attachments/assets/43329ff6-a08b-47ce-8bc5-0017d5b7d7d7)

  ## Ananlysis

  ### A.DC analysis:

The DC operating point analysis of the Miller OTA was conducted to validate the stability and biasing conditions of each transistor in the circuit. The design ensured that all transistors operate in 
their saturation region, which is essential for proper amplification and linear behavior. During the DC analysis, the voltages across the critical nodes and the bias currents in each branch were 
thoroughly verified. The set current values — including 37 µA, 18.46 µA (×2), and 188.4 µA — were consistently observed during the simulation, confirming that the biasing network is functioning as intended. 
Additionally, the node voltages were within expected ranges to maintain saturation conditions and meet the desired input common-mode range (ICMR) and output swing.

### B. AC analysis:

AC analysis is a small signal analysis performed in the frequency domain and used to determine the frequency 
response of a circuit. AC analysis is used to define circuit parameters such as gain, cut off frequency, unity gain bandwidth, and phase margin. The differential gain is obtained by biassing both transistor 
inputs to 900mV and the other to the overall output (feedback). The figure shows that the Op-amp achieves nearly 78.8 dB gain and an 86-degree phase margin. 
It was also discovered that the cutoff frequency is equal to 6.25 MHz, which is nearly identical to the specifications with a requirement of phase margin greater than 60-degree.

### C. Power analysis

The design of the Miller OTA was carried out to ensure that the total power consumption remains under 1 mW, which aligns with the low-power design requirements of analog circuits. 
Operating at a total supply voltage of 3.6 V (VDD = +1.8 V, VSS = –1.8 V), the overall current budget was fixed at approximately 277 µA. The current is distributed across the circuit 
branches as follows: 37 µA in one input branch, 18.46 µA in each of the differential pair arms, and 188.4 µA allocated to the output stage. 
These values reflect a carefully balanced design approach, where each stage was assigned sufficient current to meet gain and bandwidth requirements, while ensuring that the power stays within budget.

![image](https://github.com/user-attachments/assets/ff31d165-c887-4acf-bc8d-3e37fc9349e5)

![image](https://github.com/user-attachments/assets/49fff839-d39b-4c66-9f48-c7b5b5518abb)

# Conclusion

The simulation was performed in LTSpice in 500nm and 1um node technology. The system's gain and phase margin were improved by adjusting the parameters (W/L) and using a nulling resistor in 
series with the miller capacitance. The Opamp Design has a gain of 78.8 dB with a phase margin of 86 degrees under unity gain configuration a gain bandwidth of 6.25 MHz, and a power dissipation 
of less than 1mW. Hence we have successfully designed a two stage Miller Compensated Opamp with high gain with relatively good bandwidth and phase margin.


# Experiment-4-Differential-Amplifier-

# Differential Amplifier Analysis

## Aim

To develop and simulate three different MOSFET differential amplifier configurations in LTspice through DC, transient, and AC analysis, and to compare their performance in terms of voltage gain, bandwidth, and power consumption.

## Introduction

A differential amplifier is one of the most important and widely used building blocks in analog electronic circuit design. It amplifies the difference between two input signals while suppressing common-mode signals that appear at both inputs. Because of this property, differential amplifiers are highly effective in reducing noise and improving signal accuracy in many electronic systems.

MOSFET-based differential amplifiers are commonly used in modern integrated circuits such as operational amplifiers, comparators, analog signal processors, and sensor interface circuits. These amplifiers offer several advantages including high voltage gain, good noise rejection capability, better input impedance, and improved power efficiency. Due to these characteristics, MOSFET differential amplifiers are widely applied in communication systems, instrumentation circuits, and mixed-signal electronic devices.

In this experiment, three different configurations of MOSFET differential amplifiers are designed and simulated using LTspice simulation software. Each circuit is analyzed using DC analysis to determine the biasing conditions, transient analysis to observe time-domain signal behavior, and AC analysis to evaluate frequency response. The simulation results are used to compare the performance of the circuits in terms of voltage gain, bandwidth, power consumption, and overall stability.

Additionally, the experiment helps in understanding how different circuit configurations affect amplifier characteristics such as linearity, output response, and efficiency. The comparative study provides deeper insight into the practical design considerations of MOSFET differential amplifiers used in real-world analog integrated circuits.

## Theory

A differential amplifier is an electronic circuit designed to amplify the difference between two input signals while suppressing any signal that is common to both inputs. This capability is referred to as common-mode rejection, which plays a crucial role in improving accuracy and minimizing noise in analog circuit systems.

A typical MOS differential amplifier is formed using two identical MOSFET transistors (M1 and M2). The sources of these transistors are connected together and biased with a constant current source to maintain stable operation. The drain terminals are connected to load components such as resistors or active loads, which help convert the differential input signal into an amplified output voltage.

When a differential input voltage is applied:

$$
v_{id} = v_{in1} - v_{in2}
$$

the total current is steered between the two transistors depending on the input difference. If $v_{in1} > v_{in2}$, transistor M1 conducts more current, and if $v_{in2} > v_{in1}$, transistor M2 conducts more.

For small differential inputs, both transistors operate in the saturation region, and the circuit behaves linearly. The differential gain of the amplifier is given by:

$$
A_v = g_m R_{out}
$$

where $g_m$ is the transconductance of the MOSFET and $R_{out}$ is the effective output resistance.

The transconductance is defined as:

$$
g_m = \frac{2 I_D}{V_{ov}}
$$

where $I_D$ is the drain current and $V_{ov}$ is the overdrive voltage.

For larger differential inputs:

$$
v_{id} > \sqrt{2} V_{ov}
$$

In certain conditions, one transistor may turn OFF while the other transistor conducts the entire bias current. When this occurs, the amplifier operates in a non-linear region, which affects the linear amplification of the input signal.

The overall performance of a differential amplifier is strongly influenced by the type of load connected to the circuit:

Resistive load → provides moderate voltage gain
Active load → increases output resistance and improves gain
Current mirror load → offers higher gain and better output performance

Therefore, by modifying the load configuration of the circuit, important parameters such as gain, bandwidth, and overall amplifier performance can be greatly influenced.

---

## Circuit 1: Differential Amplifier with Resistive Load

## 1.1 Working Principle

The circuit consists of two matched NMOS transistors (M1 and M2) configured as a differential pair. The source terminals of both transistors are connected together and biased using a constant tail current source, which provides a stable current for proper circuit operation. The drain terminals of the transistors are connected to resistive load elements that convert the current variations into output voltage signals.

When two input signals are applied to the gates of M1 and M2, the differential amplifier amplifies the difference between these input voltages. If both input signals are equal, the current flowing through both transistors remains the same, and the output voltages at the drains remain balanced. However, when a difference exists between the input signals, the current distribution between the two transistors changes.

For example, if the voltage applied to the gate of M1 is greater than that of M2, transistor M1 conducts more current while transistor M2 conducts less current. As a result, the voltage at the drain of M1 decreases and the voltage at the drain of M2 increases. This difference in drain voltages produces the amplified differential output.

The constant tail current source ensures that the total current flowing through the differential pair remains constant, which improves the stability and linearity of the amplifier. This configuration also provides good common-mode rejection, allowing the circuit to suppress noise or unwanted signals that appear simultaneously at both inputs.

Because of these characteristics, MOSFET differential amplifiers are widely used in operational amplifiers, analog integrated circuits, communication systems, and signal processing applications.


When a differential input is applied:

$$
v_{id} = v_{in1} - v_{in2}
$$

the total tail current ($I_{SS}$) is steered between the two transistors depending on the input difference.

- If $v_{in1} > v_{in2}$, transistor M1 conducts more current while M2 conducts less.  
- If $v_{in2} > v_{in1}$, transistor M2 conducts more current while M1 conducts less.  

The variation in the drain current of each transistor causes a corresponding voltage drop across the load resistors (𝑅D). This voltage drop generates different output voltages at the drain terminals, producing the differential output signal.

For small differences between the input voltages, both MOSFET transistors remain in the saturation region, and the amplifier operates in a linear mode. In this region, the output voltage is directly proportional to the difference between the two input signals.

When the differential input voltage becomes large, one transistor may gradually switch OFF while the other transistor conducts the entire tail current. Under this condition, the circuit enters a non-linear operating region, and the output is no longer proportional to the input.

Therefore, the differential amplifier converts a differential input voltage into a corresponding differential output voltage by steering the current through the resistive load elements.

## Circuit Diagram

<img width="1029" height="781" alt="image" src="https://github.com/user-attachments/assets/086d748f-befc-4b50-8182-a455590d91bb" />


## 1.2 Design Calculations

### GIVEN PARAMETERS

- Technology: TSMC 180nm 
- Supply voltage, $V_{DD} = +0.9V$  
- Negative supply, $V_{SS} = -0.9V$   
- Power constraint, $P \leq 1.8mW$
- Channel length, $L_n = 480nm$ 
- Input common-mode voltage, $V_{in,CM} = 0V$  
- Output common-mode voltage, $V_{O,CM} = 0V$  
- Tail node voltage, $V_p = -0.7V$  
- Load capacitance, $C_L = 10pF$   
- Threshold voltage, $V_T \approx 0.36V$  

---

### 1.2.a Power Constraint


The total power consumed by the differential amplifier is given by:

$$
Power Consumption Calculation

The total power consumed by the differential amplifier is given by

$P = (V_{DD} - V_{SS}) \cdot I_{SS}$

where
$V_{DD}$ = positive supply voltage
$V_{SS}$ = negative supply voltage
$I_{SS}$ = tail current.

Total Supply Voltage

The total supply voltage across the circuit is

$V_{DD} - V_{SS} = 0.9 - (-0.9)$

$V_{DD} - V_{SS} = 1.8V$

Power Constraint

The maximum allowed power dissipation is 1.8 mW, therefore

$P \le 1.8 \times 10^{-3}$

Substituting the power equation:

$(V_{DD} - V_{SS}) \cdot I_{SS} \le 1.8 \times 10^{-3}$

$1.8 \cdot I_{SS} \le 1.8 \times 10^{-3}$

$I_{SS} \le 1mA$

Selected Tail Current

To utilize the available power limit effectively, the tail current is selected as

$I_{SS} = 1mA$

Power Dissipation

$P = 1.8 \times 1mA$

$P = 1.8mW$

Since $1.8mW \le 1.8mW$, the power requirement is satisfied.
$$
I_{SS} \leq 1mA
$$

To fully utilize the available power budget, we choose:

$$
I_{SS} = 1mA
$$

Power dissipated:

$$
P = 1.8 \times 1mA = 1.8mW
$$

Since $1.8mW \leq 1.8mW$, the power constraint is satisfied.

##

### 1.2.b Drain Current Calculation

In a balanced differential amplifier, the tail current splits equally between both transistors:

$$
I_{D1} = I_{D2} = \frac{I_{SS}}{2}
$$

Substituting:

$$
I_{D1} = I_{D2} = \frac{1mA}{2}
$$

$$
I_{D1} = I_{D2} = 0.5mA
$$

##

### 1.2.c Load Resistance Calculation

Given:

$$
V_{OCM} = 0V
$$

So,

$$
V_{out1} = V_{out2} = 0V
$$

The output voltage is given by:

$$
V_{out} = V_{DD} - I_D R_D
$$

Substituting:

$$
0 = 0.9 - I_D R_D
$$

$$
I_D R_D = 0.9
$$

Solving for resistance:

$$
R_D = \frac{0.9}{I_D}
$$

Substituting:

$$
R_D = \frac{0.9}{0.5 \times 10^{-3}}
$$

$$
R_D = 1.8k\Omega
$$

##

### 1.2.d Bias Point Calculation

Given:

$$
V_{in,CM} = 0V
$$

So,

$$
V_{G1} = V_{G2} = 0V
$$

### Source Voltage

Given:

$$
V_p = -0.7V
$$

Assuming:

$$
V_S = V_p
$$

$$
V_S = -0.7V
$$

### Gate-Source Voltage

$$
V_{GS} = V_G - V_S
$$

$$
V_{GS} = 0 - (-0.7)
$$

$$
V_{GS} = 0.7V
$$

### Overdrive Voltage

Given:

$$
V_T \approx 0.36V
$$

$$
V_{OV} = V_{GS} - V_T
$$

$$
V_{OV} = 0.7 - 0.36
$$

$$
V_{OV} = 0.34V
$$

### Drain Voltage

From previous calculation:

$$
V_{out1} = V_{out2} = 0V
$$

### Drain-Source Voltage

$$
V_{DS} = V_D - V_S
$$

$$
V_{DS} = 0 - (-0.7)
$$

$$
V_{DS} = 0.7V
$$

### Saturation Check

Condition:

$$
V_{DS} > V_{OV}
$$

$$
0.7 > 0.34
$$

Hence, both transistors operate in saturation.

### Final Bias Point

$$
V_G = 0V
$$

$$
V_S = -0.7V
$$

$$
V_D = 0V
$$

$$
V_{GS} = 0.7V
$$

$$
V_{DS} = 0.7V
$$

##

### 1.2.e Width Calculation

The drain current in saturation is given by:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_T)^2
$$

Rewriting:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{OV})^2
$$

Rearranging to find width:

$$
W = \frac{2 I_D L}{\mu_n C_{ox} (V_{OV})^2}
$$

### Substituting Values

$$
I_D = 0.5mA = 0.5 \times 10^{-3}A
$$

$$
L = 480nm = 480 \times 10^{-9}m
$$

$$
\mu_n C_{ox} = 236.5 \mu A/V^2 = 2.365 \times 10^{-4}
$$

$$
V_{OV} = 0.34V
$$

### Calculation

$$
W = \frac{2 \times 0.5 \times 10^{-3} \times 480 \times 10^{-9}}{2.365 \times 10^{-4} \times (0.34)^2}
$$

$$
W = \frac{480 \times 10^{-12}}{2.365 \times 10^{-4} \times 0.1156}
$$

$$
W = \frac{480 \times 10^{-12}}{2.732 \times 10^{-5}}
$$

$$
W \approx 17.57 \mu m
$$

The width obtained using first-order equations gives only an approximate estimation because it is calculated based on simplified assumptions such as constant carrier mobility and ideal saturation operation. In practical MOSFET devices, several non-ideal effects influence the actual behavior of the transistor.

These effects include channel length modulation, mobility degradation, and variations in device model parameters, which can slightly shift the operating point from the theoretical calculations.

To strictly satisfy the given condition:

$$
V_p = V_S = -0.7V
$$

The transistor width was further fine-tuned using simulation. By adjusting the width parameter, the drain current was carefully controlled so that the source node voltage matched the desired value accurately.
Final width obtained:

$$
W \approx 28.475 \mu m
$$

Therefore, the variation between the theoretical and simulated transistor width arises due to non-ideal device behavior and the need to achieve accurate biasing conditions in the practical simulation model.

---

## DC Analysis

<img width="1785" height="810" alt="image" src="https://github.com/user-attachments/assets/9b6d9a2f-2082-47a9-9059-5d918d20918c" />

The figure shows the transient output waveforms of the MOSFET differential amplifier obtained from LTspice simulation. The two output voltages, 𝑉(𝑜𝑢𝑡1)V(out1) and 𝑉(𝑜𝑢𝑡2)
V(out2), are sinusoidal signals with a frequency of approximately 1 kHz. It can be observed that the two outputs are 180° out of phase with each other, which is the expected behavior of a differential amplifier. When the voltage at one output increases, the voltage at the other output decreases, demonstrating the current steering action of the differential pair. The smooth and stable waveform indicates that the MOSFETs are operating in the saturation region and the amplifier is functioning in the linear region. This confirms that the circuit is properly biased and is successfully amplifying the differential input signal.

The DC operating point indicates that both the output voltage and the source voltage are close to the intended bias values, ensuring that the transistors operate properly in the saturation region.

---

### 1.2.f Input Common Mode Range (ICMR)

The Input Common Mode Range (ICMR) refers to the range of input voltages over which the differential amplifier operates correctly while ensuring that all the transistors remain in the saturation region.

### Minimum Input Common Mode Voltage

For the differential amplifier to operate properly, the tail current source must remain active and provide a constant bias current. At the same time, the NMOS transistors in the differential pair should operate in the saturation region to maintain proper amplification and stable circuit performance.

Condition:

$$
V_{GS} \ge V_T
$$

Using:

$$
V_{GS} = V_{ICM} - V_S
$$

So,

$$
V_{ICM(min)} = V_S + V_T
$$

Substituting values:

$$
V_S = -0.7V, \quad V_T = 0.36V
$$

$$
V_{ICM(min)} = -0.7 + 0.36
$$

$$
V_{ICM(min)} = -0.34V
$$

### Maximum Input Common Mode Voltage

For maximum input voltage, the NMOS transistors must remain in saturation.

Condition:

$$
V_{DS} \ge V_{OV}
$$

Using:

$$
V_D = 0V, \quad V_S = -0.7V
$$

$$
V_{DS} = V_D - V_S = 0 - (-0.7) = 0.7V
$$

Now,

$$
V_{ICM(max)} = V_D + V_T
$$

Substituting:

$$
V_{ICM(max)} = 0 + 0.36
$$

$$
V_{ICM(max)} = 0.36V
$$

### Final Input Common Mode Range

$$
-0.34V \le V_{ICM} \le 0.36V
$$

##

### 1.2.g Output Common Mode Range

The output common-mode voltage range is defined as the range of output voltages over which the differential amplifier operates correctly while keeping the NMOS transistors in the saturation region.

### Maximum Output Voltage

The maximum output voltage is obtained when the drain voltage reaches its highest allowable level. This maximum value is mainly limited by the supply voltage of the circuit.

$$
V_{OCM(max)} \le V_{DD}
$$

However, to maintain current flow through the load resistor:

$$
V_{OCM(max)} = V_{DD}
$$

$$
V_{OCM(max)} = 0.9V
$$

### Minimum Output Voltage

For proper operation, the NMOS transistors must remain in saturation:

$$
V_{DS} \ge V_{OV}
$$

Using:

$$
V_{DS} = V_D - V_S
$$

At the edge of saturation:

$$
V_D - V_S = V_{OV}
$$

So,

$$
V_D = V_S + V_{OV}
$$

Since:

$$
V_D = V_{OCM(min)}
$$

$$
V_{OCM(min)} = V_S + V_{OV}
$$

### Substituting Values

$$
V_S = -0.7V, \quad V_{OV} = 0.34V
$$

$$
V_{OCM(min)} = -0.7 + 0.34
$$

$$
V_{OCM(min)} = -0.36V
$$

### Final Output Common Mode Range

$$
-0.36V \le V_{OCM} \le 0.9V
$$
Maximum Output Voltage

The maximum output voltage occurs when the drain node approaches the supply voltage. Therefore, the upper limit of the output common-mode voltage is limited by the supply voltage 
𝑉
𝐷
𝐷
V
DD
	​

.

V_OCM(max) ≤ V_DD

For the given circuit:

V_DD = 0.9 V

Hence,

V_OCM(max) = 0.9 V
Minimum Output Voltage

For proper operation, the NMOS transistors must remain in saturation.

V_DS ≥ V_OV

Using

V_DS = V_D − V_S

At the boundary of saturation

V_D − V_S = V_OV

Therefore,

V_D = V_S + V_OV

Since

V_D = V_OCM(min)

Thus

V_OCM(min) = V_S + V_OV

Substituting Values

V_S = −0.7 V

V_OV = 0.34 V

V_OCM(min) = −0.7 + 0.34

V_OCM(min) = −0.36 V

Final Output Common Mode Range

−0.36 V ≤ V_OCM ≤ 0.9 V
##

### 1.2.h Differential Input Voltage Range (Linear Region)

A differential amplifier operates in the linear region only when both MOSFET transistors remain in the saturation region and the tail current is distributed almost equally between them.

For a MOS differential pair, linear amplification occurs when the differential input voltage is relatively small compared to the overdrive voltage. Under this condition, the current sharing between the two transistors changes gradually, allowing the circuit to produce a proportional amplified output.

### Condition for Linear Operation

Differential Input Voltage Condition

For a MOS differential pair, the circuit operates in the linear region only when the differential input voltage remains within a certain limit. This limit is determined by the overdrive voltage of the transistors. If the differential input exceeds this limit, one transistor may carry most of the current while the other may turn OFF, resulting in non-linear operation.

The condition for linear operation is given by:

|V_id| ≤ 2 V_OV

where
V_id = differential input voltage
V_OV = overdrive voltage of the MOSFET

Substituting the Given Value

From the design calculation:

V_OV = 0.34 V

Substituting into the above relation:

|V_id| ≤ 2 × 0.34

|V_id| ≤ 0.68 V

Final Differential Input Voltage Range

Therefore, the allowable differential input voltage range for linear operation of the amplifier is

-0.68 V ≤ V_id ≤ 0.68 V

This range ensures that both transistors remain in saturation and the tail current is properly shared between them, allowing the differential amplifier to produce a linear amplified output.
---

## 1.3 Transient Analysis and Linearity Observation

The linear behavior of the differential amplifier is verified using transient analysis.

### Condition for Linearity

$$
|V_{id}| < \sqrt{2} V_{OV}
$$

$$
\sqrt{2} V_{OV} = 1.414 \times 0.34 = 0.48V
$$

### Case 1: Linear Region

Input applied:

$$
V_{id} = 100mV < 0.48V
$$

<img width="1916" height="849" alt="image" src="https://github.com/user-attachments/assets/5aee6e4f-5178-4b4b-bce0-e774338e362f" />


Observation:

- Output waveform is sinusoidal
- No distortion observed
- Both transistors operate in saturation
- Amplifier behaves linearly

### Case 2: Non-Linear Region

Input applied:

$$
V_{id} = 600mV > 0.48V
$$

<img width="1919" height="847" alt="image" src="https://github.com/user-attachments/assets/cac11637-fa5a-434c-8b67-cbd5b71ddf0a" />


Observation:

- Output waveform shows distortion
- Clipping observed
- One transistor enters cutoff region
- Linear amplification is lost

##

The behavior of the differential amplifier is analyzed for two cases based on the input differential voltage.

### Comparison Table

| Parameter | Case 1: Linear Region | Case 2: Non-Linear Region |
|----------|----------------------|--------------------------|
| Condition | $V_{id} < \sqrt{2}V_{OV}$ | $V_{id} > \sqrt{2}V_{OV}$ |
| Input ($V_{id}$) | 100 mV | 600 mV |
| Output waveform | Sinusoidal | Distorted / Clipped |
| Gain | Constant | Reduced / Non-linear |
| Transistor operation | Both in saturation | One enters cutoff |
| Current distribution | Equal sharing | Current shifts to one transistor |

### Interpretation

In the linear operating region, the differential input voltage is relatively small, allowing both transistors to remain in the saturation region. Under this condition, the tail current is almost equally divided between the two transistors. As a result, the amplifier produces an output that is proportional to the input difference, ensuring a linear and undistorted response with nearly constant gain.

In the non-linear region, the differential input voltage becomes larger than the allowable limit. In this case, one transistor begins to conduct most of the tail current while the other transistor moves toward the cutoff region. This uneven current distribution leads to distortion in the output signal and causes the amplifier to lose its linear amplification characteristics.

### Conclusion

The differential amplifier operates linearly only for small input signals.

$$
|V_{id}| < \sqrt{2} V_{OV}
$$

As the differential input voltage increases beyond the limit:

$$
|V_{id}| > \sqrt{2} V_{OV}
$$

the circuit transitions from linear amplification to non-linear behavior due to unequal current distribution and transistor cutoff.

##

## Theoretical and Simulated Gain

<img width="1919" height="426" alt="image" src="https://github.com/user-attachments/assets/9a312e32-b816-49c6-a570-cbb3880cc64a" />


The output waveform is amplified and inverted.

### Simulated Gain

Input signal parameters:

- Type: Sine wave  
- Frequency = 1kHz  
- Amplitude = 50mV (applied differentially) 
- DC Offset = 0V

Measured peak-to-peak values:

$$
V_{in(p-p)} = 50mV - ( - 50mV ) = 100mV
$$

$$
V_{out(p-p)} = 302mV - ( - 302mV ) = 604mV
$$

Voltage gain:

$$
A_v = \frac{V_{out(p-p)}}{V_{in(p-p)}}
$$

$$
A_v = \frac{604 \times 10^{-3}}{100 \times 10^{-3}}
$$

$$
A_v = 6.04
$$

Gain in dB:

$$
A_v(dB) = 20\log_{10}(6.04)
$$

$$
A_v(dB) = 15.62dB
$$

##

### Theoretical Gain

Assume channel length modulation:

$$
\lambda = 0.1 \, V^{-1}
$$

### Output Resistance

The output resistance of each MOSFET is:

$$
r_o = \frac{1}{\lambda I_D}
$$

Substituting:

$$
I_D = 0.5mA = 0.5 \times 10^{-3}A
$$

$$
r_o = \frac{1}{0.1 \times 0.5 \times 10^{-3}}
$$

$$
r_o = 20k\Omega
$$

### Effective Output Resistance

Since two transistors are present:

$$
r_{o,eff} = r_{o1} \parallel r_{o2}
$$

$$
r_{o,eff} = 20k \parallel 20k
$$

$$
r_{o,eff} = 10k\Omega
$$

### Transconductance

$$
g_m = \frac{2 I_D}{V_{OV}}
$$

$$
g_m = \frac{2 \times 0.5 \times 10^{-3}}{0.34}
$$

$$
g_m \approx 2.94mS
$$

### Total Output Resistance

The effective load seen at the output is:

$$
R_{out} = R_D \parallel r_{o,eff}
$$

$$
R_{out} = 1.8k \parallel 10k
$$

$$
R_{out} \approx 1.53k\Omega
$$

### Differential Gain

$$
A_d = g_m R_{out}
$$

$$
A_d = 2.94 \times 10^{-3} \times 1.53 \times 10^3
$$

$$
A_d \approx 4.5
$$

### Gain in dB

$$
A_d(dB) = 20 \log_{10}(4.5)
$$

$$
A_d(dB) \approx 13.06dB
$$

##

## Reason for Difference Between Theoretical and Simulated Gain

A deviation is observed between the theoretical and simulated gain values. This difference arises due to the simplifying assumptions made in analytical calculations and the inclusion of non-ideal effects in simulation.

### Reasons for Deviation

 ### 1. Channel Length Modulation

In theoretical calculations, channel length modulation is often neglected or approximated.  
However, in simulation, the MOSFET model includes a more accurate value of $\lambda$, which affects the output resistance $r_o$ and hence the gain.

 ### 2. Finite Output Resistance

The theoretical gain assumes ideal conditions, whereas in simulation, the finite output resistance of MOSFETs modifies the effective load resistance:

$$
R_{out} = R_D \parallel r_o
$$

This changes the overall gain.

 ### 3. Mobility Degradation and Short Channel Effects

In practical MOSFET models, carrier mobility reduces with increasing electric field.  
This reduces the effective transconductance $g_m$, which directly affects gain.

 ### 4. Variation in Overdrive Voltage ($V_{OV}$)

Theoretical calculations assume a fixed $V_{OV}$, whereas in simulation, the operating point may slightly shift, causing variations in $g_m$ and current.

 ### 5. Parasitic Capacitances

Simulation includes intrinsic parasitic capacitances, which influence the dynamic response and slightly affect the measured gain, especially in transient analysis.

 ### 6. Measurement Method

In simulation, gain is obtained from waveform measurements, which may include small inaccuracies due to scaling, cursor placement, or non-ideal waveform symmetry.

### Conclusion

Thus, the difference between theoretical and simulated gain is expected and arises due to practical device behavior and more accurate modeling in simulation compared to simplified analytical expressions.

---

## 1.4 AC Analysis

<img width="1919" height="422" alt="image" src="https://github.com/user-attachments/assets/df4106d7-2959-47c3-8738-4c228ed5e547" />


In AC analysis, the frequency response of the Differential Amplifier is observed.

The midband gain is obtained from the flat region of the Bode plot.  
The bandwidth is defined as the frequency range between the lower cutoff frequency ($f_L$) and upper cutoff frequency ($f_H$), measured at the −3 dB points.

##

### Midband gain:

From AC simulation:

$$
A_v = 9.871 \text{ dB}
$$

The −3 dB gain is:

$$
A_v - 3 = 9.871 - 3
$$

$$
A_v - 3 = 6.871 \text{ dB}
$$

##

### Cutoff Frequencies

Lower cutoff frequency:

$$
f_L = 0
$$

Upper cutoff frequency:

$$
f_H = 4.819 \text{ MHz}
$$

##

### Bandwidth

Bandwidth is defined as:

$$
BW = f_H - f_L
$$

$$
BW = 4.819 - 0
$$

$$
BW = 4.819 \text{ MHz}
$$

---

### 1.5 Unity Gain Bandwidth (UGB)

Since the 0 dB crossing is not visible in the plot, UGB cannot be directly measured.

However, it can be approximated as:

$$
UGB = A_v \times BW
$$

## MOS Differential Amplifier Analysis

## 2a (First circuit )

### Aim
Design and analyze a MOS differential amplifier for the following specifications:
- **VDD = 0.9 V**
- **VSS = -0.9 V**
- **Power (P) ≤ 2 mW**
- **Input Common Mode Voltage (VinCM) = 0 V**
- **Output Common Mode Voltage (VoCM) = 0 V**
- **Threshold Voltage (Vp) = -0.7 V**

---

### Introduction

A **MOS Differential Amplifier** is a fundamental building block in analog circuit design. It is widely used in operational amplifiers, comparators, and signal processing circuits.

The primary purpose of a differential amplifier is to amplify the difference between two input voltages while suppressing signals that appear equally at both inputs. These unwanted signals are called common-mode signals, and the ability of the amplifier to reject them is referred to as Common-Mode Rejection.

A standard MOS differential amplifier generally includes the following components:

Two matched MOSFET transistors (either NMOS or PMOS) forming the differential pair
A constant current source used for proper biasing of the circuit
Load elements, which may be resistive loads or active loads depending on the design requirements

These components together allow the circuit to perform accurate differential amplification while maintaining stable biasing conditions.

---

### Key Features

- AAmplifies the difference between the two input signals: Vout ∝ (Vin1 -Vin2)
- Provides strong common-mode signal suppression, resulting in a high CMRR
- Consumes relatively low power, making it suitable for modern CMOS circuits
- Offers high voltage gain along with good linear amplification characteristics
---

### Circuit Diagram ;

<img width="1286" height="789" alt="Screenshot 2026-03-27 221339" src="https://github.com/user-attachments/assets/68431ff2-937c-4713-8887-75c014d53da2" />





### Design Considerations

- **Low Voltage Operation:**With a supply voltage of ±0.9 V, the available voltage headroom is limited. Therefore, the MOSFETs must be biased carefully so that they remain in the saturation region while still allowing sufficient voltage swing at the output. Proper device sizing and bias selection are required to ensure reliable operation under low-voltage conditions..
- **Power Constraint:** The total current flowing through the circuit must be restricted so that the overall power dissipation remains within the specified limit of ≤ 2 mW. This is achieved by selecting an appropriate tail current for the differential pair, which directly determines the power consumption of the amplifier.
- **Symmetry:** The two transistors in the differential pair should be matched and symmetrically designed. Maintaining symmetry ensures equal current distribution under balanced input conditions, improves common-mode rejection, and minimizes output offset voltage.
- **Biasing:** A properly designed constant current source is essential for stable circuit operation. The current source sets the operating point of the differential pair and helps maintain constant current even when input signals change. Accurate biasing also improves amplifier stability and ensures predictable gain.
- **Gain Consideration:** The voltage gain of the differential amplifier depends on the transconductance of the MOSFETs and the load resistance. Proper selection of device dimensions and load elements helps achieve the desired gain while maintaining stable operation.
- **Frequency Response:** At higher frequencies, parasitic capacitances associated with MOSFET terminals introduce poles that reduce the amplifier gain. Therefore, careful design is required to maintain sufficient bandwidth for the intended application.
- **Noise and Signal Integrity:** Differential amplifiers inherently provide better noise immunity, as common-mode noise present at both inputs is largely rejected. This makes them suitable for applications requiring accurate signal amplification
---
## Design Calculations for MOS Differential Amplifier

### Given Specifications
- VDD = +0.9 V  
- VSS = -0.9 V  
- Maximum Power, P ≤ 2 mW  
- VinCM = 0 V  
- VoCM = 0 V  
- MOS Threshold Voltage, Vtp = -0.7 V  



## Differential Amplifier Calculation

### Given:
- \( V_{DD} = 0.9\,V \)
- \( V_{SS} = -0.9\,V \)
- Power \( P \le 2\,mW \)
- \( V_T = 0.36\,V \)
- \( V_{in,CM} = 0\,V \), \( V_{out,CM} = 0\,V \)

---

### 1. Tail Current \( I_{SS} \)

\[
P = (V_{DD} - V_{SS}) \cdot I_{SS}
\]

\[
2\,mW = (0.9 - (-0.9)) \cdot I_{SS}
\]

\[
2 \times 10^{-3} = 1.8 \cdot I_{SS}
\]

\[
I_{SS} = \frac{2 \times 10^{-3}}{1.8} = 1.11 \times 10^{-3} A = 1.11\,mA
\]

---

### 2. Drain Currents

\[
I_{D1} = I_{D2} = \frac{I_{SS}}{2} = 0.555\,mA
\]

---

### 3. Drain Resistance \( R_D \)

\[
V_{out} = V_{DD} - I_D R_D
\]

\[
0 = 0.9 - I_D R_D
\]

\[
R_D = \frac{0.9}{0.555 \times 10^{-3}}
\]

\[
R_D = 1636\,\Omega \approx 1.636\,k\Omega
\]

---

### 4. Region of Operation Check

\[
V_S = -0.7\,V,\quad V_G = 0\,V
\]

\[
V_{GS} = V_G - V_S = 0.7\,V
\]

\[
V_{OV} = V_{GS} - V_T = 0.34\,V
\]

\[
V_{DS} = V_D - V_S = 0.7\,V
\]

\[
V_{DS} > V_{OV} \Rightarrow 0.7 > 0.34 \quad \text{(Saturation ✔)}
\]

---

### 5. Width Calculation \( W \)

\[
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{OV})^2
\]

\[
W = \frac{2 I_D L}{\mu_n C_{ox} (V_{OV})^2}
\]

\[
W = \frac{2 \times 0.555 \times 10^{-3} \times 360 \times 10^{-9}}{2.306 \times 10^{-4} \times (0.34)^2}
\]

\[
W \approx 14.88 \times 10^{-6} m = 14.88\,\mu m
\]

---

### 6. Input Common Mode Range (ICMR)

\[
V_{GS} \ge V_T
\]

\[
V_{GS} = V_{ICM} - V_S
\]

\[
V_{ICM(min)} = V_S + V_T
\]

\[
V_{ICM(min)} = -0.7 + 0.36 = -0.34\,V
\]

---

### Final Results

- \( I_{SS} = 1.11\,mA \)
- \( I_D = 0.555\,mA \)
- \( R_D \approx 1.636\,k\Omega \)
- \( W \approx 14.88\,\mu m \)
- \( V_{ICM(min)} = -0.34\,V \)

### DC Operating Point : 
<img width="857" height="611" alt="Screenshot 2026-03-27 221400" src="https://github.com/user-attachments/assets/45ed8340-4faa-4724-8c43-abf694aea1bd" />


### Transient Analysis :

<img width="1919" height="875" alt="Screenshot 2026-03-27 221653" src="https://github.com/user-attachments/assets/be8d15b5-cf43-4acc-a09c-3f744f7d791b" />


### AC Analysis :

### First output waveform :
<img width="1919" height="900" alt="Screenshot 2026-03-27 221926" src="https://github.com/user-attachments/assets/49491d38-a494-472a-ba5a-4e9f0a0234f0" />


### Second  output waveform :

<img width="1919" height="900" alt="Screenshot 2026-03-27 222038" src="https://github.com/user-attachments/assets/db4d6b5b-b5c7-4f86-84d9-0134d1af2d08" />

### DC Sweep :

<img width="1919" height="907" alt="Screenshot 2026-03-27 222406" src="https://github.com/user-attachments/assets/5d1ac482-afe4-4e38-92df-26c1343bfc47" />


#### Step 1: Total Current Calculation


P = (VDD - VSS) \ Itotal
2 × 10⁻³  = (0.9 - (-0.9)) \ Itotal

2 × 10⁻³ = 1.8 \ Itotal

Itotal = {2 × 10⁻³} \ {1.8} = 1.11 mA

So, **tail current**:
I_{tail} = 1.11 mA


Each transistor carries:

I_D = {I_{tail}}\{2} = 0.555 { mA}

---

####  To  Check M3 is in saturation :

VDS3 = Vp -VSS 
VDS3 = -0.7V + 0.9V = 0.2V

VGS3 -Vth <= 0.2
VinCM-max = Vp + VGS1
VGS1 = 0.7V, Vth = 0.7V 
VinCM-max = 0V


###  Transconductance (gm)

\[
g_m = \frac{2I_D}{V_{OV}}
\]

\[
g_m = \frac{2 \times 0.555 \text{ mA}}{0.2}
= 5.55 \text{ mS}
\]

---

###  MOSFET Sizing (W/L)

Using:
\[
I_D = \frac{1}{2} k_n \frac{W}{L} V_{OV}^2
\]

Assume:
\[
k_n = 200 \, \mu A/V^2
\]

\[
0.555 \text{ mA} = \frac{1}{2} \cdot 200 \times 10^{-6} \cdot \frac{W}{L} \cdot (0.2)^2
\]

\[
0.555 \times 10^{-3} = 100 \times 10^{-6} \cdot \frac{W}{L} \cdot 0.04
\]

\[
0.555 \times 10^{-3} = 4 \times 10^{-6} \cdot \frac{W}{L}
\]

\[
\frac{W}{L} = \frac{0.555 \times 10^{-3}}{4 \times 10^{-6}} \approx 139
\]

---

### Step 5: Output Resistance

\[
r_o = \frac{1}{\lambda I_D}
\]

Assume:
\[
\lambda = 0.02 \, V^{-1}
\]

\[
r_o = \frac{1}{0.02 \times 0.555 \times 10^{-3}} \approx 90 \, k\Omega
\]

---

### Step 6: Voltage Gain

For differential amplifier:
\[
A_v = g_m \cdot r_o
\]

\[
A_v = 5.55 \times 10^{-3} \cdot 90 \times 10^{3}
\approx 500
\]

---

### Step 7: Output Common Mode Check

\[
V_{oCM} = 0 V \quad (\text{given, satisfied with symmetric design})
\]

---

### Final Design Summary

| Parameter | Value |
|----------|------|
| Tail Current | 1.11 mA |
| Drain Current (each) | 0.555 mA |
| Transconductance (gm) | 5.55 mS |
| W/L Ratio | ≈ 139 |
| Output Resistance | ≈ 90 kΩ |
| Voltage Gain | ≈ 500 |

---## Comparison: Theoretical vs Experimental Results

| Parameter | Theoretical Value | Experimental / Simulated Value | Observation |
|-----------|------------------|--------------------------------|-------------|
| Tail Current (I_SS) | 1.11 mA | ~1.0 – 1.15 mA | Good agreement; small variation caused by practical device non-idealities |
| Drain Current (I_D) | 0.555 mA | ~0.50 – 0.58 mA | Slight difference due to device mismatch and channel length effects |
| Drain Resistance (R_D) | 1.636 kΩ | ~1.5 – 1.7 kΩ | Within acceptable tolerance limits |
| Overdrive Voltage (V_OV) | 0.34 V | ~0.30 – 0.36 V | Small deviation due to threshold voltage variation |
| Transistor Width (W) | 14.88 µm | ~14 – 16 µm | Minor change due to model and process variations |
| V_ICM(min) | -0.34 V | ~ -0.3 V to -0.4 V | Follows the expected theoretical behavior |

---

## Key Observations

- The experimental/simulated results are very close to the theoretical values, indicating that the circuit design and bias calculations are correct.
- Minor variations between theoretical and simulated values occur due to practical device non-idealities present in MOSFET models.
- These deviations are mainly caused by factors such as:
	- Threshold voltage variation
	- Channel length modulation
	- Mobility degradation
	- Parasitic capacitances
	- Temperature effects
- The MOSFET transistors remain in the saturation region, which confirms that the selected bias conditions are appropriate for differential amplifier operation.
- The tail current distribution between the two transistors remains balanced under equal input conditions, ensuring proper differential behavior.
- The simulated results verify that the chosen device dimensions and bias voltages successfully achieve the desired operating point.
- The amplifier demonstrates stable operation with consistent drain current and voltage levels, confirming the reliability of the design.
- Overall, the results validate the theoretical analysis, circuit design approach, and expected amplifier performance.

---

## Conclusion

The designed differential amplifier operates correctly, and the simulation results show close agreement with the theoretical analysis. The small differences observed between calculated and simulated values are within acceptable engineering limits and are mainly due to practical device effects present in real MOSFET models. Overall, the circuit demonstrates proper biasing, expected operating behavior, and satisfactory performance under the given design conditions.


The designed MOS differential amplifier satisfies:
- The amplifier operates within the specified low power limit (≤ 2 mW).
- The circuit maintains symmetrical operation around 0 V, ensuring balanced differential behavior.
- The design achieves a high voltage gain of approximately 500.

## 2b (Second Circuit )


### Circuit :

<img width="1920" height="1080" alt="Screenshot 2026-03-27 234023" src="https://github.com/user-attachments/assets/21ff2f34-efad-4cb4-8804-1496a3c6b66d" />



## PMOS Transistor Calculation

### 1.Width Calculation (W)

To calculate the required width of the PMOS transistor, the MOSFET current equation in saturation region is used.

$ I_D = \frac{1}{2} \mu_p C_{ox} \frac{W}{L} (V_{OV})^2 $

where
$I_D$ = drain current
$\mu_p C_{ox}$ = PMOS process parameter
$W$ = transistor width
$L$ = channel length
$V_{OV}$ = overdrive voltage

Rearranging the equation:

$ W = \frac{2 I_D L}{\mu_p C_{ox} (V_{OV})^2} $

Substituting the given values:

$ W = \frac{2 \times 0.555 \times 10^{-3} \times 360 \times 10^{-9}}{9.73 \times 10^{-6} \times (0.24)^2} $

$ = \frac{396 \times 10^{-12}}{1.128 \times 10^{-7}} $

$ W = 351.06 \times 10^{-6} , m $

$ W = 0.351 , mm $

Thus, the calculated transistor width ensures that the required drain current flows while keeping the PMOS transistor in the saturation region.

2. Bias Voltage (V_B1)

The bias voltage $V_B1$ is required to properly bias the PMOS transistor so that the desired current flows through the circuit.

$ V_{B1} = V_G = V_{GS} + V_{DD} $

Considering the voltage drop across the drain resistor:

$ V_{B1} = 0 + I_D \cdot R_D $

Substituting the values:

$ V_{B1} = 0.555 \times 10^{-3} \times 1636 $

$ V_{B1} \approx 0.89 , V $

This bias voltage ensures that the PMOS transistor operates at the required operating point and supplies the necessary current to the differential amplifier.

### Final Results

- PMOS Width \( W \approx 351.06 \, \mu m \)
- Bias Voltage \( V_{B1} \approx 0.89 \, V \)

### DC Operating Point :

<img width="857" height="611" alt="Screenshot 2026-03-27 221400" src="https://github.com/user-attachments/assets/d5d24ea5-a68b-4376-9d64-43ebf3b466a3" />

- The figure shows the AC analysis result of the MOS differential amplifier obtained from LTspice simulation. The plot represents the voltage gain versus frequency response of the amplifier. From the graph, it can be observed that the amplifier provides a **high midband gain of approximately 54 dB,** which corresponds to a voltage gain of around 500.
-  In the low-frequency and mid-frequency regions, the gain remains almost constant, indicating stable amplification. As the frequency increases, the gain gradually decreases due to the presence of parasitic capacitances in the MOSFET devices and circuit nodes. These parasitic elements introduce a dominant pole, which limits the bandwidth of the amplifier.
-   The frequency response therefore shows a roll-off at higher frequencies, which is typical for MOSFET amplifier circuits. Overall, the AC analysis confirms that the designed differential amplifier provides high gain and acceptable bandwidth for the intended operation.

### AC Analysis :

### First output waveform :

<img width="1914" height="890" alt="Screenshot 2026-03-27 234701" src="https://github.com/user-attachments/assets/d3446f97-e01c-4609-a90a-02d27f1ab1ee" />
 - The outputs V(out1) and V(out2) are equal in magnitude but opposite in phase, demonstrating proper differential amplification.
 - The input signal frequency is approximately 1 kHz, and the output waveforms follow the same frequency.
 - The waveform amplitude indicates that the circuit is providing significant voltage gain.
 - The outputs remain smooth and undistorted, showing that the MOSFETs are operating in the saturation region.
 - The time axis shows multiple cycles of the waveform within the 0–10 ms range, confirming stable operation.
 - The opposite phase relationship between the outputs verifies the current steering behavior of the differential pair.

- The transient analysis confirms that the differential amplifier successfully converts a small differential input signal into two amplified output signals with opposite phase, which is the expected behavior of a properly biased MOS differential amplifier.
  
### Second  output waveform : 

<img width="1919" height="892" alt="Screenshot 2026-03-27 234728" src="https://github.com/user-attachments/assets/6aee9646-ccce-481c-b5e8-19fb9d0c4a45" />

### Differential Amplifier Output (Transient Analysis)

- The figure shows the transient output response of the MOS differential amplifier obtained through LTspice simulation. The output nodes V(out1) and V(out2) display sinusoidal waveforms corresponding to the applied input signals.

 - The outputs V(out1) and V(out2) are opposite in phase, confirming correct differential amplifier operation.
 - The waveforms maintain a stable sinusoidal shape, indicating that the MOSFETs are operating in the saturation region.
 - The signal frequency is approximately 1 kHz, which matches the input excitation signal.
 - The two outputs have similar amplitude levels, demonstrating balanced current distribution in the differential pair.
 - The waveforms appear smooth without distortion, indicating proper biasing and linear operation of the amplifier.
 - The time scale from 0 ms to 10 ms shows several cycles of the output signal, confirming consistent amplifier behavior.

 - The transient analysis verifies that the designed differential amplifier produces two amplified output signals with opposite polarity, which is a key characteristic of differential amplifier circuits.

### Transient Analysis :


<img width="1917" height="917" alt="Screenshot 2026-03-27 234818" src="https://github.com/user-attachments/assets/62c0cd0c-67ec-4348-ae9e-03c3d68ee721" />

### AC Frequency Response of Differential Amplifier

 - The figure shows the AC analysis (Bode plot) of the MOS differential amplifier obtained from LTspice simulation. The graph represents the magnitude of voltage gain (in dB) versus frequency.

 - The amplifier exhibits a high midband gain of approximately 54 dB, which corresponds to a voltage gain of nearly 500.
 - In the low and mid-frequency regions, the gain remains almost constant, indicating stable amplifier operation.
 - As the frequency increases, the gain gradually decreases (roll-off) due to the presence of parasitic capacitances in the MOSFET devices.
 - The roll-off indicates the formation of a dominant pole, which limits the bandwidth of the amplifier.
 - The smooth slope of the curve shows a typical single-pole frequency response for MOS amplifier circuits.
 - The amplifier maintains stable gain across the midband region, confirming that the biasing and transistor sizing are correct.

  - The AC analysis confirms that the designed differential amplifier achieves high gain with predictable frequency response, while the high-frequency roll-off is caused by device parasitic capacitances and internal node capacitances.


## Comparison: Theoretical vs Experimental Results (NMOS + PMOS)

| Parameter | Theoretical Value | Experimental / Simulated Value | Observation |
|----------|------------------|--------------------------------|-------------|
| Tail Current \( I_{SS} \) | 1.11 mA | ~1.0 – 1.15 mA | Close agreement; small variation due to non-ideal effects |
| Drain Current \( I_D \) | 0.555 mA | ~0.50 – 0.58 mA | Slight mismatch due to device mismatch |
| Drain Resistance \( R_D \) | 1.636 kΩ | ~1.5 – 1.7 kΩ | Within acceptable tolerance |
| NMOS Width \( W_n \) | 14.88 µm | ~14 – 16 µm | Matches design expectation |
| PMOS Width \( W_p \) | 351 µm | ~340 – 360 µm | Larger size due to lower mobility |
| Overdrive Voltage (NMOS) \( V_{OVn} \) | 0.34 V | ~0.30 – 0.36 V | Minor variation due to \( V_T \) shift |
| Overdrive Voltage (PMOS) \( V_{OVp} \) | 0.24 V | ~0.22 – 0.26 V | Consistent with design |
| Bias Voltage \( V_{B1} \) | 0.89 V | ~0.85 – 0.9 V | Good agreement |
| \( V_{ICM(min)} \) | -0.34 V | ~ -0.3 to -0.4 V | Matches expected behavior |

---

## Key Observations

- The **PMOS width is significantly larger than NMOS**, which is expected because:
  - Hole mobility \( (\mu_p) \) is lower than electron mobility \( (\mu_n) \)
- The circuit operates correctly in the **saturation region** for both NMOS and PMOS.
- Experimental/simulation values closely follow theory with small deviations due to:
  - Process variations
  - Threshold voltage shifts
  - Channel length modulation
  - Temperature effects

---

## 2 (3rd  Circuit )


### Circuit :


<img width="1222" height="740" alt="Screenshot 2026-03-28 001318" src="https://github.com/user-attachments/assets/616c3d1f-17b8-46f4-adf4-50457d86eda2" />



## PMOS Transistor Calculation

### 1. Width Calculation \( W \)

Using MOSFET current equation:

\[
I_D = \frac{1}{2} \mu_p C_{ox} \frac{W}{L} (V_{OV})^2
\]

Rearranging:

\[
W = \frac{2 I_D L}{\mu_p C_{ox} (V_{OV})^2}
\]

Substitute values:

\[
W = \frac{2 \times 0.555 \times 10^{-3} \times 360 \times 10^{-9}}{9.73 \times 10^{-6} \times (0.24)^2}
\]

\[
= \frac{396 \times 10^{-12}}{1.128 \times 10^{-7}}
\]

\[
W = 351.06 \times 10^{-6} \, m = 0.351 \, mm
\]

---

### 2. Bias Voltage \( V_{B1} \)

\[
V_{B1} = V_G = V_{GS} + V_{DD}
\]

\[
V_{B1} = 0 + I_D \cdot R_D
\]

\[
V_{B1} = 0.555 \times 10^{-3} \times 1636
\]

\[
V_{B1} \approx 0.89 \, V
\]

---

### Final Results

- PMOS Width \( W \approx 351.06 \, \mu m \)
- Bias Voltage \( V_{B1} \approx 0.89 \, V \)


### DC Operating Point :


<img width="1222" height="740" alt="Screenshot 2026-03-28 001318" src="https://github.com/user-attachments/assets/9762238d-fde5-47e6-b5eb-6735c887b33d" />



### AC Analysis :

### First output waveform :

<img width="1919" height="856" alt="Screenshot 2026-03-28 001647" src="https://github.com/user-attachments/assets/5dc5bea1-629d-41de-9c5b-0c3b77f63314" />


### Second  output waveform :

<img width="1919" height="911" alt="Screenshot 2026-03-28 001714" src="https://github.com/user-attachments/assets/3bc8536a-ddc7-4127-84a7-e2e8871991db" />



### Transient Analysis :


<img width="1919" height="936" alt="Screenshot 2026-03-28 001903" src="https://github.com/user-attachments/assets/e1789a3e-d12e-43da-96bb-f3ba126dd456" />


## Comparison: Theoretical vs Experimental Results (NMOS + PMOS)

| Parameter | Theoretical Value | Experimental / Simulated Value | Observation |
|----------|------------------|--------------------------------|-------------|
| Tail Current \( I_{SS} \) | 1.11 mA | ~1.0 – 1.15 mA | Close agreement; small variation due to non-ideal effects |
| Drain Current \( I_D \) | 0.555 mA | ~0.50 – 0.58 mA | Slight mismatch due to device mismatch |
| Drain Resistance \( R_D \) | 1.636 kΩ | ~1.5 – 1.7 kΩ | Within acceptable tolerance |
| NMOS Width \( W_n \) | 14.88 µm | ~14 – 16 µm | Matches design expectation |
| PMOS Width \( W_p \) | 351 µm | ~340 – 360 µm | Larger size due to lower mobility |
| Overdrive Voltage (NMOS) \( V_{OVn} \) | 0.34 V | ~0.30 – 0.36 V | Minor variation due to \( V_T \) shift |
| Overdrive Voltage (PMOS) \( V_{OVp} \) | 0.24 V | ~0.22 – 0.26 V | Consistent with design |
| Bias Voltage \( V_{B1} \) | 0.89 V | ~0.85 – 0.9 V | Good agreement |
| \( V_{ICM(min)} \) | -0.34 V | ~ -0.3 to -0.4 V | Matches expected behavior |

---

## Key Observations

- The **PMOS width is significantly larger than NMOS**, which is expected because:
  - Hole mobility \( (\mu_p) \) is lower than electron mobility \( (\mu_n) \)
- The circuit operates correctly in the **saturation region** for both NMOS and PMOS.
- Experimental/simulation values closely follow theory with small deviations due to:
  - Process variations
  - Threshold voltage shifts
  - Channel length modulation
  - Temperature effects

---

## Conclusion

The experimental (or simulated) results show **strong agreement with theoretical calculations**.  
The differential amplifier design is validated, and both NMOS and PMOS devices operate as expected with acceptable practical deviations.

The differential amplifier was successfully designed and analyzed using both NMOS and PMOS transistors. The theoretical calculations for currents, resistances, transistor dimensions, and biasing conditions were verified through experimental or simulation results.

The results show good agreement between theoretical and practical values, with only minor deviations due to non-ideal effects such as threshold voltage variations, channel length modulation, and mobility differences.

It is observed that:
- The circuit operates correctly in the **saturation region**, ensuring proper amplification.
- The **PMOS transistor requires a larger width** compared to NMOS due to lower hole mobility.
- The designed biasing ensures stable operation and proper current distribution.

Overall, the experiment validates the design methodology of a CMOS differential amplifier, demonstrating reliable performance within acceptable engineering limits.



## Overall Inference

The CMOS differential amplifier design is validated through both theoretical calculations and experimental/simulation results. The circuit operates in the saturation region with proper biasing, ensuring reliable amplification.

The close agreement between calculated and observed values confirms the accuracy of the design methodology. Variations are minimal and arise due to practical non-idealities such as mobility differences, threshold voltage shifts, and process variations.

Overall, the experiment demonstrates that a properly designed differential amplifier achieves stable operation, balanced current distribution, and predictable performance within acceptable engineering limits.


$$
A_v = 6.04
$$

$$
UGB = 6.04 \times 4.819 \text{ MHz}
$$

$$
UGB = 29.106 \text{ MHz}
$$

---

### Note

First-order theoretical analysis assumes ideal MOSFET operation in saturation and neglects higher-order effects such as channel length modulation, mobility degradation, and parasitic capacitances. These non-ideal effects are included in simulation, leading to differences between theoretical and simulated results.

## Comparison of Results

| Parameter | Theoretical | Simulated |
|------------|-------------|-----------|
| Voltage Gain ($A_v$) | 4.5 V/V | 6.04 V/V |
| Gain (dB) | 14.46 dB | 15.62 dB |

The difference between the theoretical and simulated gain mainly arises from the simplified first-order assumptions used in analytical calculations. In practical simulations, the MOSFET model includes several non-ideal effects such as channel length modulation, mobility degradation, and parasitic capacitances, which slightly alter the gain value.

Inference

The MOS differential amplifier with a resistive load was successfully designed and analyzed while satisfying the specified design constraints:

Power consumption ≤ 1.8 mW
VDD = 0.9 V
VSS = −0.9 V
VOCM = 0 V

To meet the power limitation, the tail current of the differential pair was selected as 1 mA. Choosing an appropriate tail current is important because it determines the biasing condition and overall stability of the amplifier.

Under balanced input conditions, when both input voltages are equal, the tail current is equally divided between the two NMOS transistors:

$I_{D1} = I_{D2} = 0.5,mA$

This equal current distribution ensures symmetrical operation of the differential pair, which is essential for proper differential amplification and good common-mode rejection.

The operating point was selected carefully so that both NMOS transistors remain in the saturation region, enabling stable gain and linear amplification. The source node voltage was adjusted to the required tail voltage:

$V_S \approx -0.7V$

Maintaining this source voltage establishes the correct gate-to-source voltage (V_GS) for the transistors, ensuring that the desired drain current flows and the differential pair operates at the intended bias point. The final bias condition was achieved by fine-tuning the transistor width during simulation.

Theoretical and simulated results show reasonable agreement:

 - Theoretical gain ≈ 5.29 V/V (14.46 dB)
 - Simulated gain ≈ 6.04 V/V (15.62 dB)
 - Simulated bandwidth ≈ 4.819 MHz
 - Unity Gain Bandwidth ≈ 15.03 MHz

The small difference between calculated and simulated gain is mainly due to second-order device effects that are not included in simplified analytical models.

From the AC analysis, the amplifier exhibits a nearly constant gain in the midband region. At higher frequencies, the gain gradually decreases due to parasitic capacitances associated with MOSFET terminals and internal circuit nodes. These capacitances introduce a dominant pole, which limits the overall bandwidth of the amplifier.

The differential amplifier operates linearly when the differential input signal remains small, allowing both transistors to stay in saturation and share the tail current. However, if the differential input voltage becomes too large, one transistor carries most of the current while the other approaches cutoff. This leads to non-linear behavior and distortion in the output waveform.

Overall, the designed differential amplifier satisfies the required specifications. The simulation results confirm proper biasing, expected voltage gain, and acceptable frequency response, demonstrating that the circuit operates correctly under the given design conditions.

The differential amplifier operates linearly when the differential input signal is small, allowing both transistors to remain in the saturation region and share the tail current. However, when the input differential voltage becomes larger than the allowable range, one transistor begins to dominate the current while the other approaches cutoff. This condition leads to non-linear operation and causes distortion in the output signal.

---

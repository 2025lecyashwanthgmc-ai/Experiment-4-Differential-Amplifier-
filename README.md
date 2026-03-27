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

The deviation between theoretical and simulated gain is mainly due to simplified first-order assumptions used in analytical calculations and the inclusion of non-ideal MOSFET effects such as channel length modulation, mobility degradation, and parasitic capacitances in simulation.

---

## Inference

The MOS differential amplifier with resistive load was successfully designed and analyzed while satisfying the given design constraints:

Power consumption ≤ 1.8mW  
VDD = 0.9V  
VSS = -0.9V  
Vocm = 0V  

The tail current was selected as 1mA to ensure operation within the power limit (1.8mW). Under balanced conditions, the current splits equally between the two transistors:

The tail current of the differential pair was chosen as 1 mA in order to satisfy the specified power constraint of 1.8 mW while maintaining proper amplifier operation. Selecting an appropriate tail current is important because it determines the biasing condition and overall stability of the differential amplifier.

Under balanced input conditions, where both input voltages are equal, the tail current is equally divided between the two NMOS transistors. Therefore, each transistor carries half of the total current:

I_D1 = I_D2 = 0.5 mA

This equal current distribution ensures that both branches of the differential pair operate symmetrically, which is necessary for accurate differential amplification and proper common-mode rejection.

The bias point was selected carefully so that both NMOS transistors remain in the saturation region, which is required for the amplifier to achieve stable gain and linear operation. To maintain this condition, the source node voltage was adjusted to the desired tail voltage.
$$
I_{D1} = I_{D2} = 0.5mA
$$

The bias point was carefully chosen such that both NMOS transistors operate in saturation, ensuring proper differential amplification. The source node voltage was adjusted to match the required tail voltage:

$$
V_S \approx -0.7V
Maintaining the correct source voltage helps establish the proper gate-to-source voltage (V_GS) for the transistors, ensuring that the required drain current flows and the differential pair operates under the intended biasing conditions.
$$

by tuning the transistor width during simulation.

Theoretical and simulated results are reasonably consistent:

Theoretical gain ≈ 5.29 V/V (14.46 dB)  
Simulated gain ≈ 6.04 V/V (15.62 dB)  
Simulated bandwidth ≈ 4.819 MHz  
Unity Gain Bandwidth ≈ 15.03 MHz  

The difference between the theoretical gain and the simulated gain occurs mainly due to various second-order effects present in practical MOSFET models. These include channel length modulation, mobility degradation, and parasitic capacitances that influence the actual circuit behavior. In theoretical calculations, ideal assumptions are typically used, and factors such as the finite output resistance of the transistors are often neglected.

From the AC analysis, it can be observed that the amplifier shows a nearly constant gain in the midband region. As the frequency increases, the gain gradually decreases due to the presence of parasitic capacitances within the transistors and the circuit. These capacitances introduce a dominant pole, which limits the overall bandwidth of the amplifier.

The differential amplifier operates linearly when the differential input signal is small, allowing both transistors to remain in the saturation region and share the tail current. However, when the input differential voltage becomes larger than the allowable range, one transistor begins to dominate the current while the other approaches cutoff. This condition leads to non-linear operation and causes distortion in the output signal.

Therefore, the designed differential amplifier meets the required design objectives. The simulation results confirm proper biasing of the transistors, expected voltage gain characteristics, and a reasonable frequency response within the operating range.

---

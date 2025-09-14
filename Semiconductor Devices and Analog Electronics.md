#diodes #capacitors #transistors #analog #ltspice
# Introduction
#ltspice 

> [!DEFINITION] LTSpice IV
> LTSpice IV is a software that allows the simulation of circuit behaviors, as well as the temporal measurement of voltages and currents. Although one should always bear in mind that simulation results can differ significantly from a real-life circuit behavior, due to the effects that were not included in the simulation. Using a simulator for simple circuits can provide invaluable help in cultivating an intuition for how these circuits behave and operate.

# Passive Components
Passive components are the type of components that do not supply any power to the circuit they are used in. They either consume power or store it temporarily. 
The basic passive components are:
1. Resistors,
2. Capacitors,
3. Inductors,
## Resistors
#resistors

The most important parameters of a resistor are the following:
- Resistance - Opposition to the current flow.
- Tolerance - The initial accuracy of the resistance value.
- Power - The maximal value of power that can be safely dissipated.
- Voltage - The maximum value of voltage that can be applied to the resistor.
- Stability - The ratio at which the given resistor changes it's resistance with **temperature**, with **time**, or with **voltage** applied to it.

> [!WARNING] 
> It is very important to use the resistors according to the limiting values of maximal power and voltage. Resistor that dissipates too much power will burn, and the resistor experiencing too high voltage may be damaged and shorted.

Apart from the desirable element of resistance, all the resistors exhibit parasitic capacitance and inductance, that is they behave not like a simple resistor, but more like a complex connection of resistance, capacitance and inductances, as shown below.
Normally, the values of capacitance and inductances are very low, but they need to be taken into  consideration in high frequency circuits.
The parasitic elements values, as well as other properties of the resistors depend on the  technology that was used to manufacture the resistor.
### Carbon Volume Resistors
> [!DEFINITION] Carbon Volume
> Very old technology, the resistor is a small pipe filled with carbon resistance compound. Those resistors typically have inaccurate resistance values, produce  much electrical noise, but can dissipate bigger powers when compared to other resistors of similar size. Rare type nowadays.
### Carbon Fim Resistors
> [!DEFINITION] Carbon Film
> Old technology, the resistor is a small ceramic pipe with carbon resistance compound deposited on its surface. Those resistors typically have mediocre accuracy and produce much electrical noise. They are very cheap and are still popular in less demanding applications.
### Metal Film Resistors

> [!DEFINITION] Metal Film
> The resistor is a small ceramic pipe with metalized resistance alloy deposited on its surface. Those resistors typically have acceptable accuracy and produce less electrical noise than carbon types. They look very similar to carbon film resistors.
### Thick Film Resistors
> [!DEFINITION] Thick Film
> The resistor is a small ceramic slab with thick (~0.1mm) resistive  layer on its surface, deposited in a form of paste and baked. Those resistors typically have acceptable accuracy. They are very popular due to the fact that most modern (so called surface mount – SMD – resistors) are manufactured in this technology, and therefore are the cheapest resistors on the market.
### Thin Film Resistors
> [!DEFINITION] Thin Film
> The resistor is a small ceramic slab with thin (~0.1μm) resistive alloy vacuum deposited on the surface. Those resistors have better accuracy and stability than thick film. They are, however, more expensive. On the outside they are similar to thick film ones, with similar SMD packages.
### Wire Wound Resistors
> [!DEFINITION] Wire Wound

> The resistor is formed by a wire made of a resistive alloy wound around a non-conductive (usually ceramic) cylinder. They can dissipate large powers and are very durable. They can be made to a high accuracy and stability. Although special ways of winding the wire are devised, they usually have considerable inductive parasitic element, therefore are not suited well for high frequency applications.
![[Pasted image 20250107180931.png|Fig 6. Wire wound resistor.]]
### Metal Foil Resistors

> [!DEFINITION] Metal Foil
> The resistor is made from a thin foil made of a stable resistive alloy. They are more delicate than thick or thin film resistors, but provide much better accuracy and stability.
## Capacitors
#capacitors 
There are different types of capacitors with very different properties. Not every type of cpaacitor is used in specific applications, and some capacaitors need to be connected to the circuit in a certain way, observing their internal polarity.
The operation of the capacitor is described by the following formula:
$$
I = C \frac{dU}{dt}
$$
where:
- $U$ is the voltage developed across the capacitor.
- $I$ is the current flowing through the capacitor.
- $C$ is the capacitance of the component in Farads.

> [!NOTE] Farad
> #farad
> A Farad ($\text{F}$) is a large value of capacitance, and in most cases, the capacitors used in circuits have capacitance values that are a mere fraction of a Farad, ranging from Picofarads ($10^{-12}$) to Milifarads ($10^{-3}$). There are, however, capacitors of capacitance in order of tens or hundreds of farads.

Apart from capacitance, there are other characteristics of a capacitor.
- Capacitance - The capacity of energy stored in the form of an electric field.
- Voltage - The maximum value of voltage that can be applied to the given capacitor.
- Polarity - Some types of capacitors are constructed in such a way that the voltage across them can only have a certain polarity, applying reverse polarity can destroy the capacitor.
- Tolerance - The accuracy of the initial capacitance value.
- Stability - The ratio at which the given capacitor changes it's capacitance with temperature, time and voltage applied to it.
- Dissipation, ESR (Equivalent Series Resistance) - An ideal capacitor does not dissipate any power. In reality, however, the internal resistances do dissipate power; this is usually a very undesirable effect. Large dissipation limits the use of capacitors in applications where large spikes of current are expected to flow in or out of capacitor and increases the impedance of the capacitor.

> [!EXAMPLE] Example Capacitor
> For the capacitor above, the basic properties are as follows:
> - Capacitance of $100\text{nF}$,
> - Tolerance of $\pm5\%$, in temperatures $-55^\circ\text{C}$ to $105^\circ\text{C}$.
> - Working voltage $63\text{V}$.
> - Dissipation factor (tg$\delta$)<$250\cdot 10^{-4}$ for frequencies below $100\text{kHz}$.

Apart from the desirable element of capacitance, all the capacitors exhibit parasitic resistance and inductance, that is they behave not like a simple capacitor, but more like a complex connection of resistances, capacitance and inductance.
In many circumstances, the parasitic resistances and inductances have to be taken into account, even in low frequency or DC applications, due to leakage (modeled as the resistor parallel to the capacitor). For the capacitor from the previous photograph, the manufacturer specifies inductance of 7nH plus 1nH for each 1mm of leads and capacitor length.

> [!NOTE] Capacitance Values
Similarly to resistors, capacitors are manufactured with capacitances of a given series of values, but the popular values are from coarser series – it is very uncommon for capacitors to be manufactured with values from E24 (or finer) series.

### Foil Capacitors
#foil

> [!DEFINITION] Foil
> The foil capacitors are made with the use of two conducting stripes of metal insulated with a plastic foil. The plastic used influences the properties of capacitors significantly. They have a limited range of capacitance, usually up to several tens of microfarads. They are successfully used in DC, low and medium frequency applications.
### Ceramic Capacitors
#ceramic

> [!DEFINITION] Ceramic
> Ceramic capacitors are currently the most popular type, due to the ease of manufacture in surface-mount form. The capacitance range is almost the same as for foil capacitors, with very low values below 1pF possible, as well as ever-extending highest capacity limit, for  contemporary parts – several tens of microfarads. This type of capacitors is usable in all types of circuits, even for high frequencies and high voltages. There are ceramic capacitors with specific temperature coefficients, positive (capacitance grows as the temperature increases) or negative (capacitance falls as the temperature rises) – it is usable for compensation of temperature variations of different precise circuits
### Electrolytic Capacitors
#electrolytic

> [!DEFINITION] Electrolytic
> The electrolytic capacitors have a very distinctive feature – they are polarized. This means that they can be inserted in circuit only in a specific way that ensures proper voltage polarity. For special purposes, there are, however, non-polarized electrolytic capacitors, but they are rare and expensive. One more important property of electrolytic capacitors is  that they can lose capacitance with time, and the process is sped up with the temperature. The popular brands of capacitors are guaranteed to work and maintain their specified parameters  only for a few thousands hours.
### Variable Capacitors

> [!DEFINITION] Variable
> Apart from regular capacitors, there are also variable capacitors, sometimes called as trimmers. Their main use is in high frequency circuits and radios. In some applications (such as radio receivers) they are being replaced by other, cheaper to manufacture and easier to adjust  components.
## Inductors
#inductors
While not so frequently used as resistors and capacitors, they are essential components in some applications, like power  conversion and in radio frequency circuits. The inductors, compared to capacitors and resistors, are more often made to order, due to their specific properties that must be adjusted for certain application. The very distinctive and important group of inductive components are transformers, that are constituted by at least two separate inductors that are magnetically coupled to each other. The area of their uses is power supplies and, less frequently, radio frequency circuits.
The operation of the inductor is described by the following formula.
$$
U = L\frac{dI}{dt}
$$
The meaning of the symbols are:
- $U$ is the voltage across the inductor.
- $I$ is the current flowing through the inductor.
- $L$ is the inductance of the component, specified in Henrys ($\text{H}$).
From the formula, it should be understood that the voltage developed across the inductor depends on the inductance of the inductor and the rate of change of the current flowing through the inductor.

> [!NOTE] Henry
> #henry
> A Henry is a relatively large value of inductance, and in most cases the inductors used in circuits have inductance of a fraction of Henry, usually from Nanohenrys ($10^{-9}$) for RF circuits or Microhenrys ($10^{-6}$) for all other circuits. There are, however, larger inductors, whose inductances are much higher, easily larger than tens of Henrys.

Basic parameters of inductors are the following:
- Inductance: The capability of storing energy in the form of a magnetic field.
- Winding Resistance: The total resistance of the conductor (usually a wire) constituting the inductor.
- Saturation Current: The maximum current that can flow through the inductor without the rapid decrease of inductance (nonlinear effect).
- Core Material: The properties of the inductor, like saturation current, are determined by the core material.
- Stability: The amount of change of inductance with the temperature (also Curie temperature for inductors with core) and time.

> [!EXAMPLE] Example Inductor
> An example of a very small inductor that can be found in circuits is as follows:
> - Inductance $100\text{uH}$.
> - Tolerance $\pm10\%$, in temperatures $-55^{\circ}\text{C}$ to $105^{\circ}\text{C}$.
> - Resistance (maximally) $3.8\ohm$.
> - SRF $5.5 \text{MHz}$.
> - Maximum current $165\text{mA}.$

For inductors it is very important to consider the parasitance of the component, in the form of unwanted resistance and capacitance.
# Semiconductor Physics
## Doping

## Band Gaps
## Charge Separation

## Junctions
### Forward Bias
### Reverse Bias
# Diodes
Nowadays the semiconductor diodes are almost exclusively used, but it is possible to use older diodes, as vacuum tubes, as well. One important fact about diodes needs to be stressed – they are nonlinear components, that means – there are no linear relationships between voltage and current for this component. So,  for a diode, the following is true in general:
$$
\begin{align}
& f(a(t) + b(t)) \neq f(a(t)) + f(b(t)) \\
& f(k\cdot a(t)) \neq k\cdot f(a(t))
\end{align}
$$
For some specific applications and under certain assumptions, it is, however, possible to approximate the relationships with linear equations where it is desirable.
A diode has two electrodes, anode and cathode, as denoted on the following figure:
In the most basic way, the operation of a diode (so called ideal diode) can be summarized as the following:
> [!EXPLANATION] Ideal Diode Behavior
> For an ideal diode, the current can flow in only one direction – from anode to cathode. In  the opposite direction, no current can flow. In practice – there are no ideal diodes, but some get close to that.
### Structure
The semiconductor diode is built using semiconductors (for example silicon or germanium) with different type of doping (additions – like boron or phosphorus). Due to the amount of dopants, different properties of semiconductors can be obtained. In general, there are two  main types of semiconductors – P and N type. A semiconductor diode is constructed using P and N type semiconductor. Therefore, a diode is constituted by a single so called PN junction.

### Notes
> [!WARNING] 
> Do NOT connect diodes in parallel. The diode with the lower forward bias will have more current going through it, causing it to heat up and have a further decrease in the forward bias voltage; causing a run-away positive thermal loop where the current and temperature increases until the component safety ratings are exceeded.

## Models
When working with diode circuits the predicted behavior will depend heavily on the diode model used during calculations. These models exhibit the I-V characteristics of this semiconductor device.
### Piece-Wise Linear Model
As the namesake suggests, this model approximates the I-V characteristics with a piece-wise linear function of the following definition.
$$
\begin{cases}
0 & v < V_{\text{b}} \\
\frac{v}{R_\text{b}} & v > V_{\text{b}}
\end{cases}
$$
Where $V_\text{b}$ is the forward bias voltage, and $R_\text{b}$ is the symbolic resistance of the diode. This model approximates the diode into three components: **an ideal diode**, **a voltage source** and **a resistor**.
### Exponential
The Shockley diode equation relates the diode current $I$ of a p-n junction diode to the diode voltage $V_D$. This relationship is the diode I-V characteristic:
$$
I = I_S(e^\frac{V_d}{nV_T}-1)
$$
where $I_S$ is the saturation current or scale current of the diode.
### Constant Voltage-Drop
# Transistors
## Bipolar Junction Transistors
## Field-Effect Transistors

### JFET
### MOSFET
# Operational Amplifiers
## Ideal Op-Amps
## Non-Ideal Op-Amps
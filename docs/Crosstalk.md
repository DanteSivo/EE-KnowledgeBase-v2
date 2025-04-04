# Crosstalk
* Crosstalk (or X-talk) is when the switching on one signal causes noise on an adjacent line. 
* This is commonly in the form of an aggressor net (neighboring trace, plane, emission) affecting a victim net (usually a trade)
* In single-ended digital standards, the *noise margin* is typically 15% of the total voltage swing
    * A third of this margin is reserved for crosstalk. In other words, a cross talk of 5% of the voltage swing can be tolerated
    * As risetime rises and voltage swings decrease, this margin shrinks, making crosstalk even more impactful
* Crosstalk has two primary causes, **Mututal Capacitance (CM)** and **Mutual Inductance (LM)**
* Fundamentally, coupling occurs because of the generated magnetic and electric fields by a signal as it propigates down a transmission line
    * Most of these fields are tightly coupled, but there are *fringe fields*
    * As these fringe fields move away from the conductor, they begin to drop off more and more.

![](images\High Speed Design\Crosstalk\Coupling Diagram.jpg){align="left"} 

* Notice how tigher spacing of transmision lines lead to more coupling
* Bringing the return path closer to the transmission line helps to reduce the quantity of fringe fields

![](images\High Speed Design\Crosstalk\EvsM-Coupling-Diagram.jpg)

## Crosstalk Classes

1. Signal Crosstalk
    * When CM and LM produce cross talk on the same order of magnitude
    * When the return path is a wide and uniform plane
    * When the signal path is the reason for the crosstalk
    * Commonly seen on PCBs or ASICs
2. Switching Noise
    * When the return path increases coupling, causing noise
    * IE, when the return path is not a wide uniform plane, but is a single lead in a package, or a single pin in a connector
    * Here, the inductive coupled currents are much larger than capacitive coupled currents
    * Therefore the return path is *highly* inductive
    * Seen commonly in packages and in connectors
    * Aka, "Ground Bounce", Power supply Drop, Simulatenous Switching Noise (SSN) or Simulataenous Switching Output (SSO) Noise

## Crosstalk Locations
![](images\High Speed Design\Crosstalk\next-fext-diagram.jpg)

* Noise is either can be modeled as Near or Far Crosstalk
* NEXT - Near End Crosstalk $(\dfrac{V_{rev}}{V_A})$
* FEXT - Far End Crosstalk $(\dfrac{V_{rev}}{V_A})$
* **Crosstalk is only present where the signal is**
    * This means as it propigates down the line, only noise will be observed at that point
    * This means that the rest of the line is a quiet line. Where voltage and current are constant.
        * No coupled-noise current exsists here
        * The reflection of a signal can cause crosstalk as it propigates back and forth

### NEXT
* Location nearest to signal source resistance
* Two components make up NEXT as with all crosstalk, capacitive and inductive coupling
* The key here is that the magnitude of the induced crosstalk is the same polarity for NEXT.
    * The indivdual magnitudes are likely different

![](images\High Speed Design\Crosstalk\next-cap-graph.jpg){width="500"} 
![](images\High Speed Design\Crosstalk\next-ind-graph.jpg){width="500"}

$$ NEXT = \dfrac{V_{NE}}{V_A} = \dfrac{1}{4} * (\dfrac{C_M}{C_L} + \dfrac{L_M}{L_L}) = k_b $$

* $k_b$ is known as the *Backward Coefficent*
* Note how NEXT ==grows== to its maximum value. This is the risetime of the signal at work.
    * If the line is not long enough for the rise time, the maximum value will be scalled
* A good rule of thumb for acceptable noise is that the spacing of signal traces should be at least twice the trace width
    * This is good for managing fringe fields

### FEXT
* Location nearest to termination resistor
* Typically seen as length dominated
* Can be reduced by...
    * decreasing spacing to return path or coupling length
    * increasing rise time or space between agressor and victim
* Two components make up FEXT as with all crosstalk, capacitive and inductive coupling
* If the dielectric surrounds the entire transmission line and is homogenous (ie capacitive coupling is exactly the same inductive coupling)
    * No FEXT is present.
* Generally, FEXT from capacitive coupling is positive while from inductive coupling is negative.

![](images\High Speed Design\Crosstalk\fext-cap-graph.jpg){width="500"} 
![](images\High Speed Design\Crosstalk\fext-ind-graph.jpg){width="500"}

$$ NEXT = \dfrac{V_{FE}}{V_A} = \dfrac{1}{2} * (\dfrac{length}{vel * t_{rise}}) * (\dfrac{C_M}{C_L} + \dfrac{L_M}{L_L})$$

$$ k_f = \dfrac{1}{2} * (\dfrac{C_M}{C_L} + \dfrac{L_M}{L_L})$$

$$ \dfrac{length}{vel * t_{rise}} = \dfrac{T_D}{t_{rise}} $$

* $k_f$ is known as the *Forward Coefficent*

## Total X-Talk
* The total X-Talk is the sum of NEXT and FEXT
    * Keep in mind these will vary throughout the length of the transmission line
    * FEXT can also be zero if surrounded in a homogenous dielectic
* If the coupled length of the Tranmission line is SHORTER than the risetime, then NEXT will not reach its maximum value 
    * To properly scale the maximum use..
    * $NE_{scaling} = \dfrac{Length\,of\,Coupled \,Region}{Length\, of \,Risetime}$
    * $length_{rise} = vel * t_{rise}$
* In order to calculate FEXT and NEXT, the line capacitance $C_L$ and inductance $L_L$ will be needed
$$ C_L = \dfrac{T_D}{Z_O} $$
$$ L_L = T_D * Z_O $$
* $T_D$ is the propigation time from source to termination. $Z_O$ is the characteristic impedance of the line.
* As a rule of thumb, the speed of a signal in FR4 is 6 inches/ns
* For both NEXT and FEXT, the noise moves with the signal. So as the signal enters its return, you will see the same magnitude of noise again back through the line.
![](images\High Speed Design\Crosstalk\fext-ind-return.jpg){width="1000"}

## Switching Noise
* This is where the return path is highly inductive and as a result, inductive noise dominates
* Typically there is no inductance modelled on the return path. However in reality, there always is.
* When a signifcant amount of inductance is present, you get switching noise
    * Thermal Relief, long vias, skinny returns, and long returns are all good sources for Switching Noise
### Ground Bounce
![](images\High Speed Design\Crosstalk\switching-noise-model.jpg){width="1000"}
$$ V_N = L_{ret} * \dfrac{dI_A}{dt} $$
* The additional inductance creates a non-zero voltage along the return path relative to the circuit. Hence the name "Ground Bounce".
* ASIC's and connectors may reduce the number of ground pins while maintaing the same number of signals to save cost
    * But this means multiple signals are sharing the same ground
    * Which means Ground Bounce is now proportional to the number of signals per return pin

$$ V_N = L_{ret} * \dfrac{dI_A}{dt} * (number\,of\,signals)$$

* Alternatively expresed a voltage using V=IZ=IR

$$ V_N = L_{ret} * \dfrac{0.8*V_A}{t_{rise}*Z_O} * (number\,of\,signals)$$
![](images\High Speed Design\Crosstalk\ground-bounce-example.jpg){width="1000"}
### Mutual Inductance
* Along with Ground Bounce, there is mutual inductance that couples between the signal and return path inductance
* In short, the inductor in the return path acts as a voltage source, which creates an opposite polarity voltage from the return current
* This can *decrease* the total inductive ground bounce noise. Which is good...
* But this is a secondary effect compared to the additional noise from multiple signals sharing a common return.
![](images\High Speed Design\Crosstalk\mutual-inductance-example.jpg){width="1000"}

### Reducing Switching Noise
1. Increase the number of return paths such that the change in current in each path is reduced
2. Design with minimum partial self-inductance. This means a increase in the return width, decrease the length, remove thermal reliefs, etc. 
3. Reduce the space between the signal and return path as much as possible to increase their partial mutual inductance
    * Hence lowering effects from Ground Bounce
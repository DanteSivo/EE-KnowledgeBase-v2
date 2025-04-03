# Interview Anwsers

## Basic Questions

1. **What is the Equation of a Voltage Divider?**

2. **What is the definition of Capacitance?**

3. **How does a FPGA differ from a Microprocessor?**

4. **How do ADC's work?**

5. **What is the point of impedance matching?**

6. **How does a BJT work?**

7. **How does a MOSFET work?**

8. **How does an H-Bridge work?**

## Boolean Alegbra
### Simplifiy The Boolean Expression
$$ \overline{A}CC + \overline{A}BC + A\overline{B}\overline{C} + A\overline{B}C = \overline{A}BC + A\overline{B} $$

## Digital Logic
### SR Latch

## BJTs
1. **Determine $I_C$, $I_B$, $I_E$ and $V_C$, $V_B$, $V_E$**
    ![](images\bjt-question-1.JPG){ width="600" } 
    Assuming the BJT is in Active Mode, $V_{BE} = 0.7(v)$
    $$ 
    \begin{equation}
    V_{BE} = V_B - V_E = 0.7
    \\
    I_C = \beta{}I_{B} = 99I_B 
    \end{equation}
    $$

    Taking KVL from B-E
    $$ 
    \begin{equation}
    V_{sig} = R_B I_B - V_{BE} - R_E I_E = 0
    \\
    5.7(v) - (10k\Omega{})I_B - 0.7(V) - (2k\Omega{})(\beta{}+1)(I_B)= 0
    \\
    \boxed{I_B = 23.8uA}
    \\
    I_C = \beta{}I_B = \boxed{2.356mA = I_C}
    \\
    I_E = (\beta{} + 1)I_B = \boxed{2.380mA = I_E}
    \\
    V_C = V_{CC} - I_C(R_C) = 10.7 - (2.356mA)(1k\Omega{}) = \boxed{8.34(V) = V_C}
    \\
    V_E = V_C - V_E = \boxed{3.58(V) = V_E}
    \end{equation}
    $$

    Take KVL from C-E
    $$
    \begin{equation}
    V_{sig} - I_C R_C - V_{CE} - I_E(R_E) = 0
    \\
    \boxed{V_{CE} = 3.58(V)}
    \\ V_{CE} = V_{CE} + V_{BE} = \boxed{2.88(V) = V_{CE}}
    \end{equation}
    $$

    ==Check that Assumption of Operating Mode is correct==
    $$
    \begin{equation}
    V_{CE} > 0.7(V) \checkmark
    \\
    I_B > 0 \checkmark
    \end{equation}
    $$

2. **Determine $I_C$ and $V_C$**

## Op-Amp
1. **What does Op-Amp stand for?**
2. 

## RC Circuits
### Example 1

==Sketch the output given the input for the two circuits.==

   ![](images\RC-Circuits-A1.JPG){ width="600" } 

   SPICE Sim R//C//R -> [Click to Download](SPICE-files/RC-Circuits-A1_1.asc)

   SPICE Sim C//R//C -> [Click to Download](SPICE-files/RC-Circuits-A1_2.asc)

   [YouTube explaination](https://www.youtube.com/watch?v=1N99I_Z1YQc)

### Example 2

==Given the circuit starts open, when SW1 closes. What is the voltage accross C1 and C2?==

   ![](images\RC-Circuits-Q2.JPG){ width="600"}

   C1 will reach the same voltage as the input voltage after it has been completley charged. This time can be determined through the use of the equation 
   $V = Vo \cdot{} e^{-t/(RC)}$ where $t$ is determined. Since C2 is not connected to the voltage source, it remains at 0V.

   **Now, SW1 opens and SW2 closes. What is the voltage across C1 and C2 given SW1 has been closed for a long time?**

   When SW2 is closed, the voltage on C1 is equal to 5V and the voltage on C2 is 0V. Because of the potential difference, current will flow from C1 to C2 until the potential difference is 0. To determine the final voltage, the total capacitance should be considered.

   $$ 
   \begin{equation}
   Ceff = C1 + C2 = 2C
   \\
   C = \dfrac{Q}{\Delta{}V} 
   \end{equation}
   $$

   Given C1 is charged, we know the total charge on C1 is $Q_1 = C_1 \cdot{} \Delta{}V_1$
   In order to **conserve charge**, $Q_{eff}$ must equal $Q_1$. ==The amount of charge cannot change.==

   $$ 
   \begin{equation}
      Q_1 = C_{eff} \cdot{} \Delta{}V_{eff}
   \\
      C_1(V_1) = (C_1 + C_2) \cdot \Delta{}V_{eff}
   \\ 
      \dfrac{C_1(V_1)}{C_1 + C_2} = \Delta{}V_{eff}
   \end{equation}
   $$

   Therefore, the voltage on C1 and C2 will be equal at some value less than 5V.
   
### Example 3

==When SW1 closes what is Vout?==

   ![](images\RC-Circuits-Q3.JPG){ width="500"}

   ==Convservation of Charge== 
   
   The current through C2 is the same going through C1. So the charge on $q_1 = q_2$. 

   The definition of the total charge on a capacitor is $q = c \cdot{} \Delta{}v$

   $$
      \begin{equation}
         \Delta{} V_2 = V_{in} - V_{out}
         \\
         \Delta{} V_1 = V_{out} - 0
         \\
         C_2\Delta{}V_2 = C_1\Delta{}V_1
         \\
         4C(V_{in} - V_{out}) = C(V_{out} - 0)
         \\
         4(5V - V_{out}) = V_{out}
         \\
         V_{out} = \dfrac{20V}{5} = 4V 
      \end{equation}
   $$

### Example 4

 ==For the given circuit==
   
   ![](images\examples\RC-Example4.PNG){width=500} 

   1. **Right after the switch is closed (t=0)**
      1. **What is the charge on the cap** 
   
         None, so Q = 0C

      2. **Voltage across the cap** 
   
         V = 0. There is no charge but there is current 

      3. **Current across the resistor** 
         $$
         \begin{equation}
               V=IR  ,  V=\dfrac{I}{R} = \dfrac{9V}{12\Omega} = 0.75A
         \end{equation}
         $$
      4. **Voltage across the resistor**
   
         Vr = 9V

   2. **Now, when the switch is opened**
      1. **What is the charge on the cap**

         $Vc =   9V$. 
         So since $V=\dfrac{Q}{C}$. Therefore $Q=27\mu{}C$

      2. **Voltage across the cap**
         
         $Vc =   9V$. 
      3. **Current across the resistor**
         
         $I = 0$ since there is no potential difference,  $\Delta{}V$

      4. **Voltage across the resistor**
         
         $V = 0$

### Example 5

 ==For the given circuit find...==

   ![](images\examples\RC-Example5.PNG){width=500}  

   1. **Total Capacitance**

      $C_T = \dfrac{1}{C_1} + \dfrac{1}{C_2} = 4\mu{}F$

   2. **Current through the 10$\Omega$ resistor**

      $V=IR, \dfrac{V}{R} = I = dfrac{6}{10} = 0.6(A) = I_T$
      $\dfrac{V_{10}}{R_{10}} = I_{10} = \dfrac{2}{10} = 0.2(A)$

   3. **Voltage across X and Y points**

      V_X - V_Y = V_{R20} - 0 = 4(V)

   4. **Charge on 6$\mu{}F$ cap** 

      $$
      \begin{equation}
      Q_6 = Q_{12}
      Q_T = C_T * V_T = 4\mu{}C * 4(V) = 16\mu{}C
      \end{equation}
      $$
      Charge Sharing: Charge is the same across series capacitors. $Q_6 = Q_{12} = Q_T$

   5. **Voltage across each cap**  
      $$
      \begin{equation}
      Q = CV , \dfrac{Q}{V} = C = \dfrac{16\mu{}C}{C} \\
      V_6 = \dfrac{16\mu{}C}{6\mu{}F} = 2.67(V) \\
      V_{12} = \dfrac{16\mu{}C}{12\mu{}F} = 1.33(V) \\
      \end{equation}
      $$
## RL Circuits
### Example 1

 ==For the given circuit find...==

   ![](images\examples\RL-Circuits\RL-Example1.PNG){width=500}  

   1. **When the switch is closed after being open for some time.**
       1.  **Current through the circuit** $I = 0$
       2.  **Voltage across the resistor** $V_R = 0$
       3.  **Voltage across the inductor** $V_L = 12V$
   2. **After being closed for a long period of time...**
       1.  **Current through the circuit** $I = V/R = \dfrac{12V}{10k} = 1.2mA$
       2.  **Voltage across the resistor** $V_R = 12V$
       3.  **Voltage across the inductor** $V_L = 0V$

### Example 2

 ==For the given circuit find...==

   ![](images\examples\RL-Circuits\RL-Example2.PNG){width=500}  

   1. **When the switch is closed after being open for some time.**
       1.  **Current through the circuit** $I = 0$
       2.  **Voltage across the inductor** $V_L = 24V$
       3.  **Voltage across the 5$\Omega$ Resistor** $V_5 = 0$
       4.  **Voltage across the 3$\Omega$ Resistor** $V_3 = 0$
   2. **After being closed for a long period of time...**
       1.  **Current through the circuit** $I = V/R = 24V/(5+3) = 3A$
       2.  **Voltage across the inductor** $V_L = 0$
       3.  **Voltage across the 5$\Omega$ Resistor** $V_5 = IR = (3)(5) = 15V$
       4.  **Voltage across the 3$\Omega$ Resistor** $V_3 = IR = (3)(3) = 9V$

### Example 3

 ==For the given circuit find...==

   ![](images\examples\RL-Circuits\RL-Example3.PNG){width=500}  

   1. **When the switch is closed after being open for some time.**
       1.  **Current through the inductor** $I_L = 0A$
       2.  **Current through the circuit** $I = V/R = \dfrac{24}{12} = 2A$
       3.  **Current through the 4$\Omega$ resistor** $I_4 = 2A$
       4.  **Current through the 8$\Omega$ resistors** $I_8 = 2A$
       5.  **Voltage across the inductor** $V_L = 16V$
       6.  **Voltage across the 8$\Omega$ resistors** $V_8 = IR = (2)(8) = 16V$
       7.  **Voltage across the 4$\Omega$ resistor** $V_4 = IR = (2)(4) = 8V$
   2. **After being closed for a long period of time...**
       1.  **Current through the inductor** $I_L = 1.5A$
       2.  **Current through the circuit** $I = V/R = \dfrac{24}{(4+(8//8)} = 3A$
       3.  **Current through the 4$\Omega$ resistor** $I_4 = 3A$
       4.  **Current through the 8$\Omega$ resistors** $I_8 = 1.5A$
       5.  **Voltage across the inductor** $V_L = 0V$
       6.  **Voltage across the 8$\Omega$ resistors** $V_8 = 12V$
       7.  **Voltage across the 4$\Omega$ resistor** $V_4 = IR = (3)(4) = 12V$
   3. **The switch is now opened**
       1.  **Current through the inductor** $I_L = -1.5A$
       2.  **Current through the circuit** $I = 0$
       3.  **Current through the 4$\Omega$ resistor** $I_4 = 0$
       4.  **Current through the 8$\Omega$ resistors** $I_8 = -1.5A$ <- Reverse current due to back EMF from inductor
       5.  **Voltage across the inductor** $V_L = -24V$ <- Opposite of load
       6.  **Voltage across the 8$\Omega$ resistors** $V_8 = IR = (-1.5)(8) = 12$
       7.  **Voltage across the 4$\Omega$ resistor** $V_4 = 0$

### Example 4

 ==For the given circuit find...==

   ![](images\examples\RL-Circuits\RL-Example4.PNG){width=500}  

   1. **When the switch is closed after being open for some time.**
       1.  **Current through the inductor** $I_L = 0$
       2.  **Current through the circuit** $I = V/R = \dfrac{10V}{4} = 2.5A$
       3.  **Current through the 4$\Omega$ resistor** $I_4 = 2.5A$
       4.  **Current through the 8$\Omega$ resistor** $I_8 = 0A$
       5.  **Charge on the capacitor** $Q = 0C$
       6.  **Voltage across the capacitor** $V_C = 0$
       7.  **Voltage across the 8$\Omega$ resistor** $V_8 = 0$
       8.  **Voltage across the 4$\Omega$ resistor** $V_4 = 0$
       9.  **Voltage across the inductor** $V_L = 10$
   2. **After a long time being closed...**
       1.  **Current through the inductor** $I_L = 1.25A$
       2.  **Current through the circuit** $I = V/R = \dfrac{10V}{8} = 1.25A$
       3.  **Current through the 4$\Omega$ resistor** $I_4 = 0$
       4.  **Current through the 8$\Omega$ resistor** $I_8 = 1.25A$
       5.  **Charge on the capacitor** $Q = VC = (10V)(0.5F) = 5C$
       6.  **Voltage across the capacitor** $V_C = 10V$
       7.  **Voltage across the 8$\Omega$ resistor** $V_8 = 10V$
       8.  **Voltage across the 4$\Omega$ resistor** $V_4 = 0$
       9.  **Voltage across the inductor** $V_L = 0$

## Advanced Examples

### Switch Mode Power Supply
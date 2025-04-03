# Interview Questions

This is a list of basic interview questions to review and prepare for.

The anwsers are included are linked.

## Basic Questions

1. ==What is the Equation of a Voltage Divider?==

2. ==What is the definition of Capacitance?==

3. ==How does a FPGA differ from a Microprocessor?==

4. ==How do ADC's work?==

5. ==What is the point of impedance matching?==

6. ==How does a BJT work?==

7. ==How does a MOSFET work?==

8. ==How does an H-Bridge work?==

## Boolean Alegbra
### Simplifiy The Boolean Expression

$$ \overline{A}CC + \overline{A}BC + A\overline{B}\overline{C} + A\overline{B}C $$

## Digital Logic
### SR Latch

## BJTs
1. ==Determine $I_C$, $I_B$, $I_E$ and $V_C$, $V_B$, $V_E$==
    ![](images\bjt-question-1.JPG){ width="600" } 


## Op-Amp
1. ==What does Op-Amp stand for?==
2. 

## RC Circuits
### Example 1

==Sketch the output given the input for the two circuits.==

![](images\RC-Circuits-Q1.JPG){width=300 } 

### Example 2

==Given the circuit starts open, when SW1 closes. What is the voltage accross C1 and C2?==

![](images\RC-Circuits-Q2.JPG){width=400}

**Now, SW1 opens and SW2 closes. What is the voltage across C1 and C2 given SW1 has been closed for a long time?**

### Example 3

==When SW1 closes what is Vout?==
   
![](images\RC-Circuits-Q3.JPG){width=400}

### Example 4

 ==For the given circuit==

![](images\examples\RC-Example4.PNG){width=500}  

1. **Right after the switch is closed (t=0)**
    1. **What is the charge on the cap**
    2. **Voltage across the cap**
    3. **Current across the resistor**
    4. **Voltage across the resistor**
2. **Now, when the switch is opened**
    1. **What is the charge on the cap**
    2. **Voltage across the cap**
    3. **Current across the resistor**
    4. **Voltage across the resistor**
   

### Example 5

 ==For the given circuit find...==

![](images\examples\RC-Example5.PNG){width=500}  

 1. **Total Capacitance**

 2. **Current through the 10$\Omega$ resistor**


 3. **Voltage across X and Y points**


 4. **Charge on 6$\mu{}F$ cap** 


 5. **Voltage across each cap**


### Example 6

==For the given circuit==

![](images\examples\RC-Example6.PNG){width=500}  

1. **When the switch is closed after being open for some time.**
       1.   **What will the voltage on the cap be after 2 time constants**
       2.  **What will the voltage on the cap be after 6 seconds**
       3.  **When will it be fully charged**
       4.  **When will the current be reduced by 25%**
   
2.  **Given the switch is opened after a period of time.**
    1.  **What will the voltage on the cap be after 2 time constants**
    2.  **What will the voltage on the cap be after 6 seconds**
    3.  **When will it be fully discharged**
    4.  **When will the current be 25% of the maximum current**

## RL Circuits
### Example 1

 ==For the given circuit find...==

   ![](images\examples\RL-Circuits\RL-Example1.PNG){width=500}  

   1. **When the switch is closed after being open for some time.**
       1.   **Current through the circuit**
       2.  **Voltage across the resistor**
       3.  **Voltage across the inductor**
   2. **After being closed for a long period of time...**
       1.   **Current through the circuit**
       2.  **Voltage across the resistor**
       3.  **Voltage across the inductor**

### Example 2

 ==For the given circuit find...==

   ![](images\examples\RL-Circuits\RL-Example2.PNG){width=500}  

   1. **When the switch is closed after being open for some time.**
       1.  **Current through the circuit**
       2.  **Voltage across the inductor**
       3.  **Voltage across the 5$\Omega$ Resistor**
       4.  **Voltage across the 3$\Omega$ Resistor**
   2. **After being closed for a long period of time...**
       1.  **Current through the circuit**
       2.  **Voltage across the inductor**
       3.  **Voltage across the 5$\Omega$ Resistor**
       4.  **Voltage across the 3$\Omega$ Resistor**

### Example 3

 ==For the given circuit find...==

   ![](images\examples\RL-Circuits\RL-Example3.PNG){width=500}  

   1. **When the switch is closed after being open for some time.**
       1.  **Current through the inductor**
       2.  **Current through the circuit**
       3.  **Current through the 4$\Omega$ resistor**
       4.  **Current through the 8$\Omega$ resistor**
       5.  **Voltage across the inductor**
       6.  **Voltage across the 8$\Omega$ resistor**
       7.  **Voltage across the 4$\Omega$ resistor**
   2. **After being closed for a long period of time...**
       1.  **Current through the inductor**
       2.  **Current through the circuit**
       3.  **Current through the 4$\Omega$ resistor**
       4.  **Current through the 8$\Omega$ resistor**
       5.  **Voltage across the inductor**
       6.  **Voltage across the 8$\Omega$ resistor**
       7.  **Voltage across the 4$\Omega$ resistor**
   3. **The switch is now opened**
       1.  **Current through the inductor**
       2.  **Current through the circuit**
       3.  **Current through the 4$\Omega$ resistor**
       4.  **Current through the 8$\Omega$ resistor**
       5.  **Voltage across the inductor**
       6.  **Voltage across the 8$\Omega$ resistor**
       7.  **Voltage across the 4$\Omega$ resistor**

### Example 4

 ==For the given circuit find...==

   ![](images\examples\RL-Circuits\RL-Example4.PNG){width=500}  

   1. **When the switch is closed after being open for some time.**
       1.  **Current through the inductor**
       2.  **Current through the circuit**
       3.  **Current through the 4$\Omega$ resistor**
       4.  **Current through the 8$\Omega$ resistor**
       5.  **Charge on the capacitor**
       6.  **Voltage across the capacitor**
       7.  **Voltage across the 8$\Omega$ resistor**
       8.  **Voltage across the 4$\Omega$ resistor**
       9.  **Voltage across the inductor**
   2. **After a long time being closed...**
       1.  **Current through the inductor**
       2.  **Current through the circuit**
       3.  **Current through the 4$\Omega$ resistor**
       4.  **Current through the 8$\Omega$ resistor**
       5.  **Charge on the capacitor**
       6.  **Voltage across the capacitor**
       7.  **Voltage across the 8$\Omega$ resistor**
       8.  **Voltage across the 4$\Omega$ resistor**
       9.  **Voltage across the inductor**

## Advanced Examples

### Switch Mode Power Supply
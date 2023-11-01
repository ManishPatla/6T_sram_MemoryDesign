# 6T SRAM Memory Design

## Design of 4x4 SRAM Memory Array

![SRAM Cell](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/b35b1a7a-8e33-4aeb-9dc4-2f3459776175)

## Table of Contents
- [Introduction](#introduction)
- [Problem Statement and Implementation](#problem-statement-and-implementation)
- [Circuit Diagrams](#circuit-diagrams)
- [Stability of SRAM Cell](#stability-of-sram-cell)
- [Peripheral Circuits](#peripheral-circuits)
- [Test Cell View](#test-cell-view)
- [Conclusion](#conclusion)

## Introduction

**Static Random Access Memory (SRAM)** is a type of semiconductor memory used in digital electronic devices. It is widely employed in various applications, including computers and embedded systems.

The two essential requirements for SRAM cell design are:
- Data-read operation without data destruction.
- Modification of stored information during the data-write phase.


### Problem Statement and Implementation:

1. Design a pre-charge circuit to charge a BL and BL’th with capacitance of 120f in 0.5n Seconds.

2. Implement a 6T SRAM with CR=1.25 and PR=0.85 using 180nm technology. Keep Length (L) of all devices minimum and Wp=400n. Verify:
   a) Write '0' and Read '0' operation.
   b) Write '1' and Read '1' operation.
   c) Draw butterfly curve and measure SNM for Hold state, Read state, and Write state.

### Circuit Diagrams
- Circuit diagram for write and read operations

(Width of pull up transistors = 400nm, Width of access transistors = 2um, = Width of pull down transistors = 2.5um)

 ![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/8497596b-b311-4897-bd9c-1533d4da983b)

####  Write operation:
Initially word line WL is high and hence bit lines BL and Bl’ are connected to the SRAM cell. Then the write driver circuit provides the required voltage to BL and BL’ ( For write 0, BL = 0, BL’ = 1 and for write 1, BL=1, BL’ = 0). The corresponding data will be then written into the cell (Q = 0 for write 0 and Q = 1 for write 1). For a successful write operation, access transistors should be stronger than the pull up transistors which is taken care by the pull-up ratio.

####  Read operation:
To perform read operation, the memory cell should have some value. Consider, ‘1’ is stored in the memory cell (Q =1 and Q’ = 0). Initially the bit lines BL and BL’ are pre-charged to Vdd. Then the word line WL is made high. So the transistors M1, M4, M5 and M6 (From Fig 1) will turn ON. Therefore BL’ gets discharged through the series transistors M5-M1 and BL will remain at its pre-charged state. As the difference between the two bit lines build up, the sense amplifier is activated which gives output i.e. ‘1’ is read from the memory cell.



- Write Operation:
[Write '0' Operation]![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/43440a44-3111-43e9-861b-1c392c961fd5)
![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/aa3c1497-cf8b-43c7-834d-89f800c017a7)


[Write '1' Operation]![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/07faf503-1b36-4455-b6c4-f880010f5a35)
![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/a8e7a79d-58ad-464c-af7a-2bcac1d600fd)



- Read Operation:
[Read '0' Operation]![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/9951f414-ba1f-4239-9eb2-09f64c148f5b)
![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/68421432-a70c-4cb3-8ca0-5d8bbffde8c8)


[Read '1' Operation]![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/b6efd744-d1f9-4a85-8ac5-e0e60eb514c2)
![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/7a010cee-23f0-4e89-a6ae-3b8c1eda6705)



### Stability of SRAM Cell
The stability of the SRAM cell can be described by the 'Butterfly curve' which is obtained by superimposing the voltage transfer curves (VTC) of the two inverters of the memory cell.

![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/6d4de288-e2fe-4dd1-b7cc-b96cf834a952)


#### Hold State:
[Hold State]![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/37208b16-9aea-42ab-bf13-add7d71f72bc)
![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/519793d7-c0a8-44ec-a4c1-19165c0a8995)



#### Read State:
[Read State]![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/f5b500e8-e996-46c6-b2a1-bb03c37f6908)
![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/8716b755-58db-4286-9f7f-9c5f8f35df9d)






3. Draw a schematic of 6T SRAM and simulate for read and write operation.
   - Length of all the MOS: 180nm
   - Width of PMOS devices (Wp): Minimum width
   - Access Transistors Width (Wa): 1.2 x Wp
   - Pull down NMOS transistors (Wn): 1.5 x Wn
   - To account for BL and BL’ parasitic capacitance use an external capacitance of 120fF connected at BL and BL’ terminals.

### Peripheral Circuits
- Pre-charge circuit
- Isolation circuit
- Sense Amplifier
- Write driver circuit

#### Pre-charge Circuit
Pre- circuit is used to pre-charge the bit lines to Vdd before the Read operation. It consists of: a) Equalizer transistor which reduces the required pre-charge time by ensuring that both bit lines are at nearly equal voltages even if they are not pre-charged to Vdd. b) Bias transistors which pulls each of the bit lines to Vdd.
[Pre-charge Circuit]![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/6cb13785-7faf-42b8-a327-0f53ef4e2132)


#### Isolation Circuit
Isolation circuit is used to isolate the sense amplifier from the bit lines once a small change on the bit lines is detected.
[Isolation Circuit]![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/29bf1546-f564-421a-8c2f-e3af60c85eaa)


#### Sense Amplifier
The sense amplifier is responsible for detecting the value stored in the SRAM cell during the read operation and displaying that value at the output.
[Sense Amplifier]![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/8a813f0f-4d0f-4992-bb5a-b1f8a323da5b)

#### Write Driver Circuit
Write driver circuit is responsible to write the data onto the bit lines BL and BL’ during the write operation

[Write Driver Circuit]![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/2c98206c-cd0f-41d2-bfa7-1ccde497be71)


### Test Cell View

- 4x1
  
![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/1cf1b0ca-d7ba-40a9-83ba-0e6a95b1631b)

- 4x4
![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/7819bbdc-c506-404f-8f55-434e4a62d6b4)

- Test Cell View
  ![image](https://github.com/ManishPatla/6T_sram_MemoryDesign/assets/109287423/61277136-1d31-4d41-8297-d6979e4208ec)




### Conclusion
In our project, we have a 6T SRAM cell along with its peripherals (Pre-charge circuit, Isolation Circuit, Sense amplifier, and Write driver circuit). We have measured the Static Noise margin for the Hold state and Read state of the SRAM cell. We have finally designed a 2x2 Memory array and have performed the Write and Read operation on each cell.

CIRCUITING AND LOAD CALCULATIONS - BRONZE TRAINING - P5

For CAD designs only.

# Panel Schedule

42 is most common pole. Neutral is most often 100%. Mounting is SURFACE/RECESSED. Fed from: upstream panel (check one line). Under notes, write the manufacture and breaker types (Circuit Breaker Type Y). If its new, leave it blank. 

## Load KVA

The wattage of the equipment. Assume a power factor of one. Under design checklist you can find the load of different things.

## Feeder

Where you throw your feeder conductor rating and out breaker over protection setting. 

Choose overcurrent protection and feeder sizes by understanding NFPA 70 - NEC Article 310.17 (Conductor Ampacities) and NFPA 70 - NEC Article 240.6 (Standard Fuse/Breaker Ratings).

### Breaker/Overcurrent Protection

Big distinction between below 800 amps and over 800 amps. If your <800 amps and your ampacity does not match to a standard (like 20 amps) it's acceptable to go to the next standard size (if you need 55amp, you can use a 60 amp breaker). If your >800amps and your ampacity does not match to a standard, you must use the breaker that's equal or lower.

**TRIP** is the breaker. Must use standard ratings.

### Determining Feeder Size

Use CFR Feeding schedule as reference for our feeder size. If there is no N, that means you are not providing a neutral.

 <img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201021101121141.png" alt="image-20201021101121141" style="zoom:50%;" />

A 20N (20 amp circuit with 3 phase 4 wire) is going to have 4 #12 conductors and a #10 ground and those conductors are going to be run in a 3/4" conduit.

- There's 4 wires because there's 3 phases and a neutral.
- The size is based on those standards.

If it's a single pull, then you'd need 2#12, #12G, 3/4"C 

- 2 #12: one for hot one for neutral

**HOW DID THEY GET THAT CHART?**

<img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201021104101366.png" alt="image-20201021104101366" style="zoom:50%;" />

If you go to [NFPA 70 - NEC Article 310.16](https://www.nfpa.org/codes-and-standards/all-codes-and-standards/list-of-codes-and-standards/detail?code=70), it will show the ampacities of conductors with not more than 3 current carrying conductor. It shows the temperature rating; CFR Standard is if its below 100 amp load, then it should be 60 degrees C, anything over 100 amp should be 75 degrees. We have a 20 amp load to provide a 20 amp circuit, so the conductors have to be rated for the overcurrent protection (the thing protecting the conductors from overheating and failing). If the overcurrent protection doesn't limit the ampacity, then the conductors will draw more than their rated for. Then you go to the left of the chart and the size should be #12.

NFPA 70 - NEC article 250.122 gives the corresponding ground wiring size for the material for each amp. For CFR Standard, #12 is the lowest size we use (15 amp would use #12).

### System Furniture

Typically an 8 wire system. For the circuits: 3 hot one, 1 neutral, 1 ground, so put 4#12, #12G, 3/4"C.  For the dedicated 2#12, #12G, 3/4"C.

Make sure your conduits fit all the wire using pg 733 of NFPA 70.

<img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201021105141839.png" alt="image-20201021105141839" style="zoom:50%;" />

You can put 16. 

Since 3 circuits go to one feeder you must add the note: "ALL CIRCUITS WITH SHARED NEUTRALS SHALL BE PROVIDED WITH BREAKER TIE FOR SIMULTANEOUS TRIPPING"

# Branch Circuit Wiring Notes

Find under "Electrical Symbols - CFR STANDARDS">Tenant fit-out power details>Branch circuit wiring notes. Explains what it means.

HP-4a

HP: Panel designation. 4: Switch designation. a: circuit #/

# Circuiting Example

The panel is named LP,

1. Make a copy of the Panel 208 before starting and rename it Panel LP. Name it green so you can tell that you are using it.
2. Rename the title "PANEL LP"
3. Circuit the computer Receptacles:
   1. Find "Double wired quad receptacle detail" in the electrical symbols to find out the note format: PNL-X,Y. (Panelboard name - circuit number, circuit number)
   2. Add a homerun and its tag. The tag will be "**LP-1X**" (The x will be filled in later with 2 because circuit 2 has the convenience receptacles)
   3. In the panel schedule put LOAD DESCRIPTION as **COMP REC, RM G329C/G/H** 
      1. Comp rec means computer receptacle. 
      2. G329C/G/H means the 3 room numbers.
   4. Tag the other two the receptacle with "LP-1" *without* the homerun because there is only one homerun per circuit, and all these receptacle belongs in the LP-1 circuit.
      1. Try to move the tag so that the homerun points at it. Or very close near by to make the association very clear.
   5. Look in design checklist to find out Computers have a load of 200VA. So, in the schedule the calculation will be =3*.2 (200VA = .2 KVA). The three computer receptacle comes to a total load of .6 KVA.
      1. Typically, max of 4 computers per circuit so we don't overload it. 
      2. Most circuits are 20A, 120V, and **MAX LOAD IS 1920 VA**.
   6. Feeder will be **2#12, #12G, 3/4"C** because it is 20amp and single pull. View why [here](###Determining Feeder Size).
   7. Apply [category](##Category) 9. V
   8. Add the two to the label because we will start our next circuit
4. Circuit the receptacles in the office:
   1. Add a homerun
   2. Label the receptacles LP-2 in that one area 
   3. Duplex receptacles have a load of 180VA so that means there can be a max of 8 duplex receptacles per circuit. 
   4. On the panel schedule, add another load named "**CONV REC, RM G329C/G/H**". the load = 7*.18
      1. There are 7 receptacles with load of .18 KVA each. 
5. Circuit the receptacles in the mechanical room
   1. Add a home run
   2. Label LP-3 for all four receptacles. 
   3. Name it "CONV REC, RM G329K" and a Load KVA =4*.18
6. Create a dedicated circuit for one of the BAS Panel duplex receptacle.
   1. Give it a homerun and name it LP-4.
   2. Name it "DED REC" (for dedicated receptacle) or "BAS PANEL REC, RM G329K"
7. Create the circuit for the microwave and other kitchen things. 
   1. Give the microwave and its homerun "LP-5". You might need to move their tags somewhere to the side.
   2. Name it "MICROWAVE REC, " (for coffee maker it'll be "COFFEE MAKER REC" )

# Prewired furniture

Sometimes there's special wiring details for system furniture. A 3+1 (most common) means that it needs 3 general circuit and 1 dedicated circuit. or 2+2, meaning 2 general circuit and 2 dedicated.

 <img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201021094559697.png" alt="image-20201021094559697" style="zoom:67%;" />

Important to ask architecture in the beginning what their furniture vendor is going to be providing or ask for their contact information. FFNE package is the furniture provisions. 

- Example" If there's a 3+1 you ask "Hey we are assuming this is a 3+1. Please let us know otherwise in two days time. If we don't hear from you, we are going to proceed as 3+1".

We provide the power connection for the furniture. All the furniture is prewired so it just needs the junction box. The homerun is for the junction box at the wall. 

## 3+1 Circuit Example

<img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201021095304310.png" alt="image-20201021095304310" style="zoom:40%;" />![image-20201021100005803](C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201021100005803.png)



- 1 homerun has 3 circuits. Tag the homerun with "LP-15,17,19". It has three hots, one neutral (shared), and one ground (shared). In the panel schedule, get rid of the lines between the three circuits under FEEDER. There are 8 total seats for two of these systems each has load of .2 KVA but it will be divided between the 4 circuits so the calculation will be =8*.2/4. Extend this calculation to the 4 circuits. 
- The other homerun has 1 dedicated circuit. Tag with "LP-21". It has one hot, one neutral, and one ground.
- Add the FEEDER information 4#12, #12G, 3/4"C and 2#12, #12G, 3/4"C. View why [here](###System Furniture)

If there is another 3+1 that goes on the same circuit label it without the homerun and all at once: 

<img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201021095636248.png" alt="image-20201021095636248" style="zoom:50%;" />

# Loads Computation

## Category

Each element needs a category: lighting, receptacle, cooling, heating, etc. Miscellaneous is any dedicated equipment (garbage disposal, microwave, etc.). Each category has a certain demand factor. 

Computer receptacles, BAS Panel, microwaves, coffeemakers are 9 because they are dedicated equipment. System furniture are 2 because has receptacles.

## Resulting Calculations

Shows the total demand amps. You must make sure that the demand amp is <80% of the main circuit breaker rating.
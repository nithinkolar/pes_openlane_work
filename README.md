# OPENLANE 

## ABOUT THE REPOSITORY
OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, CVC, SPEF-Extractor, KLayout and a number of custom scripts for design exploration and optimization. The flow performs all ASIC implementation steps from RTL all the way down to GDSII.

You can check out the documentation, including in-depth guides and reference manuals at [ReadTheDocs](https://openlane.readthedocs.io/).


 # COURSE 
<details>
<summary>DAY 1 : Insecption of open-source EDA, Openlane and sky130pdk </summary>
<br>

# 1) Introduction to QFN-48 Package,chip,pads,core,die,and IP's and Introduction to RISC-V

- Generally an Aurdino board or an FPGA board consists of an chip or processor inside it.
- The internal veiw of chip will be as below

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/b9fba21f-28ed-4f1d-a58e-c53b86c7c015)



![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/14306000-21dc-43bf-94bc-63109a284f7e)


RISC-V is an open standard instruction set architecture based on established reduced instruction set computer principles. Unlike most other ISA designs, RISC-V is provided under royalty-free open-source licenses. 


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/8bf8e42e-712c-421c-b086-1a2a8b1d78a4)






# 2) SOC Design and OpenLANE

## a) Components of open-source digital asic design**
 - Digital ASIC design, It mainly consists of
   - RTL IP's
   - EDA Tools
   - PDK Data

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/e762216a-aee1-4363-aa3d-09251494f6f9)

      

  - Open source digital ASIC design

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/5cfc1e1e-32aa-4df8-9b14-8adb1915c344)


- What is PDK..?
  - Process Design Kit (PDK) Collection of files used to model a fabrication process for the EDA tools used to design an IC.
      - Process design rules : DRC,LVX,PEX
      - Device models
      - Digital standard cell Libraries
      - I/O libraries


 
## b) Simplified RTL2GDS Flow**

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/53443462-bc02-42d5-83fd-036da46e290b)


         1. Synthesis
         2. Floor planning and Power planning
         3. Placement 
         4. Clock tree synthsis (CTS)
         5. Routing 
         6. Sign off



## c) Introduction to Openlane ans strivechipsets**

   #### OPENLANE was started as an open-souce flow for a true Open source Tape-out experiment,
   #### STRIVES is a family of open everything socs.

  ![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/9ad09b8b-cf11-435a-80fe-59971013a821)
 

   #### Goal of Openlane asic flow is :
    - Produce a clean GDSII with no humaninterventions
         - CLEAN means 
                - No LVS voilations
                - No DRC voilations
                - Timming voilations

    - Open Lane is tunned for the skywater 130nm open PDK .
    - Open lane is containerzied which means
                - Functional out of the box 
                - Instruction to built and run natevly with flow
    - Open lane has two mode of operation 
                - Atonomous 
                - Interative


## d) Introduction to Openlane Detailed ASIC flow design


   
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/7f9566b1-9580-4735-92d5-10f0b7eafac1)

   
Here's a detailed ASIC design flow using OpenLane and the associated tools and software:

**1. Synthesis:** RTL code is synthesized into a gate-level netlist, optimizing for area, power, and timing.
   - **Tools/Software**: 
     - Yosys for synthesis.
     - ABC (A System for Sequential Synthesis and Verification) for technology mapping.
     - Cell libraries specific to the target process.
     - Yosys

       
**2. Floorplanning:** Define the chip's area and arrangement of major functional blocks.
   - **Tools/Software**: 
     - OpenROAD's TritonRoute for global placement.
     - Magic for floorplan visualization.
     - Chip floor planning - Partinioning the chip die between different system building blocks and place the I/O pads.
     - Macro floor planning - Dimensions, Pin locations, rows defination.
     - Power planning - It is typically assigned with multiple VDD and VSS (Power straps, Power pads, Power rings)
    
       
**3. Placement:** Position individual gates and standard cells optimally within the predefined areas.
   - **Tools/Software**: 
     - RePLace (REctangle PLACEr) for placement.
     - Magic for placement visualization.
     - Placement is usually done in 2 steps
              - Global placement
              - Detailed placement

       
**4. Clock Tree Synthesis:** Design a clock distribution network to ensure synchronous clock signals.
   - **Tools/Software**: 
     - OpenROAD's TritonCTS for clock tree synthesis.
    
     
**5. Routing:** Establish interconnections while adhering to design rules, optimizing for signal integrity and timing.
   - **Tools/Software**: 
     - FastRoute for global and detailed routing.
     - Magic for routing visualization.


**6. Design Rule Checking (DRC):**  Verify that the layout complies with manufacturing design rules.
   - **Tools/Software**: 
     - Magic for initial DRC checks.
     - OpenROAD's TritonRoute for DRC repair.


**7. Layout Versus Schematic (LVS) Verification:** Confirm that the physical layout matches the intended functionality described at the RTL level.
   - **Tools/Software**: 
     - Netgen for LVS checks.


**8. Parasitic Extraction:** Extract parasitic capacitance and resistance values from the layout for accurate timing analysis.
   - **Tools/Software**: 
     - QFlow's SPEF extraction tool for parasitic extraction.


**9. Static Timing Analysis (STA):** Analyze timing paths to ensure setup and hold time constraints are met.
    - **Tools/Software**: 
      - OpenSTA for static timing analysis.


**10. Physical Verification:** Perform a series of checks including DRC, LVS, and electrical rule checks (ERC).
    - **Tools/Software**: 
      - Magic for DRC and LVS checks.
      - Netgen for ERC checks.


**11. GDS2 Generation:** Convert the final layout data into GDS2 format for fabrication.
    - **Tools/Software**: 
      - Magic for GDS2 generation.Here's a detailed ASIC design flow using OpenLane and the associated tools and software:



#### Synthis exporation
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/0a78cf01-677e-4793-a95a-01ad71ba7f6a)



#### Design exploration
 ![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/b4c9b75b-6c49-4ac9-b1ea-9aa01dcae79c)


# 3) Open- Source EDA tools

#### Openlane Directory structure in detail

   - cd Desktop/
   - cd home/tools/
   - cd openlane_working_dir/
   - ls
   - cd openlane
   - docker
   - ./flow.tcl -interactive
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/03153126-15a6-4ab0-be0f-ddf08c238945)


#### Design Preparation step

    - in openlane directory
    - package require openlane 0.9
    - prep -design picorv32a

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/01e0384e-e287-4e1f-8ae2-0bc1defdabf6)



#### Review files after design synthsis and run synthsis

    - run_synthesis

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/036ba01e-067c-4850-b543-fbe91d2cc3ea)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/8078d99f-6145-4d87-829c-86a3ed0ce883)


   - Here the counter d flipflop is **1613**
   - The number of cells is **14876**
   - The flop ration for our design will be 1613/14876 = 0.108
   - In percentage = 10.08 %

     
#### Openlane Project Github link Discription

https://github.com/efabless/openlane

[Back to COURSE](https://github.com/nithinkolar/pes_Openlane_work/tree/main#course)

</details>




<details>
<summary>DAY 2 : Good floorplan vs bad floorplan and introduction to library cells </summary>
<br>


# GOOD FLOORPLAN VS BAD FLORPLAN AND INTRODUCTION TO LIBRARY CELLS

## 1) CHIP FLOOR PLANNING CONSIDERATIONS

## L1) Utilization Factor and Aspect ratio

  ![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/60754b1d-8cee-4933-9e66-6099ca8d1529)

    - Defining the width and height of the core and Die
    - Consider a netlist with 2 FF and 2 gates with the connections shown below


**STEP-1** Make the gates as a Squared box 

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/4b0c3113-6e09-4b1f-ad44-1ea8dcbd85c8)


**STEP-2** Find out the dimensions of the core and Die ( Dimensions of the standard cells )

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/16ac86d0-d26c-4930-b9c0-af5557d0c91b)



 #### For example 
  - Let us assume that each FF and Gates is on 1 cm breadth and 1cm height
  - Now Area of each standard cell will be will of 1 cm sq .
  - Allining tha area ocuupied the netlist in a in a single core .
  - Below the netlist will be fit into the core So it will be **100% utilization**
  - **Utilization factor** = Area occupied by the netlist / Total area ocuupied by the core.
  - where 4sq / 4sq = 1 . 
  - In this case when utilization factor = 1 , then the core is full no extra components can be added.
  - **Aspect ratoio** = Height / width , if it is 1 , it signifies that the core is square shaped.




## L2) Pre placed cells

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/9d04ba76-a078-48bf-9641-1198da3c4858)

  - Conisder a combinational block -> Gate level diagram.
  - Seperate that gate level diagram into two blocks.
  - Consider the multiple blocks are inside a Black box Now seperate the blackbox as two differnet IP's or Modules .
  - The Arrangements of the IP's in a chip is called as **Floor planning**.
  - The IP's will have an user defined loctions and they can be placed in a chip before the placement and rouiting is done hence these are calle as **Pre placed Cells**




## L3) Decoupling Capacitors

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/c067069d-5dad-4b45-a347-6eac8447db6f)


  - For any signal to be considered as a Logic 0 and Logic 1, It should be within the NM range ( Either NML or NMH )
  - The area between the NML and NMH is called undefined area
  - So in order to maintain the signal to be in the NML or NMh **Decoupling capacitors** are used.
  - Decoupling capacitors are mainly used to maintain the signal are not inside the undefined area.
    



## L4) Power Planning

![Screenshot from 2023-09-14 12-58-34](![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/fc5daba4-4129-4391-85b4-93741f8ae0b1)


  - Insted of using individual VDD and VSS for multiple cells in a Block.
  - Suppose if there are four cells in a Block , Each cell having seperate VDD and VSS are called as **Power Planning**




## L5) Pin placement and Logical cell placement Blockage

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/497a7a3b-caba-4b95-82f5-6063c9054059)

  - Here consider a 4 set of circuts with input, clk and output,
  - Considering all 4 circuits together and placing on a chip in such a way that INPUTS should be at one side and OUTPUT should be at one side which helps us to make the connections easily.
  - So this process is called as **Pin placement**
  - Making sure that non of the automated routing tool should not be placed near the i/p and o/p cells it needs to block the cells This is called as **Logical cell placement Blockage**
    

**Pin Placement**

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/2164d937-dda5-4d28-8903-dd18b986af9d)


**Logical cell placement Blockage**

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/ad01cb5d-3926-4024-bd9a-b13c02b7658c)




## L6) Steps to run Flopor planning using Openlane

      - These are the defalt Floorplans 
 
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/61e417ef-8640-4ade-8c7f-3abfce2e8997)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/3057d320-ae43-4d15-a8c0-b907bc703b10)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/6f217ecb-688a-46e0-b65b-873f8d270e70)


## L7)

              - In the openlane shell

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/d0d2fb7d-2c1c-4f08-937f-746106c1af9c)

              
              - To open the Floorplan we go to the required directory that is
                   > vsduser@vsdsquadron:~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/11-09_15-36/results/floorplan
              - Using the ```cd``` command.
              - Then we type the command:
                   > magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

              - The following layout is displayed

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/e3935b9d-1331-4a94-ac86-56c26406b040)

              - We can press 's' and then 'v' to align the design to the center of the screen.

              - We can right click on the mouse and pess 'z' to zoom into a desired part.

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/ba09726c-f021-40c2-9914-9918aa18b7cb)


              - We can check the details of the ports as follows
              - Hover over a port with your crosshair and press 's' on your keyboard
              - Now open the tkcon command window and type ```what```.
              - This will show you the details of the selected port.


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/45955fc8-9cb8-4119-b633-051dc342eaac)
             
              - If we zoom in a little more, we can see the tap cells.
              - They are present to prevent latch up conditions which occur in the CMOS devices

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/11cd873f-1a67-4404-ad3f-f4bd6b1a3282)

              - These are the standard cells that are used in the design




## 2) LIBRARY BINDING AND PLACEMENTS


### L1) Netlist binding and initial Place Design

       - Bind netlist with physical cells 
       - Here it defines about the shape and sixe of the standard cell
       - Each cells are defined only in either rectange shape or square shape 
       - In this example, 1 refers to NOT gate, 2 refers to AND gate.   [image 1]
       - Larger the cell size 
          > It has a least resistance path
          > Performes Faster
       - Once we have a Physical veiw of all cells, It is placed on the Floorplan according to the Netlist.  [image 2]

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/f9e0c1a2-8b6c-4024-9b0c-ac18a754ae33)



![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/f7d357b9-83aa-45af-9b4d-202da09e7ab2)



### L2 and L3) Optimize placement using estimate wire length and capacitance

        - When the cells are not extactly placed on the floorplan as in the netlist, If the relevant cells are not near to i/p or o/p.
        - Then estimation of wirelength and capacitance comes in.
        - Depending on the Capacitance and how far the cells are from input and output, Some **Buffers** are added in order to reduce the Wirelength and also to get a complete signal without any             lossses of signal ( but in cost of Area which can be minimized later )
    
          
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/b584f490-265c-4ac7-8e3e-9c89862a26a3)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/e35b0bfe-e02b-471a-ac73-c7f084d5597b)




### L4) Need for libraries and characterization 

        - Library characterization and modelling depends on some steps,
        - Logic synthesis  ->  Floor planning  ->  Placement  ->  Clock Tree synthesuis ( CTS )  ->  Routing 
        - The collection of all the standard cells are placed is one area which is referred as **Library**

        
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/d40d84b2-4b73-48f0-b3a4-b297cd617134)



### L5) Congestion aware placement using replace
          - To view the placement we type
                   > run_placement
          - In the OpenLANE shell.

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/5419a317-455e-4007-a54d-b4a5627bac5c)

          - This is the result displayed. As we can see the '/picorv32a.placement.def' file is read.

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/f189f689-8b1e-484c-8a15-1701d9d4eca1)

          - We move one directory up from the 'floorplan' folder using
                   > cd ../placement/

          - To view the placement design we use the command
                   > magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/256539e5-1af1-4071-a512-158751b0ebf5)


          - The above is displayed.
          - All these standard cells were present at the initial layout of the floorplan.

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/60fa6b7e-eec2-471c-85ee-64aad1bd72d7)


          - If we zoom in we can see the placement of the standard cells in the standard cell rows.




## 3) CELL DESIGN AND CHARACTERIZATION FLOW

### L1) Inputs for cell Design Flow
       - For each standard cell (AND,NOR,INVERTER,FF ect) There are different cell design flow
       - Each Cell Design Flow consists of 3 steps:
               - Inputs ( which mainly consists of PDK's [ DRC and LVs rules, Spice models, library ect] )
               - Design Steps (this mainly invovles 3 steps)
                      - Circuit Design
                      - Layout Design 
                      - Charecterization
               - Outputs ( Outputs we get here is  CDL circuit description language )
               
   #### User defined specifications
       - Cell height = The seperation between the power rail and ground rail defines the cell height.
       - Supply voltage = A certain cell should be operated at a certain supply voltage which is defined by the Top level design
       - Metal Layer = Certain Libraries van be designed on a particular Metal Layer.
       - Pin Location = Library nedds to decide on the pins and the pin location where it needs to be placed.

               
### L2) Circuit Design step
      - There are teo steps involved in circuit design:
            > Implement the Function itself
            > Modelling the PMOS and NMOS transisters in such a way that the aspect ratio should be matched.
            
      
### L3) Layout Design step
      - Implimenting the PMOS and NMOS values into layout are called Layout Design 
      - Steps involved in the layout design are:
           - Get the function implimented through the MOS transistors
           - Get a PMOS network graph and NMOS network graph
           - Obtain Euler's Path and draw a Stick Diagram
           - Convert the stick diagram into a proper Layout diagram
           - EXtract the paracetics from the layout and CHaracterize it interms of Timmings.

           
### L4) Typical Charaterization Flow
     - Steps involved in the characteriztion flow are :
           - Read in the Model Files
           - Read the extracted spice netlist
           - Define how to recongnise the behaviorur of the buffer
           - Read the subcircuits of the inverters 
           - Attach the neccessary Power source
           - Apply the stimulus
           - Provide the neccessary output capacitance
           - Provide the necessary simulation command.
           - Feed in all the 1 to 8 steps to a configuration file ( GUNA )


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/fe5154e9-378e-4db3-b16d-b60c6c9bc729)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/3d372061-aa6f-467e-91c4-6ae8f397ea7e)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/bb0127f8-0da4-4c54-97a5-d646a0d5aabc)



## 4) GENERAL TIMMING CHARECTERIZATION PARAMETERS

### L1) Timming Threshold definations
      - Timming Threshold Definations
          - slew_low_rise_thr
          - slew_high_rise_thr
          - slew_low_fall_thr
          - slew_high_fall_thr
          - in_rise_thr
          - in_fall_thr
          - out_rise_thr
          - out_fall_thr

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/7ce6e2dc-cd1b-41e8-bd09-cd26a7afc175)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/c5fae0b2-4348-4387-84cd-1d35a404fd4f)


         
### L2) Propogation delay and transition time

**Propagation Delay**
The time difference between when the transitional input reaches 50% of its final value and when the output reaches 50% of its final value.
     
     - There should be no negative delay in the charecterization, This can be taken care by setting a proper threshold point.

```
    Propagation delay = time(out_fall_thr)-time(in_rise_thr)

```

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/c8f98fae-8ade-471f-a7fb-b7a9479255c5)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/819ff391-1674-4184-8a13-4f77156c58a7)


**Transition Time**
The time it takes the signal to move between states is the transition time , where the time is measured between 10% and 90% or 20% to 80% of the signal levels.

```
Rise transition time = time(slew_high_rise_thr) - time (slew_low_rise_thr)
```

```
Fall transition time = time(slew_high_fall_thr) - time (slew_low_fall_thr)
```

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/4db2b129-ac3c-47b5-9036-0ebcaae936de)




[Back to COURSE](https://github.com/nithinkolar/pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 3: Design library cell using magic layout and ngspice characterization </summary>
<br>

# 1) LABS FOR CMOS INVERTER NGSPICE SIMULATIONS

   ### L1) IO Placer revision
   
   ### L2) Spice deck creation for CMOS inverter
             - Create a SPICE DECK first
             - > Connectivity information about the netlist
             - > Set a component values
             - > Identify the nodes
             - > Name the nodes


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/0a579b79-e515-4ab5-9290-2e884bb0f704)


             SPICE DECK = ***Model description***
                          ***Netlist Description***
                          M1 out in vdd vdd pmos w=0.375u L=0.25u
                          M2 out in 0 0 nmos w=0.375u L=0.25u
                          
                          cload out 0 10f

                          Vdd vdd 0 2.5
                          Vin in 0 2.5
                          
                          *** Simulation commands ***
                          .op
                          .dc Vin0 0 2.5 0.05

                          *** .include tsmc_0.25um_model.mod ***
                          .LIB "tsmc_0.25um_model.mod" CMOS_MODELS
                          .end
                          
                          
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/1a5c35e6-4863-4e0e-8ad7-f82262bd299d)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/8b9e08d8-2625-4ab2-8192-5c08496d6c4f)

   
   ### L3) Spice simulation lab for cmos inverter
                  - Spice simulation for a particular specification
                  
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/00712f88-fab6-4aac-9d8a-0afded87e25e)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/1c8b5f86-9929-429a-b96d-2c9b370e1085)


   ### L4) Switchin threshold vm
            - The CMOS on the right side has a bigger size than the one on the left.
            - These waveforms tell us that the CMOS is a very robust device. The characteristics of the CMOS are maintained across a variety of sizes.
            - The arrow is pointing to the point where 'Vin = Vout'.

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/75b15702-eb56-4b76-bb4a-f51f7f1b5442)

            - Above graph gives details on each point and its significance
            

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/2c9c0f9c-ac07-49f2-b5e5-9fce5bd8c4a7)


         - 
   ### L6) Lab steps to gitclone vsdstd cell design
            - We need to perform a git clone here from a repository that we require, to do the future labs.
            - We can type the following command
                  ```
                  git clone https://github.com/nickson-jose/vsdstdcelldesign.git
                  ```

            - Now we need to copy the 'sky130A.tech' file into the directory we just cloned
            - We can do this by using
                  ```
                  cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
                  ```
                  ```
                  magic -T sky130A.tech sky130_inv.mag & 
                  ```  
             in the follwoing directory shown in the figure


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/9518a0c0-29ec-485b-bc64-4d835fec0217)


  
## 2) INCEPTION OF LAYOUT CMOS FABRICATION PROCESS

### L1) Create Active Regions
           - Selecting a subsrate ( p-type, High resistivity, Doping level,oreintation )
           - Creating active region for transistors
                     - Step1 -> Deposit the kayer of photo resist
                     - Step2 -> Mask1 the region (protecting)
                     - Step3 -> So the UV rays doesnt hit the photoresist layer which is under Mask.
                     - Step4 -> Silicon layer is etched off in the Non masking region.
                     - Step5 -> Remove the Photoresist
                     - Step6 -> Placed in an oxidation furnance
                     - Step7 -> Isolation area will be created This process is called as LOCUS.
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/d5f98bef-3af9-4ee8-8b04-bcccfdaf593d)




![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/0b6f57ba-0ea6-4cb3-8d5a-63ee9f2c7fb4)


### L2) Formation of N-well and P-well
                   - Step1 -> Photoresist the Layer
                   - Step2 -> Mask2 in the required region
                   - Step3 -> Expose the photoresist to UV rays
                   - Step4 -> Non masking area will be wanished
                   - Step5 -> Create a P-well ,It is created by using BORON
                   - Step6 -> Create a N-well ,It is created by using Phosphorous
                   - Step7 -> Take the complete structure into High Temperature Furnace
                   - Step8 -> This diffuses the wells and make proper n-well and p-well, This is called as twin tub process

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/3aaf67b7-a70e-44c9-a1c2-d264ae0d8fa7)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/13067044-9c45-453b-a785-6379add36ccc)



### L3) Formation of gate terminal
                   - Step1 -> Gate formation involves depositing a gate oxide
                   - Step2 -> Defining gate patterns using photolithography
                   - Step3 -> Depositing gate material
                   - Step4 -> Etching to create gates
                   - Step5 -> Doping the substrate and insulating the gates.

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/207d604f-6cb4-4482-a8bb-19573451a6b5)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/b08aba6c-ee0d-4382-af4b-da6472d81af2)



### L4) Ligtly dopped drain (LDD) formation
                   - Lightly doped drain (LDD) formation involves implanting the drain and source regions of a MOSFET transistor with a lighter concentration of dopants to reduce hot 
                     electron effect and short channel effect and enhance device performance.
                   - Doing both  n+ impantation and p+ implantation.
                   - It involves plasma etching here
                   
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/297c8a84-4b71-4ad5-b1bd-31a3ebbc3ce5)



![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/e4e8b7fe-013e-44c1-824b-08559bf4eed4)

                            
### L5) Source and drain formation
                  - Source and drain formation in a MOSFET transistor typically involves doping the silicon substrate with chemicals such as arsenic or phosphorous for n-type regions 
                  (source and drain) and boron for p-type regions (source and drain).
                  - Here the source and drain are done by using ARSENIC method
                  - High temperature annealing is performed.

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/63fac5dd-abcd-4396-93e4-71cc5dd0dcfb)



![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/be252a62-261b-4e59-8888-141da477a911)


### L6) Local interconnect formation
                  - Steps to form Contacts and Interconnects(local) 
                      - Step1 -> Titanium is deposited with a process known as sputtering. 
                      - Step2 -> Wafer is heated to about 650 - 700 C in an N2 ambient furnace for 60 seconds. 
                      - Step3 -> TiSi2 contacts are formed.  TiN is also formed used for local communication. 
                      - Step4 -> TiN is etched using RCA cleaning.

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/336fd5d8-60e0-4361-ab3e-f2d9f375f44f)

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/6abeb77e-bce1-4551-bcac-ec986da0f9f5)

                      
### L7) Higher level metal formation
                 - Step1 -> Forming contacts and interconnects locally involves depositing a dielectric material like silicon dioxide
                 - Step2 -> Patterning it using photolithography
                 - Step3 -> Eetching contact holes 
                 - Step4 -> Depositing a barrier metal (e.g., titanium or titanium nitride)
                 - Step5 -> Filling with a conductor (e.g., aluminum or copper) using chemical vapor deposition (CVD)
                 - Step6 -> And then planarizing through chemical-mechanical polishing (CMP).

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/2920f5b2-78f6-4743-be52-7184e6a0ceb3)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/928b676a-c68e-4e0a-8651-66d3ddab51e1)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/e5922497-b970-4ed3-b047-44d76d7b7254)


### L8) Lab introduction to Sky130 basic layers layout and LEF using inverter

                - - Now let us look at the layout of a CMOS inverter. To open this we type the command

### L9) Lab steps to create std cell layout and extract spice netlist









[Back to COURSE](https://github.com/nithinkolar/pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 4 : Prelayout timming layout analysis and inportance of good clock tree </summary>
<br>

## 1) TIMMING MODELLING USING DELAY TABLES

### Lab challenge to find missing or incorrect rules and fix them

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/fa55462f-7b65-47f3-a4e5-8e68d129318a)

       - Converting grid info into Track info
       - Go to openlane directory / sky130_fd_sc_hd 
       - type less tracks.info

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/602d9bf5-5e1b-4430-9548-91a638e728f0)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/da8cc22a-50f0-4c1f-87c4-126e468c5c8c)


      - Here 1st value indicates the offset and 2nd value indicates the pitch along provided direction

 
 ### Setting grid values using above file info

        - ext2spice 
        - help grid
        - grid 0.46um 0.34um 0.23um 0.17um

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/a683c3e1-d7d1-4711-8386-018aab673dd5)


### Before grid vs After grid

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/c6cb22f5-3f83-40db-93b5-f58c312bf0a4)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/281679a9-746d-4628-a29c-688af381356c)



![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/70e4797b-07bc-4ef5-84f5-76d2056a818c)

        - From the above pic, its confirmed that the pins A and Y are at the intersection of X and Y tracks. So the first condition is met.
        - The PR boundary is taking 3 grids on width and 9 grids on height which says that the 2nd condition is also met



## GENERATION OF A LEF FILE
        - Once the layout is perfect we can generate the lef file
        - In the tkcon window type the following command to save the updated layout
              > save sky130_vsdinv.mag
        - once it is saved then go to the terminal window and the type 
              > magic -T sky130A.Tech sky130_vsdinv.mag &
        - A magic layout opens , In the tkcon window type 
              > lef write
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/4de5491e-5476-43b0-8b21-0dca3c552fcf)


        - Once this is done lef file should be created in the vsd file

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/91bdddce-da28-4f63-b12d-1a949b4a7e04)


        - To open the lif file type the below command in the terminal
              > less sky130_vsdinv.lef

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/e0991f65-6643-440d-9f4a-82b7bf6c078a)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/2f6141f0-aee0-44f4-99c2-0e1dc4b3a129)


## STEPS TO INCLUDE NEW STEPS IN THE SYNTHESIS

        - Open the picorv32a pwd in the terminal
        - copy the path 

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/e7915f78-3988-4446-b856-157a8e463079)

        - Go to the vsdstdcelldesign in the other terminal type 
              > cp sky130_vsdinv.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/8005ee44-8af2-42a2-9a8f-2ba7dcf19f70)

        - Now if u check in the picorv terminal, the lef file will be copied 

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/f4aab1a1-5f67-4973-8545-2b5ce7e84d70)


        - Modify the config.tcl by
             > vim config.tcl
        - In the design's config.tcl file add the below line to point to the lef location which is required during spice extraction.
               > set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
        - Include the below command to include the additional lef into the flow:
               > set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
               > add_lefs -src $lefs
        - Run the interactive mode 

        - Once the synthesis is successfull we get the following output
        - To run the floorplans and placements we typr the following commands
                > run_floorplan
                > run_placement

        - magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/7a52f164-bd7f-44a4-902d-48c900fc7e25)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/2b881a1f-2c7b-4061-a832-cdb7dd8a21d4)


## TIMMING ANALYSIS WITH REAL CLOCKS USING OPEN STA

         - Configure OpenSTA for Post-Synth Timing Analysis
         - We must create two files
              - The first one must be in the openlane directory
              - This file is known as the 'pre_sta.conf' file.

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/52bd3084-209f-4127-bf1f-3b8584be01c9)


              - The second is the my_base.sdc file.
              - This should be in the 'src/sky130' directory under the picorv32a directory.
             
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/b41c0c91-3554-4274-8b4a-5dbbb9deb6b3)

              - To run tyming analysis we type 
                    > sta pre_sta.conf

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/f08b2dc2-f795-4349-818c-8f87cde2458f)


             - There is a slack violation
             - Settinf MAX_FANOUT value to 4 reduces the slack violation.
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/6eee637f-87bd-4e8d-865e-8327f68b895b)


## Clock Tree Synthesis TritonCTS and Signal Integrity
### Run CTS

             -  To run CTS we need to type the command
                       > run_cts
                       > New .v is created

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/7e59f5cd-b2d1-41ba-a487-9b5421ad567e)

#### Timing Analysis with Real CLocks using OpenSTA

             - First we type the command 
                    > openroad.
             - Then we read the .lef file using the command
                    > read_lef /openLANE_flow/designs/picorv32a/runs/16-09_19-58/tmp/merged.lef

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/54c1ce7b-efb8-46f4-8c38-e3f97f7bb655)

              - Then we read the .def file.
                     > read_def /openLANE_flow/designs/picorv32a/runs/16-09_19-58/results/cts/picorv32a.cts.def


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/6dc7446a-7a86-4216-83ec-7344c29f54ac)

              - Then we type the below commands
                     > write_db pico_cts.db
                     > read_db pico_cts.db
                     > read_verilog /openLANE_flow/designs/picorv32a/runs/16-09_19-58/results/synthesis/picorv32a.synthesis_cts.v
                     > read_liberty -max $::env(LIB_SLOWEST)
                     > read_liberty -max $::env(LIB_FASTEST)

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/fe0fde4b-5d4f-4a80-9c22-dac80968c88b)

              - We read the .src file
                    > read_sdc /openLANE_flow/designs/picorv32a/src/sky130/my_base.sdc

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/f12dcd3c-a93f-41ad-aa0e-0fdeec4a5e7b)


              - We set the clock and then check it
                    > set_propagated_clock [all_clocks]
                    > report_checks -path_delay min_max -format full_clock_expanded -digits 4

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/b12af459-13e1-4baa-93d1-ec490dfdbbb5)



![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/3f0e2cec-c21f-430b-a607-982dadd3f87f)


              - We perform it again for the more accurate result
              
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/5b73f478-c4e7-401a-8b74-1b97502de832)


![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/9c442148-ebab-4836-a206-6195bb34d13a)



![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/199dab35-c6ed-4a1e-8dd1-ef4be013d32b)

              -  Next type the following commands 
                   > report_clock_skew -hold
                   > report clock_skew -setup

![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/e5e8a384-fe0c-4b63-92a8-db1f6f6ec3df)


[Back to COURSE](https://github.com/nithinkolar/pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 5 : Final steps for RTL2GDS using triton route and openSTA </summary>
<br>

## Power Distribution Network and Routing

After generating our clock tree network and verifying post routing STA checks we are ready to generate the power distribution network gen_pdn in OpenLANE:

     The PDN feature within OpenLANE will create:

          Power ring global to the entire core
          Power halo local to any preplaced cells
          Power straps to bring power into the center of the chip
          Power rails for the standard cells

   ### Build Power Distribution network
   
![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/f6061eef-02f9-4f41-801f-b8a89a6a4bd6)



![image](https://github.com/nithinkolar/pes_openlane_work/assets/145356962/31fa2edb-fb47-4d6d-b564-b0cee84cac48)

   ### Global and Detailed Routing

   - OpenLANE uses TritonRoute as the routing engine run_routing for physical implementations of designs. Routing consists of two stages:
           > Global Routing - Routing guides are generated for interconnects on our netlist defining what layers, and where on the chip each of the nets will be reputed
           > Detailed Routing - Metal traces are iteratively laid across the routing guides to physically implement the routing guides

   - If DRC errors persist after routing the user has two options:
           > Re-run routing with higher QoR settings
           > Manually fix DRC errors specific in tritonRoute.drc file

  ### SPEF Extraction

    - After routing has been completed interconnect parasitics can be extracted to perform sign-off post-route STA analysis. The parasitics are extracted into a SPEF file. The SPEF extractor 
      is not included within OpenLANE as of now.
           > cd ~/Desktop/work/tools/SPEFEXTRACTOR
           > python3 main.py <path to merged.lef in tmp> <path to def in routing>
    - The SPEF File will be generated in the location where def file is present


[Back to COURSE](https://github.com/nithinkolar/pes_Openlane_work/tree/main#course)

# nasscom_vsd_soc_design_workshop
# Contents
 <div class="toc">
  <ul>
    <li><a href="#header-1">Day 1 - Inception of open-source EDA, OpenLANE and sky130 PDK</a></li>
	<ul>
        <li><a href="#header-1_1"> How to talk to computers</a></li>
		<ul>
			<li><a href="#header-1_1_1">Introduction to QFN-48 Package, chip, pads, core, die and IPs</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_1_2">Introduction to RISC-V</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_1_3">From Software Applications to Hardware</a></li>
		</ul>
      </ul>
      <ul>
        <li><a href="#header-1_2">Soc design and OpenLANE</a></li>
	      <ul>
			<li><a href="#header-1_2_1">Introduction to all components of open-source digital asic design</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_2_2"> Simplified RTL2GDS flow</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_2_3">Introduction to OpenLANE and Strive chipsets</a></li>
		</ul>
	      <ul>
			<li><a href="#header-1_2_4">Introduction to OpenLANE detailed ASIC design flow</a></li>
		</ul>
      </ul>
	<ul>
        <li><a href="#header-1_3">Get familiar to open-source EDA tools</a></li>
		<ul>
			<li><a href="#header-1_3_1">OpenLANE Directory structure in detail</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_2">Design Preparation Step</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_3">Review files after design prep and run synthesis</a></li>
		</ul>
	      <ul>
			<li><a href="#header-1_3_4">OpenLANE Project Git Link Description</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_5">Steps to characterize synthesis results</a></li>
		</ul>
      </ul>
   </div>





<div class="toc">
  <ul>
    <li><a href="#header-2">Day 2 - Good floor planning considerations</a></li>
	<ul>
        <li><a href="#header-2_1"> Chip Floor planning consideration</a></li>
		<ul>
			<li><a href="#header-2_1_1">Utilization factor and aspect ratio</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_2">Concept of pre-placed cells</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_3">De-coupling capacitors</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_1_4">Power planning</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_5">Pin placement and logical cell placement blockage</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_6">Steps to run floorplan using OpenLANE</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_7">Review floorplan files and steps to view floorplan/a></li>
		</ul>
	      <ul>
		      <li><a href="#header-2_1_8">Review floorplan layout in Magic</a></li>
		</ul>
      </ul>
      <ul>
        <li><a href="#header-2_2">Library building and Placement</a></li>
	      <ul>
			<li><a href="#header-2_2_1">Netlist binding and initial place design</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_2">Optimize placement using estimated wire-length and capacitance</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_3">Final placement optimization</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_2_4">Need for libraries and characterization</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_5">Congestion aware placement using RePlAce</a></li>
		</ul>
      </ul>
	<ul>
        <li><a href="#header-2_3">Cell design and characterization flows</a></li>
		 <ul>
			<li><a href="#header-2_3_1">Inputs for cell design flow</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_3_2">Circuit design steps</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_3_3">Layout design step</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_3_4">Typical characterization flow</a></li>
		</ul>
      </ul>
	  <ul>
        <li><a href="#header-2_4">General timing characterization parameters</a></li>
		   <ul>
			<li><a href="#header-2_4_1"> Timing threshold definitions</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_4_2">Propagation delay and transition time</a></li>
		</ul>
      </ul>
</div>

   


# <h1 id="header-1">Day 1 -Inception of open-source EDA, OpenLANE and sky130 PDK</h1>	 
## <h1 id="header-1_1">How to talk to computers?</h1>
### <h1 id="header-1_1_1">Introduction to QFN-48 Package, chip, pads, core, die and IPs</h1>

**Arduino Board**:- This is an arduino microcontroller board. An open-source platform called Arduino is used to create electronics projects. The Arduino system comprises of a physical programmable circuit board, often known as a microcontroller, and an IDE (Integrated Development Environment) software that runs on your computer and is used to write and upload computer code to the board.The Arduino platform has become quite popular with people just starting out with electronics, the Arduino does not need a separate piece of hardware (called a programmer) in order to load new code onto the board -- you can simply use a USB cable. 

![image](https://github.com/user-attachments/assets/ae6cb680-bded-469d-b438-1f51ddf703e7)




**EX. Processor/SoC**:- Along with this Processor / SOC we had so many interfaces like It consist of SRAM,SOC,ADC,DAC,SPI these all are called foundary IP's.vAll devices depends upon foundary where all chips are fabricated using deposition and lithography techniques , here we follow several steps to follow the chip like 
--Crystal growth and wafer preparation
--Epitaxy
--Dielectric and polysilicon film deposition
--Oxidation
--Lithography
--Dry etching 
--Ion implantation and diffusion
--Annealing
--Silicon deposition
--Metallization
--Testing

![image](https://github.com/user-attachments/assets/2c49e6e5-1d94-4a66-be2f-9e551ace344d)

#### chip components 
if you open the IP'S it looks like as shown below , he width and breadth dimesion is 7mm*7mm
![image](https://github.com/user-attachments/assets/c4535ad3-3a0d-4da7-8bc2-63b31fc4f17b)

Inside the chip several components like pads, core, die 

(1) **Pads:** Through which we can send the signal outside/insede the chip.

(2) **Core:** Place digital logic cells like OR,AND,MUX ..  where all the logic gates are fixed.

(3) **Die:** Present at the corner. it is the size of the entire chip and Its manufacture on the silicon wafer.


![image](https://github.com/user-attachments/assets/2b86e1fe-8fbf-4d12-901d-06f9095c31f3)




### <h1 id="header-1_1_2">Introduction to RISC-V</h1>
RISC-V, where five refers to the number of generations of RISC architecture that were developed at the University of California, Berkeley. RISC is an open standard instruction set architecture (ISA) based on established RISC principles. Unlike most other ISA designs, RISC-V is provided under open source licenses that do not require fees to use. A number of companies are offering or have announced RISC-V hardware, open source operating systems with RISC-V support are available, and the instruction set is supported in several popular software toolchains.

The instruction set is designed for a wide range of uses. The base instruction set has a fixed length of 32-bit naturally aligned instructions, and the ISA supports variable length extensions where each instruction can be any number of 16-bit parcels in length. The instruction set specification defines 32-bit and 64-bit address space variants. The specification includes a description of a 128-bit flat address space variant, as an extrapolation of 32 and 64 bit variants, but the 128-bit ISA remains "not frozen" intentionally, because there is yet so little practical experience with such large memory systems.
Chip is connected to the package with the help of bond wires.




### <h1 id="header-1_1_2">From Software Applications to Hardware</h1>
Here we observe how application software enters into the system software?

Application Software -----> System Software ------> Hardware chip

Apps enters into a system software and system software converts the application  program  into binary language. There are some layers inside the system software whish are as follows
the application software like chrome ,caluclator,ms office..etc 


**Operating System, Compiler, Assembler**


The operating system manages low-level system functions, memory allocation, and input/output operations.

 The compiler transforms the operating system's C, C++, and Java output into instructions. These guidelines rely on the hardware.

 Assembler take the instructions from compiler and convert them into respective binary numbers. This binary language now send to hardware and hardware performs ouput based on the function it recieve and gives the output.
 
Instruction acts as abstract interface between C-language and the hardware.

![image](https://github.com/user-attachments/assets/b5bcf26e-e0e2-4eb5-999a-663c0e30c3e2)

The output of OS is nothing but small functions in C,C++, JAVA those will taken by the respective compiler and converted into instructions. The syntax of this instructions belongs to respective hardware ,take those instructions into assembler converts to 0 & 1 binary (machine language)

![image](https://github.com/user-attachments/assets/55fc1ce9-451b-4cc4-a991-aa0ed1fd2ec7)

![image](https://github.com/user-attachments/assets/66bee196-ad70-49c5-94a2-1ccd7e957d7d)

 
 

 ## <h1 id="header-1_2">Soc design and OpenLANE</h1>
### <h1 id="header-1_2_1">Introduction to all components of open-source digital asic design</h1>
To design Digital ASIC, few tools or things which are required from the day one. These are

**RTL Design
EDA tools
PDK data**

1[image](https://github.com/user-attachments/assets/2dcfc710-3ea7-4c27-a0d3-1fd78839404b)
**RTL design?**
Register-transfer level (RTL) is a design concept used in digital circuit design that describes how digital signals (data) move between hardware registers and how logical operations are applied to those signals in a synchronous digital circuit and asynchronous digital circuits.There are numerous open sources available for this design. like, librecores.org, opencores.org, github.com, etc...

**EDA tools?**
The tools used to design and validate printed circuit boards (PCBs), integrated circuits (ICs), and electronic systems are referred to as electronic design automation, or EDA, in general. many open sorces tools are available like Qflow, OpenROAD, OpenLANE, etc...

**PDK Data?**
PDK is process design kit. It is interface between FAB and design. This data is collections of files like,
process design rules: DRC, LVS, REX
Digital standerd cell libreries
i/o librerirs

for the EDA tools used in IC design, for the purpose to simulate the fabrication process. Utilizing Skywater technology, for for example, Google released the open source PDK for FOSS 130nm manufacture in 2020. Yet, it's currently at the 5-nm cutting age as well. However, compared to CPUs with 130nm architecture, the advanced node is more expensive and not necessary in many applications. The CPUs made at 130 nm are likewise quick. for example,

intel: P4EE @3.46 GHz(Q4'o4)

sky130_OSU (single cycle RV32i CPU) pipeline version can achieve more than 1 GHz clock.

### <h1 id="header-1_2_2"> Simplified RTL2GDS flow</h1>

![image](https://github.com/user-attachments/assets/9a765d05-80db-4423-9348-52d3fb0f5a55)



**Step 1. Synthesis**:-  In the synthesis, the design RTL is translated to a circuit out from the SCL. The resultant circuit is describes in HDL and usualy refered to the gate level netlist. the gate level netlist is functionaly equivelent to the RTL. "standard Cells" have regular layouts like Electrical. HDL,SPICE.

![image](https://github.com/user-attachments/assets/0abaab30-e279-49ca-93f2-f1ad03b00456)

                             standard cell
![image](https://github.com/user-attachments/assets/075a852a-6bab-4767-a657-74a70d6af7aa)

**Step 2. Floor/Power Planning**:-The main objective here is that to plan silicon area and distribute the power to the whole circuit. In the chip floor planning, the partition chip die between different system building blocks and place the i/o pads. In micro floor planning, we define the dimensions, pin locations, rows.
In power planning, the power network is connstructed. tipically, the chip is power by multiple VDD and GND. so, total components are connected to power supply horizontaly and vertically by metal streps. here parallel structures are used to reduce the resistance. To address the electromagnetization problem, power distribution network uses upper metal leyers, which are thicker than lower metal layers. Hence have less resistance.
![image](https://github.com/user-attachments/assets/cd3eadc6-5445-4fe4-b6bf-385cef8d07eb)
macro planning
![image](https://github.com/user-attachments/assets/72c41402-e8d6-497f-be33-f2af76b02c40)
power planning
![image](https://github.com/user-attachments/assets/7f9ddea1-10b1-467f-b6b3-b74353b5be14)



**Step 3. Placement**:- In this process, we place the gate level netlist on the floor planning rows, alligned with the sites. cells should be placed very closed to eachother to reduce the interconnnect delay. Usually placement is done in 2 steps:


**Global placement**:- It is very first stage of the placement where cells are placed inside the core area for the first time looking at the timing and congestion. Global Placement aims at generating a rough placement solution that may violate some placement constraints while maintaining a global view of the whole Netlist.

**Detailed placement**:- In detailed placements, we determined the exact route and layers for each netlist. the objective of detailed placement is valid routing, minimize area and meet timing constrains. Additional objective is minimum via and less power.
![image](https://github.com/user-attachments/assets/0f663770-f269-4c45-8003-c39dc25dbb06)




**Step 4. Clock Tree Synthesis**:- Before routing the signals, we have to route the clock. In the process of clock synthesis, we have distribute the clock to the every sequential elements. for example flipflops, registers, ADC, DAC ete. basically clock netwroks looks likes a tree. where the clock source is roots and the clock elements are end leaves. Synthesization should be done in a manner that with minimum skew and in a good shape.To minimize the clock skew by using the low-skew global routing resources for clock signals.Microsemi devices provide various types of global routing resources that significantly reduce skew.Usually a tree is a H tree, X tree etc.
![image](https://github.com/user-attachments/assets/be9b3be0-89eb-4791-a46f-4d249b28ecc4)



**Step 5. Routing**:- After routing the clock, the signal routing comes. Making physical connections between signal pins using metal layers are called Routing. Routing is the stage after CTS and optimization where exact paths for the interconnection of standard cells and macros and I/O pins are determined. There are two types of nets in VLSI systems that need special attention in routing:
![image](https://github.com/user-attachments/assets/609003d9-2d6d-43ca-a080-33cbbda9bdcc)

Clock nets
Power/Ground nets
The sky130 PDK defines the 6 routing leyers. the lowest leyer is called local interconnect layer (titanium nitride layer). Other five layers are alluminium layersIn the proccess of routing, metal trackes forms a routing grids and these grids are huge. so, devide and conquer approach is use for routing. The two types of routing is used:

**Global routing:** Generates the routing guides

**Detailed Routing:** Uses the routing guides to implement the actual wiring.



**Step 6. Sign Off**:- Once the routing is done, we can construct the final layout. This final layout will goes under the verification. Two types of verifications are there:

Physical verification: Here design rule checking will done and it will check the final layout and owners layout
Timing Verification: Here Static Timing Analysis will done.


### <h1 id="header-1_2_3">Introduction to OpenLANE and Strive chipsets</h1>

OPENLANE is an automated RTL to GDSII flow that is composed of several tools such as OpenROAD, Yosys, Magic, Netgen, Fault, CVC SPEF-Extractor, CU-GR, Klayout and a number of scripts used for design exploration and optimization. It is started as an Open-source flow for a true Open Source tape-out Experiment. striVe is a family of open everything SoCs:
Open PDK, Open EDA, Open RTL

striVe SoC Family


The main goal of OPENLANE is to produce a clean GDSII with no human intervation (no-human-in-the-loop). here the meaning of clean is that:

No LVS violations

No DRC Violations

No timing Violations

OPENLANE is tuned for skyWter130nm open PDK. it can be used to harden Macros and chips.there is two mode of operation
Autonomus : it is the push botton flow. with the push botton , it is a some time base design and due to this push botton, we get final GDSII

interactive : here we can run comamds and steps one by one.

It has large number of design examples(43 designs with their best configurations).


### <h1 id="header-1_2_4">Introduction to OpenLANE detailed ASIC design flow</h1>



The design exploration utility is also used for regression testing(CI). we run OpenLANE on ~ 70 designs and compare the results to the best known ones.

**DFT(Design for Test)**
it perform scan inserption, automatic test pattern generation, Test patterns compaction, Fault coverage, Fault simulation.After that physical implementation is done by OpenROAD app. physical implementation involves the several steps:

Floor/Power Planning

End Decoupling Capacitors and Tap cells insertion

Placements: Global and Detailed

Post Placement Optimization

Clock Tree synthesis (CTS)

Routing: Global and Detailed

Every time the netlist is modified.(CTS modifies the netlist and Post Placements optimization also modifies the netlist).so for that verification must be performed. The LCE(yosys) is used to formally confirm that the function did not change after modifying the netlist. ### Dealing with antenna rules Violation: when a metal wire segment is fabricated, it can act as antenna.as an antenna, it collect charges which can demaged the transister gates during the fabrication.



To address this issue, we have to limit the lenght of the wire. usually this is the job of the router. If router fails to do this, then there are two solutions:
Bridging attaches a higher layer intermediary.Add antenna diode cell to leak away charges.(Antenna diodes are provided by the SCL)




With OpenLANE, we took a preventive approach. here we add fake antenna diode next to every cell input after placement. Then run the Antenna checker on the routed layout. If the checker reports a violation on cell input pin, replace the fake diode cell by a real one.




**Static Timing analysis(STA)**
It involves the interconnect RC Extraction(DEF2SPEF) from the routed layout, followed by STA on OpenSTA(OpenROAD) tool. resulting report will shows the timing violations if any violations is there.

**Physical Verification (DRC and LVS)**
Magic is used for design Rules checking and SPICE Extraction from Layout. Magic and Netgen are used for LVS.



## <h1 id="header-1_3">Get familiar to open-source EDA tools</h1>
### <h1 id="header-1_3_1">OpenLANE Directory structure in detail</h1>
**Basic Linux Commands how to use in our workshop**

**pwd**: it gives the present working directory

**mkdir** : to create a new directory

**cd** : opens the particular directory

**cd ../** :goes to 1 directory back 

**cd ../../../** :goes to 3 directory back

**ls** : lists all the files and directories in the current working directory

**ls-ltr** :to list all the files and directories in linux practice directories in long listing format and according to time they are created

**command --help** : shows the complete use that command

**clear** : clears the terminal screen

Here we are working in Sky130_fd_sc_hd PDK varient. where, "sky130" is process name or node name."fd" is a foundary name (skyWater foundary)."sc" means standerd cell librery files and the last one "hd" stands for high density(basically one type of varient).

Sky130_fd_sc_hd varient contains many technology files like verilog, spice, techlef, meglef,mag,gds,cdl,lib,lef,etc. (techlef file contains the layer information).


### <h1 id="header-1_3_2">Design Preparation Step</h1>
when we enter in the OpenLANE, we have to use flow.tcl because as a name says, it will goes with the flow using the script. And by using interactive switch, we will do step by step process. without interactive switch, it will run complete flow from RTL to GDSII. Now OpenLANE is open and we can see that prompt will change now.

![image](https://github.com/user-attachments/assets/ed3aed35-fe5f-460e-b782-60dfd92f18df)

Now we have to input all the packages which required to run the flow.

![image](https://github.com/user-attachments/assets/46d2cc3c-9591-4729-ad8d-745464d16a36)

Now, here we are ready to execute the command.

Now, if we are going into the design folder in openlane, there are nearly 30-40 designs are already builted. Out of them we can open any of the design. for example, here we are opening the picorv32a.v design. In this design we can see many files are available. i.e., scr, config.tcl, etc. This config.tlc file contains every details about the design. for example, details about enrollment, clock period, clock period port etc.

![image](https://github.com/user-attachments/assets/bccf2262-0883-4353-8574-84afd9771cdd)

Here we can see that the time period is set to the 5.00 nsec. but is we see in the openlane sky130_fd_sc_hd folder, the period is set about 24 nsec. so it is not override to the main file. If it override then give first priority to the main folder.

Now, in openlane, we are going to run the synthesis, but before synthesis, we have to prepare design setup stage. for that command is ``` prep -design picorv32a```

![image](https://github.com/user-attachments/assets/38c6ad67-84c4-4525-9fea-ac6c57e292e2)

so, here it is shown that preparation is completed.


### <h1 id="header-1_3_3">Review files after design prep and run synthesis</h1>

After completing the preparation, in the picorv32a file, the run terictory is created. Inside the folder, Today's date is created. so in this terictory some folders are available which is required for openlane.

In the temp file, merged.lef file is available which was created in preparation time. if we open this merged.lef file, we get all the wire or layer level and cell level information.

![image](https://github.com/user-attachments/assets/5d7ce5a1-7e51-48c5-9fb3-523f0e6ef024)

While, in the result folder is empty because till we have not run anything and in the report folder all the folders are there about synthesis, placement, floorplanning,cts,routing,magic,lvs.

now here also one config.tcl file is available similar like design folder. But this config.tcl file contains all default parameter taken by the run.

when we make some change in the origional configuration and then we run, for example if we make a change in core utilization in the floorplanning and then we run the floorplanning, at this time in the congig.tcl file, the core utility will change and by cross checking it we can check that the modification is reflected in the exicution or not.

Now coming to the openlane, we are going to run the synthesis. for that command is ```run_synthesis``` It will take some 3-4 mnts to run the synthesis and finally synthesis will complited.

![image](https://github.com/user-attachments/assets/3424573b-ed06-4832-b089-a555c98ff989)



![image](https://github.com/user-attachments/assets/87c93d2c-d905-48e1-bb16-eead8d1575db)

### <h1 id="header-1_3_5">Steps to characterize synthesis results</h1>

From the data of synthesis, total number of counter D_flip-flops is 1613. and the number of cells is 14876.

![image](https://github.com/user-attachments/assets/5bab437f-71d6-4637-b009-8b4be8c05c09)

So, the flop ratio = (number of flip flops)/(number of total cell).

So, the flop ratio is 10.84%.

Before run, we saw that the result folder is empty. but now, after running the synthesis, we can see that all the mapping have been done by ABC.

![image](https://github.com/user-attachments/assets/35ecdff6-d6ef-43e9-9e6c-5492538b3cc0)

And in the report, we can see when the actual synthesis has done. and the actual statistics synthesis report is showing below, which is same as what we have seen before.


![image](https://github.com/user-attachments/assets/2cc3cee5-62f3-42a0-977f-f3e8f7fbb816)








# <h2 id="header-2">Day 2 - Good floor planning considerations</h2>	 
## <h2 id="header-2_1">Chip Floor planning consideration</h2>
### <h2 id="header-2_1_1">Utilization factor and aspect ratio</h2>

We shall attempt to conceal Core and Die's width and height in this section. Determining the width and height is the initial stage in the physical design flow. First, let's look at a netlist, which consists of two flipflops with a straightforward combination logic in between. An electronic design's connectivity is described by a netlist. Here, we rely on the specific flipflop's dimensions as well as the size of the logic gates (AND & OR). Let's translate the symbols into actual dimensions now. The dimensions of the Die and Core are what matter to us, not the wires' dimensions. 

Let's standard cell have dimensions of 1unit*1unit

So, area= 1 Sq. units

Use the same space for the flip-flop as well = 1 Sq. units

with help of these dimensions and netlist let's calculate the area occupied by the netlist on a silicon wafer.
![image](https://github.com/user-attachments/assets/f19dcbea-27c6-4f82-9c38-e3b8818dfa17)

![image](https://github.com/user-attachments/assets/a68ab1b0-093e-4e50-a74a-25214d87d4d)

Befor that will remove all the wires and bring all the flip flops and logic gates in a single plate. So after combining them together width and length will be 2 Sq. units each and if we calculate the total area the it will be 4 Sq. units. So now we have the rough calculation of minimum area occupied by the netlist.

![image](https://github.com/user-attachments/assets/e4858796-507e-44a1-8c5a-3981d6b09148)

What is 'Core' and 'Die' section of a  chip?

Let's have a silicon wafer on which all the logics are implemented. In thes one section is refered as 'Die' and inside the Die we have the Core. 

A **Die** which consists of core, is small semicondcutor material  specimen on which the fundamental circuit is fabricated.

A '**Core** is the section of the chip where the fundamental logic of the design is placed.

![image](https://github.com/user-attachments/assets/8bb7e18f-0ba4-41b2-8e86-639a8f11f693)

Now, Let's try to place that particular logic inside the core. The netlist will occupy the whole area inside the core it means it utilizes the core 100%. From this we can calculate the utilisation factor which is given by,

            Utilization Factor = Area occupied by netlist / Total area of the core
	   
     lets put the dimensions we have, we get
     
     Utilization factor = 4*1sq.unit / 2unit *2unit
     
			= 4sq unit /  4sq unit

So, utilization factor = 1 (It means core has utilized all the area and no spane left)

Aspect Ratio = Height /  width =  2 unit /  2unit =  1

Whenever Aspect Ratio is 1 it signifies that chip is square shaped. When it is not 1 it means the chip is in rectangular shape.

![image](https://github.com/user-attachments/assets/540d6978-a273-4907-bd7b-7748fe350a28)

For example, Lets take another dimensions of the width= 4unit and height = 2unit. So from the above formula of utilization factor we it equal to 0.5 which means the chip has not covered the whole area of the core and aspect ratio is also 0.5  which means the chip is rectangular in shape.

The leftover area can be used to placed some additional cells like buffers or something else.

![image](https://github.com/user-attachments/assets/0786334d-3ebf-4d7d-b8f1-29707ec17487)


### <h2 id="header-2_1_2">Utilization factor and aspect ratio</h2>

Lets take another example for a square chip wth dimensions 4*4 sq units. We will get utilization factor= 0.25 it means out of the whole chip area only 25% area is utilized by the netlistand 75% is available for additional cells which can be use for routing in which we will have layering. Aspect ratio we get = 1 it means chip is square in shape.

![image](https://github.com/user-attachments/assets/a837d757-4701-4ee2-8fae-7cfe9357d9d8)

**Define locations of Preplaced Cells**:-  Lets take a combinational logic which does some amount of function and assume its a huge circuit having some N Logic gates so let's devide it into some small numbers of gates. We will cut the whole circuit into two parts, and separate both of them into two blocks and both block will be implemented seperately.

![image](https://github.com/user-attachments/assets/6e0760f2-a78b-4138-95f8-1a416a900d85)

In both the blocks lets extend the input output pins and now we will black box the boxes and detached them. After black boxing, the upper portion is invisible from the top or invisible to the one , who is looking into the main netlist. now will seperate them out as two different IP's or modules.

![image](https://github.com/user-attachments/assets/4f08478e-7b25-4e38-ad9b-2d01eebc6f10)

Advantage of doing this is we can reuse them multiple times after implimenting once only. Similary there are other IP's also available for eg. Memory, Clock-gating cell, Comporator, MUX  all of these are part of the top level netlist.They recieve some signals and perform functions and deliver the outputs but the functionality of the cell is implemented only once. 

The arrangement of these IP's in a chip is refferd as **floorplanning**.

These IP's have user-defined locations, and hence are placed in chip before automated placement and routing are called **"pre-placed cells"**. 

These cells are placed in such a way that, the placement and routing tool do not touch the location of the cell.


### <h2 id="header-2_1_3">De-coupling capacitors</h2>

**surround pre-placed cells with Decoupling capacitor**:- Let consider some circuit, which is the part of the blocks which has been described earlier. When some gate (let consider AND gate) switched from 0 to 1 or 1 to 0, considered amount of the switching current required because of available small capacitance . This capacitor should be completely charged to represent logic 1 and completly discharged to represent logic 0. Consider capacitance to be 0. Rdd,Ldd,and Lss are well defoned values. During switvhing operation, the circuit demands switching current i.e. peak current. Now, due to the presence of Rdd and Ldd, there will be a voltage drop across them and the voltage at Node 'A' would be Vdd' instead of Vdd.

![image](https://github.com/user-attachments/assets/4ac8e623-d1fb-4677-9e2b-d05ccae19ca9)

So, due to this if ideal logic 1 = 1 volt then here practically it can be less then 1 volt i.e., 0.97 volts (Vdd'). So, for any signal to be considered as Logic '0' and '1' in the NM low and NM high range. It is danger case.

![image](https://github.com/user-attachments/assets/0e1d9a2f-d429-4781-a286-b194e8b7c831)

To solve this problem,, we have to put De-coupling capacitor in parallel with the circuit. Every time the circuit switches, it draws current from Cd, whereas, the  RL network is used to replenish the charge into Cd. And the amount of current needed for the circuit is supplied by the De- Coupling Capacitor.

![image](https://github.com/user-attachments/assets/71e5d571-a9e2-4bf6-ab4b-28d516726044)

In the chip it will look something like shown below Decoupling capacitors are placed in between the block a, block b and block c. So here in this whole block it has been ensured that supply is being done by the de-coupling capacitor. Once we are done with this we have taken care of the local communication.

![image](https://github.com/user-attachments/assets/5cf6d508-0553-4538-ab61-99966657316d)


### <h2 id="header-2_1_4">Power planning</h2>

Now let's consider that local circuitory and keep it as a black box and it can be repeat multiple times and there is some logic present at the boundaries also and the problem of current demand was solved by de-coupling capacitor. There is signal which is send from driver to load and the signal is basically logic 0 to logic 1. Here we need to maintain the particular driver to load line with same signal so that the load recieves the same. Now power supply is applied. Now assume 16 bit bus has to retain the same signal from driver to the load. so it should get the sufficient power from the supply. But at this bus, there is no de-coupling capacitor is available because it is not physible to put capacitor at all over the place. now, power supply is far away from the bus, that is why some voltage drop between them will occur definetly.

 ![image](https://github.com/user-attachments/assets/787a49ff-5bb8-44be-adfa-8aa2c0024b36)


When we say one particular line of 16-bit bus is logic 1 it says that the capacitor is being charged to Vdd, and whenever we say logic 0 it says that the capacitor is discharged to ground.Let consider this 16 bit bus connected to inverter. So, all the capacitor are initially charged will get discharged and vice-versa due to inverter.


![image](https://github.com/user-attachments/assets/d2fed0a3-7e21-4bce-a9e7-004a18c47d5a)


But the problem is occurs due to all capacitor is connected to the single ground. This will cause a bump in 'ground' tap point during discharging. That bump is called as Ground Bounce. If the size of the bump exceeds the noise margin levelit might enter into an undefined state and due to undefined state it can either go to logic 1 or logic 0. So here thing becomes unpredictable

![image](https://github.com/user-attachments/assets/39796acb-d2a2-4761-826a-f05e59c86b2e)


Also , all capacitors which were'0' volts will have to charge to 'V'volts through single 'vdd'tap point. This will cause lowering of voltage at Vdd tap point. As long as this voltage drop is in noise margin level we are good enough but if it goes into an undefined region then things become unpredictable.

![image](https://github.com/user-attachments/assets/903b02e4-1024-4d64-9b91-3e472a8439d0)

The phenomenon we have seen was causing the lowering of the supply voltage,this problem occured because power has applied to one point only. The solution of the problem is use multiple power supply. So, every block will take charge from neartest power supply and similarly dump the charge to the nearer ground. this type of power supply is called **mesh**.

![image](https://github.com/user-attachments/assets/ad067334-6616-4d43-b8dd-85d1d1385d89)


And the power planning is shown below,

![image](https://github.com/user-attachments/assets/9c7bb477-dd38-43f3-bb3a-ce23b577c5e1)

### <h2 id="header-2_1_5">Pin placement and logical cell placement blockage</h2>

**Pin Placement**

Lets take below designs for example that needs to be implemented. Here first circuit is driven by clk1  and second circuit is driven by clk2 and both has different inputs Din1 and Din2 respectively and outputs as Dout1 and Dout2.Along with that we have some preplaced cells as well as Blocka which recieves inputs from Din1 second input from Din2. We have another preplced cell as Blockb Which recieves input from clk1 and clk2 and provides a clk output. So currently we have 4 input ports Din1,Din2,Clk1,Clk2 and 3 output ports Dout1,ClkOut,Dout2

![image]()

let's have one more design that needs to be implemented. this types of circuits are very much helpful to understand the timing analysis of inter clocks.
now complete design becomes like given below which has 6 input ports and 5 output ports. The connectivity information between the gates is coded using VHDL/Verilog language and is called as 'Netlist'.

![image](https://github.com/user-attachments/assets/f4637fe2-bad4-4fd2-8061-0d8683ac15c3)

Let's put this netlist in the core which we have designed before and let's try to fill this empty area between core and die with the pin information. The frontend team who decides the netlist connectivity input and output and the backend team who done the pin placements. So according to the pin placements, we have to locate the preplaced blocks nearer to the inputs of the preplaced blocks.

![image](https://github.com/user-attachments/assets/bdf4efec-c7d6-4e44-9f08-f18fae3e545c)


Here one thing that we noticed is that clock-in and clock-out pins are bigger in size as compared to input and output pins. reason behind this is that, input clocks are conntinuously provides the signal to the every elements of the chip and output clock should out the signal as fast as possible. So, we need least resistance path for the clocks inputs and clocks outputs. So, bigger the size, lower the resistance.

One more thing is need to take care about is that, this pin placement area is blocked for routing and cell placements. so we nned to do logical cell placement blockage. this blockage is shoown in above image in between pins.

So, floor plan is ready for Placement and Routing step.

### <h2 id="header-2_1_6">Steps to run floorplan using OpenLANE</h2>

Before run the floorplanning, we required some switches for the floorplanning. these we can get from the configuration from openlane.

![image](https://github.com/user-attachments/assets/23317dc7-6d5e-4bd6-a48a-eda1229ca268)

Here we can see that the core utilization ratio is 50% (bydefault) and aspect ratio is 1 (bydefault). similarly other information is also given. But it is not neccessory to take these values. we need to change these value as per the given requirments also.

Here FP_PDN files are set the power distribution network. These switches are set in the floorplane stage bydefault in OpenLANE.

![image](https://github.com/user-attachments/assets/785cbae5-402c-4aa8-94a0-33c94793e791)

Here, (FP_IO MODE) 1, 0 means pin positioning is random but it is on equal distance.

In the OpenLANE lower priority is given to system default (floorplanning.tcl), the next priority is given to config.tcl and then priority is given to PDK varient.tcl (sky130A_sky130_fd_sc_hd_congig.tcl).

Now we see, with this settings how floorplan run.

### <h2 id="header-2_1_7">Review floorplan files and steps to view floorplan</h2>

In the run folder, we can see the connfig.tcl file. this file contains all the configuration that are taken by the flow. if we open the config.tcl file, then we can see that which are the parameters are accepted in the current flow.

![image](https://github.com/user-attachments/assets/e88b3965-9d85-483c-bacc-d928ac09ec98)

![image](https://github.com/user-attachments/assets/166b4c79-7941-45af-beb8-a7c07b32b183)

To watch how floorplane looks, we have to go in the results. in the result, one def( design exchange formate) file is available. if we open this file, we can see all information about die area (0 0) (660685 671405), unit distance in micron (1000). it means 1 micron means 1000 databased units. so 660685 and 671405 are databased units. and if we devide this by 1000 then we can get the dimensions of chips in micrometer.

![image](https://github.com/user-attachments/assets/6dc65290-3a61-4721-a0a1-242982e24675)

so, the width of chip is 660.685 micrometer and height of the chip is 671.405 micrometer.

To see the actual layout after the flow, we have to open the magic file by adding the command ```[magic -T /home/kunalg123/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def]```

And then after pressing the enter, Magic file will open. here we can see the layout.

![image](https://github.com/user-attachments/assets/5aef0a5f-544a-489a-80db-6afb72fd63fb)


### <h2 id="header-2_1_8">Review floorplan layout in Magic</h2>

In the layout we can see that, input output pins are at equal distance.

![image](https://github.com/user-attachments/assets/3a9dcdf2-5094-42b7-b99e-7b88d8b3e2b2)


after selecting (To select object, first click on the object and then press 's' from keyboard. the object will hight lited. to zoom in the object, click on the object and then press 'z' and for zoom out press 'sft+z') one input pin, if we want to check the location or to know at on which layer it is available, we have to open tkcon window and type "what". it will shows all the details about that perticular pin.

![image](https://github.com/user-attachments/assets/d24ddc1e-f1f8-453b-845a-2b34dd39cd48)


so, it show that the pin is in the metal 3.similarly doing for the vertical pins, we find that this pin is at metal 2.

![image](https://github.com/user-attachments/assets/03dabbb4-de16-4cc6-ad91-5489bf063ac3)


Along with the side rows,the Decap cells are arranged at the border of the side rows.

![image](https://github.com/user-attachments/assets/632b633e-de4c-4c15-9d39-fccf381ba8e6)



here we can see that first standerd cells is for buffer 1. similarly other cells are for buffer 2, AND gate etc.

![image](https://github.com/user-attachments/assets/10201728-5ba3-4971-9d83-7175bbc31f12)


## <h2 id="header-2_2">Library building and Placement</h2>
### <h2 id="header-2_2_1">Netlist binding and initial place design</h2>

**Bind netlist with physical cells**:- Lets we have the netlist of gates and shape of these gates represents the functionality of this gates. Foe example we have NOT gate as a tringular shape but in reality it is a box with physical dimensions it has width and height.Similarly for AND gate it also has a box shape in reality, Flipfops are also square boxes.So, we have given the physical dimensions to all the gates and flipflops. For everycomponent of the netlist we will give the particular shape with particular dimensions because ir real world the shapes like AND,OR gates does not exists so we make them as square all the blocks also have the width and height and proper shape.

![image](https://github.com/user-attachments/assets/8c3cd9d3-bcc2-4992-b6a0-7655ba622e73) 

Now we will remove the wires,all the gates, flipflops and blocks are present in the shelf which is called as **Library**.

A library is a place where you can find all kind of books all the gates,f/f are books here. Library also has the timing information of the perticular book like delay of the gates. Library can be devides into two sublibraries, One library consist of shape and size and other library might consist only of the delay information. Library has the various flavours of each and  every cell. Like same cell can have bigger in size in different self, bigger the size of cell lesser the resestnce path so it will work faster and will have lesser delay. We can pick up from these what we want based on the timing condition and available space on the floorplan.

![image](https://github.com/user-attachments/assets/a4add990-4b73-4674-9ceb-e3f1e96611eb)

**Placement**:- Once we have given proper shape and size to each and every gates the next step is to take those particular shapes ans sizes and place it on the floorplan. We have the floorplan with inout and output ports, we have particular netlist, and we have particular size given to each component of this netlist. So we have the physical view of the logic gates. Next step is to place the netlist onto the floorplan. We have to take the connectivity information from the netlist and design the physical view gates on the floorplan.

![image](https://github.com/user-attachments/assets/c8344c93-ee14-4042-a631-bf2c2496b63e) 

Now, we have the floorplan where we have the preplaced cells from the previous slides, Plcement will make syre that the pre placed cells locations are not affected they are kept as it as and the second thing which will be taken care of that is no cell should be placed over the pre-placed cells. We need to place the physical view of the netlist onto the floorplan in such a fashion that logical connectivity should be maintained and that particular circuit should interact with their input and output ports to maintain the timing and the delay will be minimal.

![image](https://github.com/user-attachments/assets/ce38f05b-f03a-4d4e-afd9-6d4de0dc1527)


Here first we will see the arrangement of the remaining parts from the netlist onto the floorplan.We have placed all the element in such manner that all elements are closed to it's input and output pins.
But, the distance of FF1 of Stage 4 and Din4 is still far them others. By optimizing the placement, we can solve this problem.

![image](https://github.com/user-attachments/assets/10e232c1-7751-45a7-a6d5-8edd5b823c03)


### <h2 id="header-2_2_2">Optimize placement using estimated wire-length and capacitance</h2>

**Optimize Plecement:-** In optimize placement we will resolve the problem of distancing.Lrt's take the example of FF1 to Din2. There must be a wire going from Din2 to FF1 but before going into routing the desing or wiring we will try to estimate the capacitances. If we lokk the capacitance from Din2 to FF1 it is every huge because wire length is huge in that case even the resutance will also be huge because of that length. If we send the signal from Din2 then it will be difficult for FF1 to catch that input because distance is large. So we can place some intermediate steps to maitain the Signal integrity. By this the input is succesfully driven to the FF1 from Din2. These intermediate steps are called here Repeaters , Repeaters are basically buffers that will recondition the original signal and make a bew signal which replicate the original signal and send it forward this process repeates untill we reach to the actual cell where we want to send the input in this way signal integrity is maintained. By using repeaters we resolve the problem of signal integrity but there will be a loose of area because more and more repeaters are used more area will be used of the particular floorplan.

![image](https://github.com/user-attachments/assets/b44e62f2-4aa6-4b85-8744-f6acec978135)

In the stage 1, there is no need of any repeater to transmit the signal. But in stage 2, due to high distance, the lenth of wire is high and signal is not transmitted in perticular range. so we required repeater.

![image](https://github.com/user-attachments/assets/b44e62f2-4aa6-4b85-8744-f6acec978135)

### <h2 id="header-2_2_3">Final placement optimization</h2>

As similar to stage 2, in Stage 3 also we required the buffer between gate2 and FF2.

![image](https://github.com/user-attachments/assets/3f22f197-f30c-4c79-8d30-65324710dea4)

Stage 4 is bit tricky as compared to other stages.Now we have to check that, what we have done is correct or not. For that we need to do Timing analysis by considering the ideal clocks and according to the data of analysis, we will understand that, the placement is correct or not.

![image](https://github.com/user-attachments/assets/f5397237-bc09-4c1a-9ad6-4723165b7ff9)

### <h2 id="header-2_2_4">Need for libraries and characterization</h2>

Every ICdesign Flow needs to go through the several steps. First step to go through is Logic Synthesis, let's say if we have a functionality which is coded in a form of an RTL so first we need to convert the functionality into legal hardware is refered to as Logic Synthesis. Ouput of the logic synthesis is arrangement of gates that will represent the original functionality that has been described using an RTL. 
Next step of logic synthesis is Floorplaning, in this we omport the output of logic synthesis and decide the size of the Core and Die. The next step after floorplaning is Placement, in this we take the particular logic cell send place them on the chip in such a fashion that initial timing is better. Next step is CTS(Clock tree synthesis), in this we take care that clk should reach each and every signal at the same time also take care of each clk signal has equal rise and fall.Next step is Routing, routing has to go through the certain flow dependendent on the characterization of the flip flop.And now comes the last step STA(Static timing analysis), in this we try to see the set up time, hold time, maximum achieved frequency of the circuit.
One common thing across all stages 'GATES or Cells'.

### <h2 id="header-2_2_5">Congestion aware placement using RePlAce</h2>

Right now we are not constrain about timing, but constrain about the congestion. so, we are making the congrstion is less.

The placement is donne in two stages. Global and detailed. In global placement, legalization is not happened but after detailed placement legalization will be done.

When we run the placement, first Global placement is happens. main objective of glibal placement is to reducing the length of wires.

Now opening the Magic file to see actual view of standerd cells placement.And the actual view in the magic file is given below.

![image](https://github.com/user-attachments/assets/6d87c0fe-58ed-4ff5-88d6-ac60649b9603)

If we zooom into this, we find the buffers, gates, flip flops in this.

![image](https://github.com/user-attachments/assets/8aea2c9d-560b-4397-b719-86714f9177d4)



## <h2 id="header-2_3">Cell design and characterization flows</h2>
### <h2 id="header-2_3_1">Inputs for cell design flow</h2>

In Cell Design Flow, Gates, flipflops, buffers are named as 'Standard Cells'. These standard cells are being placed in the section called as 'Library'.And in the library many other cells are available which have same functionality but the size is different.

![image](https://github.com/user-attachments/assets/ade12ffd-392f-4167-af0f-00c1d1ac1753)

If you lokk into one of the inverter from the library the cell design flowis as follows

The inverter has to represented in form of the shape, drive strength, power charracteristic and so on. Here cell design flow is devided into three parts.

1. Inputs

2. Design steps

3. Outputs

**1)Inputs**:- Inputs required for cell design is PDKs, DRC and LVS rules SPICE models, library and user defined specs. In DRC& LVS rules tech file is provided which contains design rules and actual values. Rules can be converted in to code. SPICE MODEL tells about threshold voltage equation.

![image](https://github.com/user-attachments/assets/72d1d69f-14d6-4ab9-a14c-4af5d8dafd1d)

### <h2 id="header-2_3_2">Circuit design steps</h2>

The seperation between the power rail and the ground rail defines the cell height. Cell width depends upon the timing and drive strength.

**2)design steps**:- Design involves three steps which are circuit design, layout design, characterization.

**In circuit Design** there are two steps.

First step is to implement the function itself and second step is to model the PMOS nad NMOS transistor in such a fashion in order to meet the libraray.

**3)Outputs**

The typical output what we get from the circuit design is CDL(circuit description language) file,GDSII,LEF,extracted spice netlist(.cir).


![image](https://github.com/user-attachments/assets/dc713703-c8a9-41e0-b48c-db889ec6a77d)


### <h2 id="header-2_3_3">Layout design step</h2>

In Layout Design First step is to get the function implemented through the MOS transistor through a set of PMOS and NMOS transistor and the second step is to get the PMOS network graph and the  nNMOS network graph out of the design that has been implemented.

![image](https://github.com/user-attachments/assets/c99be860-5b42-440e-8d44-99ec3847f621)

After getting the network graphs next step is to obtain the Euler's path. Eule's path is basically the path which is traced only once.

![image](https://github.com/user-attachments/assets/3d53fd05-933e-4b22-a5b5-3cb42450f511)

Next step is to draw stick diagram based on the Euler's path. This stick diagram is derived out of the circuit diagram.

![image](https://github.com/user-attachments/assets/e1440225-961d-414f-b339-4d76489360b7)



Next step is to convert this stick diagram into a typical Layout, into a proper layout and then get the proper rule we have discissed earlier. Once we get the particular layout then we have the cell width, cell length and all the specifications will be there like drain current, pin locations and so on.

![image](https://github.com/user-attachments/assets/ebce625f-1b8c-4698-8462-1744dd461d34)

Next and Final step is to extract the parasatics of that particular layout and charaterise it in terms od timing. So before that the output of the layout design will be GDSll. Once you get the extracted spice netlist then we characterize it. Characterization helps in getting timing, noiseand power information.

### <h2 id="header-2_3_4">Typical characterization flow</h2>

Let's try to build the characterization flow based on the inputs we have,

First step is to read in the model, second step is to read the extracted spice netlist, third step is to define or recognize the behaviour of the buffer, fourth step is to read the subcircuits of the inverter and then in the fifth step need to attach the necessary power supplies, sixth step is to  apply the stimulus then in the seventh step we need to provide the necessary output capacitance then in the final eighth step in which we need to provide necessary simulation command for example if we are doing transent simulation so we need to give ```.tran``` command , if we are doing DC simulation then we give ```.dc``` command.



![image](https://github.com/user-attachments/assets/a7943407-f949-4126-9e88-a6e5c07dc3c9)


![image](https://github.com/user-attachments/assets/77a884d0-ce14-42e8-a8c8-c487060b5a8e)

![image]()

![image]()

![image](https://github.com/user-attachments/assets/9dd56810-16e3-43d9-8f18-634314fd1b4c)

Next step is to feed in all this inputs from 1 to 8 in a form of a configuration file to the characterization software **"GUNA"** .

This software will generate power, noise and timing model.

![image](https://github.com/user-attachments/assets/13922b7d-7757-40b7-a425-f30dfb0256fe)

## <h2 id="header-2_4">General timing characterization parameters</h2>
### <h2 id="header-2_4_1">Timing threshold definitions</h2>


As seen in the previous section we have inverter connected back to back, we have power sources, we have the stimulus applied to the inverter all these things brings a very important point of understanding differenet threshold points of a waveform itself and it is called as "Timing threshold definitions'.

in the figure below the term 'Slew_low_rise-thr' depicts the value close to 0. and the typically value of this is about 20% it could be 30% as well.

![image](https://github.com/user-attachments/assets/afd2dfc5-186b-401d-8b35-da64ae672222)

Slew_high_rise_thr

![image](https://github.com/user-attachments/assets/7bc49d5a-d8e8-49a4-b2e4-6d617d09b95b)


Slew_low_fall_thr

![image](https://github.com/user-attachments/assets/9be0f642-d27e-437f-a0ad-870d1273c0fa)


Slew_high_fall_thr

![image](https://github.com/user-attachments/assets/8b4ffc09-f6a6-4095-8882-51bcd85cc520)


NOw, taking the waveform of input stimulus which is input of the first buffer and with that taking output of the first buffer.Similar as a slew, thresolds are for delay also available. for that same as slew, we have to take some rise and fall points from the waveforms. this tresolds are almost 50%.

in_rise_thr

![image](https://github.com/user-attachments/assets/94ff0f83-b772-4d04-bd3d-be99f850d0e8)

in_fall_thr , its typical value is 50%.

![image](https://github.com/user-attachments/assets/e6c61c21-1dd0-45bb-9d56-52a9b529c46c)

out_rise_thr

![image](https://github.com/user-attachments/assets/6b9bd9f7-c43e-4429-88ee-65017537d1e7)

out_fall_thr

![image](https://github.com/user-attachments/assets/68df140a-15e8-41c8-a091-7e4f76526778)


### <h2 id="header-2_4_2">Propagation delay and transition time</h2>

Based on these above values we are going to calculate the further values like propogation delay, current,slews etc.

If we want to calculate the delay of anything we need to subtract the out_rise_thr from in_rise_thr. Here let's take typical value 50%, let's see on the particular waveform how does it works
Time delay = Time(out_thr)-time(in_thr).

![image](https://github.com/user-attachments/assets/4427eebc-bbb2-462c-a521-4258cfb18b6c)

In the above example in_rise_thr and out_fall)thr was kept at 50%. But if the threshold ponit moves to the top the the output comes before the input and we see negative delay and negative delays are not accepted. So the reason behind having this negative delay is poor choice od threshold point so thr choice of the threshold point is really important.

![image](https://github.com/user-attachments/assets/f9a9d83b-c53a-4d1e-9f0b-74ab0972743a)

Let's take another example where we have choosed threshold point correctly but still can get a negative delay. Because uotput comes before the input that's why we are getting negative delay here, which is not accepted

![image](https://github.com/user-attachments/assets/3f4f4517-8b8a-4ef2-add8-b02cc9579c9c)

**Transition time**=  time(slew_high_rise_thr)- time(slew_low_rise_thr)

or

transition time = time(slew_high_fall_thr)- time(slew_low_fall_thr)

Let's say we have the waveform to understand the slew calculation.

![image](https://github.com/user-attachments/assets/1c6b1dc9-1143-4fd3-8498-cffddac62c76)














     

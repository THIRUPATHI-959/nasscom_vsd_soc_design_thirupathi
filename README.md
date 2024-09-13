
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




                                               ------------------*DAY1*-----------------




# nasscom_vsd_soc_design_workshop

 




**Design Preparation Step**
To open the OpenLANE we need need enter in the OpenLANE, Here we  have to use **./flow.tcl -nteractive** command use in script .  Now OpenLANE is open and we can see that prompt will change now.

![image](https://github.com/user-attachments/assets/ed3aed35-fe5f-460e-b782-60dfd92f18df)

we have to enter  input **packages require openLANE 0.9**  which required to run the flow.

![image](https://github.com/user-attachments/assets/46d2cc3c-9591-4729-ad8d-745464d16a36)

Now, we are ready 


![image](https://github.com/user-attachments/assets/bccf2262-0883-4353-8574-84afd9771cdd)

Here Our Design  time period is 5nsec. but is we see in the openlane sky130_fd_sc_hd folder, the period is set about 24 nsec. so it is not override to the main file. If it override then give first priority to the main folder.

 Before To run the synthesis, we need to prepare design setup stage,  for that command is **prep -design picorv32a** here our design name is picorv32a

![image](https://github.com/user-attachments/assets/38c6ad67-84c4-4525-9fea-ac6c57e292e2)

 Here our Design  preparation is completed.


## Merged file  and run synthesis ##

 Once complete the preparation,The merged.lef file, which was created during the preparation phase, is accessible in the temp file. Opening this merged.lef file provides access to all **wire**, **layer**, and **cell level data**. 

![image](https://github.com/user-attachments/assets/5d7ce5a1-7e51-48c5-9fb3-523f0e6ef024)


Come  to the openlane, we are going to run the synthesis. for that command is **run_synthesis**
It will take some few minutes  to run the synthesis.

![image](https://github.com/user-attachments/assets/3424573b-ed06-4832-b089-a555c98ff989)



![image](https://github.com/user-attachments/assets/87c93d2c-d905-48e1-bb16-eead8d1575db)

synthsisi completed

### Find Flop Ration from synthesis results ##

From the  synthesis reports, 
total number of counter **D_flip-flops** is   **1613**. 
&                the **number of cells**is   **14876**.

![image](https://github.com/user-attachments/assets/5bab437f-71d6-4637-b009-8b4be8c05c09)

 **Flop ratio = (number of flip flops)/(number of total cell)** = 1613/14876.  So, the flop ratio is **10.84%** and chip area for module  =147712.918400












                                            --------------------# Day 2 #-----------------------	
								     
                                                         ---# FloorPlanning#--- 
 docker

./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a

run_synthesis

run_floorplan



### Steps to run floorplan using OpenLANE ###
prior run the floorplanning ,we can get from the configuration from openlane.As we can see, by default( the aspect ratio is 1 and the core utilization ratio is 50%). In a similar manner, further information is provided.

![image](https://github.com/user-attachments/assets/23317dc7-6d5e-4bd6-a48a-eda1229ca268)


### Analyzie floorplan files and steps to run floorplan ###

In Floorplan  we have the  def( design exchange formate) file in this file we have the information about die area (0 0) (660685 671405), unit distance in micron (1000). so, the width of chip is 660.685 micrometer and height of the chip is 671.405 micrometer.

![image](https://github.com/user-attachments/assets/6dc65290-3a61-4721-a0a1-242982e24675)



To see the  layout, we have to open the magic file enter the **[magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def] &** after enter this command , Magic file will open. here we can see the layout.

![image](https://github.com/user-attachments/assets/5aef0a5f-544a-489a-80db-6afb72fd63fb)


### Analyzie the floorplan layout in Magic ###

 Observe the magic layout,input pins and  output pins are at equal distance.

![image](https://github.com/user-attachments/assets/3a9dcdf2-5094-42b7-b99e-7b88d8b3e2b2)

horizantal pin  the is at  metal 3.similarly we find vertical pin is at metal 2 and the Decap cells are arranged at the border of the side rows and we can see standard cells also as shown in the following figure 
![image](https://github.com/user-attachments/assets/d24ddc1e-f1f8-453b-845a-2b34dd39cd48)


![image](https://github.com/user-attachments/assets/03dabbb4-de16-4cc6-ad91-5489bf063ac3)


![image](https://github.com/user-attachments/assets/632b633e-de4c-4c15-9d39-fccf381ba8e6)



![image](https://github.com/user-attachments/assets/10201728-5ba3-4971-9d83-7175bbc31f12)




### Congestion aware placement using RePlAce ###

Right now we are not constrain about timing, but constrain about the congestion. so, we are making the congrstion is less.

The placement is donne in two stages. Global and detailed. In global placement, legalization is not happened but after detailed placement legalization will be done.

When we run the placement, first Global placement is happens. main objective of glibal placement is to reducing the length of wires.

Now opening the Magic file to see actual view of standerd cells placement.And the actual view in the magic file is given below.

![image](https://github.com/user-attachments/assets/6d87c0fe-58ed-4ff5-88d6-ac60649b9603)

If we zooom into this, we find the buffers, gates, flip flops in this.

![image](https://github.com/user-attachments/assets/8aea2c9d-560b-4397-b719-86714f9177d4)










### Lab steps to git clone vsdstdcelldesign ###

cd ~/Desktop/work/tools/openlane_working_dir/openlane

git clone https://github.com/nickson-jose/vsdstdcelldesign --depth=1

cd vsdstdcelldesign

cp ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .magic -T sky130A.tech sky130_inv.mag &

To get the clone, copy the clone address from reporetery and paste in openlane terminal after the command ```git clone```. this will create the folder called "vsdstdcelldesign" in openlane directory.

![image](https://github.com/user-attachments/assets/fd708406-0105-4e4a-9375-d82cb2ec54ba)

now, if we open the openlane directory, we find the vsdstdcelldesing folder in the openlane directory.


Now if we goe to the vsdstdcelldesign folder and open it, we get the .mag file,libs file etc.


now, let's open the .mag file and see that which layers are used to build the inverter. But before opening the mag file, we need tech file. so we will copy this file from this given below address,
And do copy by ```cp``` command to the location which is given below.Now, we can see that this file is copied in the vsdstdcelldesign folder.

![image](https://github.com/user-attachments/assets/989195fd-b43e-45cb-906e-7278b6e644e4)

Now, here to see the layout in magic, we don't need to write the whole address because we copy the tech file here.Now, we can see the layout of CMOS inverter in the magic like this.

![image](https://github.com/user-attachments/assets/48759296-85fa-4a43-93f0-0d25c68d20ff)


## <h3 id="header-3_2">Inception of layout ̂A CMOS faabrication process</h3>
### <h3 id="header-3_2_1">Create Active regions</h3>

**1) selecting a substrate**:- we have a p-type silicon substrate having high resistivity(5-50ohm) well dopped, and orintation(100).

**2) creating active region for transistor**:- Region where you see PMOS and NMOS. On p-type substrate we are going to create some small pockets which will be called as active region and in these pockets we are going to create PMOS and NMOS transistor. Will cretae isolation between each and every pockets. 

We create the isolation layer by depositing the Sio2 layer (~40nm) on the substrate. Now, we are depositing the Si3N4 layer (~80 nm) on the Sio2 layer.

![image]()

Before creating the pocket identify the region where we need to crete the pocket. Now will deposite a layer of photoresist(~1um) on which we will create some mask1 using UV light.

![image]()

Unwanted area has been exposed using UV light. And we get pattern the exposed area is getting washed away.

![image]()

In the next step mask will be removed and doing etching of Si3N4 layer on the exposed area.

![image]()

Now, next step is to remove photoresist by chamical reaction, because now to Si3N4 layer itslef behaves like good protecting layer for Sio2 layer. now,We will place it in the oxidation furnace. if we do LOCOS (local oxidation of silicon) process, the exposed sio2 part will grow and bird break also form. This grown sio2 will provide the perfect isolation between two PMOS and NMOS. This is how we protect two transistor communicating with each other.

![image]()

Next step is to remove the Si3N4 using hot phospheric acid.

![image]()


### <h3 id="header-3_2_2">Formation of N-well and P-well</h3>

**3) N-well and P-well formation**:- we can not form P-well and N-well at a same time. we have to protect a region while forming one of the region by photoresist. And then using mask 2 and UV light, we will do patterning of photoresist to form P-well.

![image]()

Now, the area where we want to form the P-well is exposed. now we remove the mask and by applying the ion implantaton method (~200kev)to form P-well using Boron. But still it is P implant. After performing the high temparature anneling, it will become P-well.

![image]()

We wiil do a similar process to form N-well by using mask 3 and using Phosphorus ions.

![image]()

Till now depth of wells are not define. so, by putting into the high temparature furnace (drive-in diffusion), we will define the depth of wells.

![image]()


### <h3 id="header-3_2_3"> Formation of gate terminal</h3>

**4)Gate formation**:- Gate terminal is the most important terminal of the PMOS and NMOS because from the gate terminal only we can control the thresold voltage. doping concentration and oxide capacitance will control the thresold voltage.so, first we are maintain the doping concentration here. for that we use mask 4 and again doing the ion implantation of boron ion at lower energy (~60kev).

![image]()

same process we will repeat for N-well also by using mask 5 and Arsenic ion.

![image]()

Next step is that we have to fix the oxide layer. but before that we have to remove the oxide layer because this layer is got dammeged because of the privious processes. so,first we remove the layer using HF solution and again re-grown the high quality oxide layer with same thickness.

The final step is the deposition of polysilicon layer over oxide layer with more impurities for low resistance gate terminal.Then etched out this polysilicon layer by using mask 6 and photoresist.

![image]()

After etching, remove the photoresist and gate terminal looks like,

![image]()


### <h3 id="header-3_2_4">Lightly doped drain (LDD) formation</h3>

**5) LDD formation**:- Here, we actully want P+,P-,N doping profile in the PMOS and N+,N-,P doping profile for NMOS. Reason for that is

Hot electron effect

short channel effect

For the formation of LDD, we again do ion implantation in P-well by using mask 7 and here we use phosphoros as a ion for light doping.

![image]()

Same process we will repeat for N-well. there we use mask 8 and BOron Ion.

![image]()


Now, by creating the spacers, we can protect the actual structre remain constant of P-implantt and N-implant. For that we deposite a thick Sio2 or Si3N4 layer over the gate tereminal.

![image]()

Now, we do Plasma anisotropic etching. By that side-wall spacers are formed.

![image]()


### <h3 id="header-3_2_5">Source ÃÂ drain formation</h3>

**6)source-drain formation**

Next step is deposite the very thin screen oxide layer to avoid the effect of channeling.

![image]()

Now to form the drain and source, again we do the ion implantation of arsenic at 75kev to create the N+ implant by using mask 9 in the P-well to form PMOS.

![image]()


Same process we will repeat for NMOS by using the mask 10 and boron ion in the N-well at 50kev to creat P- implant.

![image]()

Now we put this Half made CMOS into the high temparature (1000 degree)anneling. So P+ implant and N+ implant now become the source and drain.

![image]()



### <h3 id="header-3_2_6">Local interconnect formation</h3>

**7)steps tp form contacts and local interconnects**:- First step is remove the thin screen oxide layer by etching. Then deposite the titanium (Ti) using sputtering. here Ti is used because Ti has very low resistivity.

![image]()

Next step is to create the reaction between Ti layer and source, gate, drain of CMOS. For that wafer is heated at about 650-700 degree temparature in N2 ambient for about 60 seconds. and after reaction, we can see the titanium siliside over the wafer. One more reaction is heppend there between Ti and N. and it results the TIN which is used for local communication.

![image]()

Now by using mask 11 and photoresist, we will etched out the TIN and make perticular contacts. TIN is etched out by using RCA cleaning.

![image]()

Now, local interconnects are formed after etching and removing the photoresist.

![image]()


### <h3 id="header-3_2_7"> Higher level metal formation</h3>

**8)Higher level metal formation**:- These steps are very semilar like previous steps. First thing that we are noticing is that the surface is non planner. it is not good to use this type of non planner serface for matel interconnects because of the problems regarding the metal disconinuty. so, we have to plannerize the surface by depositing the thick layer of sio2 with some impurity to make less resistive layer. and then we used CMP (chemical mechanical polishing) technique to plannerise the surface.

![image]()

Now using mask 12 and photorsist we etched the sio2 layer to diposite the metal in it.

![image]()

Now remove the photoresist and seposite the thin later of TIN (~10nm) over the wafer. Because TiN is act as very good adession layer for sio2 and also act as a barrier between bottom layer and top layer of metal interconnects.

![image]()

Next step is to deposite the blanket tungsten (W) layer over the wafer. and then do the CMP here to plannerize the surface.

![image]()

This W is act as a contact holes and this holes needs to connect to the Higher metal layer. so we will deposite the Al (aluminium) layer.

![image]()

Then by using the mask 13 and photoresist, we etched the W layer out to form the contact at perticular place by Plasma etching.

![image]()

This is our first level of metal interconnets. now we again do the same process as above to deposite the second level of metal interconnect by using mask 14 for etched out the sio2 and using mask 15 for etched out Al leyer.

![image]()

The upper layer of Al is bit thicker as compared to lower layer of Al.Now, again deposite the layer of sio2 or si3N4 to protect the chip.

![image]()

And finally our CMOS is looks like this after the fabrication.

![image]()



### <h3 id="header-3_2_8"> Lab introduction to Sky130 basic layers layout and LEF using inverter</h3>

![image]()

In sky130, every color is showing the different layer. here the first layer is for local interconnect shown by blue_purple color, then second layer is metal 1 which is shown by light purple color, and the metal 2 is shown by pink color. N-well is shown by solide das line. green is N-diffusion region. and red is for polysilicon gate. similarly the brown color is for P-diffusion.

In tckon window, we can see that the selected area is NMOS and similarly we can chech PMOS also. and that is how we can check that the CMOS is working or not.

![image]()

similarly we will check for the output terminal also.(by double pressing "S" to select the entire thing at output Y).

![image]()

so, we can see that "Y" is attached to locali in cell def sky130_inv.

we can check the source of the PMOS is connected to the ground or not. and similarly we can check it for NMOS also.



### <h3 id="header-3_2_9">Lab steps to create std cell layout and extract spice netlist</h3>

To extract the file from here, we have to write the command in tckon window. and the comand is ```extract all```

![image]()

Now let's go to this location from the terminal. it is exctracted.

![image]()

we will use this .ext file to create the spice file to be use with our ngspice tool. for that we have apply the command ```ext2spice cthresh 0 rthresh 0```. this will not create anything new. now again we have to type ```ext2spice``` command in tckon window.

![image]()

so, now we are checking the location and at there spice file has been created.

![image]()

let's see what inside the spice file by "vim sky130_inv.spice".

![image])


## <h3 id="header-3_3">Sky130 Tech File Labs</h3>
### <h3 id="header-3_3_1">Lab steps to create final SPICE deck using Sky130 tech</h3>

![image]()

here, we can see the all details about the connectivity of the NMOS and PMOS and about the power supply also.

X0 is NMOS and X1 is PMOS and both's connectivity is shown as GATE DRAIN SUBSTATE SOURCE.

![image]()

Now we have to include the PMOS and NMOS lib files. it is inside the libs folder in the vsdstdcellsdesign folder.

![image]()

so, now we include this file in the terminal by ```.include ./libs/pshort.lib``` and ```.include ./libs/nshort.lib``` command.

And then set the supply voltage "VDD" to 3.3v by ```VDD VPWR 0 3.3V``` command. and similarly set the value of VSS also.

Now, we need to specify the input files. by ```Va A VGND PULSE(0V 3.3V 0 0.1ns 2ns 4ns)```.

Also add the command for the analysis like, ```.tran 1n 20n```, ```.control``` , ```run```,```.endc```,```.end```.

![image]()


after running this file we get output of ngspice like this,

![image]()

Now, ploting the graph here by command, ```plot y vs time a```.

![image]()

NOw if we increase the C3 value from 0.024ff to 2ff the graph will look like this, graph become more smoother.

![image]()


### <h3 id="header-3_3_2">Lab steps to characterize inverter using sky130 model files</h3>

Here, we have to find value of 4 parameters.
	
<ul>
	<li><a> rise time</a></li>
	</ul>
	
it is time taken to the output waveform to 20% value to 80% value.

![image]()

so, rise time= (2.2489 - 2.1819)e-09 = 66.92 psec.


<ul>
	<li><a> fall time</a></li>
	</ul>
 
it is the time take by output for transition from 80% to 20%.

![image]()

so, rise time= (4.09512 - 4.05264)e-09 = 42.51 psec.

<ul>
	<li><a> propagation delay</a></li>
	</ul>

it is the time difference between the 50% of input and 50% of the output.

![image]()

so, propogation delay =(2.2106 - 2.15012)e-09 =  60.48 psec.


<ul>
	<li><a> cell fall delay</a></li>
	</ul>
 
it is time for output falling to 50% and input is rising to 50%.

![image]()

so, cell fall delay =(4.07735 - 4.04988)e-09 =  27.47 psec.

We have successfully characterized our inverter.
Our next objective is to create a lef file using the layout and we will plugin this lef file in the picorv32a core

### <h3 id="header-3_3_3">Lab introduction to Magic tool options and DRC rules</h3>

To know more about the Magic DRC we can go to the website:- http://opencircuitdesign.com/magic/Technologyfiles/TheMagicTechnologyFileManual/DrcSection 

Link to Google_Skywaters Design Rules: - https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html

For reference , we can use the github repo of Google-Skywater: - https://github.com/google/skywater-pdk


### <h3 id="header-3_3_4">Lab introduction to Sky130 pdk's and steps to download labs</h3>

Follow the steps:

First go to the home directory.

**To download the lab files for performing DRC corrections**:

```wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz```

**To extract the lab files from the downloaded file:**

```tar xfz drc_tests.tgz```

Then go inside the lab folder drc_tests.

To list all the directories, we can use the command ```ls -al```.

To view the .magicrc file, we can use the command ```gvim .magicrc```. This file serves as the startup script for magic and tells it where to find the technology file. The technology file is already available locally in the same directory, so we can make changes to it if needed.

To start the magic tool with better graphics, we can use the command ```magic -d XR &```.

![image]()

Content of .magicrc file by using command ```vi .magicrc```

![image]()


### <h3 id="header-3_3_5">Lab introduction to Magic and steps to load Sky130 tech-rules</h3>

Use the command ```magic -d XR```

to open the magic tool. Open the met3.mag file from the file menu. we will see different layouts with different DRC values, called rule numbers.

![image]()

These rule number we can found at  Google-Skywater documentation.

![image]()

Now we will select the any layout area and check drc why in tckon.

![image]()

Next, select a blank area and hover the mouse pointer over the metal3 contact icon. Press the p button and type 'pek' in the tkcon. Then execute the command ```cif see VIA2``` in the tkcon tab. 

we will see a bunch of black squares appear inside the area.


![image]()


### <h3 id="header-3_3_6">Lab exercise to fix poly.9 error in Sky130 tech-file</h3>

Now, we will open the poly.mag file in the magic tool with the helo of the command  ```load poly.mag``` in the tkcon terminal.

![image]()

Now consider the rule poly.9 then check the website for that particular rule.

![image]()

![image]()

To find the error, we can look at the sky130A.tech file which is present in the drc_tests directory. we can open this file with the text editor of Linux itself.

![image]()

Search for 'poly.9' in the sky130A.tech file. It appears in both the POLY and uhrpoly sections, where the rules are not set properly. Add a change in both sections.

![image]()

![image]()

After making changes to the sky130A.tech file, click on Save and close the editor file.

Next, execute the command ```tech load sky130A.tech``` in the tkcon terminal. Then, run the drc check as shown below.

![image]()


### <h3 id="header-3_3_7">Lab exercise to implement poly resistor spacing to diff and tap</h3>

To correctly implement poly resistor spacing, we will need to make changes to the sky130A.tech file again.

 ![image]()

 Now will execute in Tkon after saving.

 ![image]()

To check for errors, we can make a copy of the poly.9 model from the poly.mag file in the magic window.

![image]()

To find the description of a DRC error, we can select the area with the error in the magic window and then run the command ```drc why``` in the tkcon terminal.

This will give a description of the error.

![image]()


### <h3 id="header-3_3_8">Lab challenge exercise to describe DRC error as geometrical construct</h3>

Now we will make some changes in sky130A.tech file which are as follows:

![image]()

![image]()


To find the nwell.6 model error, open the nwell.mag file in the magic tool. In the figure, the deep nwell is shown in yellow stripes and the nwell is shown in dotted green pattern.

![image]()

This error can be seen at the site as well.

![image]()

### <h3 id="header-3_3_9">Lab challenge to find missing or incorrect rules and fix them</h3>

Now we will open the magic tool and execute the commands ```drc style drc(full)``` and ```drc check```.

![image]()




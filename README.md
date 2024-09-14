
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


pmos

![image](https://github.com/user-attachments/assets/d9248e08-dee4-4e99-95cd-172a63f6add0)

nmos

![image](https://github.com/user-attachments/assets/9bb2fc50-54ac-4054-b4c7-cf716bb26a2a)

**Spice extraction**

         extract all
	 
	ext2spice cthresh 0 rthresh 0
 
	ext2spice

 ![image](https://github.com/user-attachments/assets/419e254a-2a8a-44fa-9996-05b92e7bbc71)

 ![image](https://github.com/user-attachments/assets/e8568118-9cad-4994-bdca-954cd094382f)

 ![image](https://github.com/user-attachments/assets/21171f48-ff39-4435-b688-73fb06be88db)

*grid size *

![image](https://github.com/user-attachments/assets/9d13ff74-8a31-4d33-b50c-e4123e92f4ef)

NgSpice code of Inverter:
![image](https://github.com/user-attachments/assets/0643699e-c5f8-469d-bb67-ba9d960e1c93)

plot of Y and time a AT C=0.024uf
![image](https://github.com/user-attachments/assets/442dc153-7ba7-41e4-93c0-3bf5797ec6fe)
**rise_time**
Rise Time= time taken for output to reach 80%  of 3.3v- time taken for output to reach 20%  of 3.3v
	 = 2.245e^-9 - 2.182^e-9
	 =0.063^e-9
	 =63ps
![image](https://github.com/user-attachments/assets/bfc1aa15-7b1f-4023-a304-65245d7f1f8f)

**fall_time**
Fall Time= time taken for output to reach 20% of 3.3v - time taken for output to reach 80% of 3.3v
	 = 4.0952e^-9 - 4.052^e-9
	 =0.0432^e-9
	 =43.2ps
  ![imahge]

**cell_daely**
![image](https://github.com/user-attachments/assets/06ee9de6-cc4e-4b9f-8cce-0c0ccd24d3aa)
Rise Cell Delay= time taken for output to rise 50%  of 3.3v - time taken for input to fall 50% of 3.3v
			   = 2.21103e^-9 - 2.15e^-9
			   =0.06103e^-9
			   =61.03ps


![image](https://github.com/user-attachments/assets/b277f6ed-1806-483b-bd61-ff94b6802436)

![image](https://github.com/user-attachments/assets/878425d1-baab-449c-ab7b-e6bbdaf7d3f1)
plot of Y and time a AT C=2uf
![image](https://github.com/user-attachments/assets/519a9c0e-46f3-40f3-9e38-fa0d857c0434)

![image](https://github.com/user-attachments/assets/a3339b74-fa36-4d3d-a87b-860903c6628a)

**DRC Rules checks**

cd ~
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
tar xfz drc_tests.tgz
cd drc_tests
ls -al
vi .magicrc
magic -d XR 

![image](https://github.com/user-attachments/assets/9cafa9c1-6ce0-4d49-8e84-0f2bdc5b3c05)

![image](https://github.com/user-attachments/assets/67befd5b-3f1c-4659-9694-a8ac0b14bf54)

![image](https://github.com/user-attachments/assets/b554fec1-421a-4821-9e94-63ad58023371)


**Incorrect drc poly.9 check**

![image](https://github.com/user-attachments/assets/c387ee38-a240-4772-ac3e-2c813457503b)

Without Modified DRC file

![image](https://github.com/user-attachments/assets/7583b10d-7d3a-4f1d-8aba-2fb415b60371)

![image](https://github.com/user-attachments/assets/6d65ab27-c5ed-4c80-9e5e-226b9d1b1e0a)

modified DRC File

![image](https://github.com/user-attachments/assets/b0eca235-a6a7-4d49-97be-1c6933da238e)

![image](https://github.com/user-attachments/assets/bf21db1c-b507-4003-8915-ac033a568722)





 
					-----------------# DAY-4 #----------------------
                                                        CTS & STA

       cd ~/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign magic -T sky130A.tech sky130_inv.mag &
  cat ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd/tracks.info
  
  ![image](https://github.com/user-attachments/assets/b4f66cfc-a689-40c3-ace2-ec7c3873a380)

  before grid

  ![image](https://github.com/user-attachments/assets/f233bd83-4879-4f8c-a3df-5c237ac6455b)

  after grid
  ![image](https://github.com/user-attachments/assets/9c05b945-ca62-4788-9fda-93ca3c4b126b)
  


  
Setting grid according to tracks.info
grid 0.46um 0.34um 0.23um 0.17um



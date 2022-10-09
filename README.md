# TwoStage-OTA@28nm_IITH_HACKATHON
This repository contains information about Double stage Operational Trnasconductance amplifier implemented on Synopsys Custom Compiler on 28nm technology node.
# Table of Contents
1) [Abstract](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#abstract-) <br />
2) [Synopsys Custom Compiler Tool](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#synopsys-custom-compiler-tool)
3) [Refrence Circuit Details & Circuit Diagram](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#refrence-circuit-details--circuit-diagram-) <br /> 
4) [Refrence Circuit Waveform](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#refrence-circuit-waveform-) <br />
5) [Schematic](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#schematic-) <br />
6) [Netlist](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#netlist-) <br />
7) [Actual Simulation Stimuli](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#actual-simulation-stimuli-) <br />
8) [Simulated actual waveforms](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#simulated-actual-waveforms-) <br />
9) [Observations](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#observations-) <br />
10) [Author](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#author-) <br />
11) [Acknowledgements](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#acknowledgements-) <br />
12) [References](https://github.com/Shubhang1234/TwoStage-OTA/edit/main/README.md#references-) <br />
## Abstract <br />
Operational transconductance amplifiers are 
widely used in various applications like BGRs, VCO, VGA etc. <br />
Here a double stage operational transconductance amplifier is designed and simulated on Synopsys custom compiler on 28nm technology node. 
## Synopsys Custom Compiler Tool
The [Synopsys Custom Compiler™](https://www.synopsys.com) design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. It delivers industry-leading productivity, performance, and ease-of-use while remaining easy to adopt for users of legacy tools.
## Refrence Circuit Details & Circuit Diagram <br />
The proposed operational transconductance amplifier consists of two stages: <br />
1) An input differential pair <br />
2) Common source amplifier stage <br />
This amplifier is compensated using Miller Compensation technique. As its a second order amplifier it has two poles and one zero. The Miller capacitor decreases the value of dominant pole and drifts the second pole away from dominant one hence increasing the headroom for phase margin. This effect is called pole splitting. <br />
![image](https://user-images.githubusercontent.com/56774313/155373573-14cedc3a-13c6-45fe-821e-bdb5b2cd07dd.png) <br />
Fig 1: Refrence Circuit Design of Proposed Circuit <br />
## Refrence Circuit Waveform <br />
![image](https://user-images.githubusercontent.com/56774313/155373852-d32fa98b-4f78-4053-9e01-09aa18b6a138.png) <br />
Fig 2: Refrence Circuit Waveform of Proposed Circuit
## Schematic <br />
![ckt_design](https://user-images.githubusercontent.com/56774313/155832197-56baa713-0ebf-49d3-8984-d1a6bec38373.png) <br />
Fig 3: Actual Schematic of Proposed Design
## Netlist <br />
```
*Custom Compiler Version S-2021.09
*Mon Feb 28 04:59:50 2022

.global gnd!
********************************************************************************
* Library          : wk_shubhang_ota
* Cell             : OTA_netlist
* View             : schematic
* View Search List : hspice hspiceD cmos.sch cmos_sch schematic veriloga
* View Stop List   : hspice hspiceD veriloga
********************************************************************************
.subckt ota_netlist vin+ vin- vout
xm24 net5 net5 gnd! gnd! n105 w=3.5u l=500n nf=1 m=1
xm26 net3 net5 gnd! gnd! n105 w=3.5u l=500n nf=1 m=1
xm27 vout net3 gnd! gnd! n105 w=52.5u l=500n nf=15 m=1
xm30 net2 net2 net1 net1 p105 w=12u l=500n nf=4 m=1
xm29 net4 net2 net1 net1 p105 w=12u l=500n nf=4 m=1
xm28 vout net2 net1 net1 p105 w=77u l=500n nf=22 m=1
xm23 net3 vin+ net4 net4 p105 w=12u l=500n nf=4 m=1
xm25 net5 vin- net4 net4 p105 w=12u l=500n nf=4 m=1
i27 net2 gnd! dc=2u
c24 vout gnd! c=1p
c23 net3 vout c=1p
v24 net1 gnd! dc=1
.ends ota_netlist
 
``` 
## Actual Simulation Stimuli <br />
Input common mode voltage-->0.3 V <br />
Fig 4: Small signal AC fluctuation-->vin+(L) & vin-(R) <br />![MergedImages](https://user-images.githubusercontent.com/56774313/155460689-fc33f329-06f1-4d11-811d-5864c1810580.png) <br />
## Simulated actual waveforms <br />
![Screenshot (88)](https://user-images.githubusercontent.com/56774313/194772270-d2d8a68d-ff4c-491b-b6dd-917908e76f59.png)
## Observations <br />
## Author <br />
Shubhang Srivastava <br />
Student <br />
Dept of Electrical engineering <br />
Indian Institute of Technology Jammu <br />
## Acknowledgements <br />
I would like to give my sincere thanks to undermentioned Organization/Persons for their invaluable guidance and software support which enabled me to participate and learn a lot from this Hackathon:
1) [Synopsys Team](https://www.synopsys.com)
2) Kunal Ghosh, Co-founder, [VSD Corp. Pvt. Ltd.](https://www.vlsisystemdesign.com)
3) Chinmay Panda, [IIT Hyderabad](https://iith.ac.in)
4) Sumanto Kar, [IIT Bombay](https://www.iitb.ac.in)
5) Sameer Durgoji, [NIT Karnataka](https://www.nitk.ac.in)
## References <br />
[1] Z. Yan, C. Zhang and M. Wang, "Low-Voltage Bandgap Reference 
Circuit in 28nm CMOS," 2018 IEEE Asia Pacific Conference on 
Circuits and Systems (APCCAS), 2018, pp. 14-17, doi: 
10.1109/APCCAS.2018.8605676.J. Clerk Maxwell, A Treatise on 
Electricity and Magnetism, 3rd ed., vol. 2. Oxford: Clarendon, 1892, 
pp.68–73.<br />
[2] M. H. Hamzah, A. B. Jambek and U. Hashim, "Design and analysis of 
a two-stage CMOS op-amp using Silterra's 0.13 μm technology," 
2014 IEEE Symposium on Computer Applications and Industrial 
Electronics (ISCAIE), 2014, pp. 55-59, doi: 
10.1109/ISCAIE.2014.7010209. <br />
[3] R. Nagulapalli, K. Hayatleh, S. Barker, B. N. K. Reddy and B. 
Seetharamulu, "A Low Power Miller Compensation Technique for 
Two Stage Op-amp in 65nm CMOS Technology," 2019 10th 
International Conference on Computing, Communication and 
Networking Technologies (ICCCNT), 2019, pp. 1-5, doi: 
10.1109/ICCCNT45670.2019.8944553. <br />
[4] M. P. Sarma, N. Kalita and N. E. Mastorakis, "Design of an low 
power miller compensated two stage OP-AMP using 45 nm 
technology for high data rate communication," 2017 4th International 
Conference on Signal Processing and Integrated Networks (SPIN), 
2017, pp. 463-467, doi: 10.1109/SPIN.2017.8049994. <br />
[5] E. Kargaran, H. Khosrowjerdi and K. Ghaffarzadegan, "A 1.5 v High 
Swing Ultra-Low-Power Two Stage CMOS OP-AMP in 0.18 µm 
Technology," 2010 2nd International Conference on Mechanical and 
Electronics Engineering, 2010, pp. V1-68-V1-71, doi: 
10.1109/ICMEE.2010.5558594. <br />
[6] A. Boni, "Op-amps and startup circuits for CMOS bandgap references 
with near 1-V supply," in IEEE Journal of Solid-State Circuits, vol. 
37, no. 10, pp. 1339-1343, Oct. 2002, doi: 
10.1109/JSSC.2002.803055. <br />

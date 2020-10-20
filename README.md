# README #

### HNP ###
Vertex Model simulations for HNP Gap Closure

### Authors / Contributors ###

* Michael F Staddon (University College London)
* Shiladitya Banerjee (Carnegie Mellon University)

#### created at the University College London / Carnegie Mellon University ####

### System Requirements ###

This system requires Surface Evolver 2.70 which can be downloaded at: http://facstaff.susqu.edu/brakke/evolver/evolver.html

### QUICKSTART GUIDE ###

Create a new directory for the simulation, containing the "*.fe" files, and the "wound_creation.secmd", parameters.inp", and "dynamics.secmd" files. 

The "*.fe" files are the main Surface Evolver files, containing the tissue geometry, energy definitions, and code to run the simulation for each type of simulation. This includes the WT simulation ("default.fe"), no crawling ("no_crawling.fe") and no purse-string ("no_pursestring.fe") simulations, along with simulations changing the gap or tissue geometry ("ellipse.fe" - elliptical gap and tissue, "smaller_boundary.fe" - elliptical gap and reduces boundary size, and "symmetric_gap.fe", symmetric gap geometry).

The "parameters.inp" file contains the system parameters. These are non-dimensional.

The "dynamics.secmd" file contains general simulation commands which numerically solve the dynamics of the system, and record simulation statistics.

The "wound_creation.secmd" file contains simulation commands for creating the gap.

Create folders "/images/" for simulation images, in the directory.

Run the simulation. On Windows double clicking the "wound_healing.fe" file should run it. On mac use the command line e.g.,
```
> evolver default.fe
```

During running, the simulation records statistics, such as the occurence of intercalations, the gap shape, and cell shapes. Once the simulation has completed, the following output files will have been created, where %s is the "output_name" variable:

* "shape_%s.csv" records the vertices along the gap

* "t1s_%s.csv" records the location and time of intercalations on the gap

* "rows_%s.csv" records the number of cells in each row away from the gap

* "cell_shape_%s.csv" records the cell shape in the first three rows of cells

* "tension_%s.csv" records the net tension (contractility + interfacial tension) on each edge


## Simulation Parameters ##

Simulation parameters may be changed in the "parameters.inp" file. Alternatively, values can be overwritten in the simulation file by writing them under the line "read "parameters.inp";" e.g.,
```
read "parameters.inp";
gap_tension := 3.14;
```
allowing several simulation files with different parameters in the same folder.

|Variable name              |Type   |Default value  |Description                        |
|-------------              |:----: |:-------------:|-----------------------------------|
|**Tissue properties**|||||
|kappa|float|1|Cell elastic modulus|
|A0|float|1|Preferred cell area|
|gamma|float|0.04|Cell contractility|
|pzero|float|3.5|Cell preferred shape index|
|gap_tension|float|0.14328|Gap purse-string tension|
|crawl_speed|float|0.01|Cell crawl speed|
|**Dynamic properties**|||||
|dt|float|3|Time step|
|viscosity|float|5|System viscosity|
|Lmin|float|0.1|Length under which T1s can occur|
|**Other properties**|||||
|random_seed|int|1|Random seed|
|output_interval|int|1|Timesteps between wound area recording|
|cell_output_interval|int|10|Timesteps between cell shape recording|
|img_output_interval|int|10|Timesteps between image recording|

### Reproduction instructions ###

By varying parameters and random seeds, the main results of the simulations can be reproduced using this code and analysing the output files.

### Contribution guidelines ###

* Email: shiladtb@andrew.cmu.edu

### Who do I talk to? ###

* Michael Staddon (michael.staddon.16@ucl.ac.uk)
* Shiladitya Banerjee (shiladtb@andrew.cmu.edu)

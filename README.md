# laserball-MC
Monte-Carlo simulations to measure the temporal and optical performance of a laserball calibration device. 

Originally written by Sammy Valder and Martti Nirkko, University of Sussex, (2022).

Modified by Lewis Bates, Supervisor: Dr Patrick Stowell, University of Sheffield (2023)

Updated configuration file provided by Imperial College London

Support from Alie Craplet and Dr Lauren Anthony, Imperial College London

## Dependencies
The simulations have been tested and are working using:

`gcc 5.4.0`
`root 5.34`

## Installation and running
First clone the repository

Update the parameters of the simulation using the configuration file `include/config.C`

Compile the code using ``g++ -g -o diffuser.exe diffuser.C `root-config --cflags --libs` `` - this should be done each time a change is made to the config file

Run the simulation using the executable created when compiling `./diffuser.exe`

## Configuration
The configuration file can be found at `include/config.C`. The default parameters in this repository reflect the real-life laserball calibration device developed at the University of Sussex for the scintillator phase of the SNO+ experiment. The parameters are split into sections:

**Independent variable** - this selects the variable of interest to change during simulation: 0 = the light injection point which can be displaced verticallay, 1 = glass microsphere concentration inside the scattering medium. These are the two main variables known to effect the optical and temporal performance.

**Global Constants** - Simulation constants: verbosity defining the level of detail printed whilst running, the number of photons to be simulated, and te number of bins defining the resolution of plots created.

**Laser** - Constants defining the characteristics of the light injection including intensity, numerical apeture, and wavelength.

**Diffuser Ball** - Constants realted to the physical properties of the diffusing flask. 

**Glass bubbles** - Constants defining the characteristics of the glass microspheres.

**Quartz rod** - Defining the length, diameter, and light injection offset (when kept constant) of thw quartz rod injector.

**Other** - Miscellaneous constants.

## Output Root File
Takes the form of a `ROOT` file with the name `diffuser.root`.

The contents of the root file can be examined using standard `ROOT` techniques, e.g. `root -l`, `new TBrowser()`, etc...

The root file will contain a number of histograms for each of the different values defined in the independent variable array `var[]`. These include:

`hesc` - A distribution of the time it takes for the photons to exit the diffuser flask once injected.

`hphi` - A distribution of the number of photons exiting the diffuser as a function of azimuthal angle.

`hcth` - A distribution of the number of photons exiting the diffuser as a function of polar angle.

`hang` - A 2D plot of the angular distribution of photons exiting the diffuser, combining polar and azimuthal information.

`htop` - A 2D plot of the temporal distribution of photons exiting the diffuser as a function of polar angle.

`htag` - A 3D plot of the temporal distribution of photons exiting the diffuser, combining the polar and azimuthal information.

The standard units used are: time [ns], cos(angle) [pi], light injection displacement [mm].

## Other Outputs

'XYZ.pdf' - A 3D plot of photon initial positions

'FinalXYZ.pdf' - A 3D plot of photon final positions

'Phi.pdf' - A plot of intial azimuthal distribution of photons

'Theta.pdf' - A plot of intial polar distribution of photons

'R-Theta.pdf' - A plot of intial polar distribution with respect to intial starting radius within injection rod

'Photon_Positions.csv' - Final positions and directions of photons, in columns: X, Y, Z, dx, dy, dz

## Citation
When publishing material that contains simulated data using this work, please ensure the code is referenced at all times.

You can reference this work using _TBC_. 

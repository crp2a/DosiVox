# DosiVox

**DosiVox** (version 1.0) is a free software (GNU GPL-3 licence, see above) based on the [Geant4](http://geant4.org) C++ libraries (Agostinelli *et al.*, 2003; Allison *et al.*, 2006; Allison *et al.*, 2016) and responding to the [Geant4 Software Licence](http://cern.ch/geant4/license) (version Geant4 10.1). It is developed by L. Martin, N. Mercier and S. Incerti at the IRAMAT-CRP2A\[1\] and the CENBG\[2\]. **DosiVox** allows constructing of voxelised models of archaeological objects and simulating the radioactivity for dose calculation with a Monte-Carlo approach (Martin *et al.*, 2015a; Martin *et al.*, 2015b; Martin 2015). These dose calculations can be used in the context of trapped charge dating. DosiVox uses Pilot Text Files (PTF) to set the simulation geometry and parameters, allowing the creation of a simulation by writing or editing a text file -> no skill in programming nor in Geant4 is required.

**DosiVox** runs on a Linux system and was developed on a Scientific Linux (Red Hat) virtual machine available at <http://geant4.in2p3.fr/spip.php?rubrique8>. As explained in Martin (2015): the alpha particle spectra (U_alpha, Th_alpha) are constructed from the NIST online database (version 5.0.0, October 2012; Kramida *et al.*, 2018); the beta particle spectra (Ubeta, Thbeta, Kbeta) and the gamma particle spectra (Ugamma, Thgamma) are based on the data from the NNDC (Brookhaven National Laboratory, USA <http://www.nndc.bnl.gov>) online database NuDat (version November 2009). In addition, the K gamma spectra (Kgamma) are constructed from NNDC online database NuDat (version January 2013; Kinsey *et al.*, 1996).

## Installation

You can download the software as a zip from this [URL](http://github.com/crp2a/DosiVox/archive/master.zip).

To download the package source as you see it on GitHub, for offline browsing, use this line at the shell prompt (assuming you have Git installed on your computer):

``` shell
git clone https://github.com/crp2a/DosiVox.git
```

Extract the archive of your home folder. Run the Scientific Linux virtual machine in a Windows or OS-X operating system and extract the archive in the virtual machine's Home folder. More explanations are available in the DosiVox Installation Guide.

## Usage
### Setting a simulation with PTF

Modify any PTF present in the DosiVox/data folder respecting the file's layout. The texts after the "#" symbol are comments describing the data of the line. All data must be separated by at least a space. Do not add a supplementary line unless it corresponds to data in agreement with the PTF layout. Detailed explanations are available in the DosiVox Manual.

### Launch a simulation in DosiVox

Open a terminal localised in the `DosiVox/` folder. Detailed explanations are available in the DosiVox Manual.

### Basic Commands

#### Run DosiVox (in a terminal open in the `DosiVox/` folder)

Run DosiVox without visualisation:
``` shell
build/DosiVox
```

Run the basic visualisation tool of DosiVox:
``` shell
build/DosiVox vis.mac
```

Run the visualisation of the DosiVox tool with the detectors displaying:
``` shell
build/DosiVox visdet.mac
```

WARNING: the displaying of detectors composed of a lot of geometrical elements can be costly for the computer resources 

Use `Ctrl + C` to abort the running simulation.

#### Run DosiVox under the DosiVox visualisation tool (in the "Session" box of the visualisation tool)

Run the simulation in the visualisation tool:
``` shell
control/execute 1run.mac
```

WARNING: to avoid over-consumption of the computer resources, the run under the visualisation tool is limited to 1000 particles emitted

Exit the visualisation tool (it will exit the DosiVox session too):
``` shell
exit
```

To move the displayed model, use the mouse left and scroll buttons on the display window and the keyboard arrows.  

### Results

Results of simulations are written as text files in the DosiVox/results folder with the prefix defined in the corresponding PTF. Suffixes corresponding to the detector and data type are added to the results files:

* `_error` for the listing of the killed particles,
* `_probe` for the recording of the probe detector,
* `_detectorN` for the N detector (N=1-> sub-voxelised, N=2-> single grain packing, N=3-> successive grain packings),
* `_grains` for the dose for each grain for detector 2 or 3. For detector 1, a 3D mapping is written as a text file in the `DosiVox/results/DoseMapping` folder. 

These results text files can be opened with standard spreadsheets. Detailed explanations are available in the DosiVox DosiVox Manual.

### Examples of PTF

Some examples of PTF are provided with DosiVox, in the `DosiVox/data` folder:

* `XPL0` creates two voxels filled respectively with clay and quartz. It simulates the alpha radioactivity of the U-series in the clay, allowing to record of the dose attenuation in the quartz with the probe detector.
* `XPL1` is a PTF for creating a simple voxelisation as a 3 x 3 x 3 grid and only the probe detector. Beta particles of the U-series are simulated.
* `XPL1bis` creates a similar model than `XPL1`, but with a 20 x 20 x 20 grid.
* `XPL2` creates a 20 x 20  20 voxels model with water, air and sediment-type materials to simulate gamma particles. Only the probe detector is defined
* `XPL3` defines a single random packing of grains as a detector in a 20 x 20 x 20 grid, in addition to the probe detector. Beta particles of the Th-series are simulated.
* `XPL3bis` uses the same configuration as `XPL3` but creates successive random packings of grains as detectors.
* `XPL4` defines a sub-voxelisation of 20 x 20 x 20 as detector in a voxel of the main 20 x 20 x 20 grid. Alpha particles of the U-series are simulated in this model.
* `XPL5` used the sub-voxelised detector to model a flint in a 120 x 250 x 101 sub-voxels grid. Beta particles of the U-series are simulated, and only the doses in the sub-voxels representing the flint are mapped.

Detailed explanations are available in the DosiVox Manual.

## technical support

* [Loïc MARTIN](loic.martin@u-bordeaux-montaigne.fr)		
* [Norbert MERCIER](norbert.mercier@u-bordeaux-montaigne.fr)

## References

Agostinelli *et al.*, 2003. Geant4—a simulation toolkit. *Nuclear Instruments and Methods in Physics Research Section A: Accelerators, Spectrometers, Detectors and Associated Equipment*, 506. <https://doi.org/10.1016/S0168-9002(03)01368-8>

Allison *et al.*, 2006. Geant4 developments and applications. *IEEE Transactions on Nuclear Science* 53. <https://doi.org/10.1109/TNS.2006.869826>

Allison, J., *et al.*, 2016. Recent developments in Geant4. *Nuclear Instruments and Methods in Physics Research Section A: Accelerators, Spectrometers, Detectors and Associated Equipment* 835, 186-225. <https://doi.org/10.1016/j.nima.2016.06.125>

Martin, L., Incerti, S., Mercier, N., 2015a. DosiVox: Implementing Geant 4-based software for dosimetry simulations relevant to luminescence and ESR dating techniques. *Ancient TL*, 33(1). <http://ancienttl.org/ATL_33-1_2015/ATL_33-1_Martin_p1-10.pdf>

Martin, L., Mercier, N., Incerti, S., Lefrais, Y., Pecheyran, C., Guerin, G., Jarry, M., Bruxelles, L., Bon, F., Pallier C., 2015b. Dosimetric study of sediments at the Beta dose rate scale: characterisation and modelisation with the DosiVox software. *Radiation Measurement*, 81, 134-141. <https://doi.org/10.1016/j.radmeas.2015.02.008>

Kinsey, R. R., Dunford, C. L., Tuli, J. K., Burrows, T. W., 1996. The NUDAT/PCNUDAT Program for Nuclear Data. 9th International Symposium of Capture Gamma-Ray Spectroscopy and Related Topics (Budapest, Hungary; October 1996). Data extracted from the NUDATdatabase, version Nov 2009 and Jan 2013 <https://www.nndc.bnl.gov/nudat2/reCenter.jsp?z=50&n=63>

Kramida, A., Ralchenko, Yu., Reader, J., NIST ASD Team, 2018. NIST Atomic Spectra Database (version 5.0.0) <https://physics.nist.gov/asd> [Nov 2012]. National Institute of Standards and Technology, Gaithersburg, MD. <https://doi.org/10.18434/T4W30F>

Martin, L., 2015. Caractérisation et modélisation d'objets archéologiques en vue de leur datation par des méthodes paléo-dosimétriques : simulation des paramètres dosimétriques sous Geant4. Thèse de doctorat en Physique des archéomatériaux. Pessac: Université Bordeaux-Montaigne, 304p. <http://www.theses.fr/2015BOR30055>

Rasband, W. S., 1997-2012. ImageJ, U.S. National Institutes of Health, Bethesda, Maryland, USA. <https://imagej.nih.gov/ij/>

Schneider, C. A., Rasband, W. S., Eliceiri, K. W., 2012. NIH Image to ImageJ: 25 years of image analysis. *Nature Methods*, 671. <https://doi.org/10.1038/nmeth.2089>

## License

DosiVox is provided under the terms and conditions of the DosiVox Software License (GNU GPL-3).

Neither the authors of this software system, nor their employing institutes, nor the agencies providing financial support for this work make any representation or warranty, express or implied, regarding this software system or assume any liability for its use. Please see the [LICENSE](LICENSE) file for the full disclaimer and the limitation of liability.

By using, copying, modifying or distributing the software (or any work based on the software), you agree to acknowledge its use in resulting acceptance of all terms of the DosiVox Software license.

1. Institut de Recherche sur les ArchéoMATériaux - Centre de Recherche en Physique Appliquée à l'Archéologie <http://www.iramat-crp2a.cnrs.fr>
2. Centre d'Etudes Nucléaires de Bordeaux Gradignan <http://www.cenbg.in2p3.fr>
